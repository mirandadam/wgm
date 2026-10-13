---
name: reviewing-tests
description: "Use when the requester asks to review, audit, or strengthen tests, or whether a passing suite proves anything. It gives each test a verdict, then fixes the tests in verdict order."
---

# Reviewing tests

This recipe reviews a test suite when someone asks for it. Each test is read against the checklist in [conventions/tests.md](../conventions/tests.md), and the suite as a whole against that file's suite-level questions, whose answers are reported beside the table of tests. The same file says what to do with a weak test and how to simplify a suite.

## Working through a suite

List every test in the file, then fill in a row for each:

| Test | Claims to verify | Actually asserts | Verdict | Issue |
| --- | --- | --- | --- | --- |
| `test_create_user` | User is created and persisted | `status == 200` | WEAK | Never checks DB or response body |

| Verdict | Meaning |
| --- | --- |
| **STRONG** | Does what its name claims. Would catch a real defect. |
| **ADEQUATE** | Covers the main claim, misses edge cases or secondary effects. |
| **WEAK** | Passes while the feature it names is broken. |
| **BROKEN** | A silent skip, a tautology, an empty loop, a swallowed exception. Reports green regardless. |
| **MISLEADING** | The name claims something the assertions do not verify at all. |

Fix BROKEN and MISLEADING first, then WEAK, then ADEQUATE, because the work can stop before the end, and what is left undone should then be what does least harm. A test that passes whatever the code does hides defects, which is worse than missing some.
