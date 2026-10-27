---
name: reviewing-documentation
description: "Use when someone asks for a docs critique, a documentation review, or whether the docs are accurate. It gives each section a verdict, then fixes the sections in verdict order."
---

# Reviewing documentation

How a document is written is in [conventions/writing.md](../conventions/writing.md), and what belongs in each kind and where it lives in [conventions/documents.md](../conventions/documents.md). This recipe is where breaches of those two files are found. One investigator per document set, on the tree under review, lists every section by heading and fills in a row for each: the section, the reader question it answers, the issues found, and the verdict.

The checklist:

1. **Factual accuracy.** Every claim (URLs, field names, commands, paths) matches its source of truth, such as the codebase. Where the document is the specification or a plan, as [conventions/documents.md](../conventions/documents.md) defines them, it is the source of truth, and code that disagrees is handled as [conventions/decisions.md](../conventions/decisions.md#where-decisions-are-written) says. A credential written in a document is a breach of "Trustworthy", whether or not it is correct, and the fix says where to get it instead.
2. **Correct terminology.** Proper nouns, diacritics and field names exactly as the source of truth spells them, because a reader who searches for a name spelled another way finds nothing.
3. **Completeness.** A list that reads as exhaustive is exhaustive, or says that it is not, because a reader stops looking once a list seems complete.
4. **No duplication**, as [one authoritative home per fact](../conventions/documents.md#naming-and-placement) asks. Find every fact stated in two documents, and check whether the copies have diverged.
5. **Tables for repeated structure**, prose for relationships and reasoning.
6. **Only what the reader is meant to copy goes in a code block**, because readers copy whatever they see formatted as code. A pattern used inside a config file is explained by a comment in that file instead.
7. **Concrete language.** "Services with empty credentials are skipped" beats "credential-dependent services are conditionally provisioned".
8. **Organized by task, not by component.** Read the headings alone: if they name components, rewrite them.

| Verdict | Meaning |
| --- | --- |
| **STRONG** | A newcomer following it will succeed without asking anyone. |
| **ADEQUATE** | Covers the main claim, misses an option or a secondary case. |
| **WEAK** | Reads fine while leaving the reader stuck or with a wrong mental model. |
| **BROKEN** | Makes someone do the wrong thing: a wrong command, path or sequence. |
| **MISLEADING** | The heading claims something the content does not deliver, a list that implies completeness included. |

A frozen analysis gets a verdict but no fix, except what [conventions/documents.md](../conventions/documents.md) allows, because it says what was known on the day. The table and the fixes it implies are the report. You verify each row, then fix BROKEN and MISLEADING first, then WEAK, then ADEQUATE, because the work can stop before the end, and a document that sends the reader wrong does more harm than one that only fails to help.
