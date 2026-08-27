Docker & Kubernetes Practice

This repository contains my hands-on practice and implementation tasks for Docker, Docker Compose, Docker Hub, Kubernetes, and Jenkins CI/CD.

The project covers container creation, storage, networking, resource management, troubleshooting, image registries, cleanup automation, Kubernetes workloads, and automated Docker application validation using Jenkins.

Task Completion
Docker
 Task 1 — Docker Image Creation
 Task 2 — Docker Volumes
 Task 3 — Docker Networking
 Task 4 — Docker Compose
 Task 5 — Docker Resource Management
 Task 6 — Multi-Stage Docker Build
 Task 7 — Docker Container Troubleshooting
 Task 8 — Docker Registry / Docker Hub
 Task 9 — Docker Cleanup Automation
Kubernetes
 Task 10 — Pod Creation
 Task 11 — Deployment Creation
Jenkins CI/CD
 Jenkinsfile — Declarative Pipeline
 GitHub Repository Checkout
 Docker Environment Verification
 Docker Image Build
 Container Test
 Website Content Validation
 Container Cleanup

Tasks marked with [x] have been completed and verified.

Project Structure
docker-kubernetes-practice/
│
├── kubernetes/
│   ├── task10-pod/
│   │   └── nginx-pod.yaml
│   │
│   └── task11-deployment/
│       └── nginx-deployment.yaml
│
├── task1-html/
│   ├── Dockerfile
│   └── index.html
│
├── task2-volumes/
├── task3-networking/
├── task4-compose/
├── task5-resources/
├── task6-multistage/
├── task7-troubleshooting/
├── task8-registry/
├── task9-cleanup/
│
├── Jenkinsfile
└── README.md

Tools Used
Docker
Docker Compose
Docker Hub
Kubernetes
Minikube
kubectl
Git
GitHub
Jenkins
Nginx
Jenkins CI/CD Pipeline

This repository includes a Jenkinsfile in the project root.

The Jenkins pipeline automatically checks out the GitHub repository, verifies Docker, builds the Docker image, starts a test container, validates the website, and cleans up the container after testing.

Jenkins Configuration
Configuration	Value
Repository	raveesham/docker-kubernetes-practice
Branch	main
Pipeline Type	Pipeline script from SCM
Script Path	Jenkinsfile
SCM	Git
Pipeline Stages
┌──────────────────────────┐
│     GitHub Repository    │
│ docker-kubernetes-       │
│ practice                 │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│         Jenkins          │
│      Read Jenkinsfile    │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│        Checkout          │
│     Source Code from     │
│         GitHub            │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│     Verify Project       │
│   Check project files    │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│      Verify Docker       │
│    docker --version      │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│    Build Docker Image    │
│      my-website:23       │
│       task1-html         │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│    Run Test Container    │
│       Port 8084          │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│      Test Website        │
│                          │
│ HTTP Status = 200        │
│ Expected content found   │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│         Cleanup          │
│    Remove Test Container │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│       Build SUCCESS      │
└──────────────────────────┘

Jenkins Pipeline Flow

The overall CI/CD process is:

Developer
    │
    ▼
GitHub
    │
    ▼
Jenkins
    │
    ├── Checkout Code
    │
    ├── Verify Project
    │
    ├── Verify Docker
    │
    ├── Build Docker Image
    │
    ├── Run Container
    │
    ├── Test Website
    │
    └── Cleanup
            │
            ▼
       Build SUCCESS

Docker Website

Task 1 contains a simple Nginx-based website.

The Docker image is created using:

nginx:latest


The website content is copied into:

/usr/share/nginx/html/index.html


Jenkins builds the image using:

docker build -t my-website:23 task1-html


The container is then started for testing:

docker run -d --name jenkins-my-website-test -p 8084:80 my-website:23


The Jenkins pipeline verifies that:

The container starts successfully.
The website responds with HTTP 200.
The expected website content is available.
The test container is removed after validation.
Kubernetes

The kubernetes/ directory contains Kubernetes practice tasks.

Task 10 — Pod

A basic Nginx Pod is created using:

kubernetes/task10-pod/nginx-pod.yaml

Task 11 — Deployment

An Nginx Deployment is created using:

kubernetes/task11-deployment/nginx-deployment.yaml


These tasks provide hands-on practice with Kubernetes Pods and Deployments using kubectl and Minikube.

Learning Areas

This project provides practical experience with:

Docker image creation
Docker containers
Docker volumes
Docker networking
Docker Compose
Docker resource management
Multi-stage Docker builds
Container troubleshooting
Docker Hub and image registries
Docker cleanup
Kubernetes Pods
Kubernetes Deployments
Minikube
kubectl
Git and GitHub
Jenkins pipelines
CI/CD automation
Automated Docker application testing
CI/CD Result

The Jenkins pipeline successfully performs the complete Docker application validation workflow:

GitHub
  ↓
Jenkins
  ↓
Checkout
  ↓
Docker Verification
  ↓
Docker Image Build
  ↓
Container Start
  ↓
Website Validation
  ↓
Container Cleanup
  ↓
SUCCESS


The pipeline is designed to ensure that the Docker website can be built, started, and validated automatically before considering the build successful.

Repository Status

All Docker and Kubernetes practice tasks listed in this repository have been completed and verified.

The project also includes a working Jenkins Declarative Pipeline for automated Docker image building and website validation.

Author

Raveesha M

Docker • Kubernetes • Jenkins • Git • GitHub • CI/CD
