---
layout: center
transition: fade
---

# Branching and merging

<div class="p-4 border border-green-400 rounded bg-green-50 mt-4">

**Objectives**
- Create and merge branches.
- Know the difference between a branch and a tag.

</div>

---

## Why branches?

So far our repository has been linear:

<img src="/img/gitink/git-branch-1.svg" class="rounded mt-2 max-h-28 mx-auto" />

But software development is rarely linear. We typically need:
- A working version at all times
- The ability to work on multiple features simultaneously
- A way to experiment without breaking the main project

---

<img src="/img/gopher/gophers.png" class="rounded max-h-52 mx-auto" />

Version control lets us **isolate different tracks of work** which can later be merged:

<img src="/img/gitink/git-collaborative.svg" class="rounded mt-2 max-h-36 mx-auto" />

---

## Key concepts

- **Branch** = a pointer (sticky note) attached to a commit. It moves forward as new commits are added.
- **`main`** is just a convention — nothing special about it compared to other branches.
- **HEAD** = where you are right now (literally, not a placeholder).
- Commits form a **directed acyclic graph** (DAG).
- Creating a branch is nearly free — it's just a label.

---

## Useful alias: `git graph`

Set this up now — we'll use it constantly:

```console
$ git config --global alias.graph "log --all --graph --decorate --oneline"
```

Then:
```console
$ git graph

* e7cf023 (HEAD -> main) don't forget to enjoy
* 79161b6 add half an onion
* a3394e3 adding README
* 3696246 adding instructions
* f146d25 adding ingredients
```

---

## Creating and working with branches

Create a branch `experiment` from `main` and switch to it:

```console
$ git branch experiment main   # create branch from main
$ git switch experiment        # switch to it
$ git branch                   # list branches
```

Add cilantro to `ingredients.txt`, then commit twice:

```console
$ git commit -m "let us try with some cilantro"
# (reduce amount)
$ git commit -m "maybe little bit less cilantro"
```

```console
$ git graph

* bcb8b78 (HEAD -> experiment) maybe little bit less cilantro
* f6ec7b7 let us try with some cilantro
* e7cf023 (main) don't forget to enjoy
```

---

## Exercise: Create and commit to branches

Create a second branch `less-salt` from `main`, reduce the salt, commit:

```console
$ git branch less-salt main
$ git switch less-salt
# reduce salt in ingredients.txt
$ git commit -m "reduce amount of salt"
```

Then switch back to `main` and improve the README:

```console
$ git switch main
# edit README.md
$ git commit -m "improve the documentation"
```

---

You should now have 3 branches diverging from a common ancestor:

<img src="/img/gitink/git-branch-3.svg" class="rounded mt-2 max-h-52 mx-auto" />

```console
$ git graph

* b4af65b (HEAD -> main) improve the documentation
| * bf28166 (less-salt) reduce amount of salt
|/
| * bcb8b78 (experiment) maybe little bit less cilantro
| * f6ec7b7 let us try with some cilantro
|/
* e7cf023 don't forget to enjoy
```

---

## Exercise: Merging branches

Merge `experiment` into `main`:

```console
$ git branch   # confirm you are on main
$ git merge experiment
```

<img src="/img/gitink/git-merge-1.svg" class="rounded mt-2 max-h-32 mx-auto" />

Then merge `less-salt` too:

```console
$ git merge less-salt
```

<img src="/img/gitink/git-merge-2.svg" class="rounded mt-2 max-h-32 mx-auto" />

---

Git automatically merges the changes:

```console
$ cat ingredients.txt

* 1 tbsp cilantro   ← from experiment branch
* 2 avocados
* 1 chili
* 1 lime
* 1 tsp salt        ← from less-salt branch
* 1/2 onion
```

No manual merging needed — Git figured it out because the changes were in **different parts** of the file.

---

## Deleting branches safely

After merging, check which branches are safe to delete:

```console
$ git branch --merged

  experiment
  less-salt
* main
```

Delete them — only the labels disappear, not the commits:

```console
$ git branch -d experiment
$ git branch -d less-salt
```

<img src="/img/gitink/git-deleted-branches.svg" class="rounded mt-2 max-h-36 mx-auto" />

> `git branch -D` forces deletion of an **unmerged** branch — the commits become hard to find.

---

## Tags

- A **tag** points to a commit and **never moves** (unlike a branch).
- Think: branch = sticky note, tag = commemorative plaque.
- Used to mark releases and important milestones.

Create an annotated tag:
```console
$ git tag -a nobel-2023 -m "recipe I made for the 2023 Nobel banquet"
$ git show nobel-2023
```

See the [Pro Git book on tagging](https://git-scm.com/book/en/v2/Git-Basics-Tagging) for more.

---

## Summary cheatsheet

```console
$ git branch               # see where we are
$ git branch NAME          # create branch NAME
$ git switch NAME          # switch to branch NAME
$ git switch --create NAME # create and switch in one step
$ git merge NAME           # merge branch NAME into current branch
$ git branch -d NAME       # delete merged branch
$ git branch -D NAME       # delete unmerged branch (careful!)
```

**Typical workflow:**
```console
$ git switch --create new-feature
$ git commit               # work, work, work...
$ git switch main
$ git merge new-feature
$ git branch -d new-feature
```

---

<div class="p-4 border border-green-400 rounded bg-green-50">

**Key points**
- A branch is a unit of work — to be merged with other units.
- A tag is a permanent pointer to a moment in history.
- Creating and deleting branches is cheap — do it often.

</div>