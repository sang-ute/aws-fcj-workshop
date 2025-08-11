---
title: "Deploying S3 UI Bucket and CloudFront CDN"
date: "`r Sys.Date()`"
weight: 7
chapter: false
pre: " <b> 8. </b> "
---

## **Deploy React/Vite Frontend to S3 + CloudFront**

---

### **Step 1 — Create S3 Bucket**

1. Go to **AWS Console → S3 → Create bucket**.
2. **Bucket name:**
   Give it a **unique name** (e.g., `my-frontend-app-bucket`).
   _(This is the only field you change — keep all other settings default.)_

   ![alt text](image.png)

3. Leave:

   - AWS Region → Default or your choice
   - Object Ownership → ACLs disabled
   - Block Public Access → Keep as default
   - Versioning, Encryption, Tags → default

![alt text](image-1.png)

4. Click **Create bucket**.

![alt text](image-2.png)

---

### **Step 2 — Create CloudFront Distribution**

1. Go to **AWS Console → CloudFront → Create distribution**.

![alt text](image-3.png)

Then enter your Distribution name

![alt text](image-4.png)

2. **Origin type:** Select **S3**.

![alt text](image-5.png)

3. Choose the S3 bucket you just created.

![alt text](image-6.png)

4. Keep **all other settings default**:

![alt text](image-8.png)

- Viewer protocol policy → Redirect HTTP to HTTPS
- Cache settings → Use origin cache headers
- Logging → Off

5. Click **Next**.
6. **Web Application Firewall (WAF):** Select **Do not enable**.

![alt text](image-9.png)

7. Click **Next**.
8. Review → Click **Create distribution**.

![alt text](image-7.png)

---

### **Step 3 — Set Default Root Object**

1. Go to your new CloudFront distribution.
2. **Settings → Edit**.

![alt text](image-10.png)

3. **Default root object:** `index.html`

![alt text](image-11.png)

4. Save changes.

---

### **Step 4 — Build Your Frontend**

From your local project:

```bash
cd frontend
npm run build
```

This will generate your build output in `dist/` (Vite) or `build/` (React).

![alt text](image-12.png)

---

### **Step 5 — Upload to S3**

1. Copy everything inside the `dist/` folder (not the folder itself).
2. Go to **S3 bucket → Upload**.

![alt text](image-13.png)

3. Drag-and-drop files, leave permissions default, click **Upload**.

---

### **Step 6 — Wait for CloudFront Propagation**

- It may take **a few minutes** for CloudFront to update.

![alt text](image-14.png)

- Once done, go to **CloudFront → Your Distribution → Copy the Distribution Domain Name** (not the ARN).

![alt text](image-15.png)

- Paste that into your browser to access your site.

![alt text](image-16.png)

And that's it! You've successfully set up a serverless frontend with Vite and deployed it to AWS using CloudFront and S3. You can now watch your site update in real-time as you make changes to your code. Happy AWS coding, and thank you so much for doing this workshop until now!
