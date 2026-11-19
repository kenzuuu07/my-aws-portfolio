# ☁️ AWS S3 Bootcamp: Host Your First Website on AWS

**AWS Student Builder Group – PCU Cavite** · November 19, 2026 · Philippine Christian University – Dasmariñas

In this hands-on workshop you will build a personal portfolio website with plain HTML, CSS and JavaScript,
put it on the internet with **Amazon S3**, and (bonus) deploy it automatically with **GitHub Actions**.
No frameworks, no build tools, no prior AWS experience needed.

## 🎓 Student quick start

| Phase | Time | Guide | You will… |
|---|---|---|---|
| 1 | 1:00 PM | [Getting started](instructions/01-getting-started.md) | Sign in to AWS, pick the Singapore Region, get the starter files |
| 2 | 1:20 PM | [Git & GitHub](instructions/02-git-and-github.md) | Create your own repository from this template and commit |
| 3 | 1:50 PM | [Build your website](instructions/03-build-your-website.md) | Customise the portfolio in `site/` |
| 4 | 2:20 PM | [Deploy to S3](instructions/04-deploy-to-s3.md) | Create a bucket and host your website on it |
| 5 ⭐ | 3:35 PM | [CI/CD bonus](instructions/05-cicd-bonus.md) | Read how to auto-deploy with GitHub Actions (take-home: try it later in your own AWS account) |
| 🏆 | 4:00 PM | Showcase | Show your live website |

**Your 30-second cheat sheet**

- Sign in at **https://freecil.signin.aws.amazon.com/console** (account alias **`freecil`**) as **your** username, e.g. `workshop-user-07`, with the workshop password on the instructor's slide.
- Region: **Asia Pacific (Singapore) `ap-southeast-1`**. Nothing else works.
- Bucket name: **any** valid, available name, e.g. `my-first-cloud-portfolio`. Lowercase, 3–63 characters.
- No tags needed. Your new bucket works immediately. Open and change **only your own** bucket.
- Upload the **contents** of `site/` (not the folder itself). `index.html` must sit at the top level of the bucket.
- Your site lives at `http://<bucket>.s3-website-ap-southeast-1.amazonaws.com` (**http**, not https).
- Stuck? → [TROUBLESHOOTING.md](TROUBLESHOOTING.md) → then raise your hand.

> 🔒 Only ever sign in as **your own** username. Never commit keys to GitHub, and never post the password or a photo of the slide.
> Your workshop AWS login and keys are disabled right after the event.

## 📁 What's in this repository

```text
site/                  ← the starter website you customise and deploy (index.html, style.css, script.js, assets/)
instructions/          ← step-by-step guides, one per phase
bonus/github-actions/  ← the optional CI/CD workflow (inactive until you copy it in Phase 5)
TROUBLESHOOTING.md     ← fixes for the most common problems
```

This template contains **no** `.github/workflows/` folder on purpose. Creating your repository from it runs nothing
until *you* add the workflow in Phase 5.

## License

[MIT](LICENSE). AWS and Amazon S3 are trademarks of Amazon.com, Inc. or its affiliates.
This is a community workshop, not official AWS training.
