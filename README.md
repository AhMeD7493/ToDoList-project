# Django To-Do List Application

This is a simple To-Do List application built using Django and PostgreSQL. The project is containerized using Docker and deployed using Kubernetes.

## Features

- Create, update, and delete to-do items.
- Persistent storage with PostgreSQL.
- Containerized using Docker for easy deployment.
- Scalable deployment using Kubernetes.

## Prerequisites

- Docker
- Docker Compose
- Kubernetes
- kubectl
- Minikube (for local Kubernetes deployment)

## Setup Instructions

### 1. Initialize a Git Repository

```sh
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/AhMeD7493/ToDoList-project.git
git push -u origin master

### 2. Configure Environment Variables

Create a .env file in the project root with the following content:

DB_NAME=tododb
DB_USER=username
DB_HOST=postgres-service 
DB_PASS=yourpassword
DB_PORT=5432
DJANGO_ALLOWED_HOSTS=localhost,127.0.0.1,192.168.49.2,192.168.49.2:30000


### 3. Build and Run with Docker Compose

Ensure Docker is running, then execute:

docker compose build


### 4. Access the Application

Visit http://localhost:8000 in your web browser.

### 5. Deploy with Kubernetes

Apply the Kubernetes manifests with the order:

kubectl apply -f postgres-pv.yml
kubectl apply -f postgres-pvc.yml
kubectl apply -f postgres-credentials.yml
kubectl apply -f configmap.yml
kubectl apply -f postgres-deployment.yml
kubectl apply -f postgres-service.yml
kubectl apply -f app-deployment.yml
kubectl apply -f app-service.yml

Forward the service port to your local machine:

kubectl port-forward service/django-service 8000:8000

Or Using NodePort

http://minikube-ip:30000
