# ☁️ AWS EC2 Instance Setup (Beginner Cloud Project)

This project demonstrates how to launch, connect to, and configure an EC2 instance on AWS. It includes setting up a basic Apache web server and adding a sample webpage using Amazon Linux 2023.

---

## 🛠️ Tools Used

- **AWS EC2**
- **Amazon Linux 2023**
- **Apache Web Server (httpd)**
- **SSH (MacOS/Linux Terminal)**
- **CloudShell (Optional)**

---

## 🚀 Steps to Launch and Configure an EC2 Instance

### ✅ Step 1: Sign In to AWS
- Go to [https://console.aws.amazon.com](https://console.aws.amazon.com)
- Sign in with your AWS account

---

### ✅ Step 2: Open EC2 Dashboard
- In the AWS Console search bar, type `EC2`
- Click on **EC2** under “Services”

---

### ✅ Step 3: Launch an Instance

#### 3.1 Name and OS
- Name: `MyFirstEC2`
- AMI: Amazon Linux 2023 or Ubuntu

#### 3.2 Instance Type
- Select `t2.micro` (Free Tier eligible)

#### 3.3 Key Pair
- Create/download a `.pem` key if you don't already have one
- Save it somewhere secure (e.g., `~/Downloads/ndwill_secret.pem`)

#### 3.4 Security Group Settings
- Allow:
  - **SSH** (port 22) — from your IP
  - **HTTP** (port 80) — if hosting a webpage

#### 3.5 Storage
- Leave default 8GB

---

### ✅ Step 4: Launch the Instance
- Click **Launch Instance**

---

### ✅ Step 5: Connect via SSH

#### From your terminal:
```bash
chmod 400 ~/Downloads/ndwill_secret.pem

ssh -i ~/Downloads/ndwill_secret.pem ec2-user@<your-public-ip>
