# Decisions

This file says where a decision is written, what counts as a decision, which choices need the requester's answer, when "Good to use" or "Easy to change" may be made a little worse without asking, for a larger measured gain further down the order, and how an alternative that was dropped is kept from being proposed again. [The standard](../STANDARD.md#every-behavior-is-decided-or-incidental) says why every behavior is either decided or incidental, and this file is the procedure that follows from it.

## Where decisions are written

When a decision is taken, it is written in the specification, and `WGM.md` says where that is. The text is the decision, and the repository's history keeps how it came to be.

- The specification states what a person or another system sees the product do, and what must never happen, each with a stable identifier (a section number, or an issue number where decisions live in issues) and a line giving its reason. That is what someone outside relies on, so an address or an interface another system calls belongs there too. How each is carried out belongs to the code and the as-built reference, as [documents.md](documents.md) says, because it can change without anyone outside noticing.
- The specification changes only by asking the requester, and it is never rewritten to match what was built, because then a defect would become a requirement and nobody would know what was wanted. Code that disagrees with it is a defect or a question for the requester.
- Until the change that moves it into the specification lands, a decision sits in the plan ([documents.md](documents.md)), or, where there is none, in a file where `WGM.md` says plans live. It is written there when it is taken, before anything acts on it, and there it counts as written in the specification and is cited where it sits. A later change treats as decided only what it finds written in one of these places, or beside a number's value in `WGM.md`, as [What needs an answer](#what-needs-an-answer) says. Where there is no specification yet, the first decision written starts it.
- A fix for a defect serves the decided behavior it restores. A test written for a decided behavior names its identifier, so that a failing test says which decision it protects.

## What counts as a decision

A decision is an answer, from whoever may answer (the requester, unless `WGM.md` names someone else), to one question, or a text they approved after seeing it in place. A request from whoever may answer, naming what to build or change, is a decision on what its own words say, and not on a text it points to. A choice of a kind that [needs an answer](#what-needs-an-answer) is decided only when the request names it together with its kind, as "remove the login check from the export" does. Where a request leaves real doubt about whether it decides such a choice, the run asks before it begins, or, where nobody can answer, treats the choice as undecided, as the [standard](../STANDARD.md) says. Where the run cannot tell whether the requester may answer, the request decides no such choice, and each is put to whoever may answer.

- Silence is not one, nor agreement that cannot be tied to a single question, because neither says what was chosen, so whoever builds would be writing a guess as the requester's.
- A recommendation the requester asked for stays proposed until whoever may answer accepts it, because asking for advice is not taking it.
- An answer that leaves the choice to whoever builds, such as "you choose" or "no preference", makes the behavior incidental. Whoever builds then chooses, and the choice is never written as the requester's, because a choice written as theirs could later be changed only by asking them about something they never chose.

## What needs an answer

Whoever builds chooses incidental behavior without asking, such as how a decided behavior is worded, laid out and shown in each of its states, within the [usability rules](../STANDARD.md#what-good-to-use-asks-for). Four kinds of choice need an answer instead:

- adding something the product does that no decided behavior asks for (a screen, command, option, endpoint or stored field of its own, or a step or rule a document tells its reader to follow, other than one the software or equipment it documents needs in order to work, such as setting a variable the software reads), or code that serves neither a decided behavior nor an item of the order;
- a choice whose reversal would need more than a change to the code (the shape of stored data, an address or link, an interface another system or person calls, the word for one of the product's concepts);
- a safeguard of "Trustworthy", that is, a check or limit that keeps the product trustworthy: removing one, narrowing what it protects, or adding one that neither a decided behavior, "Trustworthy" itself nor a usability rule requires (how one is written stays with whoever builds);
- changing, in `WGM.md` or for one run, the value of a number wgm sets as a default, returning it to the default included. The answer to a value set in `WGM.md` is written beside it, and counts there as written in the specification. The answer for one run, or to a return to the default, is written in the plan, or, where there is none, where `WGM.md` says plans live, and goes when the plan goes, because the default holds where `WGM.md` is silent.

## Trading without asking

"Good to use" or "Easy to change" may be made a little worse without asking, for a larger measured gain further down the order, when all of these hold for the loss:

1. It was measured in the change itself (seconds a person waits, minutes a test run takes).
2. It is small beside a measured gain in an item further down the order, counting earlier such trades for the same item, which the messages of the commits that made them show.
3. It leaves every [usability rule](../STANDARD.md#what-good-to-use-asks-for) and every [decided behavior](../STANDARD.md#every-behavior-is-decided-or-incidental) met.
4. Making the trade needs no choice that [needs an answer](#what-needs-an-answer).
5. It can be undone by a change to the code alone.

A trade whose gain is time saved now for whoever builds is never made this way.

## What is not proposed again

Before proposing something, search the history for it, because the commits that changed the text, and the reports and plans kept with them, say what was tried and why it was dropped.

An alternative worth not proposing again, such as something cut or a finding declined that a later reader would likely propose again, is written with its reason beside the rule or behavior it concerns, or, where that rule is wgm's own, in `WGM.md`. The specification of an export might say "The export is not paged, because the largest export measured is 4,000 rows", and [writing.md](writing.md#rules-that-were-tried-and-dropped) keeps a list of the rules that were tried. Any other finding declined during a run is written in the plan, or, where there is none, in a file where `WGM.md` says plans live, so that the run's later rounds do not raise it again, and it goes when the plan goes. The message of the commit that applies a run's fixes gives at most one sentence of counts for what the run found, because a commit message says what the commit changed, not what the review saw.
