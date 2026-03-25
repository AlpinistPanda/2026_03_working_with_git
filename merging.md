---
layout: center
transition: fade
---

# Merging changes and contributing

Git lets different people work independently — and then **merge** their work together.

<div class="p-4 border border-green-400 rounded bg-green-50 mt-4">

**Objectives**
- Understand that on GitHub, merging happens through a **pull request** — a change proposal.
- Create and merge a pull request within your own repository.
- Optionally contribute to the upstream public repository.

</div>

---

## Background

- In the last episode we added a recipe on a **branch** — to test it before it becomes "live".
- Now we want to bring that change into the **`main`** branch.
- The key: always know **which branch** you are on and **which direction** the merge goes.

<img src="/img/illustrations/merging.png" class="rounded mt-2 max-h-52 mx-auto" />

---

## Exercise: Merging branches with pull requests (20 min)

We assume you created a `new-recipe` branch in the previous exercise.

1. **Navigate** to your branch from the previous episode.
2. **Begin the pull request process** — look for a "Contribute" button in the branch view.
3. **Verify** the pull request: check the target repository and branch. Make sure you merge **within your own repo** (not upstream to `cr-workshop-exercises`).
4. **Create** the pull request. Browse the network — has anything changed yet?
5. **Merge** the pull request. Browse the network again. What changed?
6. Find merged branches and **delete** them. Verify the commits are still there.
7. *(Optional)* Open a pull request **to the upstream** repository.

---

## Solution: (1) Navigate to your branch

Make sure you are on the branch you want to merge **from**:

<img src="/img/merging/github-navigate-to-branch.png" class="border rounded mt-2 max-h-56 mx-auto" />

> For local paths (VS Code, command line, RStudio): switch to **`main`** first — the branch you merge **into**.

---

## Solution: (2) Begin the pull request

On GitHub, click **"Contribute"** in the branch view:

<img src="/img/merging/github-contribute.png" class="border rounded mt-2 max-h-56 mx-auto" />

> For local work, skip to step 5 (merge directly, no PR needed).

---

## Solution: (3) Verify the pull request

Check carefully before clicking Create:

<img src="/img/merging/github-comparing-changes.png" class="border rounded mt-2 max-h-56 mx-auto" />

- **Base repository**: must be *your own* (not `cr-workshop-exercises`)
- **Title**: make it descriptive
- Scroll down to see the commits and diff — are these the right changes?

---

## Solution: (5) Merge the pull request

Review once more, then click **"Merge pull request"**.

Check the network view — `new-recipe` is now merged into `main`.

**Command line / VS Code merge:**
```console
$ git switch main
$ git merge new-recipe
```

<img src="/img/merging/vscode-merging.png" class="border rounded mt-2 max-h-40 mx-auto" />

---

## Solution: (6) Delete merged branches

After merging, GitHub suggests deleting the branch:

<img src="/img/merging/github-merged.png" class="border rounded mt-2 max-h-36 mx-auto" />

Or navigate to the branches overview to delete it later:

<img src="/img/merging/github-branches-overview.png" class="border rounded mt-2 max-h-44 mx-auto" />

**Command line:**
```console
$ git branch --merged     # see which branches are safe to delete
$ git branch -d new-recipe
```

---

## Resolving a conflict (demo)

A **conflict** happens when Git can't automatically decide between two different changes to the same part of a file.

How to create one:
1. Create a new branch from `main` and change a line in a file.
2. On `main`, change the **same line** differently.
3. Try to merge — you'll get a conflict.

How to resolve:
- Click **"Resolve conflicts"** on GitHub — an editor opens showing conflict markers.
- Remove the markers, keep what you want, then commit.

---

## Summary

- Pull requests let you **propose** changes — the owner still decides what gets merged.
- Merging combines development lines. After merging, the branch label is safe to delete — the commits stay.
- Conflicts are Git's way of asking for human judgement when the same code changed in two different ways.
- We will practice collaboration much more in the collaborative Git lesson.