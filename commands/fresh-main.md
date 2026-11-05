---
description: Stash any in-progress work, checkout main, and pull latest
---

Prepare a clean main branch for new work:

1. Run `git status --short` and `git branch --show-current`; remember the starting branch.
2. If the working tree is dirty (modified, staged, or untracked files):
   `git stash push -u -m "wip: <starting-branch> <today's date>"`.
   If it is clean, skip stashing. Never use `git stash` without the `-m` message.
3. Run `git switch main` (if already on main, skip).
4. Run `git fetch origin`, then fast-forward only:
   `git merge --ff-only origin/main`.
   If the fast-forward fails because local main has diverged, stop and report — do not merge or rebase without asking.
5. Run `git status --short` to confirm clean.

Report: the starting branch, the stash ref if one was created (and how to restore it: `git stash pop`), the new `main` HEAD hash, and confirmation the tree is clean.
