# 🌐 Secure Static Website Hosting with AWS S3 + CloudFront

## 📌 Project Overview

This project demonstrates how to host a **static website securely** using:

* Amazon S3 (private bucket)
* CloudFront (CDN)
* Origin Access Control (OAC)

The architecture ensures that **only CloudFront can access the S3 bucket**, making the setup secure and production-ready.

---

## 🧱 Architecture

```
User → CloudFront → S3 (Private Bucket)
```

* CloudFront serves content globally
* S3 stores static files (HTML, CSS, JS)
* Direct access to S3 is blocked

---

## 🚀 Technologies Used

* AWS S3
* AWS CloudFront
* AWS IAM

---

## 🔐 Key Features

* ✅ Private S3 bucket (no public access)
* ✅ Secure access using Origin Access Control (OAC)
* ✅ Global content delivery via CloudFront
* ✅ Improved performance with caching
* ✅ Scalable and cost-efficient architecture

---

## 📂 Project Structure

```
src/
│── booking-history.html
│── header (1).jpg
│── index.html
│── style.css
```

---

## ⚙️ Setup Steps

### 1. Create S3 Bucket

* Create a new S3 bucket
* Enable **Block all public access**
* Do NOT enable static website hosting

---

### 2. Upload Files

* Upload `index.html` and other static assets

---

### 3. Create CloudFront Distribution

* Select S3 bucket as origin
* Choose:

  * ✅ Allow private S3 bucket access (Recommended)
  * ✅ Use recommended settings

---

### 4. Configure Origin Access Control (OAC)

* CloudFront automatically creates and attaches OAC
* Bucket policy is updated automatically

---

### 5. Set Default Root Object

```
index.html
```

---

### 6. Deploy

* Wait for CloudFront distribution to deploy
* Access via:

```
https://d4lqfqqs5m2aj.cloudfront.net/
```

---

## 🔍 Testing

| Test Case      | Expected Result |
| -------------- | --------------- |
| CloudFront URL | ✅ Website loads |
| S3 direct URL  | ❌ Access Denied |

---

## ⚠️ Common Issues & Fixes

### ❌ AccessDenied on CloudFront

* Ensure `index.html` is set as default root object
* Verify bucket policy
* Check OAC is attached

### ❌ Works with `/index.html` but not `/`

* Missing default root object

## ⚠️ Common Issues & How I Solved Them

1. **AccessDenied on CloudFront URL**  
   - Cause: Default root object not set or OAC not attached  
   - Fix: Set `index.html` as default root object and verified OAC/policy  

2. **Direct S3 URL accessible (security risk)**  
   - Cause: Public access enabled  
   - Fix: Blocked all public access and restricted S3 to CloudFront only

---

## 🎯 Learning Outcomes

* Understanding AWS S3 private bucket configuration
* Using CloudFront as a secure CDN
* Implementing Origin Access Control (OAC)
* Debugging access and permission issues

---

## 👨‍💻 Author

Jerwin Andro S

https://github.com/jerwin-18/Cloudfront-s3.git
