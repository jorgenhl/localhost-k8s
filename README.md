# Config for setup localhost kubernetes cluster

## k3d

k3d is a lightweight container orchestration tool that simplifies running k3s
clusters in Docker. k3s is a minimal, certified Kubernetes distribution
optimized for resource-constrained environments. k3d wraps k3s and makes it
easy to create, manage, and test Kubernetes clusters locally by running them
inside Docker containers. This approach is ideal for development, testing, and
CI/CD workflows, allowing developers to quickly spin up multi-node Kubernetes
clusters without the overhead of full Kubernetes installations. k3d is
particularly useful for local development and learning Kubernetes concepts
with minimal resource requirements.

### Getting Started

#### Prerequisites

Before setting up k3d, ensure you have `kubectl` installed. kubectl is the
command-line tool for interacting with Kubernetes clusters.

**Install kubectl:**

Follow the [official kubectl installation
guide](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/) for
your operating system. For Linux, you can use:

```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

Verify the installation:

```bash
kubectl version --client
```

#### Installation

Install k3d using your package manager or download from the [official
releases](https://github.com/k3d-io/k3d/releases):

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

#### Create a Cluster

Create a simple single-node cluster:

```bash
k3d cluster create mycluster
```

Create a cluster with multiple servers and agents:

```bash
k3d cluster create mycluster --servers 3 --agents 2
```

#### Interact with Your Cluster

Once created, your kubeconfig is automatically configured. Verify the
cluster is running:

```bash
kubectl cluster-info
kubectl get nodes
```

#### Delete a Cluster

Remove a cluster when you're done:

```bash
k3d cluster delete mycluster
```

For more advanced configurations and options, visit the [k3d
documentation](https://k3d.io/).

## kind
