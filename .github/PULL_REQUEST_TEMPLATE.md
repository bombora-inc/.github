<!--
The title is the part that matters most, because merges here are squashed and the title becomes the
commit message on main. It has to be a conventional commit — type(scope): description — and svu
reads it to decide the next version. A check enforces it and branch protection makes that check
required, so the merge button stays grey until the title is right.

    feat(estimation): widen the request stale window to 30 minutes
    fix(query): stop retrying an invalid filter
    feat(api)!: rename the build endpoint          breaking, bumps the major

Delete any section below that does not apply. An empty heading is worse than no heading.
-->

## What changes, and why

<!-- The diff shows what. Say why: what was wrong, or what became possible. -->

## How it was verified

<!--
Not "the command succeeded" but "the thing the command was for now works". For infrastructure that
usually means a plan somebody read, an apply, and then a read of the running system confirming it
took. Paste the line that proves it.
-->

## Rolling it back

<!--
Only if this is hard to undo. Literal values, no variables — the reader may be under pressure and
unable to reach the file that would tell them what a variable expands to. State the trigger: the
observable symptom that means stop.
-->

## Anything that now has to be remembered

<!--
A manual step, a value added by hand, a limit that will be hit later, a cost that recurs. If the
answer is "nothing", delete this section rather than writing "nothing".
-->
