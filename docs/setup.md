# Setup Guide

Detailed instructions for setting up and using this project.

## Overview

This guide covers two popular tools for running Kubernetes locally:

- **k3d**: Lightweight Kubernetes in Docker (based on k3s)
- **kind**: Kubernetes in Docker

Both are excellent choices; k3d is lighter weight while kind is closer to full Kubernetes.

## Prerequisites

Before getting started, ensure you have:

1. **Docker** - Installed and running
2. **kubectl** - Kubernetes command-line tool

### Install kubectl

Follow the [official kubectl installation guide](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/) for your OS.

**Linux example:**
```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
kubectl version --client
```

## k3d Setup

### What is k3d?

k3d is a lightweight container orchestration tool that simplifies running k3s clusters in Docker. k3s is a minimal, certified Kubernetes distribution optimized for resource-constrained environments. k3d wraps k3s and makes it easy to create, manage, and test Kubernetes clusters locally by running them inside Docker containers.

### Install k3d

**macOS (Homebrew):**
```bash
brew install k3d
```

**Linux:**
```bash
curl -s https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
```

**Windows (Chocolatey):**
```bash
choco install k3d
```

See [k3d releases](https://github.com/k3d-io/k3d/releases) for additional options.

### Create a Cluster

Simple single-node cluster:
```bash
k3d cluster create mycluster
```

Multi-node cluster with 3 servers and 2 agents:
```bash
k3d cluster create mycluster --servers 3 --agents 2
```

### Verify Cluster

```bash
kubectl cluster-info
kubectl get nodes
```

### Delete Cluster

```bash
k3d cluster delete mycluster
```

For advanced configurations, visit the [k3d documentation](https://k3d.io/).

## kind Setup

### What is kind?

kind (Kubernetes in Docker) is a tool for running local Kubernetes clusters using Docker containers as cluster nodes. It's designed for testing Kubernetes itself, but is also good for local development.

### Install kind

**Homebrew (macOS/Linux):**
```bash
brew install kind
```

**Using Go:**
```bash
go install sigs.k8s.io/kind@latest
```

See [kind releases](https://github.com/kubernetes-sigs/kind/releases) for other options.

### Create a Cluster

```bash
kind create cluster --name my-cluster
```

### Verify Cluster

```bash
kubectl cluster-info
kubectl get nodes
```

### Delete Cluster

```bash
kind delete cluster --name my-cluster
```

For more options, visit the [kind documentation](https://kind.sigs.k8s.io/).

## Working with Manifests

### Validate Manifests

Before applying manifests to a cluster, always validate them:

```bash
kubectl apply --dry-run=client -f thatfile.yaml
```

This checks syntax without making changes.

### Apply Manifests

```bash
kubectl apply -f thatfile.yaml
```

### Check Deployment Status

```bash
kubectl get pods
kubectl get svc
kubectl get ingress
```

### View Logs

```bash
kubectl logs <pod-name>
```

### Troubleshooting

See [troubleshooting.md](./troubleshooting.md) for common issues and solutions.

## Next Steps

- Review the main [README.md](../README.md)
- Check [architecture.md](./architecture.md) to understand the project structure
- See [troubleshooting.md](./troubleshooting.md) if you encounter issues
- Check [CONTRIBUTING.md](../CONTRIBUTING.md) to contribute improvements
