# Reporting a security problem

**Do not open an issue.** An issue is public the moment it exists, and it stays in the timeline
after it is closed.

Report it privately through GitHub's advisory form on the repository concerned — **Security** →
**Report a vulnerability**. That creates a private thread visible only to the maintainers.

## What to include

What you found, where, and what it lets someone do. A reproduction is welcome and not required —
a precise description of the weakness is more useful than a working exploit, and safer to send.

## If a credential has leaked

Say so first and explain second. A key in a commit, a token in a log, a value in an issue — the
first action is to revoke it, and that cannot start until somebody knows.

Assume anything that has been pushed to a public repository has been fetched and indexed. Making
the repository private afterwards does not undo that, and neither does rewriting the history.
Rotation is the only remedy.
