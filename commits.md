---
layout: center
transition: fade
---

# Recording changes

The most basic Git task: **recording changes with commits**.

<div class="p-4 border border-green-400 rounded bg-green-50 mt-4">

**Objectives**
- Record new changes to our own copy of the project.
- Understand adding changes in two separate branches.
- See how to compare different versions.

</div>

---

## Background

- Each **commit** is a snapshot of the entire project at a point in time, identified by a unique **hash**.
- A **branch** is a line of development — like a sticky note attached to a commit that moves forward as we add commits.
- **Tags** are like sticky notes that *don't* move — used to mark important versions.

<img src="/img/gopher/gophers.png" class="rounded mt-2 max-h-48 mx-auto" />

What if two people make two different changes at the same time? Git can merge them.

---

## What we want to achieve

<img src="/img/illustrations/branches.png" class="rounded mt-2 max-h-64 mx-auto" />

We'll create a new branch, add a recipe, then also modify something on `main` — so both branches diverge.

---

## Exercise: Practice creating commits and branches (20 min)

1. Make sure you are on **your fork** (`USER/recipe-book`, not `cr-workshop-exercises/recipe-book`)
2. Create a **new branch** called `new-recipe` and add a recipe file to it.
3. In a **new commit**, modify the recipe you just added.
4. Switch to **`main`** and modify a different recipe there.
5. Browse the **network graph** (Insights → Network) and locate your commits.
6. **Compare** your branch with `main` — find the differences.
7. Compare **two arbitrary commits** in the repository.
8. **Rename** the branch you created, then browse the network again.
9. Create a **tag** for one of your commits (on GitHub: create a "release").

---

## Solution: (1) Make sure you are on your fork

<img src="/img/commits/fork.png" class="border rounded mt-2 max-h-48 mx-auto" />

Your username should appear in the URL, and you should see "forked from ..." below the repo name.

---

## Solution: (2) Create a branch and add a recipe

**On GitHub:** Click the branch selector (top left, shows "main"), type `new-recipe`, and click "Create branch new-recipe from main":

<img src="/img/commits/github-create-branch.png" class="border rounded mt-2 max-h-44 mx-auto" />

Then navigate to the `sides/` directory → Add file → Create new file. Use this template:

```markdown
# Recipe name
## Ingredients
- Ingredient 1
## Instructions
- Step 1
```

---

**In VS Code:** Source Control → ⋯ → Branch → Create Branch, then switch to it:

<img src="/img/commits/vscode-create-branch.png" class="border rounded mt-2 max-h-36 mx-auto" />

Click `+` in the Source Control sidebar to stage, then commit:

<img src="/img/commits/vscode-add-and-commit.png" class="border rounded mt-2 max-h-36 mx-auto" />

---

**Command line:**
```console
$ git switch --create new-recipe main
$ git add sides/mixed-nuts.md
$ git commit -m "Add mixed nuts recipe"
```

**RStudio:** Git tab → New Branch → fill name → Create.

<img src="/img/commits/rstudio-create-branch.png" class="border rounded mt-2 max-h-36 mx-auto" />

---

## Solution: (4) Switch to main and modify a recipe

**GitHub:** Use the branch selector (top left) to switch back to `main`. Edit an existing recipe (not the one you just created — it won't even be visible on `main`).

**VS Code:** Use the branch selector at the bottom of the window:

<img src="/img/commits/vscode-change-branch.png" class="border rounded mt-2 max-h-36 mx-auto" />

**Command line:**
```console
$ git switch main
# modify a file, then:
$ git add <file>
$ git commit -m "Short summary"
```

---

## Solution: (5) Browse the commits

The `main` and `new-recipe` branches have now diverged.

**GitHub:** Insights → Network view

**Command line:**
```console
$ git graph
* b4de93b (HEAD -> main) add spring onion to poke
| * dc5d6f0 (new-recipe) adding chocolate to the mixed nuts recipe
| * b4035e3 add mixed nuts recipe
|/
*   554c187 (origin/main) Merge branch 'alex/fruit-salad'
```

**VS Code:** Open Terminal (View → Terminal) and use the command line method:

<img src="/img/commits/vscode-open-terminal.png" class="border rounded mt-2 max-h-32 mx-auto" />

---

## Solution: (6) Compare branches

**GitHub:** Add `/compare` to your repo URL:
```
https://github.com/USER/recipe-book/compare
```

**Command line:**
```console
$ git diff main new-recipe
$ git diff new-recipe main
$ git diff --name-only main new-recipe   # only file names
```

---

## Solution: (9) Create a tag

**GitHub:** Branch switcher → Tags → View all tags → Create a new release:

<img src="/img/commits/github-create-tag.png" class="border rounded mt-2 max-h-52 mx-auto" />

GitHub "releases" are Git tags with extra metadata.

**Command line:**
```console
$ git tag -a v1.0 -m "New manuscript version for the pre-print"
```

---

## Discussion

- Commit directly to `main` when there is only one line of work and it's just you.
- Use **branches** when multiple lines of work should not interfere.
- **Tags** mark important milestones — they don't move when new commits are added.
- Branches in Git are just lightweight sticky notes — creating one costs almost nothing.
- Use `.gitignore` to avoid committing temporary files, credentials, or build artifacts.