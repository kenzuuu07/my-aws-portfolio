# Phase 1 - Getting started (about 20 minutes)

**Goal:** sign in to AWS, find your workshop files, and check that your tools work.

By the end of this phase you can say:

- [ ] I signed in to the AWS Console with my own workshop account.
- [ ] The Region in the top-right corner says **Asia Pacific (Singapore)**.
- [ ] I opened the workshop repository on GitHub and read the README.
- [ ] I can open the starter website on my computer.

---

## 1. Get your sign-in details

| What | Value | What it is |
|---|---|---|
| Sign-in URL | **https://freecil.signin.aws.amazon.com/console** | The sign-in page for the workshop AWS account |
| Account alias | **`freecil`** | The workshop account's name. Type it if the page asks for *Account ID or alias* |
| IAM username | `workshop-user-07` *(the instructor gives you your number)* | **Your** AWS username for today |
| Password | *(shown on the instructor's slide)* | The same workshop password for everyone |
| Region | `ap-southeast-1` | Asia Pacific (Singapore) |

> 🔒 **Use only the username you were given.** Everyone shares one password today, so the username is what tells AWS who you are.
> Signing in as a classmate is not allowed, and AWS logs every action under the username that did it.
> Don't post the password or a photo of the slide. The workshop staff will never ask you to type the password for them.

## 2. Sign in to the AWS Console

1. Open **https://freecil.signin.aws.amazon.com/console** in your browser (Chrome, Edge or Firefox).
   - Use this exact link. Do **not** go to aws.amazon.com and click "Sign in". That page is for root users.
2. Check that **Account ID or alias** says `freecil`. If it's empty, type `freecil`.
3. Type **your** IAM username, for example `workshop-user-07`.
4. Type the **workshop password** exactly as the instructor shows it. It is case-sensitive.
5. Click **Sign in**.
6. You will normally **not** be asked to change the password today. If the instructor enabled it and you see **"You must change your password"**:
   - *Old password*: the workshop password.
   - *New password*: a personal one you will remember today, with at least 8 characters including upper- and lowercase letters, numbers and a symbol.
   - Click **Confirm password change**.

You should now see **Console Home**.

> ℹ️ Some boxes on Console Home may say *"Access denied"* or *"You don't have permissions"*.
> **That is expected.** Your account can only use Amazon S3 today. That is *least privilege*, which you learned about this morning.

## 3. Select the Singapore Region

1. Look at the **top-right corner** of the Console, next to your username.
2. Click the Region name.
3. Choose **Asia Pacific (Singapore) ap-southeast-1**.

Your account can only create buckets in Singapore. If you pick any other Region, such as Tokyo, bucket creation fails with *Access Denied*.

## 4. Open the workshop repository

1. Open the workshop GitHub link shown on the projector (also in the event chat).
2. You are looking at the **README.md** file. Read the "Student quick start" section.
3. Notice the folders:
   - `site/`: the starter website you will customise and deploy
   - `instructions/`: these guides, one per phase
   - `bonus/`: the optional CI/CD challenge (Phase 5)
## 5. Get the starter website on your computer

You will create your own copy on GitHub in Phase 2. For now, just look at the files:

1. On the repository page, click the green **Code** button → **Download ZIP**.
2. Open your **Downloads** folder, right-click the ZIP → **Extract All…** → **Extract**.
3. Open the extracted folder, then the `site` folder.
4. Double-click **index.html**. The portfolio opens in your browser. 🎉

## 6. Check your tools

| Tool | Required? | Check |
|---|---|---|
| A modern browser | ✅ Yes | Chrome, Edge or Firefox, updated |
| A GitHub account | ✅ For Phases 2 and 5 | Sign in at github.com. No account yet? Sign up now (it needs email verification). |
| A text editor | ✅ Yes | **VS Code** (recommended), Notepad++, or even Notepad |
| Git Bash | ⭕ Optional | Only for the optional command-line steps in Phase 2 |

> No GitHub account and the verification email has not arrived? **You can still finish the core workshop.**
> Use the ZIP you just downloaded, then follow Phases 3 and 4. A facilitator will help you catch up on GitHub later.

## Stuck?

- **"Your authentication information is incorrect"**: check the username (`workshop-user-07`: hyphens, two-digit seat number, all lowercase) and retype the password. Pasting can add a hidden space.
- **The page asks for an email address**: you are on the root-user page. Open https://freecil.signin.aws.amazon.com/console instead, or choose **IAM user** and type the alias `freecil`.
- **Anything else**: raise your hand. More help: [TROUBLESHOOTING.md](../TROUBLESHOOTING.md).

➡️ Next: [Phase 2 - Git and GitHub](02-git-and-github.md)
