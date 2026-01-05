# DevOps CI/CD + Docker + Kubernetes

This repo demonstrates an end-to-end DevOps workflow:
- A small Python API (Flask)
- Containerized with Docker
- Deployed using Kubernetes manifests (Deployment + Service)
- Continuous Integration using GitHub Actions

## What this project proves
- CI pipeline setup (GitHub Actions)
- Docker build and container packaging
- Kubernetes deployment patterns (replicas, probes, service exposure)
- Basic operational readiness using health checks

## Tech Stack
- Python (Flask)
- Docker
- Kubernetes (Deployment, Service, readiness/liveness probes)
- GitHub Actions (CI)

---

## Project Structure
```text
devops-ci-cd-docker-k8s/
├─ app/
│  ├─ main.py
│  └─ requirements.txt
├─ k8s/
│  ├─ deployment.yaml
│  └─ service.yaml
├─ .github/workflows/
│  └─ ci.yaml
├─ Dockerfile
├─ .dockerignore
└─ README.md
