---
layout: center
transition: fade
---

# Inspecting history

<div class="p-4 border border-green-400 rounded bg-green-50 mt-4">

**Objectives**
- Find a line of code, find out why it was introduced and when.
- Quickly find the commit that changed a specific behavior.

</div>

---

## Warm-up: Git History browser

Visit [githistory.xyz](https://githistory.xyz/) to browse file changes visually.

Try browsing the `README.rst` of [networkx](https://github.com/networkx/networkx):

**[github.githistory.xyz/networkx/networkx/blob/main/README.rst](https://github.githistory.xyz/networkx/networkx/blob/main/README.rst)**

Use left/right arrow keys to navigate through time.

---

## Searching text patterns: `git grep`

Find all lines in a repository containing a string or pattern:

```console
$ git grep TEXT
$ git grep "some text with spaces"
$ git grep -i fixme          # case insensitive
$ git grep -n fixme          # with line numbers
$ git grep -C 3 fixme        # 3 lines of context
```

To search *through all changes* (not just current state):
```console
$ git log -S sometext        # find where something got added/removed
```

**GitHub:** Use the search bar at the top of the repository.

<img src="/img/archaeology/search.png" class="border rounded mt-2 max-h-44 mx-auto" />

---

## Inspecting individual commits: `git show`

```console
$ git show HASH
```

Example:
```console
$ git show 759d589bdfa61aff99e0535938f14f67b01c83f7
```

**GitHub:** Append the hash to the repo URL:
`https://github.com/networkx/networkx/commit/759d589`

<img src="/img/archaeology/show.png" class="border rounded mt-2 max-h-44 mx-auto" />

---

## Line-by-line annotation: `git annotate`

See who last changed each line, and when — including the exact commit hash:

```console
$ git annotate FILE
# Example:
$ git annotate networkx/convert_matrix.py
```

Use `/searchterm` + Enter to search within the output. `n`/`N` to cycle, `q` to quit.

**GitHub:** "Blame" button in the file view:

<img src="/img/archaeology/annotate.png" class="border rounded mt-2 max-h-44 mx-auto" />

---

<div class="p-4 border border-blue-400 rounded bg-blue-50 mb-4">

**Discussion:** How do these common practices affect annotation?
- Wrapping long lines of text into shorter lines
- Auto-formatting tools (e.g. `black`)
- Editors that remove trailing whitespace

Each of these creates new commits that "touch" lines even if the logic didn't change.

</div>

---

## Inspecting code in the past

Create a branch pointing to a past commit to browse it safely:

```console
$ git switch --create older-code 347e6292419bd0e4bff077fe971f983932d7a0e9
# browse, inspect...
$ git switch main
$ git branch -d older-code
```

**GitHub:** Navigate to a commit, then click **"Browse files"**:

<img src="/img/archaeology/browse-files.png" class="border rounded mt-2 max-h-48 mx-auto" />

---

## Exercise: Explore archaeology commands (20 min)

Use the [networkx](https://github.com/networkx/networkx.git) repository (clone it first, then check out `networkx-2.6.3`):

```console
$ git clone https://github.com/networkx/networkx.git
$ cd networkx
$ git switch --create exercise networkx-2.6.3
```

1. Find the line containing `"Logic error in degree_correlation"`.
2. Find out **when** that line was last modified. Which commit changed it?
3. **Inspect** the commit — what changed? What's the metadata?
4. Create a branch pointing to **that commit** to browse the old code.
5. How would you get to the version **just before** that line was modified?

---

## Solution

```console
# 1. Find the line
$ git grep "Logic error in degree_correlation"
# → networkx/algorithms/threshold.py

# 2. Find who/when modified it
$ git annotate networkx/algorithms/threshold.py
# → search for "Logic error", note commit hash (90544b4fa)

# 3. Inspect the commit
$ git show 90544b4fa

# 4. Create a branch at that commit
$ git branch past-code 90544b4fa

# 5. Go to just before that commit
$ git switch --create just-before 90544b4fa~1
```

---

## Finding when something broke: `git bisect`

*"I'm sure it used to work. Strange."*

`git bisect` does a **binary search** through commits to find when a bug was introduced:

```console
$ git bisect start
$ git bisect good f0ea950   # this commit worked
$ git bisect bad main        # current commit is broken
```

Git checks out a commit halfway in between. Test it, then:
```console
$ git bisect good   # this commit still works
$ git bisect bad    # this commit is broken
```

Repeat until Git identifies the exact offending commit. Automate with:
```console
$ git bisect run python test_script.py
```

Reset when done: `git bisect reset`

---

## Summary

- `git grep` / `git log -S` — find text, find when it was added/removed
- `git annotate` / `git blame` — see who changed each line and when
- `git show HASH` — inspect any individual commit
- `git switch --create NAME HASH` — browse old code safely
- `git bisect` — find the exact commit that introduced a bug