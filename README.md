===================================================================================================================================================================================
  It is written exactly at a DevOps / Jenkins / Docker project level.

# Project Frontend – CI/CD with Jenkins & Docker

This repository contains the **frontend application** for the project, built using **Vite + TypeScript** and deployed using **Docker (Nginx)** with a **Jenkins CI/CD pipeline**.

---

## 📌 Tech Stack

- **Frontend:** Vite + TypeScript
- **Web Server:** Nginx
- **Containerization:** Docker (Multi-stage build)
- **CI/CD:** Jenkins
- **Source Control:** GitHub

---

## 📂 Project Structure

```text
project-frontend/
├── src/                     # Application source code
├── public/                  # Static assets
├── Dockerfile               # Multi-stage Docker build
├── Jenkinsfile              # Jenkins CI/CD pipeline
├── package.json             # Node dependencies
├── package-lock.json        # Dependency lock file
├── vite.config.ts           # Vite configuration
└── README.md                # Project documentation

🐳 Docker Overview

This project uses a multi-stage Docker build:

Build Stage

Uses node:20-alpine

Installs dependencies

Builds the Vite project

Runtime Stage

Uses nginx:alpine

Serves the built static files from /usr/share/nginx/html

Dockerfile Highlights

Optimized image size

No Node.js in production image

Nginx serves static frontend efficiently

🚀 Jenkins CI/CD Pipeline

The Jenkins pipeline performs the following steps:

Checkout source code from GitHub

Build Docker image

Stop & remove any existing container

Run a new Docker container with the latest build

Pipeline Features

Declarative Jenkins Pipeline

Idempotent deployment

Zero manual intervention

Easy rollback by rebuilding

▶️ How to Deploy Using Jenkins
Prerequisites

Jenkins installed

Docker installed on Jenkins server

Jenkins user added to Docker group

sudo usermod -aG docker jenkins
sudo systemctl restart jenkins

Jenkins Job Configuration

Create a Pipeline job

Select Pipeline script from SCM

Configure Git:

Repository URL:

https://github.com/Rajesh-210/project-frontend.git


Branch:

*/main


Script Path:

Jenkinsfile


Save and click Build Now

🌐 Application Access

After a successful build, access the frontend at:

http://<JENKINS_SERVER_IP>:80


(Ensure port 80 is open in the firewall or security group)

🧪 Useful Docker Commands
# List running containers
docker ps

# View logs
docker logs project-frontend-container

# Stop container
docker stop project-frontend-container

# Remove container
docker rm project-frontend-container

⚠️ Common Issues & Fixes
Jenkinsfile Not Found

✔ Ensure job uses Pipeline script from SCM
✔ Script path is exactly Jenkinsfile (case-sensitive)

Docker Permission Denied
sudo usermod -aG docker jenkins
sudo systemctl restart jenkins

Port Already in Use

Change port mapping in Jenkinsfile:

-p 8080:80


Access via:

http://<IP>:8080

📌 Future Enhancements

Docker Hub image push

GitHub webhook auto-trigger

Versioned Docker tags

Kubernetes / Docker Swarm deployment

Nginx custom configuration
=======================================================================================================================================================================
✅ 1️⃣ RESUME-READY README.md (UPGRADED)
# Project Frontend – CI/CD Automation with Jenkins & Docker

A production-ready **frontend deployment pipeline** built using **Vite + TypeScript**, containerized with **Docker**, and automated using **Jenkins CI/CD**.  
The application is served via **Nginx** using a multi-stage Docker build for optimized performance and image size.

---

## 🚀 Key Highlights

- End-to-end CI/CD pipeline using Jenkins
- Multi-stage Docker build (Node.js → Nginx)
- Automated container replacement deployment
- Clean, scalable, production-ready setup
- GitHub-integrated Jenkins pipeline

---

## 🛠️ Tech Stack

| Category | Technology |
|-------|-----------|
| Frontend | Vite, TypeScript |
| Web Server | Nginx |
| CI/CD | Jenkins |
| Containerization | Docker |
| SCM | GitHub |

---

## 📂 Project Structure

```text
project-frontend/
├── src/                    # Frontend source code
├── public/                 # Static assets
├── Dockerfile              # Multi-stage Dockerfile
├── Jenkinsfile             # Jenkins pipeline definition
├── package.json            # Dependencies
├── vite.config.ts          # Vite configuration
└── README.md               # Documentation

🐳 Docker Implementation
Multi-Stage Build Strategy

Stage 1 – Build

Base Image: node:20-alpine

Installs dependencies

Generates optimized production build

Stage 2 – Runtime

Base Image: nginx:alpine

Serves static frontend

Lightweight & secure

✔ Reduced image size
✔ Faster startup
✔ Production-ready

🔄 Jenkins CI/CD Pipeline Flow

Checkout code from GitHub

Build Docker image

Stop existing container (if running)

Deploy new container automatically

✔ No manual steps
✔ Idempotent deployment
✔ Easily repeatable builds

▶️ Deployment Instructions
Prerequisites

Jenkins installed

Docker installed

Jenkins user added to Docker group

sudo usermod -aG docker jenkins
sudo systemctl restart jenkins

Jenkins Job Configuration

Job Type: Pipeline

Definition: Pipeline script from SCM

Repository URL:

https://github.com/Rajesh-210/project-frontend.git


Branch: */main

Script Path: Jenkinsfile

Click Build Now to deploy.

🌐 Application Access
http://<JENKINS_SERVER_IP>:80


(Ensure port 80 is open)

📌 Architecture Diagram
Developer
   |
   |  Git Push
   v
GitHub Repository
   |
   |  SCM Poll / Webhook
   v
Jenkins Pipeline
   |
   |  Docker Build
   v
Docker Image
   |
   |  Docker Run
   v
Nginx Container
   |
   v
End User Browser

🧠 DevOps Concepts Demonstrated

CI/CD automation

Docker multi-stage builds

Immutable deployments

Infrastructure consistency

Production-grade frontend hosting
