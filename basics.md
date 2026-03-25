---
layout: center
transition: fade
---

# Git basics

<div class="p-4 border border-green-400 rounded bg-green-50 mt-4">

**Objectives**
- Create Git repositories and make commits.
- Understand the structure of a repository.
- Inspect project history.
- Write useful commit messages.

</div>

---

## What is Git and a Git repository?

- Git is a version control system: **records and saves snapshots** of a folder as it changes over time.
- Every **commit** is a snapshot of the *entire project* at that moment, assigned a unique version hash.
- Snapshots live inside a hidden `.git` folder — delete it and you delete the history (but keep the files).
- The `.git` folder uses relative paths — you can move the whole repo and it still works.
- Git **does not record anything automatically** — you have to ask it to.
- Many interfaces exist: command line, graphical apps, web interfaces.

---

## Recording a snapshot

Git records changes in **two steps**: stage, then commit.

```console
$ git add FILE.txt          # stage (focus)
$ git commit                # commit (save the snapshot)
```

<img src="/img/git_stage_commit.svg" class="rounded mt-2 max-h-52 mx-auto" />

---

## Configuring Git (command line)

Set these once before you start:

```console
$ git config --global user.name "Your Name"
$ git config --global user.email yourname@example.com
$ git config --global core.editor nano
$ git config --global init.defaultBranch main
```

Verify:
```console
$ git config --list
```

---

## Creating a repository

**Command line:**
```console
$ mkdir recipe
$ cd recipe
$ git init -b main
$ git status        # check what's going on
```

**GitHub (browser):** Click "+" → "New repository":

<img src="/img/basics/new-repo-plus.png" class="border rounded mt-2 max-h-36 mx-auto" />

Fill in the form and check **"Add a README file"**:

<img src="/img/basics/new-repo-form.png" class="border rounded mt-2 max-h-40 mx-auto" />

---

## Adding files and committing

Create `ingredients.txt` and `instructions.txt`, then:

**Command line:**
```console
$ git add ingredients.txt
$ git commit -m "adding ingredients"

$ git add instructions.txt
$ git commit -m "adding instructions"
```

**Browser:** Click **"Add file"** → **"Create new file"**:

<div class="grid grid-cols-2 gap-4 mt-2">
<img src="/img/basics/add-file.png" class="border rounded w-full" />
<img src="/img/basics/edit-file.png" class="border rounded w-full" />
</div>

---

Edit the commit message before saving:

<img src="/img/basics/commit-changes.png" class="border rounded mt-2 max-h-44 mx-auto" />

---

## Exercise: Record changes

Add `1/2 onion` to `ingredients.txt` and `"enjoy!"` to `instructions.txt`.

**Command line** — first see what changed:
```console
$ git diff
```

Then commit each change separately:
```console
$ git add ingredients.txt
$ git commit -m "add half an onion"
$ git add instructions.txt
$ git commit        # without -m: Git opens your editor for the message
```

**Browser:** Click the pen symbol to edit:

<img src="/img/basics/pen-symbol.png" class="border rounded mt-2 max-h-36 mx-auto" />

---

## Git history and log

**Command line:**
```console
$ git log
$ git log --oneline
$ git log --stat
```

**Browser:** Click the history/commits icon:

<div class="grid grid-cols-2 gap-4 mt-2">
<img src="/img/basics/commits.png" class="border rounded w-full" />
<img src="/img/basics/history.png" class="border rounded w-full" />
</div>

---

Key things about commit hashes:
- Each uniquely identifies a project state
- Not integers — they're content-based checksums (so two identical contents always produce the same hash)
- `--oneline` shows first 7 characters — usually enough to identify a commit uniquely
- Output is **newest first**

---

## Ignoring files with `.gitignore`

Not everything should be committed: compiled binaries, generated files, secrets.

Create a `.gitignore` file in your repo:

```shell
# ignore compiled Python files
*.pyc
__pycache__

# ignore generated HTML
*.html
!foo.html      # except this one (manually maintained)

# ignore everything under build/
build/
```

- `.gitignore` should itself be committed — so all contributors see the same behaviour.
- **All files should be either tracked or ignored.**
- See [github/gitignore](https://github.com/github/gitignore) for templates.

---

## Graphical interfaces

Command line and browser aren't the only options:

- [GitHub Desktop](https://desktop.github.com)
- [SourceTree](https://www.sourcetreeapp.com)
- [Full list of GUIs](https://git-scm.com/downloads/guis)

---

## Summary cheatsheet

```console
$ git init -b main   # initialize a new repository
$ git add FILE       # stage a file for the next commit
$ git commit         # create a commit from staged changes
$ git status         # see what's going on
$ git log            # see history
$ git diff           # show unstaged changes
$ git show HASH      # show a specific commit
$ git mv             # move/rename a tracked file
$ git rm             # remove a tracked file
```

> Git is not ideal for large binary files — consider [git-annex](http://git-annex.branchable.com) for those.

---

<div class="p-4 border border-green-400 rounded bg-green-50">

**Key points**
- One command to start: `git init -b main`
- Commits tell a story — write them as if someone else needs to understand in 15 years.
- Git stores everything in `.git` — the working directory is just a view.
- Commit often. Better too many than too few.

</div>