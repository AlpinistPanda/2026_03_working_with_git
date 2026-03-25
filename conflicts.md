---
layout: center
transition: fade
---

# Conflict resolution

<div class="p-4 border border-green-400 rounded bg-green-50 mt-4">

**Objective:** Understand merge conflicts well enough to fix them.

</div>

---

## What is a conflict?

Two branches modify the **same part** of the same file in **two different ways**:

<div class="grid grid-cols-3 gap-3 mt-4">

<div class="p-3 border border-gray-400 rounded bg-gray-50 text-sm">

**Original:**
```
1 tbsp cilantro
2 avocados
1 chili
1 lime
1 tsp salt
1/2 onion
```

</div>

<div class="p-3 border border-blue-400 rounded bg-blue-50 text-sm">

**Branch A** (more cilantro, more lime):
```
2 tbsp cilantro
2 avocados
1 chili
2 lime
1 tsp salt
1/2 onion
```

</div>

<div class="p-3 border border-purple-400 rounded bg-purple-50 text-sm">

**Branch B** (less cilantro, more onion):
```
1/2 tbsp cilantro
2 avocados
1 chili
1 lime
1 tsp salt
1 onion
```

</div>

</div>

Git can figure out the lime and onion changes — but not the cilantro conflict.

---

## Conflicts are good!

- Git will **not silently overwrite** one of two differing modifications.
- Conflicts look scary but with practice they're manageable — and rare.
- You don't encounter conflicts in simpler systems because you *can't do* the parallel work those systems prevent.

<div class="p-4 border border-blue-400 rounded bg-blue-50 mt-4">

**Discussion**
- What if two people work on the same file but different sections?
- What if you work in isolation for 6 months and then try to merge?
- How are conflicts avoided in non-Git collaboration? (Only one person at a time? Declaring intent upfront?)

</div>

---

## Preparing a conflict

Create two branches with conflicting changes to cilantro:

```console
$ git branch like-cilantro main
$ git branch dislike-cilantro main

# on like-cilantro: change to 2 tbsp cilantro
# on dislike-cilantro: change to 1/2 tbsp cilantro
```

Verify the differences:
```console
$ git diff main like-cilantro
$ git diff main dislike-cilantro
```

---

## Merging — the conflict appears

The first merge succeeds:
```console
$ git switch main
$ git merge like-cilantro       # fast-forward, no conflict
```

The second fails:
```console
$ git merge dislike-cilantro

CONFLICT (content): Merge conflict in ingredients.txt
Automatic merge failed; fix conflicts and then commit the result.
```

Check status:
```console
$ git status
# both modified: ingredients.txt
```

---

## What the conflict looks like



Git inserts **conflict markers**:
- `<<<<<<< HEAD` — your current branch's version
- `=======` — the divider
- `>>>>>>> dislike-cilantro` — the incoming branch's version

---

## Resolving the conflict

<div class="p-4 border border-green-400 rounded bg-green-50">

**Steps:**
1. `git status` and `git diff` — see what's in conflict
2. Edit the file — decide what to keep, remove all conflict markers
3. The file should now look exactly how you want it
4. `git status` and `git diff` again — verify
5. `git add ingredients.txt` — mark as resolved
6. `git commit` — complete the merge (message is pre-filled)

</div>

---

## Optional: Using `git mergetool`

A visual tool makes it easier — current branch is left, incoming is right, result is in the middle:

<img src="/img/conflict-resolution/mergetool.png" class="border rounded mt-2 max-h-52 mx-auto" />

```console
$ git mergetool
```

After resolving, close the tool and commit. No `git add` needed when using `mergetool`.

---

## Strategies: ours or theirs

When you know which version to keep without manual editing:

```console
# Keep our version (current branch) when in doubt:
$ git merge -s recursive -Xours less-avocados

# Keep their version (incoming branch) when in doubt:
$ git merge -s recursive -Xtheirs less-avocados
```

---

## Aborting a merge

Not ready to resolve? Talk to a colleague first?

```console
$ git merge --abort
```

The repository returns exactly to the state before the merge.

---

## Avoiding conflicts

**Human measures:**
- Plan which branch you'll commit to before starting
- Don't put unrelated changes on the same branch

**Collaboration measures:**
- Open an issue and discuss before starting a long-lived branch

**Technical measures:**
- **Share early and often** — push frequently, the selfish thing is also the kind thing
- Pull/rebase often to stay up to date with upstream
- Resolve conflicts while they're small

---

<div class="p-4 border border-green-400 rounded bg-green-50">

**Key point:** Conflicts usually appear because of insufficient communication or a suboptimal branching strategy — not because Git is broken.

</div>