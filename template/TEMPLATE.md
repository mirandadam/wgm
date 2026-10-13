# What good means, here (template)

_This file alone is dedicated to the public domain under CC0 1.0 (https://creativecommons.org/publicdomain/zero/1.0/). Fill it in, and the result is yours._

Copy it beside your agent instructions as `WGM.md`, point your agent instructions at it, and delete this paragraph, the line above, and "(template)" from the title.

## Pointers

Each pointer is one line. It names where a fact is already written and does not restate it, so what the agent instructions already say is not repeated here. A fact written nowhere else, such as what blocks a change, is written here. A line that does not apply says so. A line marked "(default: …)" has that answer unless you have a different one, and says "the default" where it holds. Every other line needs yours.

- **wgm** is at …, a link to the public repository at a tag or commit, or the path of a whole copy. For a plain copy, which keeps no git history, this line also gives its tag or commit, because the recipes change from one commit to the next.
- **Who may answer**: … (default: whoever asks). Name someone when the person who asks may not decide for the product, as in a team whose manager decides its scope, or when people outside the team can start a run, as with a bot that a comment starts, because otherwise whoever asks can approve anything that needs an answer, the removal of a safeguard included.
- **Where things are written**: … for each of these the project keeps: the directives (the vision and the specification among them, which hold what the product is for, its vocabulary and its rules), the as-built references, the frozen analyses (observations of use among them), the insights drawn from observations, the recordings and quotations of observations (outside the repository), the backlog (where findings go), the plans (default: beside this file) and any agent instructions besides those that point here. `conventions/documents.md` describes the kinds of document, the backlog and plans.
- **Good to use, here**: the devices and network the product is for, whether a throttled test or a hand measurement checks the budget for waiting on them, and the products its people already know. The standard's section "What good to use asks for" reads this line, and a product with no screen in a web browser says the line does not apply.
- **How use is observed**: whose use of the product is observed, in which of the two forms `recipes/observing-use.md` describes, and how often or at which milestones. If no use is observed, say why. A blank here is a finding in every review of the experience.
- **Conventions in force**: which of the four checks in `conventions/static-checks.md` exist, and where (default: none). For the rest, where this file is silent, each file in `conventions/` holds unchanged. Write here what differs from it, the commit convention where the history does not show one, and anything a recipe would otherwise have to infer, such as a review procedure of your own, or a number wgm sets as a default that you set differently, why, and who answered.
- **What blocks a change**, and what only reports: … To find out, look at the hooks, the pipelines, and the checks that exist but are run by hand.

## Standing reviews

Each standing review takes one row, as the review tier in `conventions/verification.md` describes standing reviews. A review whose findings and report must not go anywhere the public can read, as those of a review of exposure in a public repository, gets, under the table, a line naming the private place they go.

| Review | Hunts for | Recipe and perspectives | Milestone |
| ------ | --------- | ----------------------- | --------- |
|        |           |                         |           |
