---
name: making-a-plan
description: "Use when someone asks for a plan, or how something people will use should work ('design this', 'what should this look like') before anything is built. It produces a plan and builds nothing."
---

# Making a plan

Four steps, in this order.

1. **Investigate**: read what you have been asked to build, inspect the repository, and check what tools this machine has (runtime, package manager, test runner, formatter, and anything the work depends on), running a trivial command through each rather than looking for the binary. For a change people will use, read the insights drawn from observations, and the observations they name, where `WGM.md` says they are. Report what you found and what is missing.
2. **Specify**: put to whoever asked the questions that are left, those whose answers change the plan most for the least effort to answer first.
3. **Plan**: write it where this repository keeps plans, holding what "What the recipes share" in [README.md](README.md) says a plan holds. A plan for a change people will use opens with its design: the moment it answers (who, trying to do what, stopped by what, in the words of an observation or marked as a guess), at least two designs that answer it, sketched far enough to show what each costs and loses, the one that needs less explaining and why the others were not taken, the usability rules of [GOOD-TO-USE.md](../GOOD-TO-USE.md) it touches where the product has a screen in a browser, and the moments the next observation looks for again, because without them the change cannot be found to have worked. Quote a rewritten paragraph as it will read, because a review sees only what the plan contains.

   Mark each behavior the plan describes as decided by whoever asked, written as [conventions/decisions.md](../conventions/decisions.md) says, or as incidental, and ask before the plan is approved about each of a kind that [needs an answer](../conventions/decisions.md#what-needs-an-answer). The incidental ones are listed together for whoever asked to read, because a choice whoever asked would have made otherwise is cheapest to catch before it is built, and any they question is asked about. When the product behaves differently depending on who acts, on what, or in which state, show whoever asked a few concrete cases before the plan is approved, and let them say what they expect in each without being told what the plan decided, and where an answer differs from the plan, ask which is right, because a decision can be written exactly as it was given and still not be what whoever asked meant.

   Then review the plan with [reviewing-a-change.md](reviewing-a-change.md).

4. **Stop.** Whoever asked starts a fresh assistant session for implementation, because the plan, not the conversation that made it, must be enough to build from. They give it these words:

   > Read the plan, investigate the repo, and tell me if we're ready. Write each decision I give you, each step you do differently from the plan and why, each finding you decline, and where the work stands, into the plan and its log as you go, before acting on it. Set aside any step that needs a decision you cannot find there, do the steps that do not depend on it, and ask me at the end.

   When the session stops, whoever asked answers what it asks, or tells it to start if it says it is ready, or starts another session with the same words.
