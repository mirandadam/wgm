# Verification

This file says how a project shows that it is "Trustworthy", the first item of [the order](../STANDARD.md). Each required behavior is verified, and kept verified, by the strongest of three tiers that can reach it: a mechanical check if one can, otherwise a deterministic test, and a review only where neither can. Test behavior, not implementation, because a test of the implementation fails when the code changes and the behavior does not, and can pass when the behavior breaks. How to write and simplify tests is in [tests.md](tests.md).

## The three tiers

| Tier | Mechanism | Verifies | Gating |
| --- | --- | --- | --- |
| **Mechanical** | lint, format, type and reference checks, build | Syntactic and structural invariants, cheaply, on every change | **Blocks** |
| **Deterministic test** | unit, integration, end-to-end | Behavior and contracts: status, shapes, stored effects, flows | Critical subset **blocks**; full suite **reports** |
| **Review** | adversarial investigators or a human rubric | Judgment, and that something is absent (no leak, no path around a check) | **Never gates**; surfaces findings |

A review is the fallback for what cannot be automated, never an escape from a test that could exist, because a review runs only at its milestone and a test on every change. A behavior whose strongest tier is review is checked by the standing review that hunts for it, and is not written off as unverified, because nobody looks again at what was written off. Where there is nowhere to stop a change (a prose tree, or one maintainer pushing straight to the deployed branch), every check runs and reports, and `WGM.md` says so. A person approving a merge request is a gate of its own, which `WGM.md` lists under what blocks a change.

Only the cheap, deterministic, high-signal checks block, because a slow check holds up every change, a wrong one stops changes that are fine, and people soon learn to override both. When in doubt, a check reports. Where there is a test suite, its coverage and run time are measured, and an unexplained drop in coverage, or growth in run time, is a finding, though deleting tested code lowers coverage and is still a good change.

## Steps that delete, replace or rebuild stored data

Count what a step that deletes, replaces or rebuilds stored data or a stored document was meant to change, before the step and after it, and look again at what depended on what the step changed, because such a step can end without an error and still have changed nothing, or more than it should.

## What the runtime layer owes you

Where the product runs as a service, it detects while running what the tiers did not catch: structured logs in which a correlation id and the acting principal are fields, not words in a message string, because a field can be searched. Few alerts, on the highest-signal failure modes only, because people stop reading alerts that fire for nothing.

## The review tier

A standing review is a recipe a person runs at a named milestone: a release, a change to what the product is for, a change about to be merged in an area that has failed before. `WGM.md` lists them, each with what it hunts for, the recipe and its milestone, which is an event the project already marks, because a milestone that exists only in `WGM.md` never arrives. A review whose reports show a year of runs without a finding is a candidate for dropping, and dropping one that protects "Trustworthy" [needs an answer](decisions.md#what-needs-an-answer).

The findings a run defers go to the backlog, and its report, written even when it found nothing, is kept as a frozen analysis that gives the date it ran, unless `WGM.md` names another place, and one that holds a secret is kept as [recipes/README.md](../recipes/README.md#what-the-recipes-share) says. A review that cannot fail found nothing. Its findings are verified against the tree, as [recipes/README.md](../recipes/README.md) says, then fixed now, deferred or declined, and a finding that can become a mechanical check or a regression test moves to that tier and leaves the review.
