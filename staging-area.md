---
layout: center
transition: fade
---

# Using the Git staging area

<div class="p-4 border border-green-400 rounded bg-green-50 mt-4">

**Objectives**
- Learn how to tell a story with your commit history.
- Demystify the Git staging area.

</div>

---

## Commit history is telling a story

Your code is important — but the *history* is too. It explains how the code came to be.

Which of these histories is most useful?

<div class="grid grid-cols-2 gap-4 mt-2 text-sm">

<div class="p-3 border border-green-400 rounded bg-green-50">

**Good — logical units:**
```
6f0d49f implement feature C
fee1807 implement feature B
6fe2f23 implement feature A
```

</div>

<div class="p-3 border border-red-400 rounded bg-red-50">

**Bad — noise:**
```
ab990f4 saving three months of work
bf39f9d more work on feature B
45831a5 removing debug prints...
72d78e7 feature A broken, starting B
49dc419 wip
```

</div>

</div>

We want clean commits — but we also want to **save often**. The staging area solves this tension.

---

## Interactive commits: `git commit --patch`

The simplest way to commit only part of your changes:

```console
$ git commit --patch    # or: git commit -p
```

For each change, you choose:
- `y` — include this change in the commit
- `n` — skip it for now
- `s` — split into smaller pieces (if separated by blank lines)
- `q` — abort everything
- `?` — more options

The `-p` flag also works on `add`, `restore`, `checkout`, and `reset`.

---

## Exercise: Interactive commits

1. Make **two changes** in `instructions.txt` — one at the top, one at the bottom.
   **Make sure they're separated by several unmodified lines.**
2. Run `git commit --patch` and commit one of the changes.
3. Repeat for the other change.
4. Inspect with `git log`, `git status`, `git diff`, `git diff --staged`.

> **When is this useful?** When you've made several changes to a file but want to record them as separate logical commits.

---

## The staging area

What if there are so many changes you can't sort them out in one interactive session?

The **staging area** is a preparation zone — a middle ground between your working directory and the next commit.

You can stage, unstage, and restage multiple times before committing.

---

## Analogy: moving boxes

- You're moving and have a box to pack.
- You can put things in and take them out.
- You wouldn't mix bathroom, kitchen, and living room items in one box.
- **Staging** = putting items in the box.
- **Committing** = sealing it and sticking on a descriptive label.

---

## Analogy: shopping receipts

You need two receipts — one for work items, one for home items.

1. Go through the store and collect everything in your basket (`work in progress`).
2. At checkout, put **home stuff** on the conveyor belt (`git add`).
3. Check the belt (`git diff --staged`) and your basket (`git diff`).
4. Pay (`git commit`).
5. Repeat for work stuff.

---

## Staging area commands

```console
$ git add FILE          # stage a file (or changes within it)
$ git diff              # show unstaged changes (working dir vs. staging)
$ git diff --staged     # show staged changes (staging vs. last commit)
$ git diff HEAD         # show all changes (working dir vs. last commit)
```

Undo operations:
```console
$ git restore FILE              # discard unstaged changes
$ git restore --staged FILE     # unstage (keep changes in working dir)
$ git reset --soft HEAD~1       # undo last commit, keep changes staged
```

---

<img src="/img/staging-basics.svg" class="rounded mt-2 max-h-72 mx-auto" />

---

## Exercise: Using the staging area

1. Make **two different changes** to `ingredients.txt` and `instructions.txt` that don't belong together.
2. Use `git add` to stage **only one** of the changes.
3. Use `git status`, `git diff`, and `git diff --staged` to see what's going on.
4. Feel some regret — **unstage** the staged change with `git restore --staged`.

---

<div class="p-4 border border-blue-400 rounded bg-blue-50 mb-4">

**Discussion**
- When is it better to "save" with `git commit` vs. just `git add`?
- Is it a problem to make many small commits?

</div>

<div class="p-4 border border-green-400 rounded bg-green-50">

**Key point:** The staging area helps you create well-defined, logical commits — even when your actual work is messy.

</div>