# The standard

This file says what "good" means: the ranked order every change is judged by (one condition, then four costs), and what "Good to use" and "Easy to change" ask for in practice. Every change is held to this standard, whether or not anyone reviews the change. What things are called, where they live and how decisions are written are in [conventions/](conventions/), and the tiers of verification that show the product meets "Trustworthy" are in [conventions/verification.md](conventions/verification.md).

The product may be software, or a text kept in a repository, such as a presentation, a report, teaching material or an official document, and one repository may hold both, as release notes beside the code they describe. A text is the product when its readers are those the work is for, not those who do it. Each fact such a text states, and each commitment it makes for someone, is a claim "Trustworthy" applies to, so it comes from a source whoever writes the text can point to, or it is a question, never a guess. A structure an outside authority sets for it, such as the fields of a procurement form, and a passage someone else wrote and answers for, change only by asking. The rest of wgm was written for software and for the documents about the work, so each of its rules applies to such a text where it fits the text's form and readers, and whoever sets one aside says which and why. Its checks for "Good to use" are those of [conventions/writing.md](conventions/writing.md) and [recipes/reviewing-documentation.md](recipes/reviewing-documentation.md), not the browser checks below.

The one file a repository keeps of its own is **`WGM.md`**, made from [template/TEMPLATE.md](template/TEMPLATE.md). The **requester** is the person you work for: whoever asked for the work, which in a session is the person at the terminal. Where `WGM.md` names who may answer, a question that needs an answer goes to them. Where the requester needs someone else's answer, getting it is the requester's part, and where nobody can answer, as in a scheduled run, the question goes in the report and nothing that depends on it is done.

## The order

1. **Trustworthy.** The product does what it claims, and can show it. It states what it does not do. It keeps working, and when it fails it never loses anything without saying so. Nobody sees or changes what they are not allowed to.
2. **Good to use.** Measured by how rarely people get stuck and how easily they get unstuck, not by how much it offers.
3. **Easy to change.** Measured by how much the next person must understand, and how long the work takes them once they do, not by how many lines there are. This comes before running and building it because a product that is easy to change can be made cheaper later, and a cheap product that is hard to change cannot be made easy to change later.
4. **Cheap to run.** In money, and in the attention of the people who keep it running.
5. **Cheap to build.** What the task at hand costs to make, now. It is last because it is paid once, and a shortfall in any item above it is paid for as long as the product lives. So when a requirement in hand can be met by a design that is cheaper now or by one that is cheaper over the product's life, the second wins by default.

The requester decides what the product lets people do, while this standard is about giving them that at the least human time and money over its life, the requester's time included. "Trustworthy" is a condition, never traded. The other four are costs, ordered by who pays them longest and most often: the people who use the product, the next person to change it, those who run it, and whoever builds it now. Nobody can measure these costs while making a change, so the order stands in for the measurement. With the answer that [conventions/decisions.md](conventions/decisions.md#what-needs-an-answer) asks for, removing a safeguard of "Trustworthy" or narrowing what the safeguard protects is not a trade but a change in what the product claims to protect.

A change is judged by what it does to each item, in this order, and the order is the only ranking. Every rule in wgm serves an item of it, a finding weighs as much as the item it harms, and when two rules pull apart, the one serving the earlier item wins. Each rule says why it exists, and applies where its reason does. Where the reason does not hold, neither does the rule, and whoever sets it aside says so, in the report or the commit message, rather than skipping it in silence. A rule that gives no reason applies as written. A number a rule sets, such as how many rounds, how long or how large, is a default, because a number that suits one project rarely suits every other. `WGM.md` may set another, saying why, and that needs an answer, as [conventions/decisions.md](conventions/decisions.md#what-needs-an-answer) says. A change must not make an earlier item worse to improve a later one, except as [trading without asking](conventions/decisions.md#trading-without-asking) allows. If such a trade seems right, ask the requester, and write the answer as [conventions/decisions.md](conventions/decisions.md) says.

A written decision that seems wrong is changed the same way: by asking, never by working around it, because a workaround leaves written a decision that is no longer true.

When two parts of one item pull apart, whoever builds chooses and writes the trade down. Inside "Trustworthy", they ask instead.

Three rules for trading between the items:

- Being earlier in the order does not justify any cost. An improvement there must still be worth what it costs in later items. Whoever builds judges that, and writes it down where the next person to pay the cost will read it:
  - a cost that repeats each time the product is run or changed goes in the [as-built reference](conventions/documents.md), the documents that say how the product actually works;
  - a cost the next editor of that code pays goes in a comment in that code;
  - a cost paid once goes in the message of the commit that pays it.
- A cost that repeats belongs to the item where it repeats. A slow test suite is paid on every change, so it is a cost of changing the product, not of building it once.
- "Good to use" or "Easy to change" may be made a little worse without asking, for a larger measured gain further down the order, only under the conditions in [Trading without asking](conventions/decisions.md#trading-without-asking), and whoever builds writes the measured loss and the measured gain in the message of the commit that makes it.

## What good to use asks for

The usability rules below are seven checks for a product operated through a screen in a web browser. Each can be verified on a diff or by driving the product, and each is written from the moment someone would get stuck. Failing any one makes the product worse for everyone, but passing all seven does not show that it is good to use. Only observing the product in use shows that, as [recipes/observing-use.md](recipes/observing-use.md) describes, and the change that follows is planned with [recipes/making-a-plan.md](recipes/making-a-plan.md).

### Every screen has its states

The ideal, empty, loading, partial and error states are designed, not discovered. Wherever a phone is expected, offline is a sixth. Empty says what belongs here and offers the action that fills it. Loading shows a skeleton of what is coming, not the previous screen.

### A failure is a sentence

The sentence that reports a failure is written once, at the boundary between the system and the person, in the product's words: what happened, why, and what to do next. It never contains the transport's words, a status code, a stack trace or an identifier the person has never seen, because they can do nothing with what they do not recognize. What the person entered is kept, and the sentence says where. Where the product shows a status, it says why, not only the status word ("Paused: payment overdue", not "Paused").

### There is a budget for waiting

- A press visibly registers inside a tenth of a second.
- The result shows inside four tenths of a second.
- When it cannot, whatever loads, a screen or a part of one, shows its loading state by then, while a submitted form keeps its busy state, and once a second has passed, an indicator says what is happening.
- Past ten seconds, there is a way to cancel or leave, or a recorded reason there is none.

The tenth of a second, the one second and the ten seconds are the limits Card, Robertson and Mackinlay (1991) and Jakob Nielsen (1993) give for a response to feel instant, for the flow of thought to hold and for attention to stay, and four tenths is the Doherty threshold, from Doherty and Thadhani's IBM paper of 1982. The budget is checked on the devices and network listed in `WGM.md`, not on the developer's machine. `WGM.md` says whether a throttled test checks it on every change or a hand measurement does at a milestone.

### The address is the state

What survives a refresh and a shared link is decided and written down: the view, the thing open in it, and the choices a person made to get there. The browser's back button works, and while a dialog or panel is open it closes that rather than leaving the page.

### Recognition, not recall

The context a decision needs (what was chosen, what it costs, what is left) is on the screen where the decision is made, not on the one before. An identifier someone would otherwise copy and type elsewhere is a link to what it names.

### One vocabulary, chosen

Labels use the words of the person, not the schema. The product's concepts and the one word for each are written with the product's other decisions, and `WGM.md` says where. Where a retired word could return and no test would fail, a [vocabulary check](conventions/static-checks.md) catches it.

### One control per job, and accessible

- **Consistency.** The same thing looks the same everywhere and nothing else looks like it. Each screen has one primary action, so that the next step is never in doubt, and it looks the same on every screen, in color and placement, whatever the action is. Warnings look the same wherever they appear, and so do errors. Buttons, status colors and text sizes come from a fixed set, as [conventions/static-checks.md](conventions/static-checks.md) describes. The conventions people already know (the products listed in `WGM.md`) are followed, not improved.
- **Forms.** A form is built as a form element and behaves like one: a label bound to every field, `autocomplete` and `inputmode`, submit on Enter, a busy state on submit, required fields marked before anyone types, and a number box that takes its limits from its own `min` and `max`.
- **Accessibility.** WCAG 2.2 AA is the minimum, not the goal. A run checks what a tool can, and a person checks the rest, because tools find only part of what it asks. Beyond it, each change a sighted person would notice is announced once to screen readers, so that someone who cannot see it learns of it. An action that opens something or leads somewhere, such as a dialog or a new page, moves focus into it, and the dialog or page has a name that says where the person now is. A dialog that closes returns focus to what opened it. Any other change, such as a saved form, is announced by a live region. Targets are at least 44 CSS pixels where a finger is expected, and at least 24 where a pointer is. 24 is the WCAG 2.2 AA minimum, and 44 its AAA level.

## What easy to change asks for

The five principles below are about "Easy to change".

### Lean towards simplicity

Simplicity means fewer concepts, fewer special cases and fewer modes, not fewer lines. When two designs both work, take the one that needs less explaining. [recipes/reviewing-the-mechanisms.md](recipes/reviewing-the-mechanisms.md) is the long form of this principle.

- Build for the second case when it arrives, not before: no configuration that nothing reads and no hook without a caller. A case nobody has asked for is not a requirement in hand, so building for it adds to what the next person must understand and saves nothing.
- Delete commented-out code, since git keeps it in the history.
- Do not handle inputs that the type system or the caller's contract already excludes. If unsure, assert. Input that crosses a trust boundary is checked where it enters, because there the contract is only a claim, and "Trustworthy" comes first.

### Prefer the fix that makes the next mistake harder

Correct today is the minimum. What matters is whether the design leaves the next change easier or harder than it found it.

So the unit of a fix is the cause, not the symptom in front of you. If the same mistake can happen in three other places, repairing one of them is not finished work. Where something holds only by luck or by convention, make it hold by construction, because a rule that is only a comment asking the next person not to break it is not a rule.

Design for the change nobody has asked for yet by generalizing the shape, not the feature set: a name and a signature that carry the concept rather than the first caller's needs, documentation written as part of the design rather than after it. A layer, an option or an abstraction still needs a current requirement behind it, so inline what has one concrete user until a second exists.

### Every behavior is decided or incidental

Every behavior costs whoever maintains it: code to read, tests to keep, and a place for defects. Each is one of three:

- **Decided**: whoever may answer decided it, and it is written where [conventions/decisions.md](conventions/decisions.md) says decisions are written. A requirement is a decided behavior.
- **Proposed**: put to whoever may answer and not yet answered, so neither decided nor incidental. A proposed behavior is not removable, and no change that carries it lands until they answer, because it would rest on an answer nobody gave.
- **Incidental**: everything else the product does, a choice made while building it, by a person or an assistant. An incidental behavior is not a requirement because it exists, because it is old, or because a document describes it. Before altering or removing it, whoever builds looks for what relies on it, in the code and in what is known of how people use the product, because a person who relies on it ranks above what the removal saves. Whoever builds goes ahead when nothing is found, unless it is a choice that [needs an answer](conventions/decisions.md#what-needs-an-answer).

### Do now what belongs to now

Work that is part of the task at hand gets done as part of the task at hand. Before writing anything down as "later", ask whether it can simply be done now. If it genuinely cannot, ask where it will be most useful rather than where it is easiest to put, because much of what reads like backlog is a sentence that belongs beside the code it describes.

### Write for a person

Everything a person reads (code, comments, tests, commit messages, documents, failure output, and the account of the work handed back to whoever asked for it) is written to be understood without holding the whole codebase in mind.

- Put the explanation where the reader will be standing when they need it.
- Say why before what. A file and line number is a reference, not an explanation.
- Make failure messages tell the reader what to do next, not merely what went wrong.
- Write commit messages, merge request descriptions, issues, comments, reports and documentation as [conventions/writing.md](conventions/writing.md) says, and commit messages in the form [conventions/commits.md](conventions/commits.md) gives.
- Name things so that the name carries the meaning, which makes most of the comment unnecessary.

In code, comments and tests, remove anything whose absence would change neither what the product does nor what a reader takes from the text, at each level in turn: the statement, then the section, then the whole file, because everything kept is read again by every next person. Cut ideas, not words. Keep an example only where a reader would get the rule wrong without it.

## Checking your own work

Before you call something done, ask yourself six questions:

1. Is there a design that also works and needs less explaining? ([Lean towards simplicity](#lean-towards-simplicity))
2. Have you changed what made this possible, or only what went wrong this time? ([Prefer the fix that makes the next mistake harder](#prefer-the-fix-that-makes-the-next-mistake-harder))
3. Is anything on your "later" list actually doable now? ([Do now what belongs to now](#do-now-what-belongs-to-now))
4. Could someone who does not know this code read what you wrote and act on it? ([Write for a person](#write-for-a-person))
5. Did this make an earlier item of the order worse, other than by a trade that [trading without asking](conventions/decisions.md#trading-without-asking) allows? If so, ask before calling it done.
6. Is every decision the requester took for this work written in the [specification](conventions/decisions.md#where-decisions-are-written), and is nothing else written there as one? If not, write the missing ones and put the rest to the requester before calling it done.
