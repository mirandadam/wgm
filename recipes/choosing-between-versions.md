---
name: choosing-between-versions
description: "Use when the requester wants to converge on something that is easier to recognize than to specify, by choosing between two alternatives at a time: a writing rule, a specific text, interface text, a mockup, a working prototype. Words that ask for it: 'A/B', 'show me two versions', 'let me choose', 'refine the style guide', 'which wording'. It produces the winning alternative and a log of every choice and why, and changes nothing else."
---

# Choosing between versions

This recipe ends with the alternative the requester prefers and a log of every choice that led to it. It is for things a person recognizes faster than they can describe: a writing rule, one text, the words on a button, a screen, a prototype.

For what the product's users see, the requester's preference only picks what to try, but whether it works is measured by observing the product in use, as [observing-use.md](observing-use.md) says.

## What is compared

The two alternatives in a pair differ in one thing, except in the comparisons under "Controls", so the choice says which way that thing should go. The thing that varies is whatever is being refined: the rule given to the generator, the text itself, or the instructions for a design.

A generator produces both alternatives in a clean session, from the same input, with only the variant it was given. The generator never sees the conversation with the requester. If it did, the pair would test what the generator heard in that conversation, and the result would not hold without the conversation. When a rule is being refined, the generator also writes from scratch at least once, from the kind of input it will have in real use, and not only rewrites existing texts.

When the variant changes only a word or two, do not generate the two texts separately. Two texts generated apart differ in far more than the rule, and the vote follows the difference that is not the rule. Revise one text twice instead, once under each variant, so that the two differ only where the rule does.

## Each pair

1. Generate the pair and shuffle which alternative is A and which is B. Keep the key where the requester cannot see it before voting.
2. Show both alternatives in full, in the same way, one pair at a time. Say how long each one is and what input it came from, but not which variant produced which.
3. Ask which one is better, and why, in a sentence. When the chosen one can still be improved, ask for the passage.
4. Before doing anything else, write the pair in the log: the two variants, the choice, the requester's own words, and what changes because of it.
5. Tell the requester what the two variants differed in. The vote is blind, but the requester is not.

## Changing the variant

Try removing something before adding anything. A rule, instruction or element that loses a pair, and loses again when that pair is generated again, comes out, and the log says why, so that nobody adds it back.

A passage the requester rewrites becomes a rule that carries that passage as its example. Test the rule on the same input first, then on inputs it has not seen.

Test every change in a pair before keeping it, even one that seems obviously right. The generator follows a rule more literally than whoever wrote it meant ([conventions/writing.md](../conventions/writing.md) lists rules that failed this way). It also copies an example's incidental wording into texts where that wording does not fit.

## Controls

- Every few pairs, compare the current variant with the original or with what is in use today, to see whether the variant spoils what was already good.
- Before stopping, run pairs on inputs the variant has never seen.
- Each output is one sample, and the same variant can produce a different result on another run. Draw conclusions from the pattern across pairs, and if a decision rests on one pair, generate that pair again.
- From time to time, make the two alternatives differ widely instead of by one detail. Small changes alone settle on the best of what was already tried, which may be mediocre. This matters most in design.

## Cost

A pair of texts, interface text included, costs seconds. A pair of mockups costs minutes. A pair of working prototypes costs enough that it should be reserved for a choice that mockups cannot settle.

## Stopping

Stop when the requester prefers the current variant and cannot say what would improve it, or when the choices start to contradict each other without a reason being given. The winning variant goes where it will be used, and the log goes beside it or into the commit that lands it.
