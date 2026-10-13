---
name: reviewing-the-mechanisms
description: "Use when the requester asks to find unnecessary complexity, simplify the architecture, or review the mechanisms of the whole repository. It reports and changes nothing."
---

# Reviewing the mechanisms

A review of a whole repository for unnecessary complexity, across every tracked file. The goal is to reduce how much system a person must understand and interact with, without losing value that matters.

## Principles

Beyond what [the standard](../STANDARD.md) says under "Lean towards simplicity":

1. **Localize essential complexity.** Complexity that exists because stakeholders impose genuinely conflicting needs may be justified. Make it explicit and contained.
2. **Low frequency is not low value.** Weigh the cost of absence, not the frequency of use, because recovery, incident response, audit, migration, rollback and onboarding are rarely exercised and expensive to lose.
3. **Do not trade silently.** Shifting effort or risk to another group in the table below is a trade, not a simplification. Write it down, and ask first about one that makes an earlier item of [the order](../STANDARD.md#the-order) worse, unless [trading without asking](../conventions/decisions.md#trading-without-asking) allows it.
4. **Each artifact serves its own audience.** Two artifacts that serve the same reader are a candidate for merging, and one that serves two readers badly is a candidate for splitting.

## What must be preserved

The table says what each group would notice losing. Everything else may change.

| Who | What must remain true |
| --- | --- |
| **The organization that owns it**: management, product and requirements owners | Business rules and requirements correctly implemented and traceable to their source; the system keeps delivering its value at a sustainable cost |
| **People who hold it accountable**: auditors, security, regulators, investigators after an incident | Access control, traceability, leak prevention, and evidence sufficient for an investigation |
| **People who use it**: end users, content authors and maintainers | Usable, accessible, predictable workflows; clear paths for authoring, review, provenance, publishing and correction |
| **People who build and run it**: developers, administrators, infrastructure maintainers | Comprehensible architecture; straightforward onboarding, testing and debugging; reliable deployment, monitoring, backup, recovery and security |

## Procedure

Send three investigators with the same brief, each surveying every tracked file, because a finding two of them reach independently is likely real. That needs each to hold the whole repository, so where none can, read it part by part, as [reading-it-cold.md](reading-it-cold.md#when-not-to) says.

1. Survey every tracked file: implementation, architecture, user and developer workflows, documentation, configuration, deployment, and the concepts tying them together.
2. For each significant source of complexity, ask **what need does this serve, and is there a simpler way to serve it?** Three answers are acceptable (already the simplest sound way, a simpler way exists, it serves no current need), and one more finding matters as much as a simpler way: a need with no sound implementation. Do not invent work.
3. Ground every conclusion in the repository: check references, usage, tests and history before calling anything unnecessary.
4. Set aside stylistic issues. Report only what would materially change how much system someone must understand.

## Report

Open with where the complexity concentrates and why. Then findings, by likely impact, each stating what was observed and where, why it is unnecessary and for whom, what simpler alternative preserves the affected needs, and what would change the conclusion. Raise questions where the right simplification depends on intent the investigator cannot infer.
