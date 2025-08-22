# 🌟 Ashutosh Web Portfolio

A simple, fast, and fully static personal portfolio website built with **HTML**, **CSS**, and **JavaScript**.  
This project **automatically deploys** to an **Amazon S3** bucket using **GitHub Actions** whenever changes are pushed to the `main` branch.

---

## ✨ Features
- 🔧 **Zero-framework static site**: `index.html`, `style.css`, `script.js`
- 🚀 **Continuous deployment** to S3 on every push to `main`
- 🌐 **Optional S3 Static Website Hosting** (public read)
- 🧪 **Easy local development** — open `index.html` directly or run a local web server

---


## 📁 Project Structure
```
📂 Folder Structure
├─ .github/
│ └─ workflows/
│ └─ main.yml # CI/CD workflow (see below)
├─ index.html # Main page
├─ style.css # Styles
├─ script.js # Client-side scripts
└─ README.md
```

## 🧰 Prerequisites

Before setting up and deploying this project, ensure you have:

- 📂 A **GitHub repository** for this project
- ☁️ An **AWS account** with permissions to create and manage S3 buckets
- 💻 **AWS CLI** installed (optional, for manual deployments)
- 🪣 An **S3 bucket** (example: `tws-portfolio-1234` in `us-east-1`)

> 💡 You can rename the bucket and region — just make sure to update the values in both `main.yml` and your AWS setup.

---

## 🧪 Run Locally (Development)

You can preview the project locally by either opening `index.html` in your browser or running a lightweight web server.

**Using Python 3:**
```bash
python3 -m http.server 8000
# Visit http://localhost:8000
```
---

## ☁️ One-Time AWS Setup

### 1️⃣ Create the S3 Bucket
```bash
aws s3 mb s3://tws-portfolio-1234 --region us-east-1
```
### 2️⃣ Enable S3 Static Website Hosting
```bash
Disable "Block all public access" on the bucket.
Add the following Bucket Policy to allow public read access:
```
```
   {"Version": "2012-10-17",
       "Statement": [
         {
           "Sid": "PublicReadGetObject",
           "Effect": "Allow",
           "Principal": "*",
           "Action": ["s3:GetObject"],
           "Resource": ["arn:aws:s3:::tws-portfolio-1234/*"]
         }
       ]
      }
```
---

## 🌐 Website Endpoint

Once hosting is enabled, your site will be available at a URL like:  

   http://tws-portfolio1234.s3-website-us-east-1.amazonaws.com

---

## 🤖 CI/CD with GitHub Actions

This project uses GitHub Actions for **automatic deployment** to S3 whenever changes are pushed to the `main` branch.  
The workflow file is located at:  

--- 

### 🔑 Required GitHub Secrets
In your repository, go to:  
**Settings → Secrets and variables → Actions**, and add:

- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`

---

## ❗ Troubleshooting

### 🚫 403 Forbidden on Website Endpoint
- Public access might still be blocked, or the **bucket policy** is missing.
- You may be using the wrong **region-specific website endpoint**.

### 🔒 GitHub Actions Fails with "AccessDenied"
- The IAM user is missing one or more of the following permissions:  
  `s3:PutObject`, `s3:DeleteObject`, `s3:ListBucket`
- GitHub **Secrets** are not configured or have typos.

### ⚠️ Bucket Name Already Exists
- S3 bucket names are **globally unique**.  
- Choose a different name, e.g.:  
  `tws-portfolio-<random-string>`

## 📜 License
This project is licensed under the **MIT License** — feel free to use, modify, and distribute.  
If your project requires a different license, update this section accordingly.

---

## ✨ Output Screenshot

### TWS Portfolio
<img width="1900" height="1029" alt="Screenshot 2025-08-22 115211" src="https://github.com/user-attachments/assets/50341a15-1b20-403c-a5b6-f17da62a7906" />

---

<img width="1569" height="964" alt="Screenshot 2025-08-22 140816" src="https://github.com/user-attachments/assets/78095b39-5a63-42b4-ad5f-7f1723316050" />



