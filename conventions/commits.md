# Commit messages

There are two conventions, for two kinds of repository. A repository follows the one `WGM.md` chooses, or else the one its history shows. `WGM.md` chooses where the history does not show one, as in a new repository or a mixed history. How the message itself is written is in [writing.md](writing.md).

## Unprefixed

For a repository whose log is read as prose, usually by its one maintainer. The subject is a full sentence with no prefix:

> Take the backups and the key material out of the working tree

## Prefixed and typed

For a repository with several maintainers and rotating contributors, where the log is read by tooling and by people who were not there:

- First line: `prefix: short imperative summary`, under 72 characters, because GitHub and similar tools cut a longer one off when they list commits
- Prefixes: those your tooling reads, such as `feat:`, `fix:` and `docs:`
- Reference issue numbers when applicable

## Mechanical commits

Whichever convention you adopt, record bulk formatter sweeps and mass renames in `.git-blame-ignore-revs` (one line per commit hash, with a comment naming the sweep), so `git blame` can skip them once `blame.ignoreRevsFile` is set, which is per-clone.
