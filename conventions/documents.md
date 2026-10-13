# Documents and naming

This file says what kinds of document a project keeps, where each lives and when it stops existing, and how things are named and placed. The three kinds are the same in every project, but the folders that keep them vary from one project to the next.

## Three kinds, three homes

- **Directives** tell a reader _what to do and why_: the vision, the specification (the requester's decisions about what the product does), the constraints on the architecture that the requester decided, and the procedures and conventions of the work. The vision, the specification and the constraints hold no implementation specifics, such as file paths, metric names or config values, because how a decided behavior is carried out belongs to the code and the as-built reference. The specification grows with the number of decisions, not with the size of the code. Where it grows with the code, it is describing what was built.
- **As-built references** describe _how things actually work_, for a developer working in the codebase. They keep what the code cannot say (the reasons, the order of a task, and the ways it goes wrong) and drop what the code says plainly.
- **Frozen analyses** are point-in-time reports: audits, version comparisons, requirements studies, stakeholder summaries.

A project might keep them in `docs/core/`, `docs/dev/` and `docs/analyses/`, and `WGM.md` says where yours live. Put each fact in the kind that owns it. No document gives the size or the number of the repository's own files, because both are stale on the next commit. A document names the files instead.

## An analysis is frozen when it is published

A published analysis is never edited afterwards, because it says what was known on the day it was made, and a later reader needs exactly that. A document that keeps changing cites it by date.

Observations of people using the product are frozen analyses, and the insights drawn from them are an as-built reference. [recipes/observing-use.md](../recipes/observing-use.md) says how each is written.

## A finished plan is deleted

A plan approved and not yet executed sits beside `WGM.md`, unless `WGM.md` names another place. It belongs to none of the three kinds, and it is deleted, with the requester's approval, when the change that executes it is finished. Where the plan is in the repository, the commit that finishes that change deletes it.

To delete it, first move every durable fact the plan carries into the kind of document that owns it, or into the backlog. Then delete the plan. Where it was in the repository, git history keeps it. Deciding where each durable fact goes is the whole of the work. It is [the standard](../STANDARD.md)'s "do now what belongs to now" applied to what a plan leaves behind.

## The backlog holds only what is still open and still actionable

An entry says what to do and where to start. Something deliberately left unfixed is a declined finding, not an entry, and [decisions.md](decisions.md#what-is-not-proposed-again) says where it goes. Why an entry matters and how it was measured go where the backlog keeps its history (the commit that adds the entry, or a comment on the issue), so that the entry stays short. What a person was seen or heard to do goes in an observation, which the entry cites. A decision is not an entry, and the requester is asked instead.

## A directive states a rule

A directive states a rule. It never leaves a question open or weighs options, because a reader follows either as if it were the rule. Where a rule is not settled, the directive states the current default as the rule. The specification is the exception. There, a rule the requester has not settled is not written as a default, and the requester is asked instead.

## Naming and placement

- **Group by task, not by layer.** Readers look for "share a record", not "the permissions module".
- **One authoritative home per fact and per function.** A constant, helper or fact is _defined_ in exactly one place, and everything else links to it or imports it, because two copies drift apart and the reader cannot tell which is right. The home of a decision is where it is written when it is taken, so a specification that states a decision the code implements is not a second copy of the fact. The specification is the fact.
- **Match the domain and the existing vocabulary**, in the domain's own language, and use the same name for the same concept in every layer, because a concept with two names reads as two concepts.
- **Order by the reader's path**, simplest task first, because most readers come for the simplest task and stop once they have it.
- **Explain why, not what.** This is [the standard](../STANDARD.md)'s "write for a person" applied to a comment. A comment justifies a non-obvious choice or warns of a pitfall. A comment beside a decided behavior names its identifier in the specification, and no comment presents an incidental choice as a requirement. Delete a comment whose absence costs the reader nothing, and where the code needs a _what_ comment, make the code clearer instead.
