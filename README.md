# What good means

Everyone wants good work, but few can say what good means. What good means, or wgm, is how I say it: a standard for software work, with recipes, which are procedures a person or a coding assistant runs in your repository. At its heart are five items, in the order every change is judged by.

1. **Trustworthy.** It does what it claims, and can show it.
2. **Good to use.**
3. **Easy to change.**
4. **Cheap to run.**
5. **Cheap to build.**

The first is a condition, never traded. The other four are costs, ranked by who pays them longest and most often: the people who use the product, the next person to change it, those who run it, and whoever builds it now. "Cheap to build" comes last because it is paid once, while a shortfall in any item above it is paid for as long as the product lives. [STANDARD.md](STANDARD.md#the-order) says what each item asks. Its checks for "Good to use" are written for a product used in a web browser, and wgm also serves a product that is itself a text, such as a report or an official document. With the recipes come conventions for how things are named, placed and written. All of it takes for granted that you know your tools, so it says what to do and what doing it costs, not how to use them.

This is the standard I hold my own work to. Use it as it is, adapt it through your `WGM.md`, or write your own starting from it. The license allows all three.

## Layout

| File or folder | What it holds |
| --- | --- |
| [`STANDARD.md`](STANDARD.md) | The ranked order every change is judged by, and what "Good to use" and "Easy to change" require in practice. |
| [`GOOD-TO-USE.md`](GOOD-TO-USE.md) | Part of the standard: seven rules for a product used in a web browser. |
| [`recipes/`](recipes/README.md) | Procedures for reviewing and planning work, choosing between two versions of a text, a rule or a design, writing the text a product's users read, and learning from a session, each run when someone asks for it or at a standing review's milestone. Most are expensive by design. |
| [`conventions/`](conventions/) | What things are called, where they live, how decisions, texts and tests are written, and how a project shows that its claims are true. Each holds where `WGM.md` is silent. |
| [`template/`](template/) | A blank for `WGM.md`, the optional file where your repository says what differs from wgm's defaults, and an example filled in for an invented project. |
| [`CONTRIBUTING.md`](CONTRIBUTING.md) | How to report a problem or propose a change. |
| [`LICENSE`](LICENSE) | The CC BY 4.0 license, which covers everything but `template/TEMPLATE.md` and the line "Using it" asks you to add, both free to copy as the License section says. |

## Using it

To decide whether to use it, read [`STANDARD.md`](STANDARD.md), then how a recipe is chosen in [`recipes/README.md`](recipes/README.md), then [`template/EXAMPLE.md`](template/EXAMPLE.md). You read the rest when you fill in the template or when a recipe points you to it.

Your assistant needs wgm within reach: a link to this repository at a fixed tag or commit, such as `https://github.com/mirandadam/wgm/tree/<tag or commit>`, or a whole copy where it can read it, as a git submodule (`git submodule add https://github.com/mirandadam/wgm.git wgm`), a clone beside your repositories, or a plain copy. A submodule is empty in a clone made without `--recurse-submodules`, and in a pipeline that does not fetch submodules, until `git submodule update --init` runs, so say so in your README. A recipe links to others, so one installed alone, such as an assistant's skill, loses what those links point to.

Then add a line like this one to your agent instructions (the file a coding assistant reads first, such as `AGENTS.md` or `CLAUDE.md`), naming where wgm is with its tag or commit, which a plain copy does not keep, so take it from the clone or the link you copied it from:

```
Follow wgm at <link or path, with its tag or commit>. Before you change anything in the repository, or when asked for a review, a plan or an opinion on the work, read its `STANDARD.md` and `recipes/README.md`, and if you cannot find them, stop and say so.
```

Where wgm's defaults do not fit your project, copy [`template/TEMPLATE.md`](template/TEMPLATE.md) to `WGM.md` beside your agent instructions, fill in the lines that differ, and add "Read `WGM.md` beside this file first." to the line above. Name where you already write decisions down, such as your issues: that is your [specification](conventions/decisions.md#where-decisions-are-written), and wgm asks for no other.

## Status

This is the third release, v0.3. It was drafted with an assistant and reviewed with its own recipes, but I have not yet read every file line by line, so its rules may change until 1.0, as I adopt each file and as running the recipes teaches something. Its use for texts that are the product is the least tried. Parts of `reviewing-a-change.md`, `making-a-plan.md` and `writing-text-user-sees.md` have not been run as they now read, so they are not known to work. If something here is wrong or unclear, report it as an issue on this repository.

## License

Copyright (C) 2026 Daniel Araújo Miranda. Licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/), whose full text is in `LICENSE`. You may copy, share, change and use any part of it, commercially or not. If you share it, keep the copyright notice, give credit, link to the license, say if you changed it, and do not suggest that I endorse you or your use. A credit line can read: "What good means (wgm), Copyright (C) 2026 Daniel Araújo Miranda, https://github.com/mirandadam/wgm, CC BY 4.0, https://creativecommons.org/licenses/by/4.0/".

The exception is `template/TEMPLATE.md`, which is dedicated to the public domain under [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/). Copy it and fill it in. The result is yours, and you owe no attribution or notice. The line "Using it" asks you to add may also be copied with no attribution or notice.
