# Troubleshooting

Common issues and solutions when working with localhost-k8s.

## Cluster Issues

### Cluster won't start with k3d

**Problem**: `k3d cluster create` fails with Docker error

**Solutions**:

- Ensure Docker daemon is running: `docker ps`
- Check available disk space: `df -h`
- Try deleting existing cluster: `k3d cluster delete <name> && k3d cluster
  create <name>`

### kubectl can't connect to cluster

**Problem**: `Unable to connect to the server`

**Solutions**:

- Verify cluster is running: `k3d cluster list` or `kind get clusters`
- Check kubeconfig: `kubectl config current-context`
- Reset kubeconfig: `kubectl config use-context <cluster-name>`

## Manifest Issues

### YAML validation fails

**Problem**: `error validating "file.yaml"`

**Solutions**:

- Check syntax: `kubectl apply --dry-run=client -f file.yaml`
- Validate indentation (YAML uses 2 spaces, not tabs)
- Use an editor with YAML linting (VS Code with YAML extension)

### Manifest applies but pod doesn't start

**Problem**: Pod remains in Pending or CrashLoopBackOff state

**Solutions**:

```bash
# Check pod status
kubectl describe pod <pod-name>

# Check logs
kubectl logs <pod-name>

# Check events
kubectl get events --sort-by='.lastTimestamp'
```

## Ingress Issues

### Ingress not routing traffic

**Problem**: Cannot reach service through ingress

**Solutions**:

- Verify ingress is created: `kubectl get ingress`
- Check ingress rules: `kubectl describe ingress <ingress-name>`
- Verify backend service exists: `kubectl get svc`
- Test service directly: `kubectl port-forward svc/<service-name> 8080:80`

## Docker Issues

### Docker container runs out of disk space

**Problem**: Cluster creation fails with disk space error

**Solutions**:

```bash
# Clean up unused Docker resources
docker system prune -a

# Check Docker disk usage
docker system df
```

## Getting Help

- Check logs: `kubectl logs -f <pod-name>`
- Describe resources: `kubectl describe <resource-type> <resource-name>`
- Review events: `kubectl get events`
- Search issues: <https://github.com/jorgenhl/localhost-k8s/issues>
