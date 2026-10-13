---
name: reviewing-the-exposure
description: "Use when the requester asks for a security review, an audit of access control, or whether the product keeps what it holds from those not allowed to see or change it. It covers the whole tree, reports, and changes nothing."
---

# Reviewing the exposure

A review of a whole repository for what it lets out: who can see or change what they should not, what reaches the system unchecked, what one principal can learn of another's, and where a secret or a copy of the data sits. For one change, use the exposure perspective in [reviewing-a-change.md](reviewing-a-change.md).

## Principles

1. **A rule enforced only where the untrusted party runs is not enforced.** A client, a form or a document can hide an operation, but only the side that holds the data can refuse it.
2. **Absence is a finding.** A check that exists nowhere is reported as missing. Do not assume a check exists because the code around it would need one.

## Perspectives

Every brief names where the rules of who may see what are written, and the deployment the project actually has.

- **Who may see or change what**: for every operation that reads or writes something owned or restricted, trace the check that grants it: where it runs, what it reads, and what happens when the principal is anonymous, deactivated or of another group. Drive the real interface out of order and as the wrong user. List the operations with no check, and the checks that exist only where the untrusted party runs.
- **What reaches the system**: every place input crosses in: request bodies, query parameters, uploads, headers used for routing, identifiers interpolated into a query or a shell, HTML rendered back to a person. For each, find the validation that stands between it and the store, the file system, the shell or another person's screen.
- **What keeps one principal from another**: where the product holds data for more than one tenant, user or group, find the mechanism that separates them (a schema, a role, a filter, a key), and every path that reaches the store without passing through it: raw queries, background workers, exports, search indexes, caches, logs.
- **Secrets and copies**: for every credential, key and token, trace where it is read from, where it is written (logs, error messages, responses, the repository and its history), and where a full copy of the data can leave (backups, downloads, debug endpoints).

## Procedure

1. Read the rules first: the documents that say who may see what, and the requirements behind them. Ask the requester for a running instance and a credential for each kind of principal the perspectives drive, and, where `WGM.md` does not say, where the rules of who may see what are written and what deployment the project has.
2. Run the perspectives in parallel. For a claim about behavior, require the request that shows it.
3. Where the product runs, verify a finding by making the request. A finding that rests on reading alone says so.

## Report

Open with the boundary in one sentence: where the product refuses what it should, and whether anything gets around it. Then findings ranked by what an attacker reaches first, each naming the operation, the principal that should not reach it, the place where the rule holds or fails (never the screen that hides it), and the fix that makes the next mistake harder: a check by construction over a check by convention. Then what holds, named so it is not disturbed. Close with what could not be verified without credentials, a running instance or a copy of the data, and what would settle it.

In a public repository, the report and its findings are kept in the private place `WGM.md` names, or with the requester, because each finding is a way in until it is fixed. The same holds for any question set aside, or finding declined, that carries one. None of these goes anywhere the public can read, such as the backlog, a plan, the specification or a frozen analysis, and a plan records only that they are kept privately.
