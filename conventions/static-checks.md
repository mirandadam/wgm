# Static checks

This is [STANDARD.md](../STANDARD.md)'s "make it hold by construction" with a tool attached: a test that reads the source, not the running system, and fails when the convention drifts. It is the right tool when the property is true of the _text_ of the repository and the behavioral suite demonstrably cannot see it. Break the property on purpose and watch the suite stay green, then write the check.

Four checks worth writing:

- **A vocabulary.** Each retired word mapped to the one that replaced it, checked against every string a user can read. The mapping, not the ban, is the value.
- **A visual grammar.** A closed set of button classes, status colors and text sizes, with an assertion that the stylesheet defines no rule the markup never names. Class names built by interpolation are a closed list of exemptions, each naming the code that builds it.
- **A configuration surface.** Every environment variable the code reads, held against the runbook, walking the helper functions, not only literal environment access.
- **What may not be published**: a credential or key, in any repository, and, where the repository is public, a real host, home directory or internal name, in the tree and the commit messages alike.

Rules:

- Run a new check against three trees, each a copy in a scratch directory, never `git checkout`:
  1. The clean tree: it stays quiet.
  2. The tree with the violation: it fires. Where the check exists because a committed file broke the rule, the violation is that file as it was.
  3. The fixed tree with the mistake made once more: it fires. A check that no longer fires on the mistake was broken by the fix, and the fix is what is questioned.

  Delete a check that cannot tell the first two apart.

- Exemptions are a closed list with reasons, because an open one lets anyone silence the check without anyone meaning to.
- The failure message names the remedy: what to write instead, which file, which line.
