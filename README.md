# 🚀 MEAN Stack DevOps Assignment

## Project Objective
This project demonstrates a complete DevOps implementation for a MEAN stack application including:

- Docker containerization
- Docker Hub image publishing //fronted & backed 
- Ubuntu VM deployment (AWS EC2)
- Jenkins CI/CD pipeline
- Nginx reverse proxy setup

---

# 🏗️ Architecture Overview
```text

Client Browser
⬇
Nginx (Port 80)
⬇
Frontend (Angular Container)
⬇
Backend (Node.js/Express Container)
⬇
MongoDB (Docker Container)

```

All services are containerized and orchestrated using Docker Compose.

---

# 📦 Technologies Used
```text
Node.js
Express.js
Angular 15
MongoDB
Docker
Docker Compose
Jenkins
Nginx
AWS EC2 (Ubuntu 22.04)
```
---
# 📁 Project Structure
```text
mean-devops-assignment/
│
├── backend/
│ └── Dockerfile
│
├── frontend/
│ └── Dockerfile
│
├── docker-compose.yml
├── default.conf
├── Jenkinsfile
└── README.md

```

# Docker Containerization

## Backend Dockerfile
---
Uses Node 18
Installs dependencies
Exposes port 8080
---

## Frontend Dockerfile
---
Multi-stage build
Builds Angular project
Serves using Nginx (alpine)
---

#Ubuntu VM Setup (AWS EC2)

## Launch Ubuntu VM
---
OS: Ubuntu 22.04
Open ports:
22 (SSH)
80 (Application)
8081 (Jenkins)
---

# Install Docker
```text
sudo apt update
sudo apt install docker.io -y
sudo systemctl enable docker
sudo systemctl start docker
```
# Deploy Application
```text
docker-compose pull
docker-compose up -d
```
Check containers:
```text
docker ps
```
# CI/CD Pipeline (Jenkins)
---
Jenkins pipeline stages:
Clone GitHub repository
Build backend Docker image
Build frontend Docker image
Push images to Docker Hub
Deploy containers using Docker Compose
Pipeline automatically triggers on code updates.
---

# Docker Hub Images
```text
vignesh0777/mean-backend:latest
vignesh0777/mean-frontend:latest
```
# Nginx Reverse Proxy Configuration
```text
server {
    listen 80;

    location / {
        proxy_pass http://frontend;
    }

    location /api/ {
        proxy_pass http://backend:8080/;
    }
}
```
# Application accessible at:
---
http://<EC2_PUBLIC_IP>
---
# Verification Commands
```text
docker ps
docker logs backend
docker logs nginx
```

