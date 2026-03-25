---
layout: center
transition: fade
---

# What to avoid

---

## When committing: what not to do

<div class="grid grid-cols-2 gap-4 mt-2">

<div class="p-3 border border-red-400 rounded bg-red-50">

**Commit messages that explain "what" but not "why"**

As useless as a code comment saying "this is a loop". But don't let imperfect messages stop you from committing at all.

</div>

<div class="p-3 border border-red-400 rounded bg-red-50">

**Committing generated files**

Compiled/generated files make it hard to run on different platforms, add noise to diffs, and inflate repo size.

Use [`.gitignore`](https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files) to exclude them. Use [templates](https://github.com/github/gitignore) for common languages.

</div>

</div>

---

<div class="grid grid-cols-2 gap-4 mt-4">

<div class="p-3 border border-red-400 rounded bg-red-50">

**Committing huge files**

A `git rm` later doesn't remove the file from *history*. The repo stays bloated.

Add size checks to your CI pipeline, or use code review to catch accidental additions.

</div>

<div class="p-3 border border-red-400 rounded bg-red-50">

**Waiting too long because code is "unfinished"**

Many OK-ish commits are better than a few perfect ones. Too few large commits make undoing changes harder.

The longer you wait, the harder it gets to commit at all.

</div>

</div>

---

<div class="p-4 border border-red-400 rounded bg-red-50 mt-4">

**Committing unrelated changes together**

Makes it hard to undo one change without also undoing the other.

But: big ugly commits are still better than no commits — especially in early, chaotic project phases.

</div>

---

## When working with branches: what not to do

<div class="p-3 border border-red-400 rounded bg-red-50 mb-4">

**Not updating your branch before starting new work**

Few things are worse than finishing a feature and discovering conflicting changes were merged weeks ago — or that someone else already did the same thing.

**Pull/update before you start new work.**

</div>

<div class="p-3 border border-red-400 rounded bg-red-50 mb-4">

**Too ambitious a branch that risks never being completed**

A branch that grows forever with too many features will have conflicts everywhere when you finally try to merge it.

Keep branches focused and short-lived.

</div>

<div class="p-3 border border-red-400 rounded bg-red-50">

**Over-engineering branch layout in small projects**

Complex rules and safeguards may prevent contributions — even your own. Add restrictions only as the project and team grow.

</div>

---

<div class="p-4 border border-blue-400 rounded bg-blue-50">

**Discussion:** What are we missing on this page?

If you're a seasoned Git user — what pitfalls have we left out? What would you add?

</div>