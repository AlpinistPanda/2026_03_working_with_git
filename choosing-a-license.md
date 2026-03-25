---
layout: center
transition: fade
---

# Choosing a License

---

## Why you should choose a license

From the [GitHub documentation](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository):

> "You're under no obligation to choose a license. However, without a license, the default copyright laws apply, meaning that you retain all rights to your source code and **no one may reproduce, distribute, or create derivative works** from your work."

---

## Software vs. non-software licenses

GitHub was originally built for software, so most license guidance is software-focused. But it's important to distinguish:

- **Software** → typically MIT, Apache, GPL, etc.
- **Non-software creative works** (data, writing, images) → typically [Creative Commons](https://creativecommons.org/) licenses

The Creative Commons specifically recommends [**against** using CC licenses for software](https://creativecommons.org/faq/#can-i-apply-a-creative-commons-license-to-software).

---

## Choosing a license on GitHub

Even if you skipped it during repo creation, you can still use GitHub's license helper.

From your repo, click **"Add File" → "Create new file"** and type `LICENSE` in the filename box. A **"Choose your license template"** button appears:

<img src="/img/choosing-a-license/choose_a_license_template.jpg" class="border rounded mt-2 max-h-48 mx-auto" />

---

You'll see a list of the most commonly used licenses with summaries, full text, and an option to add your name:

<img src="/img/choosing-a-license/license_chooser.jpg" class="border rounded mt-2 max-h-80 mx-auto" />

Click through a few licenses to compare them.

---

## Which license to pick?

<div class="grid grid-cols-2 gap-4">

<div class="p-4 border border-blue-400 rounded bg-blue-50">

**Not a federal employee?**

Recommend **MIT** or **Apache License**.

Both are permissive and widely used in open source — good defaults for most projects.

</div>

<div class="p-4 border border-yellow-400 rounded bg-yellow-50">

**US federal employee?**

Code written as part of official duties **cannot be copyrighted**. Use something like the **Unlicense** (similar to [BLAST's license](https://www.ncbi.nlm.nih.gov/IEB/ToolBox/CPP_DOC/lxr/source/scripts/projects/blast/LICENSE) from NIH).

</div>

</div>

---

## For our recipe — Creative Commons Zero

Food recipes are [legally "uncopyrightable"](https://www.copyright.gov/circs/circ33.pdf) under US law. So the right choice is **Creative Commons Zero (CC0)** — which means we claim no copyright at all.

Select CC0, then click **"Review and submit"**:

<img src="/img/choosing-a-license/cc0_review_and_submit.jpg" class="border rounded mt-2 max-h-40 mx-auto" />

Then click **"Commit Changes"** to add the license to your repository.
