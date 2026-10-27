---
name: reading-it-cold
description: "Use when someone opens with something vague ('review this', 'tell me what you think') or asks whether the repository still holds together, on a change after reviewing-a-change's rounds, and, where `WGM.md` lists it as a standing review at a release, on everything a release ships. One reader reads the whole, with no perspective and no history. It reports and changes nothing."
---

# Reading it cold

One investigator reads the whole with no perspective assigned and no knowledge of how it came to be this way, and returns a ranked opinion. A perspective is a hypothesis, so a set of them searches where you already suspect, and leaves the contradictions between files unassigned: a closing sentence promising what another file does not hold, a word used in three places and defined in none, two files each permitting what the other forbids. A reader told what to look for cannot see them, and a reader who knows why each sentence survived will not.

1. **Send one investigator, not three**, with the whole at once, no checklist and no account of what you already suspect.
2. **Ask for an opinion, not findings**: a real judgment, ranked by what would change a decision, naming the single weakest part and the single best.
3. **Demand evidence.** Every concrete claim cites the file and quotes the text.
4. **Take the ranking, check the details.** A cold reader states wrong details with confidence, so it is the ranking that is worth having.

**On a change**, after the rounds of [reviewing-a-change.md](reviewing-a-change.md), because a fix can make files contradict each other and the rounds on the fixes read only the fixes: the reader gets the diff, its commit messages, the files it touches read whole, and the plan whole, with the decisions the rounds put in it, because what it says was built is a claim the reader checks. A change with no plan carries instead the decisions it executes, copied from where they are written. The backlog, the run's log and the rounds' reports stay out, so that the reader is not told what to find.

**Before a release**, where `WGM.md` lists it as a standing review, once more on everything the release ships, because a review of a change reads only what changed, and a trap in text no change touched reaches the release unread. Here the brief names what to rank, by harm, without saying where to look: contradictions between files, claims that are false, and sentences that would do harm if followed to the letter. Whatever else it reports that is still to do goes to the backlog.

Do not run it when the repository is too large for one reader to hold at once, because a cold read of what it cannot see returns platitudes. Read it part by part instead, one reader per part, and say in the report that nobody read the parts against each other.
