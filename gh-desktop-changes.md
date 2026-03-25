---
layout: center
transition: fade
---

# Making changes with GitHub Desktop

**Scenario:** You've created a repository on the web, but now you have multiple files to add. The web interface isn't ideal for this — GitHub Desktop is.

---

## Step 1: Open GitHub Desktop and sign in

<img src="/img/gh-desktop-changes/desktop_welcome.jpg" class="border rounded mt-2 max-h-56 mx-auto" />

Sign in: **File > Options** (Windows) or **GitHub Desktop > Preferences** (Mac), then the **Accounts** tab.

---

## Step 1: Clone your repository

Use **File > Clone repository** (not just the welcome screen button):

<img src="/img/gh-desktop-changes/clone_repo.jpg" class="border rounded mt-2 max-h-56 mx-auto" />

Under the **GitHub.com** tab, find your recipes repository. Choose a local folder and click **Clone** to download all files and history.

---

## Step 2: Add new files

Download and unzip [avocado_recipes.zip](https://github.com/MikeTrizna/github-without-command-line/raw/master/data/avocado_recipes.zip) — it contains 2 more recipes in Markdown format.

Copy the new `.md` files into your cloned repository folder.

<div class="p-4 border border-green-400 rounded bg-green-50 mt-4">

**Exercise:** How has the Changes tab of GitHub Desktop updated?

</div>

---

Enter a commit message and click **Commit**:

<div class="grid grid-cols-2 gap-4 mt-2">

<figure>
  <img src="/img/gh-desktop-changes/desktop_changes.jpg" class="border rounded w-full" />
  <figcaption class="text-center text-sm text-gray-500 mt-1">Changes tab — stage and commit</figcaption>
</figure>

<figure>
  <img src="/img/gh-desktop-changes/desktop_history.jpg" class="border rounded w-full" />
  <figcaption class="text-center text-sm text-gray-500 mt-1">History tab — view your commits</figcaption>
</figure>

</div>

Now check the repository on GitHub. *Do you see the new files yet?*

---

The commit exists locally but hasn't been sent to GitHub yet. Click **"Push origin"** (top right) to upload your changes.

<div class="p-4 border border-blue-400 rounded bg-blue-50 mt-4">

**Commit → Push workflow:**
1. Make changes to files locally
2. Commit (saves a snapshot locally)
3. Push (syncs your local commits to GitHub)

</div>

---

## Step 3: Resolve a conflict

What happens when you and a collaborator make **conflicting changes** at the same time?

**On GitHub.com** — edit `README.md` to add links in this order:

```markdown
* [Salad](avocado_tomato_salad.md)
* [Smoothie](avocado_smoothie.md)
* [Guacamole](guacamole.md)
```

**Locally** — edit `README.md` with the **opposite order**, then commit:

```markdown
* [Smoothie](avocado_smoothie.md)
* [Salad](avocado_tomato_salad.md)
* [Guacamole](guacamole.md)
```

---

Try to push. Notice the new options that appear instead of "Push origin":

<img src="/img/gh-desktop-changes/conflicting_changes_options.jpg" class="border rounded mt-2 max-h-48 mx-auto" />

Click **"Pull origin"** — you'll get a conflict warning:

<img src="/img/gh-desktop-changes/resolve_conflicts.jpg" class="border rounded mt-2 max-h-36 mx-auto" />

---

Open the local `README.md` in a text editor. Git has marked the conflicting lines:

<img src="/img/gh-desktop-changes/vscode_conflicts.jpg" class="border rounded mt-2 max-h-52 mx-auto" />

Remove the conflict markers, keep the version you want, then push again.

---

<div class="p-4 border border-yellow-400 rounded bg-yellow-50">

**Resolving conflicts**

Running into a conflict is scary — but normal. If you feel like you're digging a deeper hole while resolving it, you can always **delete the local copy and clone again from GitHub**. Your changes on GitHub are safe.

</div>
