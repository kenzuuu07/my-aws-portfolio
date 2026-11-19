# Phase 3 - Build your website (about 45 minutes)

**Goal:** turn the starter portfolio into *your* portfolio, using plain HTML, CSS and JavaScript.

By the end of this phase you can say:

- [ ] My name, introduction, skills and at least one project are on the page.
- [ ] I replaced at least one image, or I know how to.
- [ ] The page still loads correctly when I double-click `index.html`.
- [ ] My changes are committed to my GitHub repository (Path A, B or C from Phase 2).

---

## What each file does

```text
site/
├── index.html      ← CONTENT: the text, headings, links and images (what is on the page)
├── style.css       ← LOOK: colors, fonts, spacing, layout (how it looks)
├── script.js       ← BEHAVIOUR: menu button, dark mode, fun facts (what it does)
└── assets/         ← IMAGES used by the page
    ├── profile-placeholder.png
    ├── project-1.png
    ├── project-2.png
    └── project-3.png
```

- Amazon S3 shows **`index.html`** when someone visits your website, so the name must be exactly `index.html`, all lowercase.
- `index.html` loads the other two files with **relative paths**:
  ```html
  <link rel="stylesheet" href="style.css">
  <script src="script.js" defer></script>
  ```

Search the files for these comments. They mark the parts meant for you:
`CHANGE YOUR NAME HERE` · `REPLACE THIS IMAGE` · `CUSTOMIZE YOUR SKILLS` · `CHANGE YOUR PROJECT DETAILS` · `CUSTOMIZE`

## Relative paths, the #1 cause of broken websites

A **relative path** says where a file is *compared to the current file*.

| You write | Browser looks for | Works on S3? |
|---|---|---|
| `assets/me.jpg` | the `assets` folder next to `index.html` | ✅ Yes |
| `/assets/me.jpg` | the root of the website | ⚠️ Only if `assets/` is at the bucket root |
| `C:\Users\Juan\Pictures\me.jpg` | **your** laptop's drive | ❌ Never. Visitors don't have your laptop |
| `assets/Me.JPG` when the file is `me.jpg` | a different file! | ❌ S3 names are **case-sensitive** |

> 💡 Windows doesn't care about uppercase vs lowercase, so a wrong case works on your laptop but **breaks on S3**.
> Use **lowercase file names with no spaces**, for example `my-photo.jpg` rather than `My Photo.JPG`.

## How to add your own photo

1. Choose a photo you are happy for **anyone on the internet** to see. A square photo of 400×400 px or more works best.
2. Rename it to lowercase with no spaces, for example `me.jpg`.
3. Copy it into the `site/assets/` folder.
4. In `index.html`, find `REPLACE THIS IMAGE` and change
   `src="assets/profile-placeholder.png"` to `src="assets/me.jpg"`.
5. Update the `alt` text. It describes the image for screen readers.
6. Save, then refresh the browser. Keep images under ~1 MB so the page loads fast.

## Exercises

### 🟢 Beginner (everyone)

1. Change the name in the `<title>`, the navigation brand, the big heading and the footer.
2. Rewrite the introduction and the **About me** paragraph.
3. Edit the **quick facts** list.
4. In **Skills**, edit names and change `--level: 80%` values. Add one skill by copying a `<li>` line.
5. Change at least one **project** title and description.

### 🟡 Intermediate

1. Change `--color-primary` and `--color-dark` at the top of `style.css` to your own colour theme.
2. Replace the profile image and a project image with your own.
3. Add a **fourth project card**: copy a whole `<article class="card"> … </article>` block.
4. Edit the `funFacts` list in `script.js` with three facts about you.
5. Open DevTools (**F12**), click the phone icon (device toolbar), and check the page on a phone-sized screen.

### 🔴 Optional advanced

1. Add a new section, for example **Achievements**: a `<section>`, a link in the nav, and styling.
2. Add an `error.html` page and later set it as the **Error document** in S3 static hosting.
3. Add a "Back to top" button that appears after scrolling (JavaScript: `window.addEventListener("scroll", …)`).
4. Validate your HTML at https://validator.w3.org (upload `index.html`) and fix any errors.

## Design planning (optional)

Facilitators can help you sketch a layout on paper or in Figma. **Design must not block building.**
If you are not sure what to design, keep the starter layout and change only the content and colours. That is a great result.

## Before you continue

- [ ] Double-click `index.html`: text, colours, **images** and the **menu/dark-mode buttons** all work.
- [ ] No file names with spaces or capital letters in `assets/`.
- [ ] Your changes are uploaded/committed to your GitHub repository.
- [ ] Nothing private on the page: no phone number, home address, student ID or passwords.

➡️ Next: [Phase 4 - Deploy to Amazon S3](04-deploy-to-s3.md)
