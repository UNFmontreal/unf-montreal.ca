# unf-montreal.ca

How to maintain this website?

To ensure both languages are in-sync, if you fix a content in only one language, *please* open a [PR](https://github.com/UNFmontreal/unf-montreal.ca/pulls) so the maintenance team will make sure both languages are corrected.

## Deploying the site

Deployment is automated with **GitHub Actions**.

## Running locally

1. **Fork** this repository on GitHub (if you are not a team member).

2. **Clone your fork (or the repo for team members)** (recommended: pull submodules on first clone):
   ```bash
   git clone --recurse-submodules https://github.com/<your-user>/school-brainhack.github.io.git
   cd school-brainhack.github.io
   # (optional) add the upstream remote for syncing later
   git remote add upstream https://github.com/school-brainhack/school-brainhack.github.io.git
   ```

3. **Ensure submodules are current** (safe to re-run anytime):
   ```bash
   git submodule update --init --recursive
   ```

4. **Install Hugo (Extended)**  
   Follow [Hugo installation docs](https://gohugo.io/getting-started/installing/) and install the **extended** variant.

5. **Serve locally**:
   ```bash
   hugo server -D        # include drafts
   # or, to also include future/expired content:
   # hugo server -D -F -E
   ```
   Hugo serves at [http://localhost:1313](http://localhost:1313) by default. Browse to confirm everything compiles.

# Updating the Team Page (Hugo)

This site lists team members as individual Markdown files in each language:

* `content/en/team/`
* `content/fr/team/`

Each person has one file per language (e.g., `andre_cyr.md`), plus a section index (`_index.md`). The pages are rendered by the `layouts/teacher/` templates.

---

## Add a new member

1. **Duplicate an existing file** in `content/en/team/` (e.g., `andre_cyr.md`) and rename it to `first_last.md`.
2. Do the same in `content/fr/team/` so both languages exist. Use the **same filename** in both folders.
3. Edit the **front matter** and body. Keep the same keys used by current files. Typical fields:

```yaml
---
title: "First Last"           # Display name
role: "Research Assistant"    # Shown under the name (may be `designation` in some files)
email: first.last@org.org      # Optional
image: "/images/team/first_last.jpg"  # Path under `static/`
weight: 10                     # Lower shows earlier in the list
social:
  - icon: github
    url: https://github.com/username
  - icon: linkedin
    url: https://www.linkedin.com/in/username/
draft: false                   # Set true to hide
---
Short bio or responsibilities.
```

> **Note:** Match the exact keys already used in the repo (open a couple of existing profiles and copy their structure). Some themes expect `designation`, `facebook`, `twitter`, etc.

---

## Add/replace the photo

1. Save the image to `static/images/team/first_last.jpg` (create the `team/` folder if it doesn’t exist).
2. Use a **square** image (e.g., 600×600) to avoid cropping surprises.
3. Reference it in the front matter `image:` field (leading slash `/images/...`).

---

## Change order or hide temporarily

* **Order**: adjust `weight` (smaller number = earlier).
* **Hide**: set `draft: true` (in both language files).
* **Remove**: delete both language files and any image.

---

## Edit an existing member

Open the person’s file in each language (`content/en/team/first_last.md` and `content/fr/team/first_last.md`), update fields or text, and save.

---

## Troubleshooting

* Page missing? Ensure **both** language files exist and `draft: false`.
* Image not showing? Confirm the path starts with `/images/` and the file lives under `static/images/...`.
* Weird layout? Compare your front matter keys to a working profile (the theme expects specific names).

