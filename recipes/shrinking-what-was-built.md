---
name: shrinking-what-was-built
description: "Use when the requester asks which behaviors of an area anybody decided, asks to remove what nobody decided, or wants a specification for code that already exists: 'this is too big', 'what here does anyone need', 'shrink this'. It produces three lists of behaviors and questions to the requester on the incidental ones. The removals are separate changes."
---

# Shrinking what was built

This applies [the standard](../STANDARD.md)'s "every behavior is decided or incidental" to what already exists: it sorts what an area of the product does into decided and incidental, finds what relies on the incidental, and lists what can go. How a decided behavior is built, and whether it could be built with less, is the question of [reviewing-the-mechanisms.md](reviewing-the-mechanisms.md).

## How to run it

Whoever runs the recipe chooses the area with the requester: a feature, a module or a command, small enough for one investigator to hold, since a run over a whole repository returns a list nobody acts on. One investigator goes to each area, as "What the recipes share" in [README.md](README.md) describes, and:

1. **Lists what the area does** as a person or another system sees it: every screen, endpoint, command, option, stored field, file written, message sent and limit enforced. The list comes from the code, not from the documents, which show what someone believed.
2. **Traces each behavior** to the identifier in the specification that it serves, directly or as the fix of a defect. A behavior that traces to none is incidental, unless it is [proposed](../STANDARD.md#every-behavior-is-decided-or-incidental): that one goes in none of the lists, and the report names it as waiting.
3. **Looks for what relies on each incidental behavior**: the callers, the stored data that carries it, the other systems and scripts that read it, and the logs of use where there are any. It marks the ones that are a [safeguard](../conventions/decisions.md#what-needs-an-answer) of any part of "Trustworthy", the first item of [the order](../STANDARD.md), and says where it looked: not finding a use is evidence only as strong as the places searched.
4. **Sorts** the behaviors into three lists: "decided"; "relied on", the incidental ones something relies on or that are a safeguard of "Trustworthy"; and "unused", the incidental ones nothing was found relying on.
5. **Reads the area's specification** and lists the sentences that say how something is carried out rather than what the requester decided, the sentences whose history shows they were written to match the code, and the decided behaviors the code does not do.

## What comes out

- **The three lists**, with how many behaviors each holds, and each behavior with where it is in the code and, for an incidental one, where the search for use looked.
- **The proposed behaviors**, apart from the lists, each named as waiting for the requester's answer.
- **Questions for the requester**:
  - for each behavior in the "relied on" list of a kind that [needs an answer](../conventions/decisions.md#what-needs-an-answer), whether to decide it (it then enters the specification) or to plan its removal with what replaces it, the rest staying incidental;
  - for the "unused" list, which behaviors to remove and whether to ask the people who use the product first;
  - for each sentence the reading of the specification listed, whether it stays in the specification.
- **The removals** the requester approves, each an ordinary change reviewed with [reviewing-a-change.md](reviewing-a-change.md), taking with it the tests that held only that behavior. If something turns out to rely on a removed behavior, the removal is reverted and the requester is asked about the behavior. Once they are made, the run reports how many lines of code and of documents they took out.
