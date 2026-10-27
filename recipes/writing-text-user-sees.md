---
name: writing-text-user-sees
description: "Use when someone wants the text a product's users read (labels, buttons, hints, messages, help, spoken text for a screen reader) written or rewritten, in one language or in several, from what each text must do and not from the text that exists. Words that ask for it: 'rewrite the copy', 'the wording is poor', 'write the interface text in Portuguese and English', 'settle the vocabulary'. It produces the chosen text for every slot in each language, the vocabulary it settled, and a list of the defects it found on the way. It changes no behavior."
---

# Writing the text the user sees

This ends in new text for every slot, written once per language by writers who never saw the old text, the vocabulary that text settled on, and a list of defects found along the way. A slot is one place where the product speaks to its user. It is not a review of the text that exists. The old text is thrown away on purpose, because a writer who sees it writes a variation of it, and a variation keeps its faults.

It is for products whose words are poor, inconsistent, or written in one language and translated. It is not for the product's events, rules, prices, plot or endings, which stay as they are. The text only says them.

## What it takes as given

The behavior of the product, and the decisions about it. The writers are told what each slot does, and none of this recipe's steps changes that.

What a user already knows when each text appears is not known, because the text that would have taught it is being rewritten. You state it as an assumption, in one place, and whoever asked confirms it before any writer starts.

## Before starting

While whoever asked is there, ask in one batch whatever would change the work:

- the texts in scope, and the texts out of scope (the product's story, if it has one, and anything another recipe covers);
- the languages, and whether each is written natively, which is the default, or translated;
- what a user is assumed to know on first contact, as said above;
- the budget, and which models may write. A pilot on one screen, in each language, costs little and shows whether the rest is worth running;
- whether a writer may invent a small detail the notes do not give. If not, every such detail is a finding.

## The roles

The **explainer** is a session with read access to the code. It writes notes about meaning and no wording. A **writer** is an investigator with fresh context, one per language and run, with its own scratch directory and no access to the code. You do the capture, the leak scan, the comparison and the application, and check everything an explainer or a writer reports.

## The steps

1. **Capture.** Run the product on an instance whose data nobody needs, because loading saved scenarios can write to its data. Put a numbered placeholder in place of every text on every screen and state that is in scope, and take a screenshot. Where the screen updates its own text, take the screenshot of a frozen copy, because a live screen can put the old text back between the placeholder and the screenshot. The numbers must be the same in every language. To make them so, align the second language to the first by the structure of the screen, not by position, because the languages differ by a node or two. Give a text that is not on any screen (what a screen reader says, a tooltip, a message that appears only in rare states) a slot of its own with no screenshot, and put each state that cannot be reached by hand into the capture with a saved scenario. Check each scenario against the code, because a scenario that shows a state the product never reaches gives every writer a false fact. Capture a scrolling region whole, lifted out of its layout, and give the screenshots an index of the slot numbers each one shows, built from the placeholders and checked against each screenshot, because a writer who is not made to look at every screenshot looks at a few. Name the screenshots and the scenarios, and write the index's entries, without the product's words, because a file name or a label leaks them as well as a text does. Measure each slot's limits in characters and lines in the product as rendered, for the explainer. Text out of scope is masked with its kind ("[story line]"), never left readable, because it carries the product's words and the writers repeat them.
2. **Explain.** For each slot the explainer writes what it is, what pressing it does and costs, what it must carry, when it appears and does not, the values and units that fill it, its limits in characters and lines, as the capture measured them, and a tag for the concept it expresses, a code that carries no word (such as C12), reused wherever two slots express the same one. It writes each constraint as hard (a real limit of the code or layout, with the reason) or soft (inherited from the old wording, with what else changes with it). It also lists the facts the screen must teach and when to teach each: on first sight, on first use, on demand, or only when it changes. It does not quote, paraphrase closely or suggest any wording, and it does not use the product's own words for its concepts. It describes them.
3. **Scan the notes for leaks.** Search the notes for the product's own terms, in every language, for every old text above a few words, for five words in a row shared with the old text, for the names of files and entries in the code, and for any word the notes use as a name for a concept, the explainer's own coinages included. You dismiss a hit that is an ordinary word the notes cannot do without, and send each other hit back to the explainer, who rewrites the passage, because a script that swaps the word leaves phrases nobody would write. Expect the second pass to be needed. The words a leak puts in the notes are echoed by the writers, so any word the notes contain is not evidence when the writers choose it.
4. **Write.** Each writer gets only the placeholder screenshots and their index, the notes, the product's name in the writer's language, the glossary once there is one, and the brief, which carries the project's rules of form for the text its users read in that language, but none of the product's words, and tells the writer to read nothing else, not even the agent instructions. For each slot it returns three candidates, best first, differing in wording and in how much they say, each with what else must change with it, and, once for all slots, the word it chose for each concept and its questions. It must list the screenshots it opened, and a run whose list is short is repeated. At least two runs per language, because a word chosen once is a guess. The writers of different languages never see each other's output, and a language is never given another's text to translate. Where a template has a count in it, the writer gives the singular and the plural as two plain strings. Answer the writers' questions from the code, and add the answers to the notes, scanned as in step 3, for the writers who come after.
5. **Discover the vocabulary, then settle it.** Group every candidate by concept tag, and count, in each language and across its runs, the words the writers chose. A word the glossary already holds stays decided. Any other word that holds in all runs of its language, and that nothing the writers were given contains, is settled by the evidence. Then read the rest slot by slot, because one concept can cover slots that need different phrasing, and a count by concept alone makes the runs look further apart than they are. Whoever asked confirms the settled words, a word not confirmed joining the rest, and decides the rest from a short list, each with a recommendation, the counts and the cost of the alternatives, because the word for one of the product's concepts [needs an answer](../conventions/decisions.md#what-needs-an-answer). Decisions that follow from another (a unit follows the noun, a letter on a grid follows the name) are derived, not asked. Words are not settled before step 4, because settling them before makes every writer defend the word instead of looking for a better one.
6. **Apply the decisions mechanically.** Write the decided words as a glossary of words to prefer and words to avoid, per language, with the product's other decisions, where `WGM.md` says. A script picks, for each slot and language, the text a decision names, or else the candidate from all that language's runs that fits it best. Only the slots whose best candidate still breaks the glossary go back to a writer, and a named text that breaks it goes back to whoever asked. Changing a decision about a word means editing one line of the glossary and running the script again, which sends back to a writer only the slots no candidate fits.
7. **Check, then apply.** Every chosen text is compared with the behavior it describes, and checked for facts the notes did not give, other than the small details whoever asked allowed. The old text is kept for this comparison only. The texts are applied to the product a group at a time, with its tests, because the product's tests quote its text. A product with few texts can take them all in one change instead, with the tests, provided a test fails on any placeholder left in the product.

## The defects found on the way

The explainers and the writers keep finding places where the product, not the text, is the problem: labels that promise more than an option does, texts that are false in some states, texts that can never appear, and a mechanic the interface does not explain. They go in a list of their own, each verified in the code before it is written down, and are not fixed by wording. Each goes to whoever asked, because changing a behavior can be a choice that [needs an answer](../conventions/decisions.md#what-needs-an-answer).

## What goes wrong

- The writers look at the screenshots only if made to.
- A writer repeats whatever words are in its notes, and a history left in a screenshot or a brief shows up as agreement. Agreement with the old text is not evidence unless the old text was hidden.
- A language that is translated reads as one. Do not give a writer another language's candidates, and read the languages' vocabulary against each other afterwards, because the same concept may need a different word in each.
- A batch of screens written without the decisions already taken invents its own words. Carry the glossary to every later batch.
- A model that writes with more flavor invents more. Compare models on a small task before running one over everything, and weigh what each costs against what it adds.
- A model's refusal to write, or its being stopped by a safety classifier, is a result, to be recorded, not a reason to retry the same request with another model.

## What it ends in

- For each slot and language, the chosen text and the candidates it beat.
- The glossary, with the decisions whoever asked took and the counts they rested on.
- The list of defects found.
- The questions set aside, numbered, each with a recommendation.

Whether the new text works for the people who read it is measured by observing the product in use, as `WGM.md` says it is observed. A pair of finished candidates whoever asked cannot choose between goes to [choosing-between-versions.md](choosing-between-versions.md).
