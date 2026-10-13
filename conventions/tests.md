# Tests

This file says what a passing test must prove, and how to write, check and simplify tests, for any suite, whether unit, integration or end-to-end (E2E), in any language or framework. It is read whenever tests are written, and [recipes/reviewing-tests.md](../recipes/reviewing-tests.md) runs it as a review. The examples are from an HTTP service with a database, but the rules are not.

## Core principle

A passing test must mean the behavior it names actually works. This is "Trustworthy", the first item of [the order](../STANDARD.md): the product does what it claims, and the suite is the evidence.

## The per-test checklist

### 1. Could the test pass while the behavior it names is broken?

Read the name, then read only the assertions: if they all pass, has the claimed behavior been proven? If you replaced the implementation with a hardcoded value, or removed a validation or an auth check, would any assertion fail?

Walk the test assuming the feature is completely broken: empty data, wrong values, missing fields. Would anything catch it? Four patterns pass regardless:

- **Silent skips.** A loop searches for a record, finds nothing, ends, and no assertion fires. Assert the record was found before asserting on it.
- **Empty collections.** Zero iterations means zero assertions. Assert the collection is non-empty before looping.
- **Overly broad matching.** `expected_word in long_string`, where the word also appears in boilerplate or headers.
- **An absent rival.** A test that one value wins over another (a fallback, a precedence, a tie-break) with the other value not present. It passes whether the rule works or the winner was simply the only thing there. Put the rival in.

**Red flags:** asserting only on status codes, on types instead of values, or that _something_ was returned instead of _what_.

### 2. Is the mock boundary appropriate?

Mocks belong at the edges: external APIs, databases, file systems, clocks. A test that mocks internal functions of the module under test is hiding behavior, not isolating it.

### 3. Are the inputs realistic and distinctive?

Non-trivial: special characters, unicode, realistic lengths. Distinctive: if `title` and `description` are both `"test"`, a swap is invisible. Non-default: if the default language is `"en"`, setting `"en"` proves nothing.

### 4. Does it cover the full claimed path?

For integration and E2E, trace the data flow. A test claiming "write via A, read via B" writes distinctive values, reads back through B rather than a shortcut like querying the database directly, and asserts the values written rather than structural validity. Reach a runtime state the way a user does: **do not fabricate it** (DOM injection, route mocks, manual class additions, fixture-only flags) when the real flow is available.

### 5. Does it cover the sad path?

Invalid input produces the specific expected error: assert `422`, not `!= 200`, which also passes on a crash. Forbidden operations are rejected rather than "completed". Missing resources return the right error, not a silent empty response. One validation error, one auth failure and one edge case are worth more than five variations on the happy path.

### 6. Is it isolated and deterministic?

Would it pass alone, in a different order, in parallel? Does it set up and tear down its own data? Does it wait for async work, or hope?

### 7. Will the failure output diagnose the problem?

`assert r.status_code == 200` gives `422 != 200`, which leaves you unable to tell a test bug from a code bug, so assertion messages should carry the response body, the payload and the record id. Capture state on failure from a fixture rather than from print statements added by hand, and set test logs more verbose than production.

## Suite-level health

### Is each test needed?

If you deleted it, would a bug go undetected that no other test catches? If not, it is weight. Ten tests over one path to one outcome are one test, and tests that execute lines rather than verify behavior (getters, config loading, pass-throughs) are none.

### Is the test at the right level?

The pyramid is a cost model, not a dogma: unit cheap, integration moderate, E2E expensive, slow and flaky. For each E2E test, could the core assertion be proven by a cheaper one? If so, push it down and slim what remains to a smoke check. E2E should verify what nothing cheaper can: wiring, infrastructure, cross-service contracts, whole user flows.

### How long does the suite take?

Measure before cutting: run with per-test timing and look at the slowest handful, which own most of the wall clock. Then replace fixed sleeps with settled-state waits, and share expensive setup across a group, with isolation real enough that it cannot leak: rolled-back transactions, namespaced resources, separate tenants.

## When you find a weak test

If the behavior is gone, propose deleting the test. Otherwise, strengthen it. If the strengthened test fails because the code is wrong, keep the weak test and add the strengthened one marked `xfail` with a reason and a tracking link, so the gap stays visible and the weak test still runs. Flag it, and do not delete it unilaterally, because a weak test still checks part of a behavior the product has, which makes it a safeguard of "Trustworthy", and removing one [needs an answer](decisions.md#what-needs-an-answer). Never weaken a test to make it pass. A test coupled to one reproduction rather than the category of bug breaks on any incidental change, so rewrite it for the category.

## When you simplify a suite

Simplify _structure_, never _assertions_: a simplified test can pass while exercising less, with no red signal.

- **Allowed:** dedupe fixtures, merge near-identical cases into a parametrized one, retire a superseded suite after folding its live coverage into an active one, delete tests for removed features.
- **Forbidden:** relaxing an assertion, broadening an expected value, widening a status check (`== 200` → `!= 500`), wrapping assertions in `try/except`, dropping a sad path or an edge case.

**The check:** measure coverage before and after, and name the diff. A drop is fine when the commit justifies it, as for the code of a removed feature. An unexplained drop means a behavior was lost, so the drop is a finding and the change is not a cleanup.

Back-filling coverage for behavior that already shipped untested is additive, not simplification, so it goes in a commit of its own, where it does not hide a simplification's drop in coverage. A regression test shipping with a fix is part of that fix.
