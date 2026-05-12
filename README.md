# Microservices Deployment on Kubernetes

This project is something I built to practice deploying multiple services together on Kubernetes. It has three small Python services that talk to each other — a user service, a task service, and a notification service.

## What I built

- **user_service.py** — handles basic user stuff like creating and managing users
- **task_service.py** — creates and assigns tasks to users
- **notification_service.py** — sends a notification when a task is assigned or updated

Each service runs in its own Docker container and they all talk to each other inside the Kubernetes cluster.

## Why I built this

In my work I deploy microservices on AWS EKS regularly, but I wanted to build something from scratch to understand how services communicate inside a cluster, how to write Dockerfiles properly, and how to structure a multi-service project cleanly.

## Tech used

- Python for the services
- Docker to containerize each service
- Kubernetes to deploy and manage them
- Helm for packaging the deployment
- ArgoCD for GitOps-style continuous delivery

## How to run it

Make sure you have Docker and kubectl set up, then:

```bash
# build the images
docker build -t user-service .
docker build -t task-service .
docker build -t notification-service .

# deploy to kubernetes
kubectl apply -f k8s/

# check if everything is running
kubectl get pods
kubectl get svc
```

## What I learned from this

Setting up inter-service communication inside Kubernetes is trickier than it looks. Getting the service names and ports right in the environment variables took some debugging. Also learned how ArgoCD syncs automatically when you push changes to Git — which is really useful for real projects.

---

Feel free to clone and try it out. If something doesn't work, raise an issue and I'll look into it.

— Harish
