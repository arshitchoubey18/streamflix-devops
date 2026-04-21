# 🚀 StreamFlix DevOps Project

A production-ready **Netflix-style streaming frontend** deployed using a complete **DevOps pipeline approach** with Docker, Nginx, and AWS EC2.

---

## 📌 Project Overview

This project demonstrates how a modern frontend application can be:

* Containerized using **Docker**
* Served via **Nginx**
* Built and deployed directly on **AWS EC2 (Cloud-only, no local setup)**
* Structured for CI/CD integration (Jenkins ready)

---

## 🛠️ Tech Stack

* **Frontend**: React + Vite
* **Containerization**: Docker
* **Web Server**: Nginx
* **Cloud**: AWS EC2
* **CI/CD (Optional)**: Jenkins

---

## ⚙️ Prerequisites

Before deployment, ensure:

* AWS account
* EC2 instance (Ubuntu recommended)
* Security Group allows:

  * Port **22** (SSH)
  * Port **80** (HTTP)

---

## ☁️ Deployment on AWS EC2 (Cloud Only)

### Step 1: Connect to EC2

```bash
ssh -i your-key.pem ubuntu@YOUR_EC2_PUBLIC_IP
```

---

### Step 2: Install Dependencies

```bash
sudo apt update
sudo apt install -y docker.io git

sudo systemctl enable docker
sudo systemctl start docker

sudo usermod -aG docker ubuntu
newgrp docker
```

---

### Step 3: Clone Repository

```bash
git clone https://github.com/arshitchoubey18/streamflix-devops.git
cd streamflix-devops
```

---

### Step 4: Build Docker Image

```bash
docker build -t streamflix .
```

---

### Step 5: Run Application

```bash
docker rm -f streamflix-app || true

docker run -d \
  --name streamflix-app \
  -p 80:80 \
  --restart unless-stopped \
  streamflix
```

---

### Step 6: Access Application

Open in browser:

```
http://YOUR_EC2_PUBLIC_IP
```

---

## 🔄 Update Deployment (After Code Changes)

```bash
cd streamflix-devops
git pull origin main

docker build -t streamflix .
docker rm -f streamflix-app || true

docker run -d \
  --name streamflix-app \
  -p 80:80 \
  --restart unless-stopped \
  streamflix
```

---

## 🧪 Verification Commands

```bash
docker ps
docker logs streamflix-app
curl http://localhost
```

## 🔥 Key Highlights 

* End-to-end **cloud deployment without local dependency**
* Production-ready **Docker + Nginx setup**
* Scalable architecture for CI/CD pipelines
* Hands-on experience with **AWS EC2 deployment**

---

## 📌 Future Enhancements

* CI/CD automation using Jenkins
* Docker Hub integration
* HTTPS setup using Nginx + SSL
* Kubernetes deployment

---

## 👨‍💻 Author

**Arshit Choubey**
 → DevOps Engineer

---

## 📜 License

MIT License © 2026 Arshit Choubey
