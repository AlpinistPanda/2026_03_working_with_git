---
layout: center
transition: fade
---

# Aliases and configuration

<div class="p-4 border border-green-400 rounded bg-green-50 mt-4">

**Objective:** Use aliases for your most common commands.

</div>

> If you're frustrated about remembering or typing a command — create an alias.

---

## What are aliases?

- **Shortcuts** for Git commands: e.g. `git ci` instead of `git commit`
- Based on simple string replacement
- Can be **global** (across all repos, stored in `~/.gitconfig`) or per-repository (in `.git/config`)
- Global aliases help you stay consistent across projects

<div class="p-4 border border-blue-400 rounded bg-blue-50 mt-4">

**Discussion:** When to alias?
- How many times should you type a command before aliasing it?
- Will short two-letter aliases actually save time — or just confuse colleagues?

</div>

---

## The most useful alias: `git graph`

You've already seen this one. If you haven't set it yet:

```console
$ git config --global alias.graph "log --all --graph --decorate --oneline"
```

Then in any repository:
```console
$ git graph
```

---

## Using external commands in aliases

Prefix with `!` to call any shell command:

```console
$ git config alias.hi '!echo hello'
$ git hi
hello
```

Note: this creates a **local** alias (stored in `.git/config`, not synced to remotes).

---

## Useful aliases

```console
$ git config --global alias.st status
$ git config --global alias.di diff
$ git config --global alias.br branch
$ git config --global alias.ci "commit -v"
$ git config --global alias.ap "add --patch"
$ git config --global alias.dic "diff --staged --color-words"
$ git config --global alias.diw "diff --color-words"
$ git config --global alias.dis "!git --no-pager diff --stat"
$ git config --global alias.fe fetch
$ git config --global alias.graph "log --all --graph --decorate --oneline"
```

---

What each does:

| Alias | Command | Notes |
|---|---|---|
| `st` | `status` | |
| `di` | `diff` | |
| `br` | `branch` | |
| `ci` | `commit -v` | shows diff in editor |
| `ap` | `add --patch` | stage interactively |
| `dic` | `diff --staged --color-words` | what's about to be committed |
| `diw` | `diff --color-words` | word-level diff |
| `dis` | `diff --stat` | files changed, not contents |
| `fe` | `fetch` | |
| `graph` | `log --all --graph ...` | visualise branches |

For the `--patch` aliases, enable single-key mode:
```console
$ git config --global interactive.singlekey true
```

---

## Advanced aliases

These are for the curious — try to figure out what they do:

```console
$ git config --global alias.cif "commit -v -p --fixup"
$ git config --global alias.rb "rebase --autosquash"
$ git config --global alias.rbi "rebase --interactive --autosquash"
$ git config --global alias.ls-ignored "ls-files -o -i --exclude-standard"
$ git config --global alias.new "log HEAD..HEAD@{upstream}"
$ git config --global alias.rec "!git --no-pager log --oneline --graph --decorate @{upstream}^^^..HEAD"
```

---

## Advanced configuration

Beyond aliases, Git has many useful settings:

```console
$ git config --global core.pager "less -RS"
$ git config --global core.excludesfile ~/.gitignore
$ git config --global merge.conflictstyle diff3
$ git config --global diff.wordRegex "[a-zA-Z0-9_]+|[^[:space:]]"
$ git config --global diff.mnemonicPrefix true
```

---

## URL aliases (remote shortcuts)

Tired of typing `git@github.com:myusername` repeatedly?

```console
$ git config --global url.git@github.com:.insteadOf gh:
$ git config --global url.git@github.com:/username/.insteadOf ghu:
```

Now `git clone ghu:recipe` automatically expands to `git clone git@github.com:/username/recipe`.

View all your current aliases:
```console
$ cat ~/.gitconfig
```