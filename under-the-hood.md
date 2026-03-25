---
layout: center
transition: fade
---

# Git under the hood

<img src="/img/stranger.jpg" class="rounded mt-4 max-h-52 mx-auto" />

<div class="p-4 border border-green-400 rounded bg-green-50 mt-4">

**Objective:** Verify that branches are pointers to commits and extremely lightweight.

</div>

---

## Down the rabbit hole

You will **never need to go inside `.git`** in daily work — but exploring it reveals exactly how Git works.

Create a new repository, make a couple of commits, then:

```console
$ cd .git
$ ls -l

drwxr-xr-x  branches
-rw-r--r--  COMMIT_EDITMSG
-rw-r--r--  HEAD
drwxr-xr-x  objects
drwxr-xr-x  refs
...
```

**The `.git` directory IS the Git repository.** Delete it and you delete all history (but keep the working files).

---

## Git's object model

Every commit is stored as an **object** containing:
- Author and commit message
- A reference to a **tree object** (the directory listing at that moment)
- Tree objects reference **blob objects** (file contents) or other trees

<img src="/img/commit-and-tree.png" class="rounded mt-2 max-h-56 mx-auto" />

<p class="text-center text-sm text-gray-500 mt-1">Image from the <a href="https://git-scm.com/book/">Pro Git book</a>. License CC BY 3.0.</p>

---

## Commits form a graph

Each commit links to its parent(s). Merge commits have two parents.

<img src="/img/commits-and-parents.png" class="rounded mt-2 max-h-52 mx-auto" />

<p class="text-center text-sm text-gray-500 mt-1">A commit and its parents — from the <a href="https://git-scm.com/book/">Pro Git book</a>. License CC BY 3.0.</p>

This forms a **directed acyclic graph (DAG)**. Branches and tags are simply pointers to commits.

---

## Git is a content-addressed storage system

- Each object is identified by its **SHA-1 hash** (a 40-character hex string).
- The hash is derived from the **content** — the same content always produces the same hash.
- Stored objects never change — modifying a commit creates a **new** object.
- This is why it's very hard to lose committed data: the old objects remain until garbage-collected.

Explore raw objects:
```console
$ git cat-file -p HEAD       # show the commit object
# note the "tree" hash, then:
$ git cat-file -p <tree-hash>   # show the tree
$ git cat-file -p <blob-hash>   # show a file's contents
```

---

## Demo: Branches are just files

Create a branch and look inside `.git/refs/heads/`:

```console
$ git switch --create idea
$ cd .git/refs/heads
$ ls -l

-rw-r--r--  idea
-rw-r--r--  main

$ cat idea
045e3db14740c60684d745e5fb891ae71e335611
```

A branch is literally a **text file containing a commit hash**. That's it.

---

## Demo: Creating branches manually

Copy that file to create new branches instantly:

```console
$ cp idea idea-2
$ cp idea idea-3
$ cp idea idea-4
$ cp idea idea-5
```

Now edit `.git/HEAD` to point to `idea-3`:
```
ref: refs/heads/idea-3
```

Back in the working directory:
```console
$ git branch

  idea
  idea-2
* idea-3
  idea-4
  idea-5
  main
```

**You just created 4 branches and switched to one by editing two text files.**

---

## Demo: `git add` doesn't lose data

A common fear: *"I staged version A, then staged version B — is A gone?"*

```console
$ echo 'Once added, hard to lose!' > test-add
$ git add test-add
$ echo 'Oops' > test-add
$ git add test-add
```

Version A seems gone — but it's stored as a **dangling blob**:

```console
$ git fsck

dangling blob dc3b15f60045eea7a87639436ed75021130579e0

$ git cat-file -p dc3b
Once added, hard to lose!
```

Git only garbage-collects unreferenced objects after a while. **If you committed it, it's almost impossible to truly lose.**

---

<div class="p-4 border border-blue-400 rounded bg-blue-50">

**Discussion**
- Why does Git use content-based hashes instead of sequential integers (1, 2, 3...)?
- What does it mean that branches are just text files pointing to hashes?
- How does this explain why creating a branch costs almost nothing?

</div>