# Kubernetes Node.js Application Deployment

A simple Node.js web application deployed on Kubernetes using Pods, Deployments, and Services.

This project demonstrates the fundamental Kubernetes concepts required to deploy, expose, and manage a containerized application in a Kubernetes cluster.

---

### Kubernetes Components Used

- Pod
- Deployment
- Service (NodePort)
- Docker Container

---

## Architecture

```text
Client Browser
       |
       v
Kubernetes Service (NodePort)
       |
       v
Node.js Deployment
       |
       +---- Pod 1
       +---- Pod 2
       +---- Pod 3
```

---

## Technologies Used

- Node.js
- Express.js
- Docker
- Kubernetes
- Minikube
- kubectl

---

## Project Structure

```text
.
├── app.js
├── package.json
├── Dockerfile
├── deployment.yaml
├── service.yaml
└── README.md
```

---

## Getting Started

### Clone the Repository

```bash
git clone https://github.com/<your-username>/<repository-name>.git

cd <repository-name>
```

### Install Dependencies

```bash
npm install
```

### Run the Application Locally

```bash
node app.js
```

Visit:

```text
http://localhost:3000
```

---

## Docker Setup

### Build Docker Image

```bash
docker build -t nodejs-k8s-demo:v1 .
```

### Run Docker Container

```bash
docker run -p 3000:3000 nodejs-k8s-demo:v1
```

Verify:

```text
http://localhost:3000
```

---

## Kubernetes Deployment

### Create Deployment

```bash
kubectl apply -f deployment.yaml
```

Verify deployment:

```bash
kubectl get deployments
```

Verify pods:

```bash
kubectl get pods
```

---

### Create Service

```bash
kubectl apply -f service.yaml
```

Verify service:

```bash
kubectl get svc
```

Example output:

```text
NAME         TYPE       CLUSTER-IP      PORT(S)
my-service   NodePort   10.100.200.37   80:31112/TCP
```

---

## Access the Application

For Minikube:

```bash
minikube service my-service
```

Or:

```bash
minikube service my-service --url
```

---

## Scaling the Application

Scale to 5 replicas:

```bash
kubectl scale deployment nodejs-deployment --replicas=5
```

Verify:

```bash
kubectl get pods
```

