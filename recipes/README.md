# The recipes

A recipe is a procedure you run when someone asks for one. Some are run at a named milestone as standing reviews, which [conventions/verification.md](../conventions/verification.md) describes.

## Choosing one

Each kind of request below goes to the cheapest recipe that answers it. A request of two kinds, neither of them to build or fix, goes to the cheaper of the two, except as the line on a change says, and its report names the part it did not answer and the recipe that would. A request to build or fix that also asks for a recipe gets both, in the order the work needs, such as a plan before the building and a review after it.

- A request to build or fix something: no recipe. The standard applies.
- A vague request about the tree: [`reading-it-cold.md`](reading-it-cold.md), a cold read, in which one reader with fresh context, told nothing of what to look for, reads the whole of what is under review.
- A vague request about what the session taught: [`learning-from-a-session.md`](learning-from-a-session.md).
- A request about what people get stuck on, or about something a user said, including a complaint about using the product that arrives as an issue in the tracker: [`observing-use.md`](observing-use.md).
- A request to choose between versions of a text, a rule or a design: [`choosing-between-versions.md`](choosing-between-versions.md).
- A request about which behaviors anybody decided, or about removing what nobody did: [`shrinking-what-was-built.md`](shrinking-what-was-built.md).
- A request to judge a change (a diff, a branch, or a document or plan being changed), whatever else it asks, fixing what it finds included: [`reviewing-a-change.md`](reviewing-a-change.md), which says when a cold read of it follows. A request to build as well gets both, as above.
- A request about whether the tests prove what they claim: [`reviewing-tests.md`](reviewing-tests.md).
- A request about whether a document lets its reader act: [`reviewing-documentation.md`](reviewing-documentation.md).
- A request for a plan, or about how something people will use should work, before anything is built: [`making-a-plan.md`](making-a-plan.md).
- A request for one of the four reviews named here, or about symptoms spread out that no single change explains: whichever of [`reviewing-the-experience.md`](reviewing-the-experience.md), [`reviewing-the-exposure.md`](reviewing-the-exposure.md), [`reviewing-the-mechanisms.md`](reviewing-the-mechanisms.md) and [`reviewing-the-premises.md`](reviewing-the-premises.md) has the matching entry in the Questions column of the table below. Run together, those that apply are "Reviewing everything".

[`reviewing-tests.md`](reviewing-tests.md), the report mode and the test-strength perspective of [`reviewing-a-change.md`](reviewing-a-change.md), and the concrete cases shown before a plan is approved in [`making-a-plan.md`](making-a-plan.md), have never been run, and [`reviewing-the-experience.md`](reviewing-the-experience.md), [`reviewing-the-exposure.md`](reviewing-the-exposure.md), [`observing-use.md`](observing-use.md) and the design that opens a plan in [`making-a-plan.md`](making-a-plan.md) have been run only in part. A recipe that has not been run is not known to work, so run it as written.

Each recipe opens with a frontmatter block, for assistants that load the whole tree as skills. Whether an assistant loads them that way or not, this section says which recipe a request goes to.

## What the recipes share

A run involves three roles. The requester, as [the standard](../STANDARD.md) defines the term, decides where `WGM.md` names nobody else as who may answer, and otherwise brings that person's answer. Whoever runs the recipe, a person or an assistant session, gives each investigator its brief (the written instructions it receives), verifies what the investigators find and, where the recipe ends in a revision, applies the fixes. An investigator is a separate reader that knows only its brief: another person, or an assistant session started for it. Such a reader is said to have fresh context.

Where a recipe sends investigators, it follows **Investigation** and **Verification** below. The assumptions after them apply to every recipe.

**Investigation.** Every investigator works against the tree under review and edits nothing in it. Nobody changes that tree while they read, so that every finding points at text that is still there when it is verified. Running the product and working on copies in a scratch directory are not edits. The product is run on an instance whose data nobody needs, or on a copy of the data kept only where that data may be, because a review that writes to data people use can lose it. Where the only instance holds data people use, it is only read, and a finding that needs a write there is reported unverified. An investigator deletes or changes only what it created, found by the identifiers it noted when it created them, never by a pattern such as a name prefix, because a pattern also matches what someone else created. Each brief asks the investigator to keep what it showed apart from what it inferred, and to say where it looked when a search found nothing, because whoever reads the report takes an inference, or an absence searched for in one place, for something shown.

Where a recipe uses more than one investigator, they work in parallel, each with fresh context, and none sees the others' findings. Each gets the perspective the recipe gives it, if any: what that investigator is told to look for, such as deletion or exposure. Where the recipe gives none, they all receive the same brief, and a finding more than one investigator reaches independently is more likely real than a finding only one reaches.

**Verification.** Whoever runs the recipe checks every finding against the repository before acting on it, and does not hand this check to anyone else, because investigators are often wrong, and another reader checking them can be wrong in the same way. A finding that rests on a measurement is verified by running the investigator's script again, or by making the measurement it describes, because the numbers a report quotes are the investigator's claim, not the verification. A finding weighs as much as the item of the order it harms, as [the standard](../STANDARD.md#the-order) says, and a violation of the repository's own rules harms the item the rule serves. Judge severity against the deployment the project actually has: a trade-off that is fine in a trusted, self-hosted setting is not a vulnerability.

Every recipe also assumes the following:

- It was asked for, by name or clearly enough that nothing cheaper would answer, or it is a step of a recipe that was. Nothing that runs often (a hook, a schedule, a pipeline) starts a recipe, because a recipe takes minutes and several readers, and run on every commit or push it would hold up each one and spend them on a question nobody asked.
- The requester's time is the scarcest in a run, because the run can do many things at once and the requester answers one question at a time. So, while the requester is there, the run first looks around and asks, in as few batches as it can, whatever would change its work. Then it works to the end: it sets aside each question that comes up, does everything that does not depend on the answer, and stops early only when nothing is left that can be done without one, as at each vote in `choosing-between-versions.md`. At the end it puts the questions set aside together, in one message, numbered, each with its recommendation. Every question explains what it asks about and what each answer would change, so that the requester can answer it without opening the change or reading back through the conversation. A question about a text also shows the passage as it reads now, in place, as the next bullet says of the text proposed. The questions keep their numbers until they are answered.
- Text proposed to the requester, at any point, has each of its claims checked where it can be shown true (the repository, the running product, the document it cites) before it is shown, and is shown in place, with its heading and the sentences around it, because a sentence that reads well alone can be wrong beside its neighbors.
- What the run tells the requester as a fact, such as a count, a diagnosis or a statement that something is done, is checked against the thing it describes, not against a log or an earlier report that says so. Where the thing described cannot be reached, the run says what the fact rests on.
- A fix changes only what its finding names, which for a fact is every place in what the run reviews that states it, as step 4 of [reviewing-a-change.md](reviewing-a-change.md) says of a change. Moving text, or widening what a sentence covers, is a finding of its own, verified like any other, because a fix that reaches past its finding is where the next defect most often comes from.
- A fix to how a text is written changes how the text says something, never what it says, beyond cutting what the reader does not use. The text's numbers, names, commands, paths and quotations, the strength of each obligation ("must", "should", "may", "optional") and the position the text takes stay as they are, and the fix adds no fact the text did not contain. Nor does it change a structure an outside authority sets for the text, such as the fields of a procurement form, the sections an audit reply must follow or the layout of a slide template. Where the fix would need a fact the text lacks, or a change to that structure, or the text can be read two ways, the fix is a question, asked where the recipe asks its questions, never a guess. Before the fixed text is shown or applied, it is compared with the text it replaces, item by item from that list, and checked for added facts. Correcting what a text says, such as a wrong command, is a finding of its own, verified like any other. An invented text, such as `template/EXAMPLE.md`, is settled by whoever writes it.
- A finding in a passage someone else wrote and answers for, such as a colleague's section of a report, is handled as in a change that is not the requester's in [reviewing-a-change.md](reviewing-a-change.md): it is reported and given to each later full round, no fix is applied to it unless asked, and while it is not fixed it does not keep the rounds going.
- The run writes as it goes. A decision or a declined finding is written when it is taken, as [conventions/decisions.md](../conventions/decisions.md) says. A question is written when it is set aside, and the state of the work (what is done, what is under way, the next step) whenever it changes, both in the plan, or, where there is none, in a file where `WGM.md` says plans live. Where the plan is what the run reviews, or sits in the tree investigators read, these records and the report go in a separate file where `WGM.md` says plans live. So placed, they are not edits to what the run reviews. Each is written before the run acts on it, so a session can stop at any moment, and one whose history was replaced by a summary reads what is written and goes on from it.
- In a public repository, a finding that carries a secret or a way in, the report that holds it, and any question set aside or finding declined that carries one are kept privately, as [reviewing-the-exposure.md](reviewing-the-exposure.md) says of its own findings. This holds whichever recipe found them and even where `WGM.md` names a public place for findings, because each is a way in until it is fixed.
- In any repository, a credential that may still work is reported to the requester, to be revoked, because removing it from the text leaves it in the history.
- The run decides by itself, except where:
  - a fix would reverse a written decision or add or change a behavior or a choice of a kind that [needs an answer](../conventions/decisions.md#what-needs-an-answer);
  - a finding cannot be verified either way and acting on it is expensive to undo;
  - the request itself is wrong;
  - the requester's answer can be read two ways that differ in what the change does;
  - it is about to act on a decision it cannot find where decisions are written;
  - step 3 of [reviewing-a-change.md](reviewing-a-change.md) sets a finding aside as a question;
  - it needs to start the product, give it data or drive it, and finds nothing written that says how and works when tried;
  - the bullet above on a fix to how a text is written makes the fix a question.

  Those are the questions it sets aside.

- The local facts it needs are in `WGM.md`, beside the agent instructions. The recipe itself is not edited, because `WGM.md` is where every run looks for them, and an edit would be lost at the next update. Most recipes also run without `WGM.md`, or with it not yet filled in. They then work from the repository itself and say which facts they had to infer.
- A copy of wgm that a repository uses and does not write, wherever it is kept or linked, is not part of what a run reviews, because it is not that repository's work. A problem found in it, or a proposal for it, is stated without the repository's names, code or data and given to the requester to report as an issue on wgm, because the issue is public.

## The recipes side by side

| Recipe | Takes as given | Questions | Costs | Ends in |
| --- | --- | --- | --- | --- |
| `reading-it-cold.md` | nothing | whether the whole (a tree, or a change and its texts) still holds together | one reader, one pass | a ranked opinion |
| `reviewing-a-change.md` | everything but the change | one change: code, a document, or a plan | two rounds that read the whole change, with one or three investigators each. Then up to two rounds on the fixes, one investigator each, unless asked for more, and one round on the fixes that follow the answers. For a text its users read, a cold read and a round on its fixes. | a revision, or a report for a change that is not the requester's |
| `reviewing-the-experience.md` | what the product is for, and the mechanisms | what the product is like to use | parallel perspectives, and a run of the real product | a report |
| `reviewing-the-exposure.md` | what the product is for, and the rules of who may see what | who can see or change what they should not | parallel perspectives, and a run of the real product where one runs | a report |
| `reviewing-the-mechanisms.md` | what the product is for | the mechanisms that serve it | parallel investigators, one pass | a report |
| `reviewing-the-premises.md` | nothing | whether what the product is for holds | parallel investigators, one pass | a report |
| `shrinking-what-was-built.md` | the requester's decisions | which behaviors of one area anybody decided | one investigator per area, and a search for use | three lists and questions |
| `reviewing-tests.md` | the code the tests are for | whether a passing test proves what it claims | a checklist and a verdict per test | a revision, in verdict order |
| `reviewing-documentation.md` | the product the documents describe | whether a document lets its reader act | one investigator per document set, a row per section | a revision, in verdict order |
| `observing-use.md` | what the product is for | what people get stuck on | the product in use, observed and written down | an observation file and insights |
| `making-a-plan.md` | the request | how it will be built, and, for a change people will use, its design | questions to the requester, then a review of the plan | a plan |
| `choosing-between-versions.md` | the requester's preference | something easier to recognize than to describe: a rule, a text, interface text, a mockup | two versions at a time | the version the requester prefers, and a log of every choice |
| `learning-from-a-session.md` | the session's memory | what a session that ran recipes teaches about the recipes, the conventions and the standard | run by the session that did the work, before it ends | proposals |

## Reviewing everything

No separate recipe exists for it. Once a cold read has been done and the requester wants more depth, run together whichever of `reviewing-the-experience.md`, `reviewing-the-exposure.md`, `reviewing-the-mechanisms.md` and `reviewing-the-premises.md` apply. Start with many hypotheses, and keep only what the repository supports. Each recipe has its own report shape when it runs alone, but run together, they produce one report:

1. **The verdict on the core idea**: is the project's central bet sound?
2. **Findings ranked by importance**, each with file and line, why it matters, and what to do instead. Grouped by theme, not by file.
3. **What is genuinely good**, named so that later changes keep it.
4. **What you would not do**: tempting changes that would be over-engineering here, with the reason.
5. **Decisions that belong to the requester**: where a finding implies a choice, ask.
6. **A suggested order**, highest value for the cost first.

A short list of load-bearing findings beats an exhaustive inventory. The report is where the review ends. If the requester then wants execution, offer to write the plan.
