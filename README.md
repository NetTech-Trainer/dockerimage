
# 📦 Docker Image Management with AWS ECR & Docker Hub

A complete step-by-step guide to authenticate, push, pull, and manage Docker images using:

* **AWS Elastic Container Registry (ECR)**
* **Docker Hub**

This guide is suitable for DevOps engineers, cloud engineers, and students learning container deployment workflows.

---

## 📌 Overview

This repository explains how to:

* 🔐 Login to AWS ECR
* 📤 Push Docker images to ECR
* 📥 Pull Docker images from ECR
* 🚪 Logout from ECR
* 🔐 Login to Docker Hub
* 📤 Push Docker images to Docker Hub
* 📥 Pull Docker images from Docker Hub
* 🚪 Logout from Docker Hub

---

# 🔷 Prerequisites

Before starting, ensure you have:

* Docker installed
* AWS CLI installed
* AWS account with IAM permissions for ECR
* Docker Hub account
* Configured AWS credentials (`aws configure`)

---

# 🔹 Part 1: AWS ECR (Elastic Container Registry)

## 1️⃣ Configure AWS CLI

```bash
aws configure
```

Provide:

* AWS Access Key
* AWS Secret Key
* Default Region (e.g., ap-south-1)
* Output format (json)

---

## 2️⃣ Create ECR Repository

```bash
aws ecr create-repository --repository-name my-app --region ap-south-1
```

---

## 3️⃣ Login to AWS ECR

```bash
aws ecr get-login-password --region ap-south-1 | \
docker login --username AWS \
--password-stdin <account-id>.dkr.ecr.ap-south-1.amazonaws.com
```

Example:

```bash
aws ecr get-login-password --region ap-south-1 | \
docker login --username AWS \
--password-stdin 123456789012.dkr.ecr.ap-south-1.amazonaws.com
```

Expected output:

```
Login Succeeded
```

---

## 4️⃣ Tag Docker Image for ECR

```bash
docker tag myapp:latest \
123456789012.dkr.ecr.ap-south-1.amazonaws.com/my-app:latest
```

---

## 5️⃣ Push Image to ECR

```bash
docker push 123456789012.dkr.ecr.ap-south-1.amazonaws.com/my-app:latest
```

---

## 6️⃣ Pull Image from ECR

```bash
docker pull 123456789012.dkr.ecr.ap-south-1.amazonaws.com/my-app:latest
```

---

## 7️⃣ Logout from ECR

```bash
docker logout 123456789012.dkr.ecr.ap-south-1.amazonaws.com
```

---

# 🔹 Part 2: Docker Hub Registry

## 1️⃣ Login to Docker Hub

```bash
docker login
```

Or:

```bash
docker login -u <your-username>
```

---

## 2️⃣ Tag Image for Docker Hub

Format:

```
username/repository:tag
```

Example:

```bash
docker tag myapp:latest username/myapp:latest
```

---

## 3️⃣ Push Image to Docker Hub

```bash
docker push username/myapp:latest
```

---

## 4️⃣ Pull Image from Docker Hub

```bash
docker pull username/myapp:latest
```

Pull public image example:

```bash
docker pull nginx
```

---

## 5️⃣ Logout from Docker Hub

```bash
docker logout
```

---

# 🔥 Complete Workflow Example

```bash
# Build Image
docker build -t myapp .

# Tag for ECR
docker tag myapp:latest <account-id>.dkr.ecr.ap-south-1.amazonaws.com/my-app:latest

# Push to ECR
docker push <account-id>.dkr.ecr.ap-south-1.amazonaws.com/my-app:latest
```


---

# 👨‍💻 Author

**Sagar**

DevOps | Cloud | Docker | AWS

---

Just tell me what level you want 🚀

