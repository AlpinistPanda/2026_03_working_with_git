---
layout: center
transition: fade
---

# Interrupted work

<div class="p-4 border border-green-400 rounded bg-green-50 mt-4">

**Objective:** Learn to switch context or abort work without panicking.

</div>

> There is almost never reason to clone a fresh copy to complete a task you have in mind.

---

## The real world is chaotic

You're in the middle of a debugging spree — 27 modified files, debug prints everywhere.

Your colleague walks in: *"Can you fix and commit this thing right now?"*

**What do you do?**

Git gives you several clean ways to handle this without losing anything.

---

## Option 1: Stashing

`git stash` temporarily stores your working directory and staging area changes, returning your code to the last commit state.

```console
$ git stash              # put away all changes
$ git stash pop          # bring them back
$ git stash list         # see all stashes
$ git stash save NAME    # give it a name (useful if it might sit for a while)
$ git stash drop         # drop the most recent stash
```

Stashes form a **stack** — you can stash multiple batches and pop them in any order with `git stash pop INDEX`.

---

## Exercise: Stashing (15 min)

1. Make a change to a file.
2. Check `git status` / `git diff`, then `git stash`. Check again — changes are gone.
3. Make a **separate, unrelated** change (different lines). Commit it.
4. `git stash pop` — your original changes are back.

**Optional / advanced:**
5. Stash twice. Check `git stash list`. Pop them in reverse order.
6. Stash a change, then modify the **same line** differently, then `git stash pop`. What happens? (Hint: resolve the conflict like a merge conflict — no extra commit is created.)
7. What does `git graph` show when you have something stashed?

---

<div class="p-4 border border-gray-300 rounded bg-gray-50">

**Solutions**

5: `git stash pop INDEX` lets you choose which stash to pop.

6: Git asks you to resolve the conflict the same way as a merge conflict.

7: It shows an extra commit hash with `refs/stash`.

</div>

---

## Option 2: Create a branch

Branches work just as well for this — and are harder to forget about than stashes:

```console
$ git switch --create temporary   # save current work-in-progress
$ git add PATHS
$ git commit

$ git switch main                 # go handle the urgent thing
# ... fix, commit ...

$ git switch temporary            # come back and resume where you left off
```

Later: merge or rebase `temporary` onto `main` when you're ready.

---

## Storing junk you don't need but don't want to lose

Sometimes you write something, don't need it right now, but don't want to delete it.

**Stash:** quick and easy, but easy to forget.

**Branch:** better for longer-term storage — branches show up in `git graph` and `git branch`, making them harder to overlook if you come back weeks later.

> Note: if you leave a branch alone for too long and `main` moves on, merging later can get messy — but at least the data is still there.