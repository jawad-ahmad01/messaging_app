<div align="center">

# 💬 Full-Stack Realtime Chat App
### Production-Grade DevOps Deployment on Kubernetes

[![CI/CD](https://img.shields.io/badge/CI%2FCD-GitHub%20Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)](https://github.com/jawad-ahmad01/messaging_app/actions)
[![Docker](https://img.shields.io/badge/Docker-Hub-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://hub.docker.com)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-1.34.0-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)](https://kubernetes.io)
[![Helm](https://img.shields.io/badge/Helm-Monitoring-0F1689?style=for-the-badge&logo=helm&logoColor=white)](https://helm.sh)
[![Prometheus](https://img.shields.io/badge/Prometheus-Metrics-E6522C?style=for-the-badge&logo=prometheus&logoColor=white)](https://prometheus.io)
[![Grafana](https://img.shields.io/badge/Grafana-Dashboards-F46800?style=for-the-badge&logo=grafana&logoColor=white)](https://grafana.com)
[![MongoDB](https://img.shields.io/badge/MongoDB-Database-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://mongodb.com)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

<p align="center">
  A scalable, secure, real-time chat application — fully containerized, orchestrated on Kubernetes,<br/>
  with automated CI/CD, DevSecOps scanning, and full observability via Prometheus + Grafana.
</p>

</div>

---

## 📸 Project Snapshots

<table>
  <tr>
    <td align="center"><b>🔄 GitHub Actions — DevSecOps Pipeline</b></td>
    <td align="center"><b>📊 Grafana — K8s Dashboard</b></td>
  </tr>
  <tr>
    <td><img src="docs/screenshots/github-actions.png" alt="GitHub Actions Pipeline" width="100%"/></td>
    <td><img src="docs/screenshots/grafana-dashboard.png" alt="Grafana Dashboard" width="100%"/></td>
  </tr>
  <tr>
    <td align="center"><b>📈 Prometheus — CPU Metrics</b></td>
    <td align="center"><b>⚙️ kubectl — Running Pods</b></td>
  </tr>
  <tr>
    <td><img src="docs/screenshots/prometheus-metrics.png" alt="Prometheus Metrics" width="100%"/></td>
    <td><img src="docs/screenshots/kubectl-pods.png" alt="Running Pods" width="100%"/></td>
  </tr>
</table>

> 📌 **Live cluster:** 1 Node (minikube) · 24 Pods · Workload 17 · Kubernetes v1.34.0

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Architecture](#-architecture)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [CI/CD Pipeline](#-cicd-pipeline)
- [Kubernetes Setup](#-kubernetes-setup)
- [Monitoring Stack](#-monitoring-stack)
- [Getting Started](#-getting-started)
- [Project Structure](#-project-structure)
- [Contributing](#-contributing)
- [Author](#-author)

---

## 🌟 Overview

This project is a **production-grade deployment** of a full-stack real-time chat application. Beyond the application itself, the focus is on the complete DevOps lifecycle:

- **Code** is automatically built, tested, scanned, and deployed via **GitHub Actions**
- **Docker images** are built and pushed to **Docker Hub** on every commit
- **Kubernetes** pulls those images and orchestrates the deployment with autoscaling
- **Prometheus + Grafana + AlertManager** (via Helm) provide full observability
- **DevSecOps** pipeline runs SAST, dependency scanning, container scanning, and K8s security checks — all before anything reaches production

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                   GitHub Actions CI/CD                       │
│  ┌──────────────────────┐   ┌──────────────────────────┐   │
│  │      cicd.yml         │   │     devsecops.yml         │   │
│  │  Build · Test · Deploy│   │  SAST · Scan · Gate       │   │
│  └──────────┬───────────┘   └──────────────────────────┘   │
└─────────────┼───────────────────────────────────────────────┘
              ▼
┌─────────────────────────────┐
│        Docker Hub            │
│  docker build → docker push  │
└─────────────┬───────────────┘
              │ pull image
              ▼
┌─────────────────────────────────────────────────────────────┐
│                   K8s Namespace: chatapp                     │
│                                                             │
│   Ingress ──► Frontend (Deployment + HPA + Service)         │
│           └─► Backend  (Deployment + HPA + VPA + Service)   │
│                              │                              │
│               MongoDB (Deployment + VPA + PV + PVC)         │
│               Mongo Express  (Deployment + Service)         │
│               ConfigMap · Secret                            │
└─────────────────────────────────────────────────────────────┘
              ▼
┌─────────────────────────────────────────────────────────────┐
│          Monitoring Stack (Helm)                             │
│   Prometheus ──► Grafana                                    │
│   Prometheus ──► AlertManager                               │
└─────────────────────────────────────────────────────────────┘
```

---

## ✨ Features

### Application
- ⚡ **Real-time messaging** via Socket.io
- 🔐 **JWT authentication & authorization**
- 👤 **Profile management** with avatar upload
- 🟢 **Online/offline status** indicators
- 🎨 **Modern UI** with React + TailwindCSS + DaisyUI

### DevOps
- 🐳 **Dockerized** — frontend, backend, and MongoDB all containerized
- ☸️ **Kubernetes** — full manifest set per service (Deployment, Service, HPA, VPA, PV/PVC)
- 🔄 **CI/CD** — automated build → push → deploy on every commit
- 🔒 **DevSecOps** — SAST, dependency scan, container scan, K8s security scan
- 📊 **Full observability** — Prometheus metrics, Grafana dashboards, AlertManager alerts
- 📦 **Helm** — monitoring stack deployed and managed as a Helm chart
- 🚀 **Autoscaling** — HPA for traffic spikes, VPA for right-sizing pods

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | React, TailwindCSS, DaisyUI, Zustand |
| **Backend** | Node.js, Express, Socket.io |
| **Database** | MongoDB |
| **Auth** | JWT |
| **Containerization** | Docker, Docker Hub |
| **Orchestration** | Kubernetes (Minikube / K8s v1.34.0) |
| **CI/CD** | GitHub Actions |
| **Security** | SAST, Dependency Scan, Container Image Scan, K8s Security Scan |
| **Monitoring** | Prometheus, Grafana, AlertManager |
| **Package Manager** | Helm (monitoring stack) |
| **Ingress** | Nginx Ingress Controller |
| **Web Server** | Nginx |

---

## 🔄 CI/CD Pipeline

Two dedicated GitHub Actions workflows handle the full delivery lifecycle.

### `cicd.yml` — Delivery Pipeline
```
Push to master
      │
      ▼
 Build Docker image (frontend + backend)
      │
      ▼
 Run tests
      │
      ▼
 Push versioned image to Docker Hub
      │
      ▼
 Rolling deploy to Kubernetes
 (pods pull new image automatically)
```

### `devsecops.yml` — Security Pipeline
Runs in parallel on every push. All 4 gates must pass before deploy:

| Step | Tool | Duration |
|---|---|---|
| ✅ SAST — Code Scanning | Static analysis | ~1m 25s |
| ✅ Dependency Vulnerability Scan | CVE check | ~29s |
| ✅ Container Image Scanning | Image layers | ~59s |
| ✅ Kubernetes Security Scanning | Manifest audit | ~19s |

> Total pipeline duration: **~1m 38s** ✅

---

## ☸️ Kubernetes Setup

### Manifest Structure
```
k8s/
├── namespace.yml
├── configmap.yml
├── secret.yml
├── ingress.yml
├── frontend/
│   ├── deployment.yml
│   ├── service.yml
│   └── hpa.yml
├── backend/
│   ├── deployment.yml
│   ├── service.yml
│   ├── hpa.yml
│   └── vpa.yml
├── mongo/
│   ├── deployment.yml
│   ├── service.yml
│   ├── pv.yml
│   ├── pvc.yml
│   └── vpa.yml
└── mongo-express/
    ├── deployment.yml
    └── service.yml
```

### Live Cluster Status
```bash
$ kubectl get nodes
NAME       STATUS   ROLES           AGE   VERSION
minikube   Ready    control-plane   28h   v1.34.0

$ kubectl get pods -n chatapp -o wide
NAME                             READY   STATUS    RESTARTS   AGE
backend-988b8d69d-clcs9          1/1     Running   0          11h
frontend-6f4c8cd5cb-7gph8        1/1     Running   0          16h
mongo-96df897c4-xzsv6            1/1     Running   0          22h
mongo-express-dd576dd67-tqgwn    1/1     Running   4          23h
```

### Autoscaling
- **HPA** on frontend + backend — scales pods horizontally under load
- **VPA** on backend + MongoDB — right-sizes CPU/memory requests automatically

---

## 📊 Monitoring Stack

Deployed via **Helm** into the `monitoring` namespace.

```bash
# Install kube-prometheus-stack
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm install monitoring prometheus-community/kube-prometheus-stack \
  --namespace monitoring \
  --create-namespace
```

### Components

| Component | Role | Port |
|---|---|---|
| **Prometheus** | Scrapes metrics from all pods | `9090` |
| **Grafana** | Dashboards & visualization | `3000` |
| **AlertManager** | Routes alerts on threshold breach | `9093` |

### Grafana Dashboard Highlights
- Node Memory & CPU usage (27.8% / 30.0%)
- Total Pods: **24** · Workload: **17** · Nodes: **1**
- Namespace breakdown: `chatapp`, `monitoring`, `kube-system`, `ingress-nginx`

### Access Grafana
```bash
kubectl port-forward svc/monitoring-grafana 3000:80 -n monitoring
# Open http://localhost:3000
# Default: admin / prom-operator
```

---

## 🚀 Getting Started

### Prerequisites
- Docker
- Kubernetes (Minikube or any K8s cluster)
- kubectl
- Helm
- Git

### 1. Clone the repo
```bash
git clone https://github.com/jawad-ahmad01/messaging_app.git
cd messaging_app
```

### 2. Configure environment
```bash
# Create .env in root
MONGODB_URI=mongodb://root:admin@mongo:27017/chatApp?authSource=admin&retryWrites=true&w=majority
JWT_SECRET=your_jwt_secret_key
PORT=5001
NODE_ENV=production
```

### 3. Run with Docker Compose (local dev)
```bash
docker-compose up -d --build
# App: http://localhost
```

### 4. Deploy to Kubernetes
```bash
# Create namespace
kubectl apply -f k8s/namespace.yml

# Apply configs and secrets
kubectl apply -f k8s/configmap.yml
kubectl apply -f k8s/secret.yml

# Deploy storage
kubectl apply -f k8s/mongo/pv.yml
kubectl apply -f k8s/mongo/pvc.yml

# Deploy services
kubectl apply -f k8s/mongo/
kubectl apply -f k8s/backend/
kubectl apply -f k8s/frontend/
kubectl apply -f k8s/mongo-express/
kubectl apply -f k8s/ingress.yml
```

### 5. Deploy monitoring stack
```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm install monitoring prometheus-community/kube-prometheus-stack \
  --namespace monitoring --create-namespace
```

### 6. Verify everything is running
```bash
kubectl get pods -n chatapp
kubectl get pods -n monitoring
kubectl get ingress -n chatapp
```

---

## 📁 Project Structure

```
messaging_app/
├── frontend/               # React app
│   ├── Dockerfile
│   └── src/
├── backend/                # Node.js + Express + Socket.io
│   ├── Dockerfile
│   └── src/
├── k8s/                    # Kubernetes manifests
│   ├── frontend/
│   ├── backend/
│   ├── mongo/
│   ├── mongo-express/
│   ├── namespace.yml
│   ├── configmap.yml
│   ├── secret.yml
│   └── ingress.yml
├── .github/
│   └── workflows/
│       ├── cicd.yml        # Build · Test · Deploy
│       └── devsecops.yml   # SAST · Scan · Gate
├── docker-compose.yml
└── README.md
```

---

## 🤝 Contributing

Contributions are welcome from DevOps engineers and developers of all skill levels.

1. Fork the repo
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m 'Add your feature'`
4. Push to the branch: `git push origin feature/your-feature`
5. Open a Pull Request

Please ensure your changes pass the DevSecOps pipeline (SAST + vulnerability scans) before submitting.

---

## 🔮 Roadmap

- [x] Docker containerization
- [x] Kubernetes manifests (Deployment, Service, HPA, VPA, PV/PVC)
- [x] GitHub Actions CI/CD pipeline
- [x] DevSecOps security scanning pipeline
- [x] Prometheus + Grafana + AlertManager via Helm
- [ ] Multi-node cluster deployment (AWS EKS / GCP GKE)
- [ ] Group chats & media sharing
- [ ] Horizontal scaling tests under load
- [ ] ArgoCD for GitOps-based deployments

---

## 👨‍💻 Author

**Jawad Ahmad**
- GitHub: [@jawad-ahmad01](https://github.com/jawad-ahmad01)
- LinkedIn: [Connect with me](https://linkedin.com/in/jawad-ahmad01)

---

<div align="center">

⭐ **Star this repo** if you found it useful — it helps others discover it!

</div>
