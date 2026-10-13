---
name: reviewing-documentation
description: "Use when the requester asks for a docs critique, a documentation review, or whether the docs are accurate. It gives each section a verdict, then fixes the sections in verdict order."
---

# Reviewing documentation

How a document is written is in [conventions/writing.md](../conventions/writing.md), and what belongs in each kind of document, and where it lives, is in [conventions/documents.md](../conventions/documents.md). This recipe is where breaches of those two files are found.

## The checklist

1. **Factual accuracy.** Every claim (URLs, field names, commands, paths) matches its source of truth, such as the codebase. Where the document is the specification or a plan, as [conventions/documents.md](../conventions/documents.md) defines them, it is the source of truth, and code that disagrees with it is handled as [conventions/decisions.md](../conventions/decisions.md#where-decisions-are-written) says. Verify what a grep can verify. A credential written in a document is a breach of "Trustworthy", whether it is correct or not, and the fix says where to get it instead.
2. **Correct terminology.** Proper nouns, diacritics and field names appear exactly as the source of truth spells them, because a reader who searches for a name spelled another way finds nothing.
3. **Completeness.** A list that reads as exhaustive is exhaustive, or says that it is not, because a reader stops looking once a list seems complete.
4. **No duplication**, as [one authoritative home per fact](../conventions/documents.md#naming-and-placement) asks. Find every fact stated in two documents, and check whether the copies have already diverged.
5. **Tables for repeated structure**: items with a role, a status, a yes/no property. Prose for relationships and reasoning.
6. **Only what the reader is meant to copy goes in a code block**, because readers copy whatever they see formatted as code. A pattern used inside a config file is explained by a comment in that file instead.
7. **Concrete language.** "Services with empty credentials are skipped" beats "credential-dependent services are conditionally provisioned".
8. **Organized by task, not by component**, as [group by task, not by layer](../conventions/documents.md#naming-and-placement) asks. Read the headings alone: if they name components, rewrite them.

## Working through a document set

One investigator per document set, on the tree under review, which nobody changes while they read, lists every section by heading and fills in a row for each:

| Section | Reader question it answers | Issues found | Verdict |
| ------- | -------------------------- | ------------ | ------- |

The verdicts:

| Verdict | Meaning |
| --- | --- |
| **STRONG** | A newcomer following it will succeed without reading the source. |
| **ADEQUATE** | Covers the main claim, misses an option or a secondary case. |
| **WEAK** | Reads fine while leaving the reader stuck or with a wrong mental model. |
| **BROKEN** | Makes someone do the wrong thing: a wrong command, path or sequence. |
| **MISLEADING** | The heading claims something the content does not deliver, including a list that implies completeness and is not complete. |

The table and the fixes it implies are the report. Whoever runs the recipe verifies each row, then fixes BROKEN and MISLEADING first, then WEAK, then ADEQUATE, because the work can stop before the end, and what is left undone should then be what does least harm. A document that sends the reader wrong does more harm than one that only fails to help.
