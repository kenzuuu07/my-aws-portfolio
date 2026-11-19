# Troubleshooting

Find your symptom, try the fix, and raise your hand if it still fails after **5 minutes**.

## Signing in

| Symptom | Fix |
|---|---|
| "Your authentication information is incorrect" | Username is `workshop-user-07` style: lowercase, hyphens, two-digit seat number. Retype the workshop password exactly; pasting can add a space. |
| Sign-in page asks for an **email** | You are on the root-user page. Open **https://freecil.signin.aws.amazon.com/console**, or choose **IAM user** and type the alias `freecil`. |
| Signed in but it says someone else's username (top-right) | Sign out and sign in with **your own** username. Never use a classmate's account. |
| Console Home shows "Access denied" boxes | Normal. Your account only has S3 permissions. |

## Creating the bucket

| Symptom | Fix |
|---|---|
| **Access Denied** on Create bucket | Region must be **Singapore**, and leave **Tags** empty. Nothing was created, so just fix it and click Create again. |
| "Bucket with the same name already exists" | Names are unique across all of AWS. Pick a different name, e.g. add your initials. |
| "Bucket name must not contain uppercase characters" (or similar) | Use only lowercase letters, numbers and `-`. No spaces or `_`. 3–63 characters. |
| Red "Insufficient permissions to apply Default Encryption" after creating | Expected. Ignore it: your bucket is encrypted automatically. |
| You see classmates' buckets | Expected today. Open and change **only your own** bucket; every action is logged under your username. |
| A bucket says "Access Denied" | It's an instructor bucket. Use your own. |

## The website

| Symptom | Fix |
|---|---|
| **403 Forbidden** | Add the bucket policy ([Phase 4, Step 10](instructions/04-deploy-to-s3.md#step-10---allow-public-read-with-a-bucket-policy)) and turn **off** Block Public Access 3 and 4 (Step 8). |
| Saving the bucket policy gives **Access denied** | Block Public Access 3/4 are still on. |
| "Policy has invalid resource" | Your bucket name in `Resource` is wrong, or `/*` is missing at the end. |
| **404 NoSuchKey** | `index.html` is not at the top level. Did you upload the `site` *folder* instead of its *contents*? |
| **404 NoSuchWebsiteConfiguration** | Enable **Static website hosting** (Properties tab, bottom). |
| No colours / layout | `style.css` missing or in the wrong place. It must sit next to `index.html`. |
| Images don't show | Path or **capital letters** don't match: `assets/me.jpg` ≠ `assets/Me.JPG`. |
| Buttons do nothing | `script.js` missing, or a JavaScript typo. Press **F12 → Console**. |
| Old version still showing | **Ctrl+F5**, or a new incognito window. |
| "This site can't be reached" / keeps loading | The network may block `http://` S3 addresses. Try phone data, or `https://s3.ap-southeast-1.amazonaws.com/YOUR-BUCKET/index.html`. |
| Browser says "Not secure" | Normal. S3 website endpoints are HTTP only. |

## GitHub

| Symptom | Fix |
|---|---|
| No "Use this template" button | Sign in to GitHub. |
| Can't commit to the workshop repository | Correct. Commit to **your** repository (created from the template). |
| `git push` asks for a password | Use the browser upload method (Phase 2, Path A) instead. |

## GitHub Actions (bonus)

| Symptom | Fix |
|---|---|
| Workflow never appears on the **Actions** tab | The file must be exactly `.github/workflows/deploy.yml` (leading dot) on branch `main`. |
| "Secret … is missing" / "Variable S3_BUCKET is missing" | Names must match exactly; `S3_BUCKET` goes on the **Variables** tab. |
| `InvalidClientTokenId` or `SignatureDoesNotMatch` | Re-create both secrets; watch for spaces and swapped values. |
| `AccessDenied` | The key's IAM user may not upload to that bucket, or `S3_BUCKET` has a typo. |
| Green run but no change | Ctrl+F5, and make sure you edited files inside `site/`. |

## Leaked a password or key, or someone used your username?

Tell the instructor **immediately**. They can revoke access within seconds. Nobody gets in trouble for reporting quickly.
