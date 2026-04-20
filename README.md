# StreamFlix DevOps Project

A **Netflix-inspired frontend application** built with **React + Vite**, containerized using **Docker**, and deployed on **AWS EC2** using **Nginx**.  
This project demonstrates a complete **DevOps workflow** including CI/CD, containerization, and cloud deployment.

---

## 🚀 Tech Stack

- React + Vite  
- Docker (Multi-stage build)  
- Nginx  
- Jenkins (CI/CD)  
- SonarQube  
- AWS EC2  
- Docker Hub  

---

## ⚙️ Key Highlights

- Dockerized frontend application for production
- Implemented CI/CD pipeline using Jenkins
- Integrated SonarQube for code quality checks
- Automated Docker image build and deployment
- Deployed application on AWS EC2

---

## 🖥️ Deployment (EC2 - Direct Build)

## Build directly on EC2 (No Docker Hub required)**

```bash
# Update system & install dependencies
sudo apt update
sudo apt install -y docker.io git

# Enable Docker
sudo systemctl enable docker
sudo systemctl start docker
sudo usermod -aG docker ubuntu
newgrp docker

# Clone repository
git clone https://github.com/arshitchoubey18/streamflix-devops.git
cd streamflix-devops

# Build Docker image
docker build -t streamflix .

# Run container
docker rm -f streamflix-app || true
docker run -d --name streamflix-app -p 80:80 --restart unless-stopped streamflix
````

Access the application:

```
http://your-ec2-public-ip
```

---

## 📸 Screenshots

## Application Running on EC2
<img width="1366" height="646" alt="image" src="https://github.com/user-attachments/assets/fa3b0a05-5390-4f22-a118-933c349b539c" />

## Docker Container Running
<img width="1366" height="646" alt="image" src="https://github.com/user-attachments/assets/62b5e23f-0338-4b22-a0f5-640550cabf2d" />

## EC2 Instance Running
<img width="1366" height="564" alt="image" src="https://github.com/user-attachments/assets/5521dee7-3668-4eb4-9f5d-cf28e96fa1a7" />

## Security Group (Ports Open)
<img width="1366" height="564" alt="image" src="https://github.com/user-attachments/assets/add233e6-5cdb-4282-aaff-fd8bbfbc6193" />

## Jenkins Pipeline Success





---

## 🔄 CI/CD Flow

GitHub → Jenkins → SonarQube → Docker Build → EC2 Deployment

---

## 👨‍💻 Author

**Arshit Choubey**
DevOps Engineer

GitHub: [https://github.com/arshitchoubey18](https://github.com/arshitchoubey18)
