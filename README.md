# devops-capstone

## 🚀 Project Overview
This project demonstrates a complete **DevOps Lifecycle** implementation for a Node.js web application. The goal was to replace manual deployment with a fully automated **Continuous Integration and Continuous Deployment (CI/CD)** pipeline.

The project hosts the application on an **AWS EC2** instance, uses **Docker** for containerization, **Jenkins** for automation, and **Prometheus & Grafana** for real-time monitoring.

---

## 🛠️ Tech Stack & Tools
* **Cloud Provider:** AWS EC2 (Ubuntu 22.04 LTS)
* **Containerization:** Docker & Docker Hub
* **Orchestration:** Jenkins (Pipeline as Code)
* **Application:** Node.js (v18) & Express.js
* **Monitoring:** Prometheus (Metrics) & Grafana (Visualization)
* **Version Control:** GitHub
* **Scripting:** Bash (Backups) & Cron (Scheduling)

---

## ⚙️ CI/CD Flow Explained
The automation is handled by a `Jenkinsfile` that executes the following pipeline stages:

1.  **Build:** Jenkins triggers on a GitHub push, checks out the code, and builds a new Docker image.
2.  **Login:** The pipeline securely authenticates with Docker Hub using encrypted credentials.
3.  **Push:** The newly built image is tagged and pushed to the Docker Hub registry for versioning.
4.  **Deploy:** Jenkins pulls the latest image onto the production server, stops the old container, and starts the new one on **Port 3000**.
5.  **Monitor:** Prometheus continuously collects system metrics, which are visualized on a Grafana dashboard.

---

## 💻 Setup Instructions (Build & Run Locally)
To test this application on your local machine (without Jenkins/AWS), follow these commands:

### Prerequisites
* [Docker Desktop](https://www.docker.com/products/docker-desktop/) installed.
* Git installed.

### 1. Clone the Repository
```bash
git clone [https://github.com/Risi2004/devops-capstone.git](https://github.com/Risi2004/devops-capstone.git)
cd devops-capstone
