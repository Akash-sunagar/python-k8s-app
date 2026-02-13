Containerized Flask Application with CI/CD and Kubernetes Deployment
Project Overview

This project demonstrates a complete DevOps workflow by deploying a containerized Flask application using Docker, Kubernetes, and a CI/CD pipeline with GitHub Actions.

Whenever code is pushed to the main branch, the pipeline automatically builds a Docker image and pushes it to DockerHub. The application is then deployed on Kubernetes.

Architecture Flow

Developer pushes code to GitHub.

GitHub Actions CI pipeline triggers.

Docker image is built.

Image is pushed to DockerHub.

Kubernetes Deployment pulls the image.

Pods run the Flask application.

Service exposes the application to users.

Technologies Used

Python (Flask)

Docker

Kubernetes (EKS)

GitHub Actions (CI/CD)

DockerHub (container registry)

Git (version control)

Project Structure
python-devops-project/
│
├── app/
│   ├── app.py
│   ├── requirements.txt
│   └── Dockerfile
│
├── k8s/
│   ├── namespace.yaml
│   ├── deployment.yaml
│   ├── service.yaml
│   └── ingress.yaml
│
└── .github/
    └── workflows/
        └── pipeline.yml

Application Details

A simple Flask web application.

Runs on port 5000.

Returns a welcome message:

Hello from DevOps Project!

Docker Setup
Build the Docker image
docker build -t <dockerhub-username>/python-app ./app

Run the container
docker run -d -p 5000:5000 <dockerhub-username>/python-app

Access the application
http://localhost:5000

Kubernetes Deployment
Step 1: Create namespace
kubectl apply -f k8s/namespace.yaml

Step 2: Deploy application
kubectl apply -f k8s/deployment.yaml

Step 3: Expose service
kubectl apply -f k8s/service.yaml

Step 4: Apply ingress
kubectl apply -f k8s/ingress.yaml

CI/CD Pipeline (GitHub Actions)
Pipeline Trigger

Automatically runs on push to the main branch.

Pipeline Steps

Checkout code from GitHub.

Login to DockerHub using secrets.

Build Docker image.

Push image to DockerHub.

GitHub Secrets Required

Add these secrets in:

Repository → Settings → Secrets and variables → Actions

DOCKER_USERNAME
DOCKER_PASSWORD

How CI/CD Works (Simple Flow)

Developer pushes code.

GitHub triggers pipeline.

Docker image is built.

Image is pushed to DockerHub.

Kubernetes uses the updated image.

How to Access the Application in Kubernetes

After deployment:

http://<node-ip>:<nodeport>

Key DevOps Concepts Demonstrated

Containerization using Docker

Kubernetes Deployment and Service

CI/CD with GitHub Actions

