# Documents and naming

This file says what kinds of document a project keeps, where each lives and when it stops existing, and how things are named and placed.

## Three kinds, three homes

- **Directives** tell a reader _what to do and why_: the specification (the decisions about what the product does) and the procedures and conventions of the work. The specification holds no implementation specifics, such as file paths or config values, because how a decided behavior is carried out belongs to the code and the as-built reference. The specification grows with the number of decisions, not with the size of the code, and where it grows with the code, it is describing what was built.
- **As-built references** describe _how things actually work_, for a developer in the codebase. They keep what the code cannot say (the reasons, the order of a task, the ways it goes wrong) and drop what the code says plainly.
- **Frozen analyses** are point-in-time reports: audits, comparisons, studies, observations of people using the product. A published analysis is never edited afterwards, except to remove what must not be kept there, such as a secret, because it says what was known on the day, and a document that keeps changing cites it by date. The insights drawn from observations are such a document.

`WGM.md` says where yours live. Put each fact in the kind that owns it. No document gives the size or the number of the repository's own files, because both are stale on the next commit.

## A finished plan is deleted

A plan approved and not yet executed sits beside the agent instructions, unless `WGM.md` names another place. It belongs to none of the three kinds, and it is deleted, with its log and with the approval of whoever asked, when the change that executes it is finished, by the commit that finishes that change where the plan is in the repository. First move every durable fact the plan and its log carry into the kind of document that owns it, or into the backlog. Deciding where each goes is the whole of the work.

## The backlog holds only what is still open and still actionable

An entry says what to do and where to start. Something deliberately left unfixed is a declined finding, not an entry, and [decisions.md](decisions.md#what-is-not-proposed-again) says where it goes. Why an entry matters and how it was measured go where the backlog keeps its history (the commit that adds the entry, or a comment on the issue), so that the entry stays short. A decision is not an entry, and is asked of whoever asked instead.

## A directive states a rule

It never leaves a question open or weighs options, because a reader follows either as if it were the rule. Where a rule is not settled, a procedure or convention states the current default as the rule, and the specification, which holds only decisions, leaves it out and asks.

## Naming and placement

- **Group by task, not by layer.** Readers look for "share a record", not "the permissions module".
- **One authoritative home per fact and per function.** A constant, helper or fact is _defined_ in exactly one place, and everything else links to it or imports it, because two copies drift apart and the reader cannot tell which is right. A specification that states a decision the code implements is not a second copy, because the specification is the fact.
- **Match the domain and the existing vocabulary**, in the domain's own language, and use the same name for the same concept in every layer, because a concept with two names reads as two concepts.
- **Order by the reader's path**, simplest task first, because most readers come for the simplest task and stop once they have it.
- **Explain why, not what.** A comment justifies a non-obvious choice or warns of a pitfall. A comment beside a decided behavior names the decision it serves, and no comment presents an incidental choice as a requirement. Where the code needs a _what_ comment, make the code clearer instead.
