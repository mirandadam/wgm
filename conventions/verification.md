# Verification

This file says how a project shows that it is "Trustworthy", the first item of [the order](../STANDARD.md). Each required behavior is verified, and kept verified, by the strongest of three tiers that can reach it: a mechanical check if one can, otherwise a deterministic test, and a review only where neither can. Where the product runs as a service, logs and alerts also detect fast what slipped past those tiers.

## Core principle

**Verify each requirement with the strongest tier that can actually reach it, and shrink what must be verified first** (code that does not exist cannot break). Test behavior, not implementation, because a test of the implementation fails when the code changes and the behavior does not, and can pass when the behavior breaks. How to write and simplify tests is in [tests.md](tests.md), and [recipes/reviewing-tests.md](../recipes/reviewing-tests.md) reviews them.

## The three tiers

A tier weaker than the strongest one that reaches a behavior may check it too. A review is the fallback for the genuinely unautomatable, never an escape from a test that could exist, because a review runs only at its milestone, and a test runs on every change. Do not record a behavior as permanently unverified when a review could own it, because nobody looks again at what was written off. A behavior whose strongest tier is review is checked by the standing review that hunts for it, at its milestone.

| Tier | Mechanism | Verifies | Gating |
| --- | --- | --- | --- |
| **Mechanical** | lint, format, type and reference checks, build | Syntactic and structural invariants, cheaply, on every change | **Blocks** |
| **Deterministic test** | unit, integration, end-to-end | Behavior and contracts: status, shapes, stored effects, flows | Critical subset **blocks**; full suite **reports** |
| **Review** | adversarial investigators or a human rubric | Judgment, and that something is absent (no leak, no path around a check) | **Never gates**; surfaces findings |

The gating column assumes there is somewhere to stop a change. Where there is none (a prose tree with nothing to build, or one maintainer pushing straight to the deployed branch), every check runs and reports, and `WGM.md` says so. The review tier is a recipe's run, but a person approving a merge request is a gate of its own, which `WGM.md` lists under what blocks a change.

## Lean hard gates

Only the cheap, deterministic, high-signal checks block, because a slow check holds up every change, a wrong one stops changes that are fine, and people soon learn to override both. When in doubt, a check reports. Coverage is measured: record a baseline, and **warn** below it. The baseline is not a minimum, because deleting tested code lowers coverage and is still a good change. A justified drop is fine, but an unexplained one is a finding.

**The suite's run time is a cost too.** Measure how long the suite takes, record it, and warn when it grows. [tests.md](tests.md#how-long-does-the-suite-take) says what to do about it.

## What the runtime layer owes you

The runtime layer detects, while the product runs, what the tiers did not catch. It applies only to what runs as a service. A library, a document or a paper has none.

- **Structured logs with context.** A correlation id and the acting principal are first-class fields, not words interpolated into a message string, because a field can be searched and filtered, and a word inside a sentence cannot.
- **Few alerts, on the highest-signal failure modes**, and nothing else at first, because people stop reading alerts that fire for nothing, and then miss the one that matters. The metrics almost always exist already, so the alerts are the work.

## The review tier

A standing review is a recipe a person runs at a named milestone: a release, a change to what the product is for, a change about to be merged in an area that has failed before, the end of a stretch of work. It names what it hunts for, the recipe and perspectives it runs, and its milestone. The repository's `WGM.md` lists the standing reviews in a table, one row each. Its milestone is an event the project already marks, such as a release, because a milestone that exists only in the review's row never arrives. A standing review in your `WGM.md` is a candidate for dropping when its reports show a year of runs without a finding, because it may hunt for a mistake nobody makes any more. Dropping one that protects "Trustworthy" removes a safeguard, which [needs an answer](decisions.md#what-needs-an-answer).

The findings a run defers go to the backlog, and its report, which names the review and is written even when the run found nothing, is kept as a frozen analysis that gives the date it ran. Where `WGM.md` names another place for a review's findings and report, they go there instead. In a public repository, a review of exposure keeps its findings and report private, even where `WGM.md` names a public place for them, as [recipes/reviewing-the-exposure.md](../recipes/reviewing-the-exposure.md) says.

A review that cannot fail found nothing. It never gates. Instead, its findings are verified against the tree, as [recipes/README.md](../recipes/README.md) says, then fixed now, deferred or declined. A finding that can become a mechanical check or a regression test moves to that tier and leaves the review. A finding that would reverse a written decision, or make a choice that [needs an answer](decisions.md#what-needs-an-answer), is put as a discrete diff and asked about.

How many investigators a standing review sends, and with which perspectives, is its recipe's to say.
