---
name: learning-from-a-session
description: "Use when the requester asks, at the end of a session that ran recipes, what to learn from it: 'did the recipes work', 'what should change in the recipes'. The session that did the work runs it, with its own memory of the work, before the session ends. It produces proposals for the recipes, the conventions or the standard, and changes nothing."
---

# Learning from a session

This recipe is run by the session that did the work, because what it needs exists only in the session's memory, and the memory is gone when the session ends.

## What to gather

Facts, with the count or the quote behind each. An impression is not a finding. Where the session does not hold a fact, say so, and do not estimate.

1. **What ran.** Each recipe, on what, how many rounds, how many investigators.
2. **What each perspective found**, counted from the reports, and how many findings did not survive verification.
3. **What the fixes broke.** Every defect a later round found in an earlier round's fix.
4. **What reached the tree anyway.** Every defect found after the work was called done, including what the requester corrected, quoted in their words.
5. **What was put to the requester**: each question, when it was asked, what was decided, and what the work did in the meantime.
6. **Which of the repository's rules the work broke**, the rule quoted and the place named, including any rule the work itself added.

## What to ask

- For each rule that was followed: did it earn its cost?
- For each defect the fixes broke or that reached the tree anyway: which rule would have caught it, and is that rule missing, misplaced, or worded so that it was not followed?
- For each question put to the requester: was it one of the cases "What the recipes share" in [README.md](README.md) sets aside, and was it asked before the work or at its end rather than in the middle?
- For each rule the work broke: which round or rule should have caught it, and why did it not?

## What comes out

- **Proposals**, each a change to one recipe, convention or the standard, with the fact from the gathering beside it. The recipe does not make the change. Instead, a proposal the requester accepts becomes an ordinary change, made and reviewed with [reviewing-a-change.md](reviewing-a-change.md) in whatever session makes it. A proposal made at the end of a session is as likely to be wrong as a fix made between rounds. Where wgm is a copy the repository uses and does not write, a proposal for it that the requester accepts is given to the requester to report on wgm instead, as "What the recipes share" in [README.md](README.md) says.
- **Decisions** the proposals need, put to the requester as questions.

Nothing else.
