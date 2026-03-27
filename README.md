# 🚀 DevOps CI/CD Project – Node.js Microservice with Kubernetes & Monitoring

## 📌 Project Overview

This project demonstrates a complete **DevOps pipeline** using modern tools. It includes application development, containerization, CI/CD automation, Kubernetes deployment, auto-scaling, and monitoring — all running locally using Minikube.

---

## 🧩 Tech Stack

* **Source Control:** GitHub
* **CI/CD:** GitHub Actions
* **Containerization:** Docker (Multi-stage build)
* **Orchestration:** Kubernetes (Minikube)
* **Monitoring:** Prometheus + Grafana
* **Language:** Node.js

---

## 🏗️ Architecture

```
Developer → GitHub → GitHub Actions → Docker Build → Docker Hub
→ Kubernetes (Minikube) → HPA → Prometheus → Grafana
```

---

## 📁 Project Structure

```
devops-project/
│
├── app/
│   ├── server.js
│   ├── package.json
│
├── docker/
│   └── Dockerfile
│
├── k8s/
│   ├── deployment.yaml
│   ├── service.yaml
│   ├── hpa.yaml
│
├── monitoring/
│   └── prometheus.yaml
│
├── .github/
│   └── workflows/
│       └── cicd.yaml
│
└── README.md
```

---

## ⚙️ Application Details

* Simple Node.js API
* Endpoints:

  * `/` → Returns app status
  * `/health` → Health check endpoint

---

## 🐳 Docker (Multi-Stage Build)

* Optimized Docker image using multi-stage build
* Reduces image size and improves performance

### Build Image

```
docker build -t devops-app -f docker/Dockerfile .
```

### Run Container

```
docker run -d -p 3000:3000 devops-app
```

---

## ☸️ Kubernetes Deployment (Minikube)

### Start Minikube

```
minikube start
```

### Deploy Application

```
kubectl apply -f k8s/
```

### Access Application

```
minikube service devops-service
```

---

## ⚡ Horizontal Pod Autoscaler (HPA)

* Automatically scales pods based on CPU usage
* Configured between **2 to 5 replicas**

### Enable Metrics Server

```
minikube addons enable metrics-server
```

### Apply HPA

```
kubectl apply -f k8s/hpa.yaml
```

---

## 📊 Monitoring (Prometheus + Grafana)

### Install Monitoring Stack

```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm install monitoring prometheus-community/kube-prometheus-stack
```

### Access Grafana

```
kubectl port-forward svc/monitoring-grafana 3000:80
```

Open:

```
http://localhost:3000
```

### Default Credentials

```
Username: admin
Password: prom-operator
```

---

## 🐳 Docker Hub Integration

### Login

```
docker login
```

### Tag Image

```
docker tag devops-app <your-username>/devops-app:latest
```

### Push Image

```
docker push <your-username>/devops-app:latest
```

---

## 🔁 CI/CD Pipeline (GitHub Actions)

### Pipeline Stages

1. Code Push triggers pipeline
2. Install dependencies
3. Run application test
4. Build Docker image (multi-stage)
5. Push image to Docker Hub
6. Deploy to Kubernetes

---

## ▶️ Run CI/CD Pipeline

* Push code to `main` branch
* Pipeline runs automatically via GitHub Actions

---

## 🧪 Verification

### Check Pods

```
kubectl get pods
```

### Check Services

```
kubectl get svc
```

### Check HPA

```
kubectl get hpa
```

---

## 🧠 Key Features

* Multi-stage Docker build (optimized image size)
* Automated CI/CD pipeline
* Kubernetes deployment with scaling
* Monitoring with Prometheus & Grafana
* Local setup using Minikube

---

## 🧑‍💻 Author

**Manish Sahani**

---

## ⭐ Notes

This project is designed to simulate a **real-world DevOps workflow** and is ideal for interviews and hands-on practice.

---
