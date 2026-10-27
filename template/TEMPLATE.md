# What good means, here (template)

_This file alone is dedicated to the public domain under CC0 1.0 (https://creativecommons.org/publicdomain/zero/1.0/). Fill it in, and the result is yours._

Copy it beside your agent instructions as `WGM.md`, point your agent instructions at it, and delete this paragraph, the line above, and "(template)" from the title.

## Pointers

Each pointer is one line. It names where a fact is already written and does not restate it. A fact written nowhere else, such as what blocks a change, is written here. A line that does not apply says so. A line marked "(default: …)" has that answer unless you have a different one. Leave out any line whose default, or what the repository shows, is right.

- **wgm** is at …, a link to the public repository at a tag or commit, or the path of a whole copy, with its tag or commit where the copy keeps no git history.
- **Where things are written**: … where decisions are written (the specification), the as-built reference, the frozen analyses, observations of use among them, the insights drawn from those observations, and which part of the observations must stay outside the repository, the backlog, the plans (default: beside the agent instructions, with their logs), and, in a public repository, the private place for findings that carry a secret. `conventions/documents.md` describes each kind.
- **Good to use, here**: the devices and network the product is for, whether a throttled test or a hand measurement checks the budget for waiting on them, and the products its people already know. A product with no screen in a web browser says the line does not apply.
- **How use is observed**: whose use is observed, in which form (a moderated usability test, or field observation of real use), and how often. If no use is observed, say why.
- **Conventions in force**: which of the four checks in `conventions/static-checks.md` exist, and where (default: none). Where this file is silent, each file in `conventions/` holds unchanged. Write what differs and anything a recipe would otherwise have to infer, such as a number wgm sets as a default that you set differently, and why.
- **Standing reviews**: for each, what it hunts for, the recipe and the milestone that runs it, as `conventions/verification.md` describes (default: none).
- **What blocks a change**, and what only reports: … Look at the hooks, the pipelines, and the checks run by hand.
