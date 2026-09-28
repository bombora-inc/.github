# .github

Defaults for every repository in this organization.

GitHub reads certain files from a repository named `.github` and uses them for any repository that
does not have its own copy of that file. Nothing here is applied, deployed or run — a repository
picks a file up simply by not having one.

**This repository must be public for any of that to work.** GitHub ignores default community health
files in a private `.github`. When it is public, the defaults reach every repository owned by the
organization **including the private ones** — the visibility requirement is on this repository, not on
theirs.

## What is here

| Path | What it is |
| --- | --- |
| `.github/PULL_REQUEST_TEMPLATE.md` | Pre-filled into every pull request that has no repository-specific template. Leads with the title, because merges are squashed and the title becomes the commit message that release tooling reads |
| `CONTRIBUTING.md` | The conventions that hold across repositories: commit form, what belongs in a comment, where decisions are written down, how secrets are handled, and how an infrastructure change is verified |
| `SECURITY.md` | How to report a problem privately, and what to do first when a credential has leaked |

## What cannot live here

**`CODEOWNERS`** and **licence files** are not supported as defaults. Both must be added to each
repository — a licence because it has to be present when the project is cloned or packaged, and
`CODEOWNERS` because review routing is per repository by design.

**Shared workflows do not belong here either.** A reusable workflow must live in
`.github/workflows/` of its own repository, which inside this one would mean the path
`.github/.github/workflows/` — legal, and confusing. More importantly, callers pin a tag to a shared
workflow, so it needs a release stream of its own. The files here are live on the default branch and
nobody versions a pull request template.

## Adding to it

A repository that wants something different simply adds its own file of that name. There is no
opt-out to configure and no inheritance to reason about: the local file wins, and if there is none,
this one is used.
