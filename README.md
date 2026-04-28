# Docker-Task
# Docker Setup and Exploration on AWS EC2

## 📌 Overview

This project demonstrates the installation of Docker on an AWS EC2 instance and explores core Docker components such as images, containers, volumes, and networks.

---

## 🚀 Step 1: Connect to EC2 Instance

```bash
ssh -i Linux.pem ubuntu@<your-ec2-public-ip>
```

---

## ⚙️ Step 2: Install Docker

```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
```

### Verify Installation

```bash
docker --version
```

---

## 🐳 Step 3: Run Docker Container

```bash
docker run hello-world
```

---

## 📦 Step 4: Docker Images

### Pull Image

```bash
docker pull nginx
```

### List Images

```bash
docker images
```

---

## 📦 Step 5: Docker Containers

### Run Nginx Container (Port 80)

```bash
docker run -d -p 80:80 nginx
```

### Run Nginx Container (Port 8080)

```bash
docker run -d -p 8080:80 nginx
```

### List Containers

```bash
docker ps
```

### Stop & Remove Container

```bash
docker stop <container_id>
docker rm <container_id>
```

---

## 💾 Step 6: Docker Volumes

### Create Volume

```bash
docker volume create myvolume
```

### List Volumes

```bash
docker volume ls
```

### Use Volume with Container

```bash
docker run -d -p 8080:80 -v myvolume:/usr/share/nginx/html nginx
```

### Test Volume Persistence

```bash
docker exec -it <container_id> bash
echo "Hello from Docker Volume 🚀" > /usr/share/nginx/html/index.html
exit
```

### Remove Container & Re-run

```bash
docker rm -f <container_id>
docker run -d -p 8080:80 -v myvolume:/usr/share/nginx/html nginx
```

---

## 🌐 Step 7: Docker Network

### List Networks

```bash
docker network ls
```

### Create Network

```bash
docker network create mynetwork
```

### Run Container in Network

```bash
docker run -d --name web1 --network mynetwork nginx
```

### Test Network Communication

```bash
docker run -it --network mynetwork busybox
ping web1
```

---

## 🌍 Application Access

* Nginx on Port 80:

```
http://<your-ec2-public-ip>
```

* Nginx with Volume on Port 8080:

```
http://<your-ec2-public-ip>:8080
```

---

## 🔐 Security Group Configuration

Ensure the following inbound rules are added in AWS:

| Type       | Port | Source    |
| ---------- | ---- | --------- |
| HTTP       | 80   | 0.0.0.0/0 |
| Custom TCP | 8080 | 0.0.0.0/0 |

---

## 🧠 Key Learnings

* Docker installation and setup on EC2
* Running and managing containers
* Working with Docker images
* Data persistence using volumes
* Container communication using networks
* Port mapping and access via browser

---

## 📌 Conclusion

Successfully installed Docker on EC2 and explored its core features including containers, images, volumes, and networking. Verified application deployment using Nginx.

---
