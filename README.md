# Minikube-Kubectl-Lab

## Minikube and kubectl Lab Setup
This repository provides a step-by-step guide for setting up and managing a Kubernetes cluster locally using **Minikube** and **kubectl**.

---

## Prerequisites
Before proceeding, ensure you have the following installed:
- **Minikube**: Runs a local Kubernetes cluster inside a virtual machine.
- **kubectl**: The command-line tool for interacting with Kubernetes.

---

## Installation Instructions

### Install Minikube
- **Linux**:  
  ```bash
  curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
  sudo install minikube-linux-amd64 /usr/local/bin/minikube
  ```
- **macOS**:  
  ```bash
  brew install minikube
  ```
- **Windows** (via Chocolatey):  
  ```powershell
  choco install minikube
  ```

### Install kubectl
- **Linux/macOS**:  
  ```bash
  curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/darwin/amd64/kubectl"
  chmod +x kubectl
  sudo mv kubectl /usr/local/bin/
  ```
- **Windows**:  
  Download `kubectl.exe` from the [Kubernetes release page](https://kubernetes.io/docs/tasks/tools/install-kubectl/) and add it to your system PATH.

---

## Step-by-Step Guide

### 1️⃣ Start Minikube
```bash
minikube start
```
This initializes a local Kubernetes cluster.

### 2️⃣ Verify Cluster Status
```bash
kubectl get nodes
```
✅ Expected output: A node with a `Ready` status.

### 3️⃣ Deploy an Application
Deploy an **Nginx web server**:
```bash
kubectl create deployment nginx --image=nginx
```

### 4️⃣ Expose the Deployment
Expose it via a **NodePort service**:
```bash
kubectl expose deployment nginx --type=NodePort --port=80
```

### 5️⃣ Get Service URL
```bash
minikube service nginx --url
```
📌 This returns a URL like `http://192.168.99.100:30001`, which you can access in a browser.

### 6️⃣ Check Running Pods
```bash
kubectl get pods
```

### 7️⃣ Scale the Deployment
Scale the deployment to **3 replicas**:
```bash
kubectl scale deployment nginx --replicas=3
```
Verify scaling:
```bash
kubectl get pods
```

### 8️⃣ Delete Deployment and Service
```bash
kubectl delete service nginx
kubectl delete deployment nginx
```

---

## Example Kubernetes Workflow
```bash
# Start Minikube
minikube start

# Verify Minikube cluster
kubectl get nodes

# Deploy Nginx
kubectl create deployment nginx --image=nginx

# Expose as NodePort
kubectl expose deployment nginx --type=NodePort --port=80

# Get service URL
minikube service nginx --url

# Check running pods
kubectl get pods

# Scale to 3 replicas
kubectl scale deployment nginx --replicas=3

# Cleanup
kubectl delete service nginx
kubectl delete deployment nginx
```

---

## Conclusion
Using **Minikube** and **kubectl**, you can efficiently set up, deploy, and manage Kubernetes applications on a local machine. This setup is ideal for testing and development before moving to a production environment.

