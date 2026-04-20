# StreamFlix DevOps Project

StreamFlix is a Netflix-style frontend application used to demonstrate a complete DevOps CI/CD pipeline.

This repository allows anyone to clone the project, build a Docker image, and deploy it on AWS EC2.

---

## 🚀 What This Project Includes

- React (Vite) frontend
- Dockerized application (multi-stage build)
- Nginx for production serving
- Jenkins CI/CD pipeline
- SonarQube integration
- Docker Hub image publishing
- Automated AWS EC2 deployment

---

## 🧰 Tech Stack

- React + Vite
- Docker + Nginx
- Jenkins
- SonarQube
- AWS EC2
- GitHub Webhooks

---

# 🧑‍💻 How to Clone and Run Locally

## Step 1: Clone Repo

```bash
git clone https://github.com/arshitchoubey18/streamflix-devops.git
cd streamflix-devops
````

## Step 2: Install Dependencies

```bash
npm install
```

## Step 3: Run App

```bash
npm run dev
```

Open:

```
http://localhost:5173
```

---

# 🐳 Run Using Docker (Recommended)

## Build Image

```bash
docker build -t streamflix .
```

## Run Container

```bash
docker run -d -p 8080:80 --name streamflix-app streamflix
```

Open:

```
http://localhost:8080
```

---

# ☁️ Deploy This Project on AWS EC2 (Step-by-Step)

This is the most important section.

---

## Step 1: Launch EC2 Instance

* OS: Ubuntu
* Instance type: t2.micro
* Open ports:

  * 22 (SSH)
  * 80 (HTTP)

---

## Step 2: Connect to EC2

```bash
chmod 400 your-key.pem
ssh -i your-key.pem ubuntu@YOUR_EC2_PUBLIC_IP
```

---

## Step 3: Install Docker on EC2

```bash
sudo apt update
sudo apt install -y docker.io
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker ubuntu
```

Reconnect:

```bash
exit
ssh -i your-key.pem ubuntu@YOUR_EC2_PUBLIC_IP
```

---

## Step 4: Pull Docker Image

```bash
docker pull arshitchoubey18/streamflix:latest
```

---

## Step 5: Run Application

```bash
docker rm -f streamflix-app || true
docker run -d -p 80:80 --name streamflix-app arshitchoubey18/streamflix:latest
```

---

## Step 6: Open in Browser

```
http://YOUR_EC2_PUBLIC_IP
```

🎉 Your app is now live on AWS!

---

# 🔁 CI/CD (Optional - Advanced)

This project also supports full CI/CD:

```
GitHub → Jenkins → SonarQube → Docker → Docker Hub → EC2
```

Every push triggers:

* Build
* Code scan
* Docker image creation
* Auto deployment to EC2

---

# 🧪 Useful Commands

## Check running containers

```bash
docker ps
```

## Stop container

```bash
docker rm -f streamflix-app
```

## View logs

```bash
docker logs streamflix-app
```

---

# 📌 Notes

* Ensure EC2 security group allows **port 80**
* Docker image must be public on Docker Hub
* Use your own Docker Hub username if you fork this repo

---



