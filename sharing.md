---
layout: center
transition: fade
---

# How to turn your project into a Git repo and share it

<div class="p-4 border border-green-400 rounded bg-green-50 mt-4">

**Objectives**
- Turn your own coding project into a Git repository.
- Share a repository on the web for backup, reuse, or collaboration.

</div>

---

## The goal

<img src="/img/illustrations/sharing.png" class="rounded mt-2 max-h-56 mx-auto" />

From a folder of files → a local Git repo → shared on GitHub.

---

## Exercise: Turn your project into a Git repo (25 min)

1. Create a new directory called **myproject** with one or a few files.
2. Turn it into a Git repository.
3. Share it on GitHub (or GitLab).

Three paths available:
- **GitHub web interface** — easiest, good if you're new to Git
- **VS Code** — very easy, handles GitHub auth for you
- **Command line** — most control, requires linking manually

---

## Path 1: GitHub web interface

Log into GitHub, click **"+"** → **"New repository"**:

<img src="/img/sharing/new-repository.png" class="border rounded mt-2 max-h-44 mx-auto" />

Choose a name, add a description, and **check "Add a README file"**:

<img src="/img/sharing/create-repository-with-readme.png" class="border rounded mt-2 max-h-44 mx-auto" />

---

Then upload your files using **"+" → "Upload files"**:

<img src="/img/sharing/upload-files.png" class="border rounded mt-2 max-h-64 mx-auto" />

---

## Path 2: VS Code

Open your project folder in VS Code, click the **Source Control icon**, then:

<div class="grid grid-cols-2 gap-4 mt-2">

<figure>
  <img src="/img/sharing/vscode-publish-to-github1.png" class="border rounded w-full" />
  <figcaption class="text-center text-sm text-gray-500 mt-1">Click "Publish to GitHub"</figcaption>
</figure>

<figure>
  <img src="/img/sharing/vscode-publish-to-github2.png" class="border rounded w-full" />
  <figcaption class="text-center text-sm text-gray-500 mt-1">Choose public or private, rename if needed</figcaption>
</figure>

</div>

---

<div class="grid grid-cols-2 gap-4 mt-4">

<figure>
  <img src="/img/sharing/vscode-authorize.png" class="border rounded w-full" />
  <figcaption class="text-center text-sm text-gray-500 mt-1">First time: authorize VS Code with GitHub</figcaption>
</figure>

<figure>
  <img src="/img/sharing/vscode-publish-to-github3.png" class="border rounded w-full" />
  <figcaption class="text-center text-sm text-gray-500 mt-1">After publishing: click "Open on GitHub"</figcaption>
</figure>

</div>

---

## Path 3: Command line

Initialize and commit your project locally:

```console
$ git init -b main
$ git add LICENSE myscript.py    # or: git add .
$ git commit -m "putting my project under version control"
```

Create an **empty** repository on GitHub (do **not** check "Add a README"):

<img src="/img/sharing/create-repository.png" class="border rounded mt-2 max-h-44 mx-auto" />

---

After creating the empty repo, GitHub shows the push instructions:

<img src="/img/sharing/bare-repository.png" class="border rounded mt-2 max-h-44 mx-auto" />

Follow the "push an existing repository" section:

```console
$ git remote add origin git@github.com:USER/myproject.git  # SSH
# or:
$ git remote add origin https://github.com/USER/myproject.git  # HTTPS
$ git branch -M main
$ git push -u origin main
```

---

## Troubleshooting

<div class="p-4 border border-red-400 rounded bg-red-50 mb-3">

**`error: remote origin already exists`**
- You ran `git remote add origin` twice with different URLs.
- Fix: `git remote remove origin`, then re-add the correct URL.

</div>

<div class="p-4 border border-red-400 rounded bg-red-50">

**`remote contains work that you do not have`**
- You checked "Add a README" — your GitHub repo has a commit your local repo doesn't.
- Fix: `git push --force` (safe for brand-new repos; dangerous on shared repos).

</div>

---

## Remote repositories

A **remote** is a repository on another server. We can **push** to and **pull** from it.

Use remotes to:
- Back up your work or make it findable
- Collaborate with others

Popular hosting services:
- [GitHub](https://github.com) — widely used, commercial
- [GitLab](https://about.gitlab.com) — open-core, many universities run their own instance
- [Bitbucket](https://bitbucket.org) — commercial
- [Codeberg](https://codeberg.org) — non-profit, open-source focused

---

## Is putting code on GitHub "publishing"?

It's a good first step — but to make your code truly **findable, accessible, and citable**:

Get a **persistent identifier (DOI)** by using services like [Zenodo](https://zenodo.org).

A GitHub URL can change or disappear. A DOI is permanent and citable in papers.