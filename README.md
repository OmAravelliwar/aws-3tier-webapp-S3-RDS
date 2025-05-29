Sure! Here's a revised version of the project document tailored **for you** instead of your friend, with clearer formatting, fixed image markdown issues, and a more personalized tone. You can replace the links at the bottom with your own GitHub and LinkedIn profiles.

---

# 🚀 Deploying a Scalable AWS 3-Tier Web Application

This project demonstrates how to deploy a **production-ready 3-tier architecture** on AWS using EC2, RDS, S3, CloudFront, and Load Balancers. It allows users to upload images via a web form, stores the files in an S3 bucket, saves the URLs in a MariaDB database on RDS, and serves them efficiently through CloudFront.

---

## 🏗️ Architecture Overview

### ✅ AWS Services Used

* **VPC** with public & private subnets across 2 Availability Zones
* **EC2 Instances** for Web and App Servers (Auto Scaling + AMIs)
* **RDS (MariaDB)** in private subnets for storing image URLs
* **S3 Bucket** for storing uploaded images
* **CloudFront CDN** for delivering content globally
* **Load Balancers**:

  * External (for the Web Layer)
  * Internal (for the App Layer)
* *(Optional)* **Telegram Bot** for alerting

---

### 🔁 Upload Workflow

1. User accesses the web form on the **Web Server** via an external Load Balancer
2. Form data is sent to the **App Server** through an internal Load Balancer
3. App Server uploads the image to **S3**
4. The **S3 URL** is stored in **RDS**
5. Image is then served to the user via **CloudFront**

---

## 🔧 Deployment Steps

1. **VPC Setup**

   * Created a VPC with 4 subnets per AZ
   * Zone A & B: 1 Public + 3 Private subnets each

2. **RDS Configuration**

   * Deployed MariaDB in private subnets

3. **S3 Bucket**

   * Created in the same region for image storage

4. **App Server Configuration**

   * EC2 instance with NGINX, PHP, and MySQL connector
   * Created `/uploads` directory with proper permissions
   * Added `upload.php` to handle file uploads and DB entries

5. **App Server AMI + Auto Scaling**

   * Created AMI and used it in a Launch Template
   * Attached to Auto Scaling Group behind an **Internal Load Balancer**

6. **Web Server Configuration**

   * EC2 instance with NGINX
   * `files.html` used for the frontend form
   * Configured `nginx.conf` to proxy to App Server

7. **Web Server AMI + Auto Scaling**

   * Created AMI and Auto Scaling Group
   * Registered with an **Internet-facing Load Balancer**

8. **DNS Setup**

   * Domain pointing to the external Load Balancer for frontend access

---

## 📸 Screenshots

### 🔹 VPC & Subnet Setup

![VPC Setup](attachment)

### 🔹 EC2 Instances

![EC2 Instances](attachment)

### 🔹 Load Balancers

![Load Balancer](attachment)

### 🔹 Upload Directory with Permissions

![Upload Dir](attachment)

### 🔹 S3 Bucket View

![S3 Bucket](attachment)

### 🔹 RDS Data Entry

![RDS Result](attachment)

---

📤 **Upload flow:** Photo → S3 Bucket → URL → RDS → Delivered via CloudFront

---

## 🧠 Key Learnings

* Custom **VPC & Subnet design**
* Creating and using **AMIs** in **Auto Scaling Groups**
* Integrating **Internal & External Load Balancers**
* Configuring **NGINX + PHP + MariaDB**
* Serving assets via **S3 + CloudFront**
* Optional **Telegram alert integration**

---

## 📁 Files Included

* `files.html` – HTML form for file upload
* `upload.php` – PHP script to upload image and save URL to DB
* `nginx.conf` – Sample proxy configuration
* Screenshots of setup & results

---

## 📣 Let’s Connect!

If this project interests you or you'd like to collaborate:

* 💼 LinkedIn: [[Your LinkedIn](https://www.linkedin.com/)](https://www.linkedin.com/in/om-aravelliwar-2a27b7331/)
* 🐙 GitHub: [OmAravelliwar](https://github.com/)

---

## 🏷️ Tags

`AWS` `EC2` `RDS` `S3` `CloudFront` `LoadBalancer` `WebApp` `DevOps` `PHP` `NGINX` `VPC`

---

Would you like me to:

* Export this as a PDF?
* Save it as a `README.md` file?
* Generate a diagram for the architecture?

Let me know!
