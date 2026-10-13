---
name: reviewing-the-premises
description: "Use when the requester asks to challenge the premises, question whether the project should exist in this form, or review the value proposition, users, requirements, or constraints. It reports and changes nothing."
---

# Reviewing the premises

A review that challenges what a repository takes as given: the value it claims to deliver, the people it claims to serve, the requirements it claims to meet, and the constraints it assumes. [reviewing-the-mechanisms.md](reviewing-the-mechanisms.md) holds the needs fixed and questions the mechanisms, but this recipe questions the needs themselves. Find the premises that would do the most damage if wrong, and establish for each whether the repository supports it, contradicts it, or is silent. Investigators say whether the repository supports each premise, and the requester settles it.

## Principles

1. **Everything can be questioned.** Nothing is exempt for being old, documented, or agreed.
2. **Alternatives are probes, not proposals.** Imagining a substitute tests a premise but does not end in a redesign.
3. **Absence is evidence.** What is not tested, measured, documented or questioned shows which premises nobody is checking.
4. **The repository is partial evidence.** It shows what the system assumes, not whether anyone gets value.

## What is questioned

| Layer | The question | What to look for |
| --- | --- | --- |
| Value proposition | Why does this exist, and what if it stopped? | What the system does versus what its documentation says it is for; capabilities with no evident use; the cheapest substitute, and what it would fail to provide |
| Users and stakeholders | Are the assumed users the real ones? | Groups served that nobody lists, and groups listed that nothing serves |
| Requirements | Which requirements are real? | Stated requirements with no implementation; implementations with no stated requirement; requirements the implementation quietly contradicts |
| Constraints | Which constraints still hold? | Assumptions hardcoded but written nowhere: one tenant, one language, one region, one deployment shape, a limit chosen years ago |
| Architectural bets | Would this be built this way today? | Build-versus-buy, platform and data-model choices, boundaries that look inherited rather than chosen |
| Success criteria | How would anyone know it is working? | Metrics, tests and feedback paths that exist; premises with no way to be proven wrong |

## Procedure

Send three investigators with the same brief, each reading the whole repository, because a finding two of them reach independently is likely real. That needs each to hold the whole repository, so where none can, read it part by part, as [reading-it-cold.md](reading-it-cold.md#when-not-to) says.

1. Read the repository as an outsider: what does the system do, for whom, and why, judged from the artifacts alone. Note where the answer is unclear or two artifacts disagree.
2. For each layer, state the premise, make the strongest case for it, and keep only the challenges that survive that case. Where the repository is silent, say what evidence would settle it.
3. Invert: describe how this project would turn out to have been wasted effort, and check whether any of it is already visible.
4. Set aside challenges whose resolution would change little.

## Report

Open with the two or three premises the project rests on and how well each is supported. Then challenges, ranked by consequence, each stating the premise and where it is implied, the strongest case for it, what the repository shows, what breaks if it is wrong, and who can settle it. Mark each as a finding (the repository contradicts the premise) or a question (the repository is silent). Close with the premises that held, so they are not questioned again without new evidence.
