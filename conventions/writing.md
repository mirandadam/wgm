# Writing

This file says how to write what other people read: commit messages, merge request descriptions, issues and the comments on them, formal communications, messages to whoever decides, reports and documentation, and texts that are themselves the product, such as a presentation. Rules for a language go in a file beside this one, such as [writing-pt-br.md](writing-pt-br.md), and apply to the texts written in that language.

## Who reads each text

- **Merge request description**: the reviewer, who decides from the description alone whether to open the code. The reviewer needs what was wrong and what changes, with any measurement a convention asks for, not the story of the investigation.
- **Commit message**: a developer who finds the commit in the log months later. The developer needs the problem and the change, because the diff shows the rest. The title says what changed, literally, without metaphor.
- **Issue**: whoever will fix it or decide when. They need the symptom as the user sees it, the cause if it is known, and what is proposed. Code details go in only where they point to the exact place.
- **Comment on an issue**: whoever follows the issue and reads the comment without rereading the thread. The first sentence gives the verdict in the word that reader is looking for, such as "approved", "not approved", "decided", "fixed" or "does not reproduce". The rest of the comment supports it.
- **Formal communication** (a dispatch, an official letter, a memorandum): the unit that receives it, acts on it and files it, knowing only what the text says. It says what it asks or sends and under which rule. It does not justify itself against the recipient ("the documents go together so that the request is not returned again"). Instead, what goes beyond the rule is sent "in addition".
- **Message to whoever decides**: the manager, coordinator or advisor who decides from it. They need the decision being asked for and what it rests on.
- **Report**: whoever asked for it and will use it. They need the answer to what they asked, then what supports it.
- **Documentation section**: whoever will do the task it describes, standing at that step. They need what to do, in order, and what goes wrong.

## How to write

- Give each subject its own paragraph. Do not write telegraphic fragments, arrows, or lists of facts joined by semicolons.
- State each fact once, without a summary followed by the same detail, and without words the sentence does not need. Exactness comes before economy: write "rounded down to the nearest power of 2", not "rounded down to a power of 2", and "does not remove them on its own" when that is what happens, not "does not remove them". Do not explain what this reader already knows, because whoever fixes an issue knows the code.
- Cut what the reader does not use, but keep every fact the reader would have to ask for. A sentence cut as a repeat goes only when each of its clauses is found in the place that keeps it. The usual ceilings are 120 words for a commit message, 150 for a comment, 200 for an issue and 250 for a merge request description, not counting markers or closing lines. Documents have no ceiling, because a ceiling set without comparing texts would be a guess. Going a little over is fine when every sentence is needed, but going far over means something the reader does not use is still there.
- The first time something is mentioned, name it in full: "the Garnet container image" and "version 2.1.7", not "the image" and "2.1.7". Use the precise verb, not the team's slang for it.
- Use the field's common term. Do not invent labels or metaphors, and where the source material has one, replace it with the common term or describe the thing. A term or label that a law, a contract or the text being answered defines or uses is kept as written there, because the reader of the text being written applies that definition. Prefer the literal description even to a figure of speech the field uses often: "files that nothing deletes" rather than "orphaned files", and "waited 180 seconds" rather than "slept". Each sentence says who does what.
- Open with the concrete fact, not a summary that announces it without saying what it is: "the cache holds 512 MiB of the 2 GiB configured", not "the cache holds less than configured".
- Call each thing by the same word throughout the text. A synonym chosen for variety makes the reader wonder whether a second thing is meant: once it is "the tile", it is not later "the block".
- Items joined in a sentence or in a list share one grammatical form and one kind: facts with facts, judgments with judgments. Write "a click on the × or on the checkbox", not "a click on the × or unchecking the box".
- When one clause gives a cause, a consequence, a contrast or a condition of another, name the relation with its word ("because", "so", "but", "if"). A colon or a semicolon between such clauses leaves the reader to guess the relation: write "installing the recipes one at a time does not work, because their links break", not "does not work: their links break". A colon still introduces an example, a list, or what the sentence before it announces.

## Rules that were tried and dropped

These were tried and are not rules, each for its reason:

- "One idea per sentence" and "explain every term the reader may not know" made every text longer without making it clearer.
- "Effect before mechanism" produced vague openings, the kind "Open with the concrete fact" forbids.
- "No internal names" produced roundabout phrasing, and "say what the reviewer should check" produced a stock sentence at the end of every description.
- "A file opens with what it lets its reader do" did no better than an opening that names concrete things, which "Open with the concrete fact" already asks for.
- "A pronoun refers to something named in the same sentence or the one before" broke list items that complete the sentence opening the list.
- Giving each rule of "How to write" a name, so that a review could cite it, made no difference a review could show.
- A strict word limit shortened texts only slightly and broke the connections between sentences.
