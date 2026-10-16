---
name: making-a-plan
description: "Use when the requester asks for a plan, 'how would you approach this', or how something people will use should work ('design this', 'what should this look like') before anything is built. It produces a plan and builds nothing."
---

# Making a plan

Four steps, handed to the assistant session that will do the planning, in this order.

1. **Investigate**: read what you have been asked to build (for a change people will use, with the insights file and the observations it names, as [observing-use.md](observing-use.md) describes them, where `WGM.md` says they are), inspect the repository, and check what tools this machine has: runtime, package manager, test runner, formatter, and anything the work depends on. Where a tool depends on a system capability, run a trivial command through it rather than looking for the binary. Report what you found and what is missing.
2. **Specify**: ask the requester questions to lock down what is left. The questions whose answers change the plan most for the least effort to answer go first.
3. **Plan**: write it wherever this repository keeps plans. A plan for a change people will use opens with its design:
   - the moment it answers (a point where someone gets stuck, as [observing-use.md](observing-use.md) defines it), not a feature: who, trying to do what, stopped by what, in the words of an observation, or marked as a guess, saying whose;
   - at least two designs that answer it, sketched far enough to show what each costs and loses, since one design is a decision made before it was looked at;
   - the one that needs less explaining, as [lean towards simplicity](../STANDARD.md#lean-towards-simplicity) says, and why the others were not taken;
   - where the product has a screen in a web browser, the usability rules in [what good to use asks for](../STANDARD.md#what-good-to-use-asks-for) it touches;
   - the moments the next session of observation looks for again, because without them the change cannot be found to have worked.

   A review sees only what the plan contains, so quote a rewritten paragraph as it will read, not the substitution alone.

   Mark each behavior the plan describes as one of three:
   - the requester's decision, written as [conventions/decisions.md](../conventions/decisions.md) says, with where it was given;
   - proposed, when it is of a kind that [needs an answer](../conventions/decisions.md#what-needs-an-answer). Before the plan is approved, the requester answers it, and the answer is written beside it;
   - incidental. The incidental ones are listed together, a line each, for the requester to read, because a choice the requester would have made otherwise is cheapest to catch before it is built, and any the requester questions becomes proposed.

   When the product behaves differently depending on who acts, on what, or in which state, show the requester a few concrete cases before the plan is approved. Each case is a situation, or a cell in a table of roles against operations, and the requester says what they expect in each case without being told what the plan decided. Where the answer differs from the plan, ask the requester which is right, because a decision can be written exactly as it was given and still not be what the requester meant, and a review that checks the plan against the decisions written in it cannot see that.

   Then review the plan with [reviewing-a-change.md](reviewing-a-change.md), which covers plans too.

4. **Stop.** The requester starts a fresh assistant session for implementation, because the plan, not the conversation that made it, must be enough to build from. They give it these words:

   > Read the plan, investigate the repo, and tell me if we're ready. Write each decision I give you, each step you do differently from the plan and why, each finding you decline, and where the work stands, into the plan as you go, before acting on it. Set aside any step that needs a decision you cannot find there, do the steps that do not depend on it, and ask me at the end.

   When the session stops, what the requester does depends on why:
   - if it asks something, the requester answers;
   - if it says it is ready, the requester tells it to start.

   At any stop, the requester may instead start another session with the same words.
