# Static checks

This is [STANDARD.md](../STANDARD.md)'s "make it hold by construction" with a tool attached. A static check is the cheapest way to make a rule hold: a test that reads the source, not the running system, and fails when the convention drifts.

## When it is the right tool

It is the right tool when the property is true of the _text_ of the repository rather than of its behavior, and when the behavioral suite demonstrably cannot see it. The second condition is the one people skip. Break the property on purpose, as a test of the suite, and watch the suite stay green. Then write the check, because that measurement said so.

## Four checks worth writing

- **A vocabulary.** Each retired word mapped to the one that replaced it, checked against every string a user can read. The mapping, not the ban, is the value.
- **A visual grammar.** A closed set of button classes, status colors and text sizes, with an assertion that the stylesheet defines no rule the markup never names. Class names built by interpolation are a closed list of exemptions, each naming the code that builds it.
- **A configuration surface.** Every environment variable the code reads, held against the runbook. Walk the helper functions, not only literal environment access.
- **What may not be published**: a credential or key, in any repository, and, where the repository is public, a real host, home directory or internal name. The rule covers the tree and the commit messages alike.

The shape of the test suite, how its tests divide among unit, integration and end-to-end, has no check, because nobody could build one from a description of it.

## Rules

- Run a new check against three trees:
  1. The clean tree: it stays quiet.
  2. The tree with the violation: it fires. Where the check exists because a committed file broke the rule, the violation is that file as it was before the fix, but a variant made by hand proves only that the check can fire, not that it catches the mistake that happened.
  3. The fixed tree with the mistake made once more: it fires. A check that no longer fires on the mistake was broken by the fix, and the fix is what is questioned.

  Delete a check that cannot tell the first two apart.

- Make each of those trees as a copy in a scratch directory, never with `git checkout`, as [recipes/reviewing-a-change.md](../recipes/reviewing-a-change.md)'s "Rules that cost a defect to learn" says.
- **Exemptions are a closed list with reasons**, because an open one lets anyone silence the check without anyone meaning to.
- **The failure message names the remedy**: what to write instead, which file, which line.
