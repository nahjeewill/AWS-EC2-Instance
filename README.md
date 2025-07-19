# ☁️ AWS EC2 Instance Setup (Beginner Cloud Project)

This project demonstrates how to launch, connect to, and configure an EC2 instance on AWS. It includes setting up a basic Apache web server and adding a sample webpage using Amazon Linux 2023.

---

## 🛠️ Tools Used

- **AWS EC2**
- **Amazon Linux 2023**
- **Apache Web Server (httpd)**
- **SSH (MacOS/Linux Terminal)**

---

## 🚀 Steps to Launch and Configure an EC2 Instance

Go to https://console.aws.amazon.com/


Sign in to the AWS Management Console.



✅ Step 2: Open EC2 Dashboard
- In the AWS Console, type "EC2" in the search bar.


- Click on EC2 under “Services” to open the EC2 Dashboard.



✅ Step 3: Launch an Instance
- In the EC2 Dashboard, click “Launch instance”.


- Fill out the form:


3.1 Name and Tags
- Give your instance a name (e.g., “MyFirstEC2”).


3.2 Application and OS Images (Amazon Machine Image - AMI)
- Choose Amazon Linux 2023 or Ubuntu (free tier eligible options).


3.3 Instance Type
- Select t2.micro (Free Tier eligible).


3.4 Key Pair (login)
- Choose “Create new key pair” if you don’t have one.


- Download the .pem file — you’ll need it to SSH into the instance.


3.5 Network Settings
- Leave defaults or create a new security group.


- Ensure you allow SSH (port 22) and HTTP (port 80) if you plan to access a web server.


3.6 Configure Storage
- Leave the default (8 GB is fine).



✅ Step 4: Launch
- Click the “Launch instance” button at the bottom.


✅ Step 5: Connect to Your Instance
- Go to the Instances page in the EC2 Dashboard.


- Wait for the instance state to become “Running” and check the status checks.


- Select your instance → Click “Connect”.


- If using SSH from your terminal:
bash
CopyEdit
ssh -i /path/to/your-key.pem ec2-user@<public-ip-address>

- Replace /path/to/your-key.pem with the actual path to your .pem file.
- Replace <public-ip-address> with the one from your EC2 instance.

#  Navigate to your Terminal (MacOS)

Breakdown of Each Command Line

#### ✅ 1. SSH into EC2 Instance
##### ssh -i ~/Downloads/<your-key.pem> ec2-user@<public-ip-address>

- ssh: Secure Shell — used to remotely log into another computer.


- -i ~/Downloads/<your-key.pem>: Specifies the identity file (your private key) used to authenticate with the instance.


- ec2-user: The default username for Amazon Linux.


- @ The public IP address of your EC2 instance.


#### This command securely connects your Mac to your EC2 instance.

✅ 2. Set File Permissions

##### chmod 400 ~/Downloads/<your-key.pem>
- chmod: Changes permissions of a file.


- 400: Makes the file readable only by you. This is required for .pem files to prevent SSH from rejecting them for being too public.


- ~/Downloads/<your-key.pem>: The private key file you downloaded from AWS.


#### This command ensures your key file is secure enough to be used by SSH.


✅ 3. Update the System

##### sudo yum update -y

- sudo: Run as superuser (admin privileges).


- yum: Package manager used in Amazon Linux to install/update software.


- update: Checks for and installs the latest versions of system packages.


-y: Automatically says "yes" to all prompts.


#### This keeps your EC2 instance secure and up to date.

✅ 4. Install Packages

##### sudo yum install httpd -y

- install httpd: Installs the Apache HTTP server.


- You can replace httpd with other package names like git, wget, or unzip.


#### This command sets up a basic web server on your instance.

✅ 5. Start Apache Web Server

##### sudo systemctl start httpd

- systemctl: Used to control services (start, stop, restart).


- start httpd: Starts the Apache web server.


#### This launches your web server so it can begin serving web pages.

✅ 6. Enable Apache to Start on Boot

##### sudo systemctl enable httpd

#### Ensures that Apache starts automatically whenever the instance is rebooted.

✅ 7. Add Test Webpage

##### echo "(Write anything you want)" | sudo tee /var/www/html/index.html

- echo "(Write anything you want)": Outputs text.
- | sudo tee /var/www/html/index.html: Writes that output to a web page file with admin permissions.


#### This creates a simple web page you can view in your browser using your instance’s public IP.


#### From your terminal:
```bash
chmod 400 ~/Downloads/ndwill_secret.pem

ssh -i ~/Downloads/ndwill_secret.pem ec2-user@<your-public-ip>

chmod 400: Secures the key file

ssh -i: Connects using your private key

ec2-user: Default user for Amazon Linux

<your-public-ip>: Replace with your EC2's public IP
