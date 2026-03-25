---
layout: center
transition: fade
---

# Cloning a Git repository and working locally

So far we've worked in the browser. Now we move to your **own computer**.

<div class="p-4 border border-green-400 rounded bg-green-50 mt-4">

**Objectives**
- Clone a repository from the web and work with it locally.
- Do the same things as before (commit, branch, merge) but **locally**.
- Understand remote repositories.

</div>

---

## What is cloning?

<img src="/img/illustrations/clone.png" class="rounded mt-2 max-h-52 mx-auto" />

**Cloning** = copying the *entire* repository (all commits, branches, tags) to your computer. It's a full backup.

Changes on your local clone **do not** automatically appear on GitHub — you have to actively **push** them.

---

## What is inside a Git repository?

- All files and directories of the project.
- The **complete history** of all changes (commits).
- All branches and tags.
- Everything stored in the hidden `.git` folder at the root of the repository.

---

## Exercise: Clone and work locally (25 min)

1. **Configure Git** if you haven't already (`user.name`, `user.email`, editor).
2. **Clone** your fork of the recipe book.
3. **Create a new branch**.
4. Make a **commit** on your new branch.
5. **Switch** back to `main` and create one or two commits there.
6. **Merge** the new branch into `main`.
7. Compare the graph **locally vs. on GitHub** — see the difference?
8. Explore **remote branches**: list them and create a local branch from one.

---

## Solution: (2) Cloning the repository

**Command line (SSH):**
```console
$ git clone git@github.com:USER/recipe-book.git
```

**Command line (HTTPS):**
```console
$ git clone https://github.com/USER/recipe-book.git
```

**VS Code:** New window → "Clone Git Repository..." → paste URL → choose folder → open.

**RStudio:** File → New Project → Version Control → Git → paste URL → Create Project.

---

## Solution: (3) Creating branches locally

**Command line:**
```console
$ git switch --create another-recipe main
# or, from current branch:
$ git switch --create another-recipe
```

**VS Code:** Source Control → ⋯ → Branch → Create Branch (auto-switches):

<img src="/img/commits/vscode-create-branch.png" class="border rounded mt-2 max-h-36 mx-auto" />

---

## Solution: (4) Creating commits locally

**Command line:**
```console
$ git add new-file.md
$ git commit -m "Short summary of the change"
```

**VS Code:** Click `+` to stage, enter message, click Commit:

<img src="/img/commits/vscode-add-and-commit.png" class="border rounded mt-2 max-h-40 mx-auto" />

---

## Solution: (5) Switching branches

**Command line:**
```console
$ git switch main
# modify a file, then:
$ git add <file>
$ git commit -m "Short summary"
```

**VS Code:** Branch selector at the bottom:

<img src="/img/commits/vscode-change-branch.png" class="border rounded mt-2 max-h-40 mx-auto" />

---

## Solution: (6) Merging branches locally

**Command line:**
```console
$ git branch           # confirm you are on main
$ git status           # another way to check
$ git merge another-recipe
```

**VS Code:** Source Control → ⋯ → Branch → Merge → select source branch:

<img src="/img/merging/vscode-merging.png" class="border rounded mt-2 max-h-40 mx-auto" />

---

## Solution: (7) Local vs. remote graph

**Command line:**
```console
$ git graph
$ git log --graph --oneline --decorate --all
```

Then compare with Insights → Network on GitHub.

**Result:** Your new branch and local commits won't appear on GitHub — they exist only locally. You need to **push** to share them.

---

## Solution: (8) Remote branches

**Command line:**
```console
$ git branch          # local branches only
$ git branch --all    # includes remote-tracking branches

  another-recipe
* main
  remotes/origin/main
  remotes/origin/alex/fruit-salad
  remotes/origin/radovan/lasagna
```

Create a local branch from a remote one:
```console
$ git switch alex/fruit-salad   # shortcut — Git finds the remote match
# or explicitly:
$ git switch --track origin/alex/fruit-salad
```

**RStudio:** The branch picker lists remote branches — click one to create and track it locally:

<img src="/img/commits/rstudio-remote-branches.png" class="border rounded mt-2 max-h-36 mx-auto" />

---

## Summary

- Cloning gives you a **full backup** — all history, all branches, all tags.
- Local work (branches, commits) stays local until you **push**.
- Remote branches and local branches are separate — a local branch must exist before you can commit to it.
- We'll practice pushing in the next episode.