Minikube-Kubectl-Lab
Minikube and kubectl Lab Setup
This repository provides a step-by-step guide for setting up and managing a Kubernetes cluster locally using Minikube and kubectl.

Prerequisites
Before proceeding, ensure you have the following installed:

Minikube: Runs a local Kubernetes cluster inside a virtual machine.
kubectl: The command-line tool for interacting with Kubernetes.
Installation Instructions
Install Minikube
Linux:
bash
Copy
Edit
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
macOS:
bash
Copy
Edit
brew install minikube
Windows (via Chocolatey):
powershell
Copy
Edit
choco install minikube
Install kubectl
Linux/macOS:
bash
Copy
Edit
curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/darwin/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
Windows:
Download kubectl.exe from the Kubernetes release page and add it to your system PATH.
Step-by-Step Guide
1. Start Minikube
bash
Copy
Edit
minikube start
This initializes a local Kubernetes cluster.

2. Verify Cluster Status
bash
Copy
Edit
kubectl get nodes
Expected output: A node with a Ready status.

3. Deploy an Application
Deploy an Nginx web server:

bash
Copy
Edit
kubectl create deployment nginx --image=nginx
4. Expose the Deployment
Expose it via a NodePort service:

bash
Copy
Edit
kubectl expose deployment nginx --type=NodePort --port=80
5. Get Service URL
bash
Copy
Edit
minikube service nginx --url
This returns a URL like http://192.168.99.100:30001, which you can access in a browser.

6. Check Running Pods
bash
Copy
Edit
kubectl get pods
7. Scale the Deployment
Scale the deployment to 3 replicas:

bash
Copy
Edit
kubectl scale deployment nginx --replicas=3
Verify scaling:

bash
Copy
Edit
kubectl get pods
8. Delete Deployment and Service
bash
Copy
Edit
kubectl delete service nginx
kubectl delete deployment nginx
Example Kubernetes Workflow
bash
Copy
Edit
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
Conclusion
Using Minikube and kubectl, you can efficiently set up, deploy, and manage Kubernetes applications on a local machine. This setup is ideal for testing and development before moving to a production environment.

