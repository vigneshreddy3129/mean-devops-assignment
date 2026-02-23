# 🚀 MEAN Stack DevOps Assignment

This project demonstrates a complete DevOps workflow for a MEAN stack application including:

- Docker containerization
- Docker Hub image publishing
- Ubuntu VM deployment
- Jenkins CI/CD pipeline
- Nginx reverse proxy setup

---

# 🏗️ Architecture Overview
```text

Frontend  → Nginx → Backend  → MongoDB
```

All services are containerized and orchestrated using Docker Compose.

---

# 📦 Technologies Used
```text
- Node.js
- Express
- Angular 15
- MongoDB
- Docker
- Docker Compose
- Jenkins
- Nginx
- AWS Ubuntu VM
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

# 🐳 Docker Setup

## 1️⃣ Build Images (Handled by Jenkins CI)

Images are built and pushed to Docker Hub:

- `vignesh0777/mean-backend:latest`
- `vignesh0777/mean-frontend:latest`

---

# ☁️ VM Deployment (Ubuntu)

## 1️⃣ Install Docker
```text
sudo apt update
sudo apt install docker.io -y
sudo systemctl enable docker
sudo systemctl start docker
```
# 2️⃣ Deploy Application
```text
docker-compose pull
docker-compose up -d
```
🔁 CI/CD Pipeline (Jenkins)
```text
Pipeline stages:
Clone GitHub Repository
Build Backend Docker Image
Build Frontend Docker Image
Push Images to Docker Hub
Deploy to Ubuntu VM using Docker Compose
Pipeline runs automatically when code is updated.

```
Nginx Reverse Proxy
http://<VM_PUBLIC_IP>
default.conf
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
All traffic is routed through port 80.
```
Verification Commands
```text
docker ps
docker logs backend
docker logs nginx
```

