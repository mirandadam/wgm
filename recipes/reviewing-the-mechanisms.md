---
name: reviewing-the-mechanisms
description: "Use when someone asks to find unnecessary complexity, simplify the architecture, or review the mechanisms of the whole repository. It reports and changes nothing."
---

# Reviewing the mechanisms

A review of a whole repository for unnecessary complexity, to reduce how much system a person must understand without losing value that matters. Beyond [the standard](../STANDARD.md)'s "Lean towards simplicity":

- Complexity that exists because stakeholders impose conflicting needs may be justified, so make it explicit and contained.
- Weigh the cost of absence, not the frequency of use, because recovery, incident response, audit, migration and onboarding are rarely exercised and expensive to lose.
- Shifting effort or risk to another group is a trade, not a simplification, so write it down and ask first where it makes an earlier item of [the order](../STANDARD.md#the-order) worse, as [the standard](../STANDARD.md#the-order) says.
- Two artifacts that serve the same reader are a candidate for merging, and one that serves two readers badly for splitting.

What each group would notice losing, and so what must remain true:

- for the organization that owns it, business rules and requirements correctly implemented and traceable to their source, and value delivered at a sustainable cost;
- for those who hold it accountable (auditors, security, investigators after an incident), access control, traceability, leak prevention and evidence sufficient for an investigation;
- for the people who use it, usable, accessible, predictable workflows and clear paths for authoring, review, publishing and correction;
- for those who build and run it, a comprehensible architecture, straightforward testing and debugging, and reliable deployment, monitoring, backup, recovery and security.

Everything else may change.

Send three investigators with the same brief, each surveying every tracked file, because a finding two reach independently is likely real. Where none can hold the whole repository, read it part by part, as [reading-it-cold.md](reading-it-cold.md) says. For each significant source of complexity, ask what need it serves and whether there is a simpler way to serve it. Three answers are acceptable (already the simplest sound way, a simpler way exists, it serves no current need), and one more finding matters as much: a need with no sound implementation. Ground every conclusion in the repository, checking references, usage, tests and history before calling anything unnecessary, set aside stylistic issues, and do not invent work.

The report opens with where the complexity concentrates and why, then findings by likely impact, each stating what was observed and where, why it is unnecessary and for whom, what simpler alternative preserves the affected needs, and what would change the conclusion. Raise questions where the right simplification depends on intent the investigator cannot infer. A short list of load-bearing findings beats an exhaustive inventory. The report is where the review ends, and if whoever asked then wants the changes made, offer to write the plan.
