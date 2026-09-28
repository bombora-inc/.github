# Conventions

These apply to every repository in this organization that does not state otherwise. They exist
because a repository is read far more often than it is written, usually by someone who was not
there when it was written.

## Commits and titles

**Conventional commits, always** — `type(scope): description`, then a blank line and a body saying
**why**. The diff already shows what.

Types: `feat`, `fix`, `docs`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`, `revert`. A scope
is required and names the area touched. A breaking change takes `!` after the type or scope and a
`BREAKING CHANGE:` footer.

**Those two are checked. The rest of the title is convention, and it is git's, not ours.** Start the
description with a lowercase word, leave off the trailing full stop, keep it under about 72
characters, and write it in the imperative — "widen the window", not "widened" or "widens".

> The title sentence after the "area:" prefix omits the full stop at the end, and its first word is
> not capitalized.

— [git, `Documentation/SubmittingPatches`](https://github.com/git/git/blob/master/Documentation/SubmittingPatches)

It is not checked because it cannot be, without also refusing titles git itself calls correct:
`refs: HEAD is also treated as a ref` is right, and no regular expression can tell `HEAD` from
`Widen`. It still matters, because these titles are the release notes and inconsistency shows up
there as a page in several voices.

**The pull request title is the one that reaches `main`.** Merges are squashed, so the title
becomes the commit message, and release tooling reads it to decide the next version. Commits on the
branch are not checked; they vanish in the squash.

## What goes in a comment, and what does not

**Explain the enduring reason, not where it came from.** "Matches the old system" is worthless once
the old system is gone. Write what will still be true: what the setting does, what breaks if it
changes, what constraint it protects.

**No references to a moment in time.** No ticket numbers, no "phase two", no "as discussed". A
reader with nothing but this repository has to be able to follow it. File paths are fine — those
travel with the repository.

**Spend the words on what is unfamiliar.** A paragraph explaining an obvious field, next to one
line on a subtle protocol behaviour, is exactly backwards.

## Decisions

Anything that closed off an alternative is written up in `docs/adr/` as a numbered record: what was
chosen, what else was considered, and **specifically why each alternative loses**. If an alternative
was genuinely close, say so. A decision recorded as obvious when it was not gets reopened by the
first person who spots the trade-off that was left out.

One decision per file. If it needs the word "also", it is two.

A superseded record stays. Write a new one and link back — why something changed is worth more than
a tidy directory.

## Secrets

**Never in a repository.** Not in code, not in configuration, not in a comment, not temporarily to
test something.

Values live in a secrets manager, are added by hand once, and are read at runtime by the identity
that needs them. Prefer having no secret at all: a connection that authenticates as a workload
identity has no password to leak, rotate or store.

Be aware that **Terraform state contains secret values in plain text**. Anything passed through a
Terraform resource is readable by anyone who can read the state file, which is why secret values
are created outside Terraform wherever possible.

## Changes to infrastructure

**Verify at execution time, not from the code.** After applying a change, run it again and confirm
no changes. A second run that reports changes is a defect.

**Apply incrementally.** One thing at a time, confirm the no-op, then move on. Do not run everything
and inspect the wreckage.

**Prefer a mechanical check to an eyeball check.** "All of them are correct" is a scripted sweep,
not a scroll through a list.

**Absence is not a setting.** "Nothing is declared" and "the default is off" are different
statements, and which one is true is a property of the system, not of the file. Read what the
running object carries before writing a comment claiming it carries nothing.
