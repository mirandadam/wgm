# What good means, here

This is the `WGM.md` of an invented project that uses wgm. Its product is built from several services, each in a repository of its own, and the repositories are checked out side by side under one folder that is not itself a repository.

## Pointers

- **wgm** is at `wgm/`, a clone beside the repositories.
- **Where things are written**: each of the product's decisions is written, with why it was taken, in the issue of the change it belongs to, and the product's vocabulary is in the glossary issue. Each repository's README is its as-built reference. Frozen analyses, observations of use among them, are kept beside this file, dated in their text, and the insights drawn from the observations in the README of the repository they concern. Recordings and quotations are kept on the team's restricted drive. The backlog is `PENDING.md`, beside this file.
- **Good to use, here**: the product is used on a laptop on the office network and on a phone on the warehouse floor's wifi, and the budget for waiting is measured by hand on both before each tag. The people already know the vendor's old desktop tool, and the labels keep its names.
- **How use is observed**: in the field form, one warehouse operator a week, during a real shift.
- **Conventions in force**: `ISSUE_REVIEW.md`, beside this file, says how issues on the tracker are reviewed, and no recipe replaces it.
- **Standing reviews**: stock levels, hunting a stock level that no longer matches what was counted, with `reviewing-a-change.md`, stored data as the first round's added perspective and correctness among the second round's, on a merge request that changes how stock is computed, since two defects have reached the warehouse from there.
- **What blocks a change**: only a person reviewing the merge request. There is no pre-commit hook, and the one pipeline (`web-client/.gitlab-ci.yml`) runs only on a tag, to build a release. Linters in four of the repositories and the API's test suite are run by hand and only report.
