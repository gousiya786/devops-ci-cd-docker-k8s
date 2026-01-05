# DevOps CI/CD + Docker + Kubernetes

Minimal Flask API containerized with Docker and deployed via Kubernetes manifests.

## Tech
Python, Docker, Kubernetes, GitHub Actions

## Run locally
```bash
docker build -t demo-api:local .
docker run -p 8080:8080 demo-api:local
# http://localhost:8080
