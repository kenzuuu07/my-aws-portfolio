# Phase 4 - Deploy your website to Amazon S3

**Goal:** put your website on the internet using an S3 bucket with static website hosting.

By the end of this phase you can say:

- [ ] I created my own bucket in **Asia Pacific (Singapore)** with a name I chose.
- [ ] Static website hosting is on, with `index.html` as the index document.
- [ ] My bucket allows **public read** through a bucket policy, and nothing more.
- [ ] My HTML, CSS, JS and images load from the **Bucket website endpoint** in a private/incognito window.

Have ready: your username, the workshop password (on the instructor's slide), and the **contents** of your `site/` folder.
Get them from your repository with **Code → Download ZIP → Extract**.

---

## Step 1 - Sign in

Open **https://freecil.signin.aws.amazon.com/console** (account alias `freecil`). Sign in as **your** username, for example `workshop-user-07`, with the workshop password.

> 🔒 Everyone has the same password today, so **only ever use the username you were given.**
> Signing in as a classmate is not allowed, and every action is logged under the username that did it.

## Step 2 - Select Asia Pacific (Singapore)

Top-right Region menu → **Asia Pacific (Singapore) ap-southeast-1**.

## Step 3 - Open Amazon S3

Type **S3** in the search bar at the top → click **S3** under *Services*.

> You will see your classmates' buckets in the list too, and a few instructor buckets that say *"Access Denied"*.
> **Only ever open and change your own bucket.** AWS lets you see the others today, but every action is logged under your username.

## Step 4 - Create a general purpose bucket

Click **Create bucket**.

| Setting | What to choose |
|---|---|
| **AWS Region** | `Asia Pacific (Singapore) ap-southeast-1`. Check this! |
| **Bucket type** | **General purpose** |
| **Bucket namespace** (if shown) | **Global namespace** (default) |

## Step 5 - Choose your own bucket name

Pick **any** name you like that follows the rules, for example:

```text
my-first-cloud-portfolio      juan-delacruz-website      aws-bootcamp-project-2026
```

**Naming rules**

- ✅ only lowercase letters `a-z`, numbers `0-9` and hyphens `-`
- ✅ 3 to 63 characters, starting and ending with a letter or number
- ❌ no capitals, spaces, underscores `_`, or two dots in a row `..`; don't end with `-an` or `-s3alias`
- 🌍 names are **globally unique** across *every* AWS customer in the world. If you see *"Bucket with the same name already exists"*, someone already has that name: add something such as your initials or `-2026`.
- 🙈 the name appears in your website address, so don't use private information such as your student number.

## Step 6 - Keep the safe defaults

| Setting | Choose |
|---|---|
| **Object Ownership** | **ACLs disabled (recommended)**. Leave as is |
| **Block Public Access settings** | **Leave "Block *all* public access" CHECKED for now.** You will change it in Step 8 |
| **Bucket Versioning** | **Disable**. Leave as is |
| **Default encryption** | **SSE-S3** (Amazon S3 managed keys). Leave as is |
| **Advanced settings → Object Lock** | **Disable**. Leave as is |

## Step 7 - Create the bucket

Leave **Tags** empty (no tags are needed today) and click **Create bucket** at the bottom.

✅ A green banner says your bucket was created. **Write your bucket name down.** You need it for the rest of today.

> ℹ️ You may also see a **red** message: *"Insufficient permissions to apply Default Encryption"*.
> **That is expected. Ignore it.** Your bucket is already encrypted (SSE-S3 is automatic).

> ❌ **"Access Denied" when you click Create bucket?** Nothing was created, so fix it and click Create again:
> - the Region is not Singapore (Step 2), or
> - you added tags: remove them.

Your bucket works straight away. Click its name to open it and continue.

## Step 8 - Allow a public bucket policy (Block Public Access)

S3 has four **Block Public Access** switches. They are safety locks that override everything else:

| # | Setting | Blocks… | For our website |
|---|---|---|---|
| 1 | Block public access granted through **new ACLs** | new public ACLs | ✅ **Keep ON** (we don't use ACLs) |
| 2 | Block public access granted through **any ACLs** | all public ACLs | ✅ **Keep ON** |
| 3 | Block public access granted through **new public bucket policies** | public *bucket policies* | ⬜ **Turn OFF**: our site needs one |
| 4 | Block public and cross-account access through **any public bucket policies** | public access via policies | ⬜ **Turn OFF** |

1. **Permissions** tab → **Block public access (bucket settings)** → **Edit**.
2. **Uncheck** *Block all public access*, then **re-check** the first two (the ACL ones).
3. **Save changes** → type `confirm` → **Confirm**.

> Making something public is a **deliberate** decision. Only ever do it for content that is *meant* for everyone, like this portfolio.

## Step 9 - Enable static website hosting

1. **Properties** tab → scroll to the **very bottom**: **Static website hosting** → **Edit**.
2. **Static website hosting**: **Enable**. **Hosting type**: **Host a static website**.
3. **Index document**: `index.html` · **Error document**: leave empty, or type `index.html`.
4. **Save changes**.

At the bottom of **Properties** you now see a **Bucket website endpoint**, for example
`http://my-first-cloud-portfolio.s3-website-ap-southeast-1.amazonaws.com`.
Clicking it now shows **403 Forbidden**. That is correct, because the bucket is not readable yet.

## Step 10 - Allow public read with a bucket policy

1. **Permissions** tab → **Bucket policy** → **Edit**.
2. Copy the **Bucket ARN** shown above the editor, e.g. `arn:aws:s3:::my-first-cloud-portfolio`.
3. Paste this policy, then replace `YOUR-BUCKET-NAME` with **your** bucket name. Keep the `/*` at the end!

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadForStaticWebsite",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::YOUR-BUCKET-NAME/*"
    }
  ]
}
```

4. **Save changes**. The bucket shows a red **Publicly accessible** label. That is expected for a website.

**What this policy means, line by line:** `Effect: Allow` *lets* · `Principal: "*"` *anyone on the internet* ·
`Action: s3:GetObject` *read (download) files* · `Resource: …/*` *only the files inside this bucket*. Nobody may upload, delete or change anything.

> ⚠️ Use **exactly** this policy. Never add `s3:PutObject`, `s3:*`, or other people's names: strangers could then upload files to your bucket.

<details>
<summary>Error: "Policy has invalid resource"</summary>

The bucket name in `Resource` doesn't match your bucket exactly, or the `/*` is missing. Compare it character by character with the Bucket ARN.
</details>

<details>
<summary>Error: "Access denied" when saving the policy</summary>

Block Public Access settings 3 and 4 are still ON: redo Step 8.
</details>

## Step 11 - Upload your website files correctly

1. **Objects** tab → **Upload**.
2. Open your local `site` folder and **select everything inside it**: `index.html`, `style.css`, `script.js` and the `assets` folder.
3. **Drag them** onto the upload page (or **Add files** + **Add folder**) → **Upload** → wait for *"Upload succeeded"* → **Close**.

```text
✅ Correct                        ❌ Wrong (you dragged the folder itself)
index.html                         site/
script.js                            └── index.html ...
style.css
assets/
```

If you see `site/` at the top, open it, select everything, then use **Actions → Move** to the bucket root. Or delete it and upload the **contents** again.

## Step 12 - Open your website endpoint

**Properties** tab → bottom → **Bucket website endpoint** → click the link.

> 🔓 S3 website endpoints use **`http://`**, not `https://`. Your browser may say *"Not secure"*. That is normal for this endpoint.
> Production sites add HTTPS with **Amazon CloudFront** or **AWS Amplify Hosting**.

## Step 13 - Verify everything loads

1. Open the endpoint in a **private / incognito window**. That is how a stranger sees it.
2. Check: text (**HTML**) · colours and layout (**CSS**) · dark-mode and fun-fact buttons (**JavaScript**) · photos (**images**).
3. Press **F12 → Console**. Red `404 (Not Found)` errors name the exact missing file.
4. Try it on your phone using **mobile data** too.

🎉 **Your website is live on AWS!** Copy the endpoint URL for the showcase.

## Step 14 - Fix common errors

| What you see | Most likely cause | Fix |
|---|---|---|
| *Access Denied* on **Create bucket** | Region not Singapore, or you added tags | Step 2 / Step 7 |
| *Bucket with the same name already exists* | Name taken by someone, somewhere in the world | Choose another name |
| *Access Denied* inside a bucket | It is an instructor bucket, not yours | Open **your** bucket (Step 7 name) |
| **403 Forbidden** on the endpoint | Bucket policy missing/wrong, or Block Public Access 3/4 still ON | Steps 8 and 10 |
| **404 Not Found - NoSuchKey** | No `index.html` at the bucket root | Step 11; the name must be exactly `index.html` |
| **404 - NoSuchWebsiteConfiguration** | Static website hosting not enabled | Step 9 |
| Text but **no colours/layout** | `style.css` missing or in the wrong folder | It must sit next to `index.html` |
| **Images broken** | Wrong path or case (`Me.JPG` vs `me.jpg`) | Match the file name in `assets/` exactly |
| You still see the **old version** | Browser cache | **Ctrl+F5**, or a new incognito window |
| *"This site can't be reached"* / timeout | The campus network blocks `http://` S3 endpoints | See below |

**Campus network blocks the endpoint?**
1. Open the URL on your phone using **mobile data** (Wi-Fi off). If it works there, your website is fine and only the network blocks it.
2. Use the HTTPS fallback address: `https://s3.ap-southeast-1.amazonaws.com/YOUR-BUCKET-NAME/index.html`. Note that it ends in `/index.html`.

More answers: [TROUBLESHOOTING.md](../TROUBLESHOOTING.md)

➡️ Finished early? Try the bonus: [Phase 5 - Automatic deployment with GitHub Actions](05-cicd-bonus.md)
