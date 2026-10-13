---
name: reviewing-a-change
description: "Use when the requester asks to review a specific change, diff, branch, document, or plan, but not a whole repository. It runs in rounds, verifying the findings between them, and ends in a revision, or, for a change that is not the requester's, in a report."
---

# Reviewing a change

## Rounds

1. The first round is sized to the change. If the diff fits on one screen, send one investigator with every perspective the section below gives the round, because one reader can hold that much while looking for everything at once. If it does not, send three, one for each of those perspectives. An investigator costs about the same whatever the size of the change, because most of the cost is reading the repository. So spend less by sending fewer investigators, not by giving one a shorter brief.
2. Once steps 3 to 5 have run on the first round's findings, the second round reads the whole change again. It is sized as the first, with the perspectives the section below gives it, and it finds what the first round missed, because it reads a cleaner text with perspectives the first round did not take. These two are the full rounds, the ones that read the whole change. The author of wgm tried other numbers of full rounds: three cost too much for what they found, and one, followed only by rounds on the fixes, found too little. Where `WGM.md` sets another number, each full round after the first runs as the second does, once steps 3 to 5 have run on the round before it.
3. Verify each finding. Investigators are often wrong, and their rewrites are often denser than the sentence they replace, so take the problem, not the wording. A finding on a passage that an earlier round's fix changed, where that fix did not solve the problem it was made for, is set aside as a question, not fixed again.
4. Apply the fixes yourself, between rounds, one at a time:
   - The requester's answer that a fix applies is written down, as "What the recipes share" in [README.md](README.md) says, before the fix is made.
   - A finding that overturns a fact is fixed wherever the change carries it. To find each place, search every text a brief carries for the fact's nouns, not for the phrase the investigator quoted.
   - For code, the fix's first artifact is the test that says what must hold, run red, because a test that never failed has not shown it can catch the defect. When two designs would cost less than a review round, build both against that test and keep the one that needs less explaining.
   - A fix that adds an incidental choice adds its line to the plan's list, where there is a plan, and the round's report names the lines it added.

   A change is not the requester's when they did not make it and nobody made it for them in a session they ran, such as a colleague's branch, even one the requester assigned. For such a change, the run reports its verified findings and applies no fix unless asked, because the change is not the requester's to rewrite. Where the run cannot tell whose change it is, it asks with its first questions whether the requester wants a revision or a report, and runs as for a report until they answer. If they answer "revision", the findings reported so far are applied, as the bullets above say, and the run goes on as a revision, so that a round on the fixes reviews them. While it runs as for a report, each full round after the first receives every finding the rounds before it reported, so that it looks for others, and a finding reported but not fixed does not keep the rounds going under step 7.

5. Run the checks that apply: the smallest ones while working, the full set once a round.
6. The rounds on the fixes come after the full rounds and do not read the change again. Send one investigator with the fixes made since the last round listed one by one, told to:
   - make what they changed fail;
   - ask whether anything they added could be removed without loss;
   - name every fix that added or changed a behavior or a choice of a kind that [needs an answer](../conventions/decisions.md#what-needs-an-answer) when the requester's answer for it is not written as [conventions/decisions.md](../conventions/decisions.md#where-decisions-are-written) says (a fix that restores a decided behavior needs no answer);
   - name every incidental choice a fix added that the plan does not list.

   Fixes fail review more often than the changes they repair, and the full rounds already read the whole change.

7. After the full rounds, stop the rounds when no finding that survives verification, and is not set aside as a question, would change what the change does: the product's behavior, a test, or what a document or plan tells its reader to do. Findings about phrasing alone do not earn another round. Never run more than two rounds on the fixes without being asked, except the rounds steps 8 and 9 give. If the last round's fixes changed what the change does, say so and ask.
8. When the change carries a text its users read (a document, a manual, interface text, an issue they follow), end with a cold read: run [reading-it-cold.md](reading-it-cold.md) on the change after its rounds, and treat its findings as a round's. If any were fixed, one more round reviews those fixes, as rounds on the fixes do, whether or not anyone asked for it. That round's findings are verified and fixed too, and the review stops there. If its fixes changed what the change does, say so and ask.
9. Fixes made after the questions the run set aside are answered get one more round, as rounds on the fixes do, when they change what the change does, because the rounds before them never saw them.

## Perspectives

The first round runs deletion and adversarial, because deletion keeps the product from growing without need and adversarial follows the text as literally as an assistant will, and adds the one perspective below the change needs most. Each full round after the first takes the three it needs next, any of them again. Rounds on the fixes run deletion and adversarial, as step 6 says. The perspectives to choose from, by what the change is:

- wording, for a document, a plan or comments;
- correctness, for code;
- test strength, when the request asks whether the tests prove what they claim;
- stored data, when the change touches what is stored;
- exposure, when it touches a secret, a database copy, or who may see what;
- claim truth, when the change edits in place what comments and numbers describe;
- plan audit, when the change executes a plan.

Every brief, in every round:

- asks for each finding to name its perspective;
- names where the repository's own rules are written, since a rule no brief points at is a rule no round reads;
- carries the change whole: the diff, its commit messages, and every text the change will be measured against (the plan it executes, the issue, the merge request as drafted), since a text no brief carries is one no perspective reads;
- carries the findings the rounds before it declined, and the questions set aside and not yet answered, so that it does not raise them again.

In the rounds on the fixes, the change is context, and the fixes are what is examined.

The perspectives:

- **Adversarial**: for code, drive it out of order, twice, and fast (steps skipped or reversed, the same action repeated, a second action before the first finishes), through the real UI where there is one and the public interface where there is not. For a document or a plan, follow it exactly as written and try to make it fail. For a plan, also ask whether it does what was asked, and read each quoted passage in the file it will land in, because a passage that is right in the plan can be wrong beside its neighbors. Where the change reports what was seen (a symptom in an issue or a commit message, say), see it again: in the product, on the tree the change started from, or where it was first observed.
- **Correctness**: how is the change wrong, and what did it break?
- **Test strength**: would each test the change adds or edits fail if the behavior it claims to check broke? The investigator reads each against the checklist in [conventions/tests.md](../conventions/tests.md), the one [reviewing-tests.md](reviewing-tests.md) uses.
- **Stored data and contracts** (code only): run the old tree and the new against copies of the same stored rows.
- **Exposure**: could it put a secret, a database copy or a user's data where it does not belong? In a public repository, its findings are kept as [reviewing-the-exposure.md](reviewing-the-exposure.md) says of its own, even where `WGM.md` names a public place for them.
- **Deletion**: what should have gone, and which addition could be removed without loss? Start with the lines the change added more than once:

  ```
  git diff <base> | grep '^+' | sort | uniq -d
  ```

  `<base>` is the commit the change started from. The working tree counts, since a fix under review is often not yet committed. An untracked file is not in the diff and is read whole. Ignore blanks, closing brackets, imports and declarations. A line added twice means the places share something, and the fix belongs in the shared thing.

  Then list every behavior the change adds that a person or another system can see and that the specification does not contain, and every other choice it makes of a kind that [needs an answer](../conventions/decisions.md#what-needs-an-answer) whose answer is not written as [conventions/decisions.md](../conventions/decisions.md#where-decisions-are-written) says. Whoever runs the recipe puts to the requester each one of a kind that [needs an answer](../conventions/decisions.md#what-needs-an-answer), and checks that the plan, where there is one, lists the rest as incidental, and that no text presents them as required.

  Check the other side of any condition you delete (the `else` of an `if`).

- **Wording**: read every new sentence as the person it reaches.
- **Claim truth**: after in-place edits, is every comment, number and stated fact still true of what it describes?
- **Plan audit**: is each step done, partial, missing or deviated, and does the plan have more stages than the work needs?

## Rules that cost a defect to learn

- A new static check runs against three trees, as [conventions/static-checks.md](../conventions/static-checks.md) says.
- A plan's acceptance criterion names the test that shows it is met.
- A plan step whose "done when" checks for a string proves only that the string arrived. Read the paragraph it landed in.
- Copy a file to a scratch directory for a control, never `git checkout`, because that takes uncommitted work with it.
- Measure a claim before you repeat it: a number, or a fact carried from older text into new.
