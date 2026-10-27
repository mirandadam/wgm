---
name: reviewing-a-change
description: "Use when someone asks to review a specific change, diff, branch, document, or plan, but not a whole repository. It runs in rounds, verifying the findings between them, and ends in a revision, or, for a change whoever asked did not make, in a report."
---

# Reviewing a change

## Rounds

1. Size each full round to the change: one investigator with every perspective the round runs where one reader can hold the change while looking for everything at once, otherwise one per perspective. An investigator costs about the same whatever the size of the change, because most of the cost is reading the repository, so spend less by sending fewer investigators, not by shortening a brief.
2. Once steps 3 to 5 have run on the first round's findings, the second round reads the whole change again, with the perspectives it needs next. It finds what the first round missed, because it reads a cleaner text with other perspectives. These two are the full rounds. Where `WGM.md` sets another number, each full round after the first runs as the second does.
3. Verify each finding. Investigators are often wrong, and their rewrites are often denser than the sentence they replace, so take the problem, not the wording. A finding on a passage that an earlier round's fix changed, where that fix did not solve the problem it was made for, is set aside as a question, not fixed again.
4. Apply the fixes yourself, between rounds, one at a time. Write the answer of whoever asked, as [conventions/decisions.md](../conventions/decisions.md#where-decisions-are-written) says, before the fix it allows. Fix a fact wherever the change carries it, searching every text a brief carries for the fact's nouns, not for the phrase the investigator quoted. For code that changes behavior, begin with a test of what must hold, seen to fail on the code before the fix, because a test that has never failed has not shown that it can catch the defect. Then see it fail on a plausible wrong version of the fix too, because a test that fails on the old code can still pass on a fix that is nearly right. An incidental choice a fix adds joins the plan's list, where there is a plan.

   A change whoever asked did not make, and nobody made for them in a session they ran, such as a colleague's branch, is someone else's, so the run reports its verified findings and fixes nothing unless asked, as [the standard](../STANDARD.md#the-order) says. Where the run cannot tell whose change it is, it asks with its first questions whether whoever asked wants a revision or a report, and reports until it has the answer.

5. Run the checks that apply: the smallest ones while working, the full set once a round.
6. The rounds on the fixes come after the full rounds and do not read the change again. Send one investigator with the fixes made since the last round, listed one by one, told to make what they changed fail, to ask whether anything they added could be removed without loss, and to name every fix that made a choice of a kind that [needs an answer](../conventions/decisions.md#what-needs-an-answer) without the answer written, or added an incidental choice the plan does not list. Fixes fail review more often than the changes they repair.
7. After the full rounds, stop when no finding that survives verification, and is not set aside as a question, would change what the change does: the product's behavior, a test, or what a document or plan tells its reader to do. Phrasing alone does not earn another round. Every fix that changes what the change does gets a round on the fixes, whenever it is made, because no round has seen it. When the fixes of two rounds on the fixes in a row have each still changed what the change does, say so and ask before the next.
8. When the change carries a text its users read (a document, a manual, interface text, an issue they follow), end with a cold read of the change, as [reading-it-cold.md](reading-it-cold.md) says, and treat its findings as a round's.

## Perspectives

Every round runs deletion and adversarial, because deletion keeps the product from growing without need and adversarial follows the text as literally as an assistant will. A full round adds whichever of the others the change needs, any of them again in a later round:

- wording, for a document, a plan or comments;
- correctness, for code;
- test strength, when the request asks whether the tests prove what they claim;
- stored data, when the change touches what is stored;
- exposure, when it touches a secret, a database copy or who may see what;
- claim truth, when the change edits in place what comments and numbers describe;
- plan audit, when the change executes a plan.

Every brief asks each finding to name its perspective, names where the repository's own rules are written, and carries the change whole: the diff, its commit messages and every text the change is measured against, because a text no brief carries is one no perspective reads. The working tree counts, and an untracked file is carried whole, except the run's own plan and log. In the rounds on the fixes, the change is context and the fixes are what is examined.

- **Adversarial**: for code, drive it out of order, twice, and fast, through the real UI where there is one and the public interface where there is not. For a document, follow it exactly as written, and for a plan, follow it on paper, and try to make either fail, and for a plan, also ask whether it does what was asked, reading each quoted passage in the file it will land in. Where the change reports what was seen, see it again.
- **Correctness**: how is the change wrong, and what did it break?
- **Test strength**: would each test the change adds or edits fail if the behavior it claims to check broke? Read each against [conventions/tests.md](../conventions/tests.md).
- **Stored data and contracts** (code only): run the old tree and the new against copies of the same stored rows.
- **Exposure**: could it put a secret, a database copy or a user's data where it does not belong? Its findings are kept as "What the recipes share" in [README.md](README.md) says.
- **Deletion**: what should have gone, and which addition could be removed without loss? Lines the change added more than once are a good start, such as those `git diff <base> | grep '^+' | sort | uniq -d` lists, leaving out blanks, brackets, imports and declarations, because a line added twice means the places share something, and the fix belongs in the shared thing. Then list every behavior the change adds that a person or another system can see and that the specification does not contain, and every other choice it makes of a kind that [needs an answer](../conventions/decisions.md#what-needs-an-answer) whose answer is not written as [conventions/decisions.md](../conventions/decisions.md#where-decisions-are-written) says. You put to whoever asked each one of a kind that needs an answer, and check that the plan, where there is one, lists the rest as incidental and that no text presents them as required. Check the other side of any condition you delete.
- **Wording**: read every new sentence as the person it reaches.
- **Claim truth**: after in-place edits, is every comment, number and stated fact still true of what it describes?
- **Plan audit**: is each step done, partial, missing or deviated, and does the plan have more stages than the work needs?

## Rules that cost a defect to learn

- A new static check runs against three trees, as [conventions/static-checks.md](../conventions/static-checks.md) says.
- A plan's acceptance criterion names the test that shows it is met. A step whose "done when" checks for a string proves only that the string arrived, so read the paragraph it landed in.
- Run a command before you hand it to anyone, and before a plan or a document gives it as a check, where it is meant to run if that harms nothing, or on a copy that can be thrown away, because one that reads correctly can still fail when run. Where it can be run in neither way, say that it was not run.
- Copy a file to a scratch directory for a control, never `git checkout`, because that takes uncommitted work with it.
- After a tool that rewrites or stages files, such as a formatter or `git add -A`, read the whole diff for changes nobody meant to make.
- Measure a claim before you repeat it: a number, or a fact carried from older text into new.
