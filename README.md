# 2048 React CI/CD Deployment

Hands-on DevOps project for containerizing a React/TypeScript 2048 game and deploying it with Docker and Kubernetes.

## Project Overview

This repository uses a React application as the sample workload for practicing DevOps deployment flow. The main focus is not the game logic itself, but the steps required to package, run, and deploy a frontend application using container and Kubernetes concepts.

## Tech Stack

| Area | Tools |
|---|---|
| Frontend | React, TypeScript |
| Styling | LESS |
| Build Tooling | CRACO, React Scripts |
| Containerization | Docker |
| Orchestration | Kubernetes |
| Deployment Object | Deployment, Service |

## Repository Structure

| Path | Purpose |
|---|---|
| `src/` | React application source code |
| `public/` | Static public assets |
| `Dockerfile` | Docker image build definition |
| `deployment.yaml` | Kubernetes Deployment and Service |
| `package.json` | Application scripts and dependencies |

## Deployment Flow

```text
Developer
   |
   v
React Application
   |
   v
Docker Build
   |
   v
Container Image
   |
   v
Kubernetes Deployment
   |
   v
LoadBalancer Service
```

## Run Locally

Install dependencies:

```bash
npm install
```

Start the app:

```bash
npm start
```

Build the production bundle:

```bash
npm run build
```

## Build and Run With Docker

Build the Docker image:

```bash
docker build -t 2048-react-cicd .
```

Run the container:

```bash
docker run -p 3000:3000 2048-react-cicd
```

## Deploy to Kubernetes

Before applying the manifest, update the image in `deployment.yaml`:

```yaml
image: <dockerhub-username>/2048-react-cicd:latest
```

Apply the manifest:

```bash
kubectl apply -f deployment.yaml
```

Validate resources:

```bash
kubectl get deployments
kubectl get pods
kubectl get svc
kubectl describe pod <pod-name>
kubectl logs <pod-name>
```

## Interview Talking Points

- How a frontend app is packaged into a Docker image
- Difference between local app run and containerized app run
- Why Kubernetes Deployment uses labels and selectors
- How Kubernetes Service exposes application pods
- Difference between `ClusterIP`, `NodePort`, and `LoadBalancer`
- What to check when the pod is running but the app is not reachable

## Troubleshooting Checklist

- Confirm the Docker image builds successfully.
- Verify the container listens on the expected port.
- Check image name and tag inside `deployment.yaml`.
- Use `kubectl describe pod` for scheduling or image pull errors.
- Use `kubectl logs` for runtime errors.
- Confirm Service selector matches pod labels.

## Learning Outcome

This project is useful for explaining a basic CI/CD and Kubernetes deployment path using a simple React application. It is a good beginner-friendly repo to discuss Docker, Kubernetes manifests, service exposure, and deployment validation.
