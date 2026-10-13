# What good means, here

This is the `WGM.md` of an invented project that uses wgm. Its product is built from several services, each in a repository of its own, and the repositories are checked out side by side under one folder that is not itself a repository.

## Pointers

- **wgm** is at `wgm/`, a clone beside the repositories.
- **Who may answer**: the warehouse operations manager, for anything that needs an answer. Reach them by a comment on the change's issue, or in the terminal when they take part in the session.
- **Where things are written**: each of the product's decisions is written, with why it was taken, in the issue of the change it belongs to, and the product's vocabulary is in the glossary issue. Each repository's README is its as-built reference. Frozen analyses, observations of use among them, are kept beside this file, dated in their text, and the insights drawn from the observations in the README of the repository they concern. Recordings and quotations are kept on the team's restricted drive. The backlog is `PENDING.md`, beside this file. Plans take the default. `data-scripts/AGENTS.md` adds agent instructions for that repository alone.
- **Good to use, here**: the product is used on a laptop on the office network and on a phone on the warehouse floor's wifi, and the budget for waiting is measured by hand on both before each tag. The people already know the vendor's old desktop tool, and the labels keep its names.
- **How use is observed**: in the field form, one warehouse operator a week, during a real shift.
- **Conventions in force**: none of the four static checks exists, which is the default. `ISSUE_REVIEW.md`, beside this file, says how issues on the tracker are reviewed, and no recipe replaces it.
- **What blocks a change**: only a person reviewing the merge request. There is no pre-commit hook, and the one pipeline (`web-client/.gitlab-ci.yml`) runs only on a tag, to build a release. Linters in four of the repositories and the API's test suite are run by hand and only report.

## Standing reviews

| Review | Hunts for | Recipe and perspectives | Milestone |
| --- | --- | --- | --- |
| Stock levels | a stock level that no longer matches what was counted | `reviewing-a-change.md`, with stored data as the first round's added perspective and correctness among the second round's | a merge request that changes how stock is computed, since two defects have reached the warehouse from there |
