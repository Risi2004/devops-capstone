# devops-capstone

## 🚀 Project Overview
This project demonstrates a complete **DevOps CI/CD Pipeline** for a Node.js web application. The goal was to automate the build, deployment, and monitoring processes using industry-standard tools. 

The project involves hosting a web application on an **AWS EC2** instance, containerizing it using **Docker**, automating deployment with **Jenkins**, and monitoring system health using **Prometheus** and **Grafana**. Additionally, automated log backups are handled via **Shell Scripting** and **Cron jobs**.

---

## 🛠️ Tech Stack & Tools Used
* **Cloud Provider:** AWS EC2 (Ubuntu Linux)
* **Containerization:** Docker & Docker Hub
* **CI/CD Automation:** Jenkins (Pipeline as Code)
* **Source Control:** GitHub
* **Application:** Node.js (v18) & Express.js
* **Monitoring:** Prometheus (Metrics) & Grafana (Visualization)
* **Scripting:** Bash Shell & Crontab

---

## 🏗️ Architecture
The pipeline follows this workflow:
1.  **Source:** Developer pushes code to GitHub.
2.  **Build:** Jenkins detects changes, pulls code, and builds a Docker image.
3.  **Release:** Jenkins pushes the tagged image to Docker Hub.
4.  **Deploy:** Jenkins pulls the image on the production server and runs the container.
5.  **Monitor:** Prometheus scrapes system metrics, and Grafana visualizes them.

---

## ⚙️ Key Features & Configuration

### 1. CI/CD Pipeline (`Jenkinsfile`)
The pipeline consists of four automated stages:
* **Build Docker Image:** Packages the Node.js app.
* **Login to Docker Hub:** Authenticates securely using Jenkins Credentials.
* **Push Image:** Uploads the artifact to the registry (`risi2004/devops-capstone`).
* **Deploy:** Stops the old container and restarts the app on Port 3000.

### 2. Monitoring Setup
* **Prometheus:** configured to run on Port **9090**.
* **Grafana:** configured to run on Port **3001** (Changed from default 3000 to avoid conflict with the app).
* **Dashboard:** Visualizes CPU, Memory, and Uptime.

### 3. Automation (Backups)
* **Script:** `backup.sh` compresses `/var/log/syslog` into a timestamped `.tar.gz` file.
* **Cron Job:** Scheduled to run every minute (`* * * * *`) to ensure logs are regularly archived.

---

## 🚀 How to Run the Project

### Prerequisites
* AWS Account
* Docker Hub Account
* GitHub Account

### Step 1: Clone the Repository
```bash
git clone [https://github.com/Risi2004/devops-capstone.git](https://github.com/Risi2004/devops-capstone.git)
cd devops-capstone
