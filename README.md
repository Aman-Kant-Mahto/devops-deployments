# 📘 README.md — DevOps Assignment Documentation

![Uploading ChatGPT Image Mar 12, 2026, 11_54_18 AM.png…]()


## 🚀 MEAN Stack Application Deployment using Docker, CI/CD, and Cloud

This project demonstrates **end-to-end DevOps implementation** for deploying a full-stack MEAN (MongoDB, Express, Angular, Node.js) application using containerization, CI/CD automation, cloud infrastructure, and reverse proxy configuration.

The goal of this project is to showcase hands-on experience in:

* Containerization
* Cloud deployment
* CI/CD automation
* Infrastructure setup
* Reverse proxy configuration

---

# 🏗️ Project Architecture

```
User → Nginx → Frontend (Angular) → Backend (Node.js/Express) → MongoDB
```

### Components Used:

* Containerization → **Docker**
* Container Orchestration → Docker Compose
* Database → **MongoDB**
* Cloud Server → **Amazon Web Services** EC2
* Reverse Proxy → **Nginx**
* CI/CD Pipeline → **GitHub Actions**
* Code Repository → **GitHub**
* Image Registry → **Docker Hub**

---

# ⚙️ Infrastructure Setup

## Cloud Environment

* Ubuntu Virtual Machine on AWS EC2
* Ports Open:

  * 22 → SSH
  * 80 → HTTP
  * 3000 → Backend
  * 4200 → Frontend

---

## Server Configuration

### Install Docker

```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl enable docker
sudo systemctl start docker
```

### Install Docker Compose

```bash
sudo apt install docker-compose -y
```

---

# 🐳 Containerization

## Frontend Container

* Angular application
* Runs on port 80
* Built using custom Dockerfile

## Backend Container

* Node.js + Express API
* Connects to MongoDB container

## Database Container

* MongoDB official image
* Persistent database service

---

# 📦 Docker Compose Deployment

The application is deployed using `docker-compose.yml` to manage:

* Frontend service
* Backend service
* MongoDB service
* Service dependencies
* Network communication

### Start Application

```bash
docker compose up -d
```

### Verify Running Containers

```bash
docker ps
```

Expected:

```
frontend → running
backend → running
mongo → running
```

---

# 🔄 CI/CD Pipeline Implementation

CI/CD pipeline is implemented using GitHub Actions.

## Pipeline Workflow

When code is pushed to repository:

1. Checkout code
2. Build frontend Docker image
3. Build backend Docker image
4. Push images to Docker Hub
5. Deployment server pulls latest images
6. Containers restart automatically

## Pipeline File Location

```
.github/workflows/deploy.yml
```

---

# 🌐 Reverse Proxy Setup

Nginx is configured as reverse proxy.

## Purpose

* Route traffic from port 80
* Serve frontend
* Forward API requests to backend
* Hide internal service ports

## Nginx Configuration

```
server {
    listen 80;

    location / {
        proxy_pass http://localhost:4200;
    }

    location /api {
        proxy_pass http://localhost:3000;
    }
}
```

Application is accessible via:

```
http://SERVER_PUBLIC_IP
```

---

# 🗂️ Project Structure

```
crud-dd-task-mean-app/
│
├── frontend/
├── backend/
├── docker-compose.yml
├── README.md
└── screenshots/
```

---

# 📸 Screenshots

## CI/CD Pipeline Execution

<img width="1366" height="768" alt="Screenshot (508)" src="https://github.com/user-attachments/assets/b9d49921-7fd1-4ecd-8cf9-be9dab08748f" />


## Docker Images on Docker Hub

<img width="1366" height="768" alt="Screenshot (506)" src="https://github.com/user-attachments/assets/c05bc7b9-f555-4009-9e1f-3716a284741d" />


## Running Containers

<img width="1366" height="768" alt="Screenshot (510)" src="https://github.com/user-attachments/assets/6b050557-babf-424f-aa41-221084729812" />



## Application UI

<img width="1366" height="768" alt="Screenshot (505)" src="https://github.com/user-attachments/assets/bb38f501-dc97-412d-b0b9-a9dffb5d040b" />



## AWS Infrastructure

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/37559bae-749b-40c8-bbdc-5e6aa80d713e" />


---

# 🔐 Key Features Implemented

✅ Full-stack containerized deployment
✅ Multi-container orchestration using Docker Compose
✅ Automated CI/CD pipeline
✅ Cloud-based infrastructure deployment
✅ Reverse proxy configuration
✅ Production-style architecture

---

# 🎯 Outcome

* Successfully deployed MEAN application on cloud VM.
* Automated build and deployment pipeline implemented.
* Application accessible via reverse proxy.
* Scalable and production-like setup achieved.

---

# 👨‍💻 Author

Aman Mahto
DevOps Internship Assignment

---
