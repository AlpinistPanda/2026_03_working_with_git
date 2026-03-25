---
layout: center
---

# Creating repositories using the web interface

We will practice creating a new repository, committing changes, browsing history, and creating branches — all from the browser.

---

## Step 1: Create a repository

You usually create repositories from the web, no matter how you do your daily work. The key questions: who is the **owner** and what is the **name**?

Make sure you are **logged into GitHub**, then click the green **"New"** button (top left):

<img src="/img/creating-using-web/new-top-left.png" class="border rounded mt-2 max-h-36" />

---

Or use the **"+"** menu in the top right corner of your profile page:

<img src="/img/creating-using-web/new-top-right.png" class="border rounded mt-2 max-h-36" />

---

Fill out the form and check **"Initialize this repository with a README"**. Leave "Choose a License" as "None" for now — we'll cover that in the next section.

<img src="/img/creating-using-web/form.png" class="border rounded mt-2 max-h-80 mx-auto" />

---

You now have a repository with a README and one commit:

<img src="/img/creating-using-web/created.png" class="border rounded mt-2 max-h-80 mx-auto" />

---

## Step 2: Create a new file

Click "Add file" to create a new file, e.g. `guacamole.md`:

<img src="/img/creating-using-web/new-file-buttons.png" class="border rounded mt-2 max-h-36 mx-auto" />

Add your favorite recipe (or copy-paste this):

```
Ingredients:
- 2 avocados
- 1 lime
- 2 tsp salt

Instructions:
- cut and mash avocados
- chop onion
- squeeze lime
- add salt
- and mix well
```

---

<div class="grid grid-cols-2 gap-4">

<figure>
  <img src="/img/creating-using-web/new-file-editor.png" class="border rounded w-full" />
  <figcaption class="text-center text-sm text-gray-500 mt-1">Editing the new file</figcaption>
</figure>

<figure>
  <img src="/img/creating-using-web/new-file-commit.png" class="border rounded w-full" />
  <figcaption class="text-center text-sm text-gray-500 mt-1">Add a commit message and save</figcaption>
</figure>

</div>

---

<div class="p-4 border border-blue-400 rounded bg-blue-50">

**Discussion: Good commit messages**

- What changed is more useful than which file changed
- Document *why* something was changed, not just what
- Write messages in English that will be understood 15 years from now by someone else
- ["My favourite Git commit"](https://fatbusinessman.com/2019/my-favourite-git-commit)
- ["On commit messages"](https://who-t.blogspot.com/2009/12/on-commit-messages.html)
- ["How to Write a Git Commit Message"](https://chris.beams.io/posts/git-commit/)

</div>

---

## Step 3: Modify a file

Click on the file, then the **pen icon** (top right) to edit it. Improve the recipe, write a commit message, and commit.

<div class="grid grid-cols-2 gap-4 mt-2">

<figure>
  <img src="/img/creating-using-web/edit-file-preview.png" class="border rounded w-full" />
  <figcaption class="text-center text-sm text-gray-500 mt-1">Editing and previewing the file</figcaption>
</figure>

<figure>
  <img src="/img/creating-using-web/commits-browse.png" class="border rounded w-full" />
  <figcaption class="text-center text-sm text-gray-500 mt-1">Browsing commits</figcaption>
</figure>

</div>

---

<img src="/img/creating-using-web/commits-example.png" class="border rounded mx-auto max-h-48 mb-4" />

<div class="p-4 border border-green-400 rounded bg-green-50">

**Summary:** We saw how to do basic file management from the web. It's not ideal for lots of content, but very convenient for quick edits and contributions. We'll now look at more advanced workflows.

</div>

---

## Markdown

Markdown is a lightweight markup language for formatted text, created by John Gruber and Aaron Swartz in 2004.

Open a [new CodiMD document](https://codimd.carpentries.org/new), then switch to the **split pane** view (icon top left):

<img src="/img/creating-using-web/codimd_edit.png" class="border rounded mt-2 max-h-52 mx-auto" />

---

Practice these Markdown elements in CodiMD:

| Element | Syntax |
|---|---|
| Headers | `# H1`, `## H2` |
| Bold | `**bold**` |
| Italics | `*italic*` |
| Bullets | `- item` |
| Ordered list | `1. item` |
| Link | `[text](url)` |
| Image | `![alt](url)` |

<div class="mt-4 p-4 border border-green-400 rounded bg-green-50">

**Exercise:** Use these Markdown skills to edit your `README.md` or `guacamole.md` files.

</div>
