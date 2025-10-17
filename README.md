# Django Notes App with Kubernetes & Ingress

**Created by: Ankita Gavali** 🚀

A modern Django notes application deployed on Kubernetes with NGINX Ingress controller, featuring playful port configurations and scalable architecture. This project demonstrates advanced Kubernetes concepts including Ingress routing, service port mapping, and local development with Kind clusters.

## 🚀 Features

- **Django Backend**: RESTful API for notes management
- **Kubernetes Deployment**: Scalable container orchestration
- **NGINX Ingress**: Smart routing with multiple access paths
- **Playful Port Configuration**: Multiple service ports (4141, 4545, 4899)
- **Kind Cluster**: Local Kubernetes development environment

## 🏗️ Architecture

```
Browser → Ingress Controller → Service → Pods → Django App
   ↓              ↓              ↓        ↓         ↓
localhost    nginx:80      port 4141   port 8000  Django
```

## 📋 Prerequisites

1. **Docker**: For containerization
2. **Kind**: Kubernetes in Docker
3. **kubectl**: Kubernetes command-line tool
4. **Python 3.9**: For Django application

## 🛠️ Installation & Setup

### 1. Create Kind Cluster with Ingress Support
```bash
# Create cluster with proper port mappings
kind create cluster --name demo --config kind-ingress-config.yaml
```

### 2. Install NGINX Ingress Controller
```bash
kubectl apply -f https://kind.sigs.k8s.io/examples/ingress/deploy-ingress-nginx.yaml
```

### 3. Deploy Django Application
```bash
# Apply all Kubernetes resources
kubectl apply -f k8s/namespace.yml
kubectl apply -f k8s/deployment.yml
kubectl apply -f k8s/service.yml
kubectl apply -f k8s/ingress.yml
```

## 🌐 Access Points

Your Django app is accessible through multiple paths:

- **`http://localhost/`** → Main app (port 4141)
- **`http://localhost/home`** → Home section (port 4545)
- **`http://localhost/app`** → App section (port 4899)

## 🔧 Configuration Details

### Service Ports
- **Port 4141**: Main application access
- **Port 4545**: Admin/home access
- **Port 4899**: API access
- **Target Port**: 8000 (Django app)

### Ingress Configuration
- **Host**: localhost
- **SSL Redirect**: Disabled for local development
- **Rewrite Target**: All paths rewritten to `/`

## 📁 Project Structure

```
django-notes-app-kubernetes/
├── k8s/
│   ├── namespace.yml      # Kubernetes namespace
│   ├── deployment.yml     # App deployment (3 replicas)
│   ├── service.yml        # Service with multiple ports
│   └── ingress.yml        # Ingress routing rules
├── Dockerfile             # Container configuration
├── kind-ingress-config.yaml # Kind cluster setup
└── README.md             # This file
```

## 🚀 Development

### Build Docker Image
```bash
docker build -t anks123/my-notes-app:latest .
```

### Deploy to Kubernetes
```bash
kubectl apply -f k8s/
```

### Check Status
```bash
kubectl get all -n mynotes-app-namespace
kubectl get ingress -n mynotes-app-namespace
```

## 🎯 Key Features

- **Scalable**: 3 replicas for high availability
- **Modern**: Kubernetes-native deployment
- **Accessible**: Direct localhost access without port forwarding
- **Flexible**: Easy to extend with additional Django apps

## 👨‍💻 Author & Contributions

**Ankita Gavali** - Full Stack Developer & DevOps Engineer

### What I Built:
- ✅ **Kubernetes Deployment**: Configured 3-replica Django app deployment
- ✅ **Ingress Controller**: Set up NGINX Ingress with custom routing
- ✅ **Playful Port Configuration**: Creative service port mapping (4141, 4545, 4899)
- ✅ **Kind Cluster Setup**: Local Kubernetes development environment
- ✅ **Docker Containerization**: Optimized Django app containerization
- ✅ **Complete CI/CD**: Jenkins pipeline for automated deployment

### Technologies Used:
- **Backend**: Django, Python 3.9
- **Containerization**: Docker
- **Orchestration**: Kubernetes, Kind
- **Ingress**: NGINX Ingress Controller
- **CI/CD**: Jenkins
- **Infrastructure**: Local development with Kind clusters

## 📝 Project Highlights

This setup demonstrates:
- **Advanced Kubernetes patterns**: Multi-port service configuration
- **Ingress routing strategies**: Path-based routing with rewrite rules
- **Local development**: Kind cluster with proper port mappings
- **Scalable architecture**: 3-replica deployment for high availability
- **DevOps best practices**: Complete containerization and orchestration

Perfect showcase of modern DevOps and Kubernetes expertise! 🎉