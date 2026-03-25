---
layout: center
transition: fade
---

# Copy and browse an existing project

Instead of starting from scratch, we'll explore an **existing repository** first — so you can see all the cool Git features before creating your own.

<div class="p-4 border border-green-400 rounded bg-green-50 mt-4">

**Objectives**
- See a real Git repository and understand what's inside it.
- Understand how version control enables advanced history inspection.
- See how Git allows multiple people to collaborate easily.
- **See the big picture** instead of memorising commands.

</div>

---

## Creating your own copy by forking

A **repository** is a collection of files tracked by Git. A **GitHub repository** adds access control on top.

<img src="/img/illustrations/fork.png" class="rounded mt-2 max-h-52 mx-auto" />

We'll fork the exercise repository to get our own copy — which we'll modify in later exercises.

---

Go to the repository on GitHub and click **"Fork"** (top right):

<img src="/img/browsing/forking.png" class="border rounded mt-2 max-h-56 mx-auto" />

You'll be redirected to **YOUR/recipe-book** — your personal copy.

> Always be aware: are you looking at *your* fork or the *upstream* original?

---

## Exercise: Browsing an existing project (25 min)

Browse the **recipe-book** repository and explore commits and branches. Use hints below.

1. Browse the **commit history** — are messages understandable?
2. Compare history with the **network graph** (Insights → Network). Find the branches.
3. How can you find out when a recipe was **last modified**?
4. How many changes did the **Guacamole** recipe receive?
5. Which recipes include the ingredient **"salt"**?
6. In Guacamole, find out **who modified each line last** (Blame view). Who added cilantro?
7. Can you **use or share** these recipes? Look for a license file.
8. Browse **Issues and Pull Requests** in the upstream repository.

---

## Solution: (1) Commit history

Every change, when it happened, and who made it. Each change has a unique identifier like `554c187`.

<img src="/img/browsing/history.png" class="border rounded mt-2 max-h-64 mx-auto" />

**Command line:** `git log` or `git log --oneline`

---

## Solution: (2) Network graph

The commit history looks linear, but the network view reveals branches and merges.

<img src="/img/browsing/network.png" class="border rounded mt-2 max-h-64 mx-auto" />

**GitHub:** Insights → Network tab

**Command line:** `git log --graph --oneline --decorate --all`

---

## Solution: (3) When was a file last modified?

Navigate to the file and click **"History"** (top right):

<img src="/img/browsing/file-history.png" class="border rounded mt-2 max-h-60 mx-auto" />

**Command line:** `git log sides/guacamole.md`

---

## Solution: (5) Search for "salt"

<img src="/img/browsing/search.png" class="border rounded mt-2 max-h-56 mx-auto" />

> Searching a freshly-forked repo may take a few minutes while the index builds.

**Command line:** `git grep salt` or `git grep -C 3 salt` (3 lines of context)

---

## Solution: (6) Who modified each line? (Blame)

<img src="/img/browsing/annotate.png" class="border rounded mt-2 max-h-60 mx-auto" />

Switch to "Blame" view in the file browser. Click the commit message to see the full change.

**Command line:** `git annotate sides/guacamole.md`

---

## Solution: (7) License

<img src="/img/browsing/license.png" class="border rounded mt-2 max-h-60 mx-auto" />

The `LICENSE` file says **Creative Commons Zero 1.0** — equivalent to public domain. Use freely, no conditions.

---

## Solution: (8) Issues and Pull Requests

In the **upstream** repository (`cr-workshop-exercises/recipe-book`):

- **Issues** — notes, bug reports, and feature ideas. They create a permanent discussion record.
- **Pull Requests** — proposed changes. Anyone can propose; only the owner can accept.

---

## Summary

- Git lets us understand a project much more deeply than just files on disk.
- By forking the repository, we created our own copy — ready for making changes in the next exercise.
- Viewing history, blame, search, and network graphs are all built-in Git/GitHub features.