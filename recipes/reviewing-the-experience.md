---
name: reviewing-the-experience
description: "Use only when the requester asks for a UX pass or a review of what the product is like to use, for a product operated through a screen. It is expensive, because it drives the real application. It reports and changes nothing."
---

# Reviewing the experience

## When

Run it when the backlog has accumulated many small interface items, or before a stretch of user-facing work. It is not for one reported bug, which is an ordinary fix, and not right after a run whose findings are not acted on yet.

## Goal

Find the few design decisions that generate whole classes of user-visible problems, including places where people get stuck that nobody has reported yet, and say which change would remove the most. This is "Good to use", the second item of [the order](../STANDARD.md), checked against its usability rules and against what people have been seen to do.

The unit of a finding is a **class of places where people get stuck, with one cause**. A finding that cannot name the symptoms it explains is a bug report, not yet a finding.

## Perspectives

- **First session**: before reading the client, drive the real application as a new user, at a phone width and a laptop width. Register, create something, use it, break something, try to recover. Count taps, scroll distance and the collapsed sections a person must open on the common path. It is mandatory, and it finds the most.
- **Conceptual model and wording**: list every concept the interface names, where it is first met, and the words used for it. Then find the concepts with two names, and the names with two concepts.
- **Feedback and failure**: for every gesture that changes something, what says it worked, what says it failed, and what shows it in flight.
- **Layout and affordance**: what is reachable, what looks clickable, what the visual language distinguishes. Read the stylesheet as a system: count the colors, the type sizes, and the meanings each accent carries.
- **Rules the user must learn**: product rules enforced by the server, traced to what a user sees when one refuses them. A rule discovered only at the moment of refusal is a design problem wherever it is implemented.

Where the product has a screen in a web browser, each perspective reads [the standard's section on "Good to use"](../STANDARD.md#what-good-to-use-asks-for) and reports against its rules by name, so a run can say which rule a finding breaks and which rule would have caught it. The perspectives are an expert review. They add to what people were seen to do but do not replace it.

## Procedure

1. **Ask the requester first** where people get stuck, what kinds, on what devices, and how far a change may go. Those answers decide what is in scope. Ask as well how the assistant drives the application and takes a screenshot at both widths, because the first-session perspective cannot run without them.
2. **Survey the shape of the system**: entry points, views, documented contracts, backlog, and the observations and insights, wherever `WGM.md` says they are. What the backlog already records counts as known, and is evidence for a broader cause rather than a finding of its own.
3. **Run the perspectives**, each with a scratch directory outside the repository and a word limit. Require `file:line` for code claims, and a screenshot, a count or a quoted string for experience claims. A wording finding quotes the string as the user sees it, because paraphrase hides the problem, and the problem is usually the exact word.
4. **Converge.** Keep what more than one perspective reached by different routes, and what a single perspective can prove. Then ask what one cause would explain the most of it.

## Report

Open with the root cause in one sentence, and the evidence that it is one cause and not several. Then:

- **The findings**, ranked by symptoms removed per unit of work, each naming the cause, the evidence with counts and quotes, and the symptom classes it explains. The best finding is not the deepest. It is often in the interface's surface (labels, layout, feedback) rather than its architecture.
- **Larger changes**: the one or two changes to the product's model that would matter more than any individual fix, each with its cost and what would be lost. Say when a smaller change first would settle whether the larger one is needed.
- **What is working**, and should not be disturbed by what follows.
- **What people were seen to do**, and what was only inferred, with the date use was last observed, or the reason `WGM.md` gives for no use being observed. A blank there is a finding.
- **What could not be verified**, and what would settle it.

If the requester then asks for a plan, the decisions it needs, especially any that reverse a written product decision, are put to the requester as questions before it is written.
