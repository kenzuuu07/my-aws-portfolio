# Phase 2 - Git and GitHub fundamentals (about 30 minutes)

**Goal:** create *your own* copy of the workshop repository and make your first commit.
**No command line required.** Everything below works in the browser.

By the end of this phase you can say:

- [ ] I have my own repository created from the workshop template.
- [ ] I edited a file on GitHub and committed the change.
- [ ] I can explain *repository*, *commit*, *branch* and *push* in one sentence each.

---

## The four words you need today

| Word | Plain meaning | Real-life comparison |
|---|---|---|
| **Repository (repo)** | A project folder that remembers its whole history | A Google Drive folder with unlimited "undo" |
| **Commit** | A saved snapshot of your changes, with a message | Pressing "Save" *and* writing a note about what changed |
| **Branch** | A separate line of work. `main` is the official one | A draft copy of an essay you can merge back in |
| **Push** | Sending your local commits up to GitHub | Uploading your saved work to the cloud |

**Git** is the tool that tracks changes. **GitHub** is a website that hosts Git repositories online.

## 1. Create your repository from the template

1. Sign in to **github.com**.
2. Open the workshop repository (link on the projector).
3. Click the green **Use this template** button → **Create a new repository**.
   - Don't see the button? Make sure you are signed in.
4. Fill in:
   - **Owner**: your GitHub username
   - **Repository name**: for example `my-aws-portfolio`
   - **Visibility**: **Public** (it will be part of your portfolio). Never put secrets in it.
   - Leave *Include all branches* **unchecked**.
5. Click **Create repository**.

You now have **your own independent repository**. Changes you make here do not affect the workshop repository or anyone else.

> ✅ **Checkpoint:** the page title shows `your-username/my-aws-portfolio` with *"generated from …"* under it.

## 2. Your first commit, in the browser

1. In **your** repository, click **README.md**.
2. Click the ✏️ **pencil icon** (Edit this file).
3. At the very top, add a line such as:
   ```markdown
   # Juan's AWS Portfolio - built at the AWS S3 Bootcamp 2026
   ```
4. Click **Commit changes…** (green button).
5. In **Commit message** write something meaningful, for example `Add my name to README`.
6. Keep **Commit directly to the `main` branch** selected → **Commit changes**.

🎉 That was a **commit**. Click the **clock icon / "Commits"** link to see your history.

## 3. How you will edit the website (pick one path)

### Path A - Recommended: edit on your computer, upload to GitHub in the browser

This gives you an instant preview, and you never touch the command line.

1. In your repository: **Code → Download ZIP** → extract it.
2. Edit the files in `site/` with VS Code (or Notepad), then **double-click `index.html`** to preview.
3. When you are happy, go to your repository on GitHub, open the **`site`** folder, click **Add file → Upload files**, and drag in the files you changed.
   - Changed an image? Open `site/assets` first, then upload into that folder.
4. Write a commit message (for example `Update about section`) → **Commit changes**.

### Path B - Quick edits directly on GitHub

Click any file (for example `site/index.html`) → ✏️ → edit → **Commit changes**.
Tip: press the **`.`** (period) key on your repository page to open **github.dev**, a VS Code editor in your browser.

### Path C - Optional: Git Bash (for the curious)

```bash
# 1. Copy your repository to your computer (use YOUR repository URL from Code > HTTPS)
git clone https://github.com/YOUR-USERNAME/my-aws-portfolio.git
cd my-aws-portfolio

# 2. Tell Git who you are (once per computer)
git config --global user.name "Your Name"
git config --global user.email "you@example.com"

# 3. Edit files in site/ ... then see what changed
git status

# 4. Stage, commit, push
git add site/
git commit -m "Customize my portfolio"
git push
```

The first `git push` opens a browser window to sign in to GitHub. Never paste your GitHub password or a token into a chat or file.

> If something goes wrong on Path C, switch to Path A. The command line is **not** required to finish the workshop.

## Common problems

| Problem | Fix |
|---|---|
| No **Use this template** button | Sign in to GitHub first. On small screens it may sit under the **…** menu. |
| "Repository name already exists" | Pick another name, for example `my-aws-portfolio-2`. |
| I edited the workshop repository instead of mine | You cannot. You will see "Fork this repository" instead. Go back to **your** repository. |
| `git push` asks for a password | Close it and use Path A. Facilitators can set up Git credentials later. |

➡️ Next: [Phase 3 - Build your website](03-build-your-website.md)
