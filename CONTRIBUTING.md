# Contributing

Thank you for your interest in contributing! Here are some guidelines to help
you get started.

## How to Contribute

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/my-improvement`)
3. Commit your changes (`git commit -am 'Add my improvement'`)
4. Push to the branch (`git push origin feature/my-improvement`)
5. Open a Pull Request

## Code Standards

- Follow YAML conventions for Kubernetes manifests
- Include clear commit messages
- Test your changes locally with k3d or kind before submitting a PR
- Ensure manifests are valid using `kubectl apply --dry-run=client -f <file>`

## Pull Request Process

- Provide a clear description of the changes
- Reference any related issues
- Ensure your changes don't break existing configurations
- Wait for review and address any feedback

## Reporting Issues

Please use GitHub Issues to report bugs or request features. Include:

- Clear description of the issue
- Steps to reproduce (if applicable)
- Your environment (OS, Kubernetes version, etc.)
