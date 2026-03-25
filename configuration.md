---
layout: center
transition: fade
---

# Configuring Git

> You don't need these settings if you work **only** through the GitHub web interface. VS Code and RStudio may prompt you to set them up automatically.

Settings are stored in `~/.gitconfig`. To see current settings:

```console
$ git config --list --show-origin
```

---

## Name and email

Every Git commit records who made it. Set your name and email once:

```console
$ git config --global user.name "Your Name"
$ git config --global user.email yourname@example.com
```

Use the same email as your GitHub account. If you prefer privacy, use:

```
YOUR_GITHUB_USERNAME@users.noreply.github.com
```

GitHub still connects contributions to your account, but the address is not reachable.

---

## Default branch name

Git's default branch has historically been `master`, but `main` is now preferred. Set it globally:

```console
$ git config --global init.defaultbranch main
```

---

## Useful alias

A shortcut to visualize branch structure in the terminal:

```console
$ git config --global alias.graph "log --all --graph --decorate --oneline"
```

Then use it with:

```console
$ git graph
```

---

## Default text editor

Git sometimes opens a text editor for commit messages. Set a safe default:

```console
$ git config --global core.editor nano
```

Common alternatives:

| Editor | Command |
|---|---|
| VS Code | `code --wait` |
| Vim | `vim` |
| Emacs | `emacs` |

---

## Authenticating to GitHub

**How does GitHub know who you are?** Four options:

<div class="grid grid-cols-2 gap-4 mt-2">

<div class="p-3 border border-blue-400 rounded bg-blue-50">

**SSH** (classic)

Uses SSH key pairs. Test with:
```console
$ ssh -T git@github.com
```
If you see `Hi USERNAME! You've successfully authenticated...` — you're set.

Clone URLs start with: `git@github.com:`

</div>

<div class="p-3 border border-green-400 rounded bg-green-50">

**HTTPS + Git Credential Manager**

Works easily on Windows and Mac. Test with:
```console
$ git config --get credential.helper
```
If it returns something, you're likely configured.

Clone URLs start with: `https://github.com/`

</div>

</div>

---

<div class="grid grid-cols-2 gap-4 mt-4">

<div class="p-3 border border-purple-400 rounded bg-purple-50">

**VS Code**

VS Code handles GitHub auth through its own built-in flow — it will guide you through the process automatically.

Use **HTTPS** clone URLs: `https://github.com/`

</div>

<div class="p-3 border border-yellow-400 rounded bg-yellow-50">

**RStudio**

Uses HTTPS authentication via the `usethis` R package:

```r
usethis::git_default_branch_configure()
```

See the [installation instructions](https://coderefinery.github.io/installation/ssh/) for full setup.

Use **HTTPS** clone URLs: `https://github.com/`

</div>

</div>
