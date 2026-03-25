---
layout: center
transition: fade
---

# Motivation

<div class="p-4 border border-green-400 rounded bg-green-50 mt-4 text-left">

**Objectives**

- Make sure nobody leaves the workshop without starting to use some form of version control.
- Discuss the reasons why we advocate distributed version control.

</div>

---

## Git is all about keeping track of changes

Tracked changes on GitHub ([example repo](https://github.com/bast/runtest/commits/main/runtest/run.py)):

<img src="/img/git-log-github.png" class="border rounded mt-2 max-h-56 mx-auto" />

---

The same history, viewed in the terminal:

<img src="/img/git-log-terminal.png" class="border rounded mt-2 max-h-64 mx-auto" />

---

## Why do we need to keep track of versions?

**Problem: If you have to find your code from 17 days ago, can you?**

Version control answers questions like:

- "It broke... hopefully I have a working version somewhere?"
- "Can you please send me the latest version?"
- "Which version are you using?"
- "Which version did the authors use in the paper I'm trying to reproduce?"
- "Found a bug! Since when was it there?"
- "I'm sure it used to work. When did it change?"
- "My laptop is gone. Is my thesis now gone?"

---

## Features: roll-back, branching, merging, collaboration

**Problem: Your code worked two days ago, but errors now — you don't know what changed.**

**Problem: You and a colleague want to work on the same code at the same time.**

- **Roll-back**: always go back to a previous version and compare
- **Branching and merging**:
  - Work on different ideas simultaneously
  - Multiple people can work without interfering
  - Experiment and discard bad ideas safely

---

<img src="/img/gopher/gophers.png" class="rounded mx-auto max-h-72" />

<p class="text-center text-sm text-gray-500 mt-1">Branching explained with gophers — image via <a href="https://gopherize.me/">gopherize.me</a></p>

- **Collaboration**: review, compare, share, discuss
- [Example network graph](https://github.com/coderefinery/git-intro/network)

---

## Reproducibility

**Problem: Someone asks about your results from 5 years ago. Can you get the same results now?**

- How do you indicate which version of your code was used in your paper?
- When you find a bug, how do you know exactly **when it was introduced**?

With version control you can "annotate" code ([browse this example](https://github.com/networkx/networkx/blame/main/networkx/algorithms/boundary.py)):

<img src="/img/git-annotate.png" class="border rounded mt-2 max-h-52 mx-auto" />

---

## Talking about code

**Problem: You want to show someone a few lines from your project.**

Which is more practical?

- *"Clone the code, go to `src/util.rs`, search for `time_iso8601`. Oh — use the version from August 2023."*
- Or send a [permalink](https://github.com/NordicHPC/sonar/blob/75daafc86582feb06299d6a47c82112f39888152/src/util.rs#L40-L44):

<img src="/img/code-portion.png" class="border rounded mt-2 max-h-44 mx-auto" />

---

## What we typically like to snapshot

- Software (this is how it started, but Git/GitHub can track a lot more)
- Scripts
- Documents (plain text much better than Word documents)
- Manuscripts (great for LaTeX or [Quarto](https://quarto.org/) collaboration)
- Configuration files
- Website sources
- Data

---

<div class="p-4 border border-blue-400 rounded bg-blue-50 mb-4">

**Discussion:** Someone tried to track versions without Git. What problems do you anticipate?

```
myproject-2019.zip
myproject-2020-February.zip
myproject-2021-August.zip
myproject-2023-09-19-working.zip
myproject-2023-09-21.zip
myproject-2023-09-21-test.zip
myproject-2023-09-21-myversion.zip
myproject-2023-09-21-newfeature.zip
... (100 more files)
```

</div>

<div class="p-4 border border-gray-300 rounded bg-gray-50">

**Solution:** Sharing with a collaborator and merging changes later is a lot of work. Finding when a bug was introduced is nearly impossible.

</div>

---

## Difficulties of version control

Let's be honest — there are some challenges:

- One more thing to learn (worth it; a basic career skill)
- Difficult if collaborators don't want to use it — in the worst case you can version control **on your side** and email them versions
- Advanced features can be tricky, but basics are usually enough

---

## Why Git and not another tool?

- **Easy to set up**: no server needed
- **Very popular**: you'll likely need to contribute to someone else's Git-tracked code
- **Distributed**: good backup, no single point of failure, work offline, simpler open-source collaboration
- Major **platforms** like [GitHub](https://github.com), [GitLab](https://gitlab.com), and [Bitbucket](https://bitbucket.org) are built on Git

> Any version control is better than none — [Subversion](https://subversion.apache.org), [Mercurial](https://www.mercurial-scm.org), [Pijul](https://pijul.org/) are all fine alternatives.
