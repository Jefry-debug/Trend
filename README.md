# React Application Deployment using Docker, Jenkins, Terraform & AWS EKS

## Project Overview

This project demonstrates the deployment of a React application using a complete DevOps CI/CD pipeline.

The application is containerized using Docker, stored in DockerHub, deployed to AWS EKS using Kubernetes, and automated using Jenkins with GitHub Webhooks.

---

# Technologies Used

- React
- Docker
- DockerHub
- GitHub
- Jenkins
- Terraform
- AWS EC2
- AWS EKS
- Kubernetes
- AWS CLI
- kubectl
- Prometheus
- Grafana

---

# Project Architecture

GitHub Repository

↓

GitHub Webhook

↓

Jenkins Pipeline

↓

Docker Build

↓

DockerHub

↓

AWS EKS

↓

Kubernetes Deployment

↓

AWS LoadBalancer

↓

React Application

---

# Prerequisites

- AWS Account
- Docker
- Git
- Jenkins
- Terraform
- AWS CLI
- kubectl
- eksctl
- DockerHub Account

---

# Setup Instructions

## 1. Clone Repository

```bash
git clone https://github.com/Jefry-debug/Trend.git
cd Trend
```

---

## 2. Build Docker Image

```bash
docker build -t jefryjo/trend-app:latest .
```

---

## 3. Run Docker Container

```bash
docker run -d -p 3000:80 jefryjo/trend-app:latest
```

Open:

```
http://localhost:3000
```

---

## 4. Push Docker Image

```bash
docker login

docker push jefryjo/trend-app:latest
```

---

## 5. Provision Infrastructure

```bash
cd terraform

terraform init

terraform validate

terraform plan

terraform apply
```

---

## 6. Create EKS Cluster

```bash
eksctl create cluster \
--name trend-cluster \
--region ap-south-1 \
--nodes 2
```

---

## 7. Configure Kubernetes

```bash
aws eks update-kubeconfig \
--region ap-south-1 \
--name trend-cluster
```

---

## 8. Deploy Application

```bash
kubectl apply -f deployment.yaml

kubectl apply -f service.yaml
```

---

## 9. Verify Deployment

```bash
kubectl get deployments

kubectl get pods

kubectl get svc
```

---

## 10. Configure Jenkins

Install Plugins

- Git
- Docker
- Docker Pipeline
- Kubernetes
- Pipeline
- GitHub

Create Pipeline

Repository

```
https://github.com/Jefry-debug/Trend.git
```

Script Path

```
Jenkinsfile
```

Enable

```
GitHub hook trigger for GITScm polling
```

---

## 11. GitHub Webhook

Payload URL

```
http://<JENKINS-PUBLIC-IP>:8080/github-webhook/
```

Content Type

```
application/json
```

Event

```
Push Event
```

---

## 12. Monitoring

Install Prometheus and Grafana

```bash
helm install monitoring prometheus-community/kube-prometheus-stack \
-n monitoring
```

---

# Jenkins Pipeline

The Jenkins Pipeline performs:

1. Checkout Source Code

2. Build Docker Image

3. Login to DockerHub

4. Push Docker Image

5. Deploy to Kubernetes

---

# Output

Application URL

```
http://<LoadBalancer-DNS>
```

DockerHub Repository

```
https://hub.docker.com/r/jefryjo/trend-app
```

GitHub Repository

```
https://github.com/Jefry-debug/Trend
```

---

# Author

Name: Jone Jefry
