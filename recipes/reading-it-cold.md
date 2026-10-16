---
name: reading-it-cold
description: "Use when the requester opens with something vague ('review this', 'tell me what you think') or asks whether the repository still holds together, on a change after reviewing-a-change's rounds, and, where `WGM.md` lists it as a standing review at a release, on everything a release ships, before the release. One reader reads the whole, with no perspective and no history. It reports and changes nothing."
---

# Reading it cold

One investigator reads the whole repository with no perspective assigned and no knowledge of how it came to be this way, and returns a ranked opinion.

A perspective is a hypothesis, so a set of them searches where you already suspect. That leaves the contradictions between files unassigned: a closing sentence promising what another file does not hold, a word used in three places and defined in none, two files each permitting what the other forbids. A reader who was told what to look for cannot see them, and a reader who knows why each sentence survived will not.

## How to run it

1. **Send one investigator, not three**, with the whole tree at once. Give it no checklist and no account of what you already suspect, for the reason the opening of this recipe gives.
2. **Ask for an opinion, not findings.** Ask for a real judgment, not a summary or a list of nitpicks. It is ranked by what would change a decision, and it names the single weakest part and the single best.
3. **Demand evidence.** Every concrete claim cites the file and quotes the text, so it can be checked without a second pass.
4. **Take the ranking, check the details.** A cold reader states wrong details with confidence, so it is the ranking that is worth having.

## On a change

The same reader and the same four steps, with the change in place of the tree. It comes after the rounds of [reviewing-a-change.md](reviewing-a-change.md) because a fix can make files contradict each other, and the rounds on the fixes read only the fixes.

- **Goes in**: the diff, its commit messages, and the files it touches, read whole rather than by hunk. Also the plan, whole, with the corrections and decisions the rounds put in it, because what it says was built is a claim, not history, and a claim is what the reader checks. A change with no plan carries instead the requester's decisions it executes, copied from where they are written.
- **Stays out**: the backlog and the rounds' reports, for the same reason.
- **After**: a reader holding the plan may weigh its word over the code's where the two differ, but checking the details, as "Take the ranking, check the details" says, catches the difference.

## Before a release

Where `WGM.md` lists it as a standing review at a release (see [conventions/verification.md](../conventions/verification.md)), run it once more before a release, on everything the release ships rather than the change, because a review of a change reads only what changed, and a trap in text no change touched reaches the release unread. This is the one cold read whose brief names what to rank, in place of step 1's "no checklist": contradictions between files, claims that are false, and sentences that would do harm if followed to the letter, ranked by harm, because only those change the decision to release. Whatever else it reports goes to the backlog.

## When not to

Do not run it when the repository is too large for one reader to hold at once, because a cold read of what it cannot see returns platitudes. Read the repository part by part instead, one reader per part, and say in the report that nobody read the parts against each other.
