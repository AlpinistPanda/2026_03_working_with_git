---
layout: center
transition: fade
---

# Practical advice: How much Git is necessary?

---

## Use `git status` constantly

Unsure which branch you're on, or what state the repository is in?

```console
$ git status
```

This is one of the most useful Git commands — it tells you:
- Which branch you're on
- What's staged and about to be committed
- Which files aren't tracked yet

**Use it constantly. It's always safe.**

---

## Writing useful commit messages

Convention: **one line summary, one blank line, then details (if needed)**:

```text
increase alpha to 2.0 for faster convergence

the motivation for this change is to enable ...
...
this is based on a discussion in #123
```

<div class="p-4 border border-blue-400 rounded bg-blue-50 mt-4">

**Key rules**
- **Why** something changed is more important than **what** changed.
- Cross-reference issues and discussions when relevant.
- Bad messages: `"fix"`, `"oops"`, `"save work"`, `"wip"`
- Write for someone else 15 years from now — including future you.

</div>

---

## Good commit message examples in the wild

Browse real projects for inspiration:
- [SciPy](https://github.com/scipy/scipy/commits/main)
- [NumPy](https://github.com/numpy/numpy/commits/main)
- [Pandas](https://github.com/pandas-dev/pandas/commits/main)
- [Flask](https://github.com/pallets/flask/commits/main)

References:
- ["My favourite Git commit"](https://fatbusinessman.com/2019/my-favourite-git-commit)
- ["On commit messages"](https://who-t.blogspot.com/2009/12/on-commit-messages.html)
- ["How to Write a Git Commit Message"](https://chris.beams.io/posts/git-commit/)

> **Better any commit than no commit. Don't let perfect be the enemy of good enough.**

---

## What level of branching complexity?

**Simple personal project:**
- Start with just `main`
- Use branches for unfinished/untested ideas
- Use tags to mark milestones

**Small team, OK with things breaking occasionally:**
- Commit to `main` and feature branches

**Small team, changes reviewed before merging:**
- Create feature branches for all changes
- Merge only via pull/merge requests
- Consider write-protecting `main`

---

## How and when to commit?

- **Commit early and often** — too many commits is better than too few
- Once committed, it's very hard to truly lose your work
- Always commit (or stash) before doing anything risky
- Use the **staging area** to craft clean commits even from messy work
- Later: `git add -p` and `git commit -p` for fine-grained control

---

## How large should a commit be?

- **Better too small than too large** — small commits are easier to combine; large ones are hard to split
- A commit at end of day is a natural unit
- Smaller commits are easier for others to review
- A commit should ideally contain **one logical change** — but imperfect commits are still better than none

---

<div class="p-4 border border-green-400 rounded bg-green-50">

**Key point:** There is no one-size-fits-all. **Start simple and grow your Git practice with your project.**

</div>

<div class="p-4 border border-blue-400 rounded bg-blue-50 mt-4">

**Discussion:** How do you plan to use Git?
- Solo researcher? Small team? Open source project?
- What's the biggest challenge you anticipate?

</div>