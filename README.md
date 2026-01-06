# DevOps CI/CD with Azure DevOps, Docker, AKS & Helm

This repository demonstrates an end-to-end DevOps CI/CD workflow using Azure DevOps YAML pipelines, Docker, Azure Kubernetes Service (AKS), and Helm.

The project reflects real-world enterprise DevOps practices, including containerization, registry management, and Kubernetes deployments managed through Infrastructure-as-Code style templates.

---

## What This Project Demonstrates

- CI/CD using Azure DevOps multi-stage YAML pipelines  
- Docker image build and push to Azure Container Registry (ACR)  
- Kubernetes deployment to Azure Kubernetes Service (AKS)  
- Application lifecycle management using Helm charts  
- Health checks and readiness for production-style deployments  

---

## Application Overview

The application is a lightweight Python Flask API designed for CI/CD and Kubernetes deployment demonstrations.

Endpoints:
- /        – basic service response  
- /health – health check for Kubernetes probes  

---

## Architecture Overview

GitHub Repository  
↓  
Azure DevOps Pipeline (YAML)  
↓  
Docker Build  
↓  
Azure Container Registry (ACR)  
↓  
Azure Kubernetes Service (AKS)  
↓  
Helm (Deployment + Service)

---

## Tech Stack

DevOps & Cloud:
- Azure DevOps (YAML pipelines)
- Azure Container Registry (ACR)
- Azure Kubernetes Service (AKS)
- Helm

Containers & Orchestration:
- Docker
- Kubernetes (Deployment, Service, probes)

Application:
- Python
- Flask

---

## Repository Structure

devops-ci-cd-docker-k8s/
- app/
  - main.py
  - requirements.txt
- azure-devops/
  - azure-pipelines.yml
- helm/
  - demo-api/
    - Chart.yaml
    - values.yaml
    - templates/
      - deployment.yaml
      - service.yaml
- k8s/
  - deployment.yaml
  - service.yaml
- .github/workflows/
  - ci.yaml
- Dockerfile
- .dockerignore
- README.md

---

## CI/CD Pipeline (Azure DevOps)

The Azure DevOps pipeline is defined in:

azure-devops/azure-pipelines.yml

Pipeline stages:

1. Build & Test  
   - Install Python dependencies  
   - Run basic application validation  

2. Build & Push Docker Image  
   - Build Docker image  
   - Push image to Azure Container Registry  
   - Tag images with build ID and latest  

3. Deploy to AKS  
   - Fetch AKS credentials  
   - Create Kubernetes namespace if missing  
   - Deploy application using Helm upgrade/install  

---

## Helm Deployment

Kubernetes resources are managed using a Helm chart located at:

helm/demo-api/

The Helm chart includes:
- Kubernetes Deployment (replicas, container image, health probes)
- Kubernetes Service (LoadBalancer by default)

Helm enables:
- Versioned deployments
- Simplified upgrades and rollbacks
- Parameterized configuration

---

## Azure DevOps Configuration (Required)

To run this pipeline in Azure DevOps, configure the following outside this repository.

Service Connections:
- ACR_SERVICE_CONNECTION  
  (Docker Registry → Azure Container Registry)
- AZURE_RM_SERVICE_CONNECTION  
  (Azure Resource Manager → Subscription or Resource Group)

Pipeline Variables:
- ACR_LOGIN_SERVER (example: myacr.azurecr.io)
- AKS_RESOURCE_GROUP
- AKS_CLUSTER_NAME

No secrets are stored in this repository.

---

## Run Locally (Optional)

Docker:
docker build -t demo-api:local .
docker run -p 8080:8080 demo-api:local

Access:
- http://localhost:8080
- http://localhost:8080/health

---

## Why This Repository Matters

This project demonstrates how DevOps pipelines are implemented in production environments, showcasing:

- CI/CD automation using Azure DevOps
- Kubernetes deployment best practices
- Secure handling of credentials and secrets
- Enterprise-ready cloud-native workflows

---

Author  
Fathima Gousiya  
DevOps / Systems Engineer  
LinkedIn: https://linkedin.com/in/Fathima-gousiya
