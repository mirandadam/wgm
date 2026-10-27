# Tests

This file says what a passing test must prove, and how to write, check and simplify tests, for any suite in any language. It is read whenever tests are written, and a review of a suite reads each test against it and fixes the weakest first. The examples are from an HTTP service with a database, but the rules are not.

A passing test must mean the behavior it names actually works. This is "Trustworthy", the first item of [the order](../STANDARD.md): the product does what it claims, and the suite is the evidence.

## The per-test checklist

1. **Could the test pass while the behavior it names is broken?** Read the name, then only the assertions. If you replaced the implementation with a hardcoded value, or removed a validation or an auth check, would any assertion fail? Four patterns pass regardless: a silent skip (a loop finds nothing and no assertion fires), an empty collection (zero iterations, zero assertions), overly broad matching (`expected_word in long_string`), and an absent rival (a test that one value wins over another, with the other value not present). Asserting only on status codes, on types instead of values, or that _something_ was returned is a red flag.
2. **Is the mock boundary appropriate?** Mocks belong at the edges: external APIs, databases, file systems, clocks. A test that mocks internal functions of the module under test is hiding behavior, not isolating it.
3. **Are the inputs realistic and distinctive?** Special characters, realistic lengths, and values that differ from one another and from the defaults, because if `title` and `description` are both `"test"`, a swap is invisible, and setting a field to its default value proves nothing.
4. **Does it cover the full claimed path?** For integration and end-to-end, write distinctive values, read them back through the real path rather than a shortcut, and assert the values, not structural validity. Reach a runtime state the way a user does, not by fabricating it, when the real flow is available.
5. **Does it cover the sad path?** Invalid input produces the specific expected error: assert `422`, not `!= 200`, which also passes on a crash. Forbidden operations are rejected rather than "completed", and missing resources return the right error, not a silent empty response. One validation error, one auth failure and one edge case are worth more than five variations on the happy path.
6. **Is it isolated and deterministic?** Would it pass alone, in another order, in parallel? Does it set up and tear down its own data, and wait for async work rather than hope?
7. **Will the failure output diagnose the problem?** `422 != 200` leaves you unable to tell a test bug from a code bug, so assertion messages should carry the response body, the payload and the record id, state is captured on failure from a fixture, and test logs are more verbose than production.

## Suite-level health

If deleting a test would let no bug through that no other test catches, it is weight, so ten tests over one path to one outcome are one test, and tests that execute lines rather than verify behavior are none. The pyramid is a cost model, so for each end-to-end test, ask whether the core assertion could be proven by a cheaper one, and keep end-to-end for what nothing cheaper can verify, such as wiring and whole user flows. Measure before cutting run time, with per-test timing, because the slowest handful own most of the wall clock. Then replace fixed sleeps with settled-state waits and share expensive setup across a group, with isolation real enough that it cannot leak.

## When you find a weak test

If the behavior is gone, propose deleting the test. Otherwise strengthen it, and if the strengthened test fails because the code is wrong, keep the weak test running and add the strengthened one marked `xfail` with a reason and a tracking link. Do not delete a weak test that is the only check of part of a behavior the product has, because that makes it a safeguard of "Trustworthy", and removing one [needs an answer](decisions.md#what-needs-an-answer). Never weaken a test to make it pass. A test coupled to one reproduction rather than the category of bug breaks on any incidental change, so rewrite it for the category.

## When you simplify a suite

Simplify _structure_, never _assertions_, because a simplified test can pass while exercising less, with no red signal. Allowed: dedupe fixtures, merge near-identical cases into a parametrized one, retire a superseded suite after folding its live coverage into an active one, delete tests for removed features. Forbidden: relaxing an assertion, broadening an expected value, widening a status check, wrapping assertions in `try/except`, dropping a sad path or an edge case. Measure coverage before and after and name the diff, because an unexplained drop means a behavior was lost, so the change is not a cleanup. Back-filling coverage for behavior that shipped untested goes in a commit of its own, and a regression test shipping with a fix is part of that fix.
