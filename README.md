# Automated CI/CD Pipeline for a Dockerized Flask Application on AWS

---

## 📌 Project Overview

I built this project to understand **how a complete CI/CD pipeline works in a real-world DevOps setup** using core tools like Jenkins, Docker, and AWS.

The project implements an **automated CI/CD pipeline** that deploys a **2-tier Flask + MySQL application** on an **AWS EC2 instance**.  
Whenever code is pushed to GitHub, Jenkins automatically builds Docker images and deploys the updated application using Docker Compose.

---

## 🛠️ Tech Stack

- **Cloud**: AWS EC2 (Ubuntu 22.04)
- **CI/CD**: Jenkins
- **Containerization**: Docker, Docker Compose
- **Backend**: Python Flask
- **Database**: MySQL
- **Version Control**: Git & GitHub
- **OS**: Linux
- **Scripting**: Bash

---

## 🧱 Architecture Overview
```
Developer
|
| git push
v
GitHub Repository
|
| Webhook / SCM Poll
v
Jenkins (on AWS EC2)
|
|-- Build Docker Image
|-- Run Docker Compose
v
Docker Containers on EC2
|
|-- Flask Application
|-- MySQL Database
```

---
## 🚀 Key Features

- Jenkins installed and configured on AWS EC2
- Automated CI/CD pipeline using Jenkinsfile
- Dockerized Flask application
- Multi-container deployment using Docker Compose
- Automatic redeployment on every GitHub code push
- Persistent MySQL storage using Docker volumes

---

## 📂 Repository Structure
```
├── app.py
├── requirements.txt
├── Dockerfile
├── docker-compose.yml
├── Jenkinsfile
└── README.md
```

---

## 🔁 CI/CD Pipeline Workflow

1. Developer pushes code to GitHub  
2. Jenkins pulls the latest code from the repository  
3. Jenkins builds the Flask Docker image  
4. Existing containers are stopped (if running)  
5. Docker Compose deploys Flask and MySQL containers  
6. Updated application becomes live on AWS EC2  

---

## 📜 Jenkinsfile Breakdown

The Jenkins pipeline is defined using **Pipeline-as-Code**.

### Stages

- **Clone Code**
  - Fetches the latest code from the GitHub repository

- **Build Docker Image**
  - Builds the Flask application Docker image

- **Deploy with Docker Compose**
  - Stops existing containers
  - Rebuilds and starts updated containers in detached mode

This ensures **zero manual intervention** during deployments.

---

## 🐳 Docker & Docker Compose

- **Dockerfile**
  - Defines the Flask application runtime
  - Installs dependencies and exposes port `5000`

- **docker-compose.yml**
  - Orchestrates Flask and MySQL containers
  - Uses a shared Docker network
  - Includes health checks and restart policies
  - Uses Docker volumes for MySQL data persistence

---

## ✅ Deployment Verification

After a successful Jenkins build:

- Flask app is accessible at:
http://<EC2_PUBLIC_IP>:5000

- Running containers can be verified using:
```bash
docker ps
```

## 📦 What I Learned
Setting up Jenkins on AWS EC2

Writing Jenkins pipelines using Jenkinsfile

Containerizing applications with Docker

Managing multi-container applications with Docker Compose

Automating deployments using CI/CD pipelines

Debugging Docker, Jenkins, and permission-related issues

##👤 Author
Anurag Singh

