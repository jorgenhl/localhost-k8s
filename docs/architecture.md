# Architecture

This document outlines the structure and design of the localhost-k8s project.

## Project Structure

```
localhost-k8s/
├── README.md              # Main project documentation
├── CONTRIBUTING.md        # Contribution guidelines
├── CHANGELOG.md           # Version history
├── LICENSE                # MIT License
├── thatfile.yaml          # Kubernetes manifests
├── docs/                  # Extended documentation
│   ├── architecture.md    # This file
│   ├── setup.md          # Detailed setup guide
│   └── troubleshooting.md # Common issues and solutions
└── .github/              # GitHub configuration
    ├── workflows/        # CI/CD pipelines
    └── ISSUE_TEMPLATE/   # Issue templates
```

## Overview

This project provides configuration and documentation for running Kubernetes clusters locally using tools like k3d or kind. It serves as a reference for:

- Local Kubernetes development
- Testing Kubernetes manifests
- CI/CD pipeline development
- Learning Kubernetes concepts

## Kubernetes Manifests

All Kubernetes manifests are YAML files that define resources to be deployed on a cluster. Current manifests include:

- **Ingress configurations**: Network traffic routing rules
- Additional components as the project grows

## Tools Supported

- **k3d**: Lightweight Kubernetes in Docker (based on k3s)
- **kind**: Kubernetes in Docker

## Design Principles

1. **Minimal dependencies**: Keep the project lightweight
2. **Documentation-first**: Clear guides for users
3. **Reproducibility**: Consistent, well-tested configurations
4. **Community-friendly**: Easy to contribute and extend
