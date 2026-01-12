# CI/CD Pipeline Implementation for Apache Web Server on Linux VM using Azure DevOps

## 📌 Project Overview
This project demonstrates a **complete CI/CD (Continuous Integration and Continuous Deployment) workflow** using **Azure DevOps**.  
A static website is automatically deployed to a **Linux Virtual Machine running Apache Web Server** whenever changes are pushed to the repository.

The project focuses on real-world DevOps practices including automation, artifact management, secure deployments, and Linux permission handling.

---

## 🎯 Project Objectives
- Automate website deployment using Azure DevOps
- Implement CI and CD using YAML pipeline
- Deploy website files to Apache on a Linux VM
- Understand artifact usage in CI/CD
- Handle real-world deployment issues (permissions)

---

## 🛠️ Tools & Technologies Used
- **Azure DevOps** (Repos, Pipelines, Artifacts)
- **Linux Virtual Machine (Ubuntu)**
- **Apache Web Server**
- **Git & GitHub**
- **SSH (PuTTY)**
- **YAML**

---

## 🏗️ Architecture Flow
Code Push (Azure Repos)
↓
Continuous Integration (CI)

Checkout source code

Prepare website files

Create & publish artifacts
↓
Continuous Deployment (CD)

Connect to Linux VM via SSH

Deploy files to Apache directory

Restart Apache service

yaml
Copy code

---

## ⚙️ Apache Setup on Linux VM

### 1️⃣ Install Apache
```bash
sudo apt update
sudo apt install apache2 -y
2️⃣ Start and Enable Apache
bash
Copy code
sudo systemctl start apache2
sudo systemctl enable apache2
3️⃣ Verify Apache Status
bash
Copy code
sudo systemctl status apache2
Expected status:

arduino
Copy code
Active: active (running)
4️⃣ Apache Web Root Directory
Apache serves files from:

bash
Copy code
/var/www/html
Project website directory:

bash
Copy code
/var/www/html/website2-linking-vm-apchi
🌐 Azure VM Networking Configuration
Go to Azure Portal → VM → Networking

Add an Inbound Security Rule

Port: 80

Protocol: TCP

Action: Allow

Website access URL:

perl
Copy code
http://<VM-PUBLIC-IP>/website2-linking-vm-apchi/
📁 Source Code Management (Azure Repos)
All website files (index.html, CSS, JS) are stored in Azure Repos.

Git Commands Used
bash
Copy code
git add .
git commit -m "Updated website content"
git push origin main
⚠️ Note:
Apache does not read files directly from the repository.
Changes appear on the VM only after the pipeline runs.

🔁 CI/CD Pipeline Explanation
🔹 Continuous Integration (CI)
CI is responsible for:

Fetching source code from Azure Repos

Preparing website files

Creating and publishing build artifacts

CI Tasks:

Checkout source code

Copy website files

Publish build artifacts

🔹 Continuous Deployment (CD)
CD is responsible for:

Deploying artifacts to the Linux VM

Restarting Apache to reflect changes

CD Tasks:

Copy files to VM using SSH

Deploy to Apache web directory

Restart Apache service

✅ Since the pipeline automatically deploys code, this project implements CI/CD, not only CI.

📦 Artifact Usage
Artifacts act as a bridge between CI and CD.

Flow:

powershell
Copy code
CI → Artifact Creation → CD → Deployment
Benefits:

Clean and consistent deployments

Separation of build and deployment

Easy rollback if required

❌ Deployment Error Faced (Real-Time Issue)
Error Message
css
Copy code
Permission denied /var/www/html/website2-linking-vm-apchi
Root Cause
Apache web directory is owned by root

Azure DevOps connects using a non-root SSH user

Linux restricted write access

✅ Resolution (Permission Fix)
Executed on Linux VM using PuTTY:

bash
Copy code
sudo chown -R azureuser:azureuser /var/www/html/website2-linking-vm-apchi
sudo chmod -R 755 /var/www/html/website2-linking-vm-apchi
✔️ Enabled secure deployment
✔️ Followed industry best practices
✔️ No root login required

🔄 How Updates Work
Whenever website files are modified:

Edit the file (e.g., index.html)

Commit and push changes to main

Azure DevOps pipeline triggers automatically

Files are deployed to the Linux VM

Apache serves the updated content

🧪 Validation
After a successful pipeline run:

perl
Copy code
http://<VM-PUBLIC-IP>/website2-linking-vm-apchi/
If changes are not visible:

Perform a hard refresh: Ctrl + Shift + R

📚 Key Learnings
Difference between CI and CI/CD

Azure DevOps YAML pipelines

Artifact management

Linux file permissions

Apache deployment automation

Real-world DevOps troubleshooting

📌 Conclusion
This project demonstrates a real-world CI/CD automation workflow using Azure DevOps and Linux infrastructure.
It highlights practical DevOps skills such as pipeline creation, automated deployment, and resolving production-level issues.

👤 Author
Shaik Mohameed Anays
Final Year B.Tech – Computer Science & Business Systems
Aspiring DevOps Engineer 🚀

markdown
Copy code

---

## ✅ What this README gives you
- Crystal clear understanding when repo is opened
- Beginner-friendly + professional
- Interview-ready explanation
- Real DevOps scenario included
