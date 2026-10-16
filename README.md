# What good means

Everyone wants good work, but few can say what good means. What good means, or wgm, is how I say it: a standard for software work, with recipes, which are procedures a person or a coding assistant runs in your repository. At its heart are five items, in the order every change is judged by.

1. **Trustworthy.** It does what it claims, and can show it.
2. **Good to use.**
3. **Easy to change.**
4. **Cheap to run.**
5. **Cheap to build.**

The first is a condition, never traded. The other four are costs, ranked by who pays them longest and most often: the people who use the product, the next person to change it, those who run it, and whoever builds it now. That is why "cheap to build" comes last. It is paid once, while a shortfall in any item above it is paid for as long as the product lives. [STANDARD.md](STANDARD.md#the-order) says what each item asks, and its checks for "Good to use" are written for a product used in a web browser. wgm also serves a product that is itself a text, such as a presentation, a report or an official document, as [STANDARD.md](STANDARD.md) says.

With the recipes come conventions for how things are named, placed and written and for how a project shows that its claims are true. All of it is written for you, whoever does the work. It takes for granted that you know your tools, so it says what to do and what doing it costs, not how to use them.

This is the standard I hold my own work to. Use it as it is, adapt it through your `WGM.md`, or write your own starting from it. The license allows all three.

## Layout

| File or folder | What it holds |
| --- | --- |
| [`STANDARD.md`](STANDARD.md) | The ranked order every change is judged by (one condition, then four costs), and what "Good to use" and "Easy to change" require in practice. |
| [`recipes/`](recipes/README.md) | Procedures for reviewing and planning work, observing a product in use, choosing between two versions of a text, a rule or a design, and learning from a session. Each is run when someone asks for it, or at the milestone of a standing review, and most are expensive by design: reviewing a change sends from two to eleven assistant sessions by default. |
| [`conventions/`](conventions/) | Rules for what things are called, where they live, how decisions, texts and tests are written, and how a project shows that its claims are true. Each says what holds where `WGM.md` is silent, and the template asks for what differs. |
| [`template/`](template/) | A blank for the one file your repository keeps of its own, `WGM.md`, and an example filled in for an invented project. |
| [`CONTRIBUTING.md`](CONTRIBUTING.md) | How to report a problem or propose a change. |
| [`LICENSE`](LICENSE) | The text of CC BY 4.0, the license of everything but `template/TEMPLATE.md`, which is under CC0 1.0. |

## Using it

To decide whether to use it, read [`STANDARD.md`](STANDARD.md), then how a recipe is chosen in [`recipes/README.md`](recipes/README.md), then [`template/EXAMPLE.md`](template/EXAMPLE.md). You read the rest when you fill in the template or when a recipe points you to it.

Your assistant needs the whole of wgm, unedited, within reach, and there are two ways to give it that. Where the assistant can reach the internet, point it at this repository at a fixed tag or commit, such as `https://github.com/mirandadam/wgm/tree/<tag or commit>`. Where it cannot, keep a whole copy where it can read it: a git submodule, a clone beside your repositories, or a plain copy. A submodule takes one command:

```
git submodule add https://github.com/mirandadam/wgm.git wgm
```

Anyone who later clones your repository runs `git submodule update --init`, or clones with `--recurse-submodules`, because otherwise their `wgm/` folder is empty. Say so in your README, where they will read it, and have the `wgm` line of your `WGM.md` point to that note, so that an assistant that finds the folder empty can name the command. A pipeline that runs an assistant needs `git submodule update --init` too, or its checkout's option for submodules, because many pipelines, such as GitHub Actions and GitLab CI, check out without submodules by default.

Installing the recipes one at a time as an assistant's skills (instruction files it loads by name) does not work, because their links to [`STANDARD.md`](STANDARD.md) and to one another break. An assistant that loads the whole tree as skills keeps the links.

Then, in your repository:

1. Copy [`template/TEMPLATE.md`](template/TEMPLATE.md) to `WGM.md`, beside your agent instructions (the file a coding assistant reads first, such as `AGENTS.md` or `CLAUDE.md`).
2. Fill it in, starting with where wgm is. A link names its tag or commit, a submodule's commit is recorded by your repository, and a clone shows its own. A plain copy keeps no git history, so write its tag or commit down, taking it from the clone you copied it from, or from the link you downloaded it from, such as `https://github.com/mirandadam/wgm/archive/<tag or commit>.zip`. For the choices the conventions leave to you, read the files in [`conventions/`](conventions/), check what your hooks and pipelines do, and answer every line. Name in your `WGM.md` where you already write decisions down, such as your issues. That is your [specification](conventions/decisions.md#where-decisions-are-written), and wgm asks for no other. [`template/EXAMPLE.md`](template/EXAMPLE.md) shows one filled in for a running product, at the length to aim for.
3. Paste this line into your agent instructions exactly as written:

   ```
   Read `WGM.md` beside this file first, then `STANDARD.md` and `recipes/README.md` in the wgm it names. If you cannot find those two, stop and say so.
   ```

`WGM.md` is the file you own. It says where things are, and where your repository writes what it has decided. You never edit this repository to fit yours, because everything in it looks up the facts it needs in that file.

## Status

This is the second release, v0.2. It was drafted with an assistant and reviewed with its own recipes, but I have not yet read every file line by line, so its rules may change until 1.0, as I adopt each file and as running the recipes teaches something. Its use for texts that are the product is the least tried. If something here is wrong or unclear, report it as an issue on this repository.

## License

Copyright (C) 2026 Daniel Araújo Miranda. Licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/), whose full text is in `LICENSE`. You may copy, share, change and use any part of it, commercially or not. If you share it, keep the copyright notice, give credit, link to the license, say if you changed it, and do not suggest that I endorse you or your use. A credit line can read: "What good means (wgm), Copyright (C) 2026 Daniel Araújo Miranda, https://github.com/mirandadam/wgm, CC BY 4.0, https://creativecommons.org/licenses/by/4.0/".

The exception is `template/TEMPLATE.md`, which is dedicated to the public domain under [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/). Copy it and fill it in. The result is yours, and you owe no attribution or notice. The line that step 3 of "Using it" asks you to paste may also be copied with no attribution or notice.
