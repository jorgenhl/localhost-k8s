# Copilot CLI Custom Instructions

## Pre-Commit Validation Checklist

Before committing any changes to git, perform the following validation steps
that match the GitHub Actions CI/CD pipeline:

### 1. Markdown Linting

Validate all markdown files using markdown linting:

```bash
find . -name "*.md" -type f | xargs markdownlint
```

If linting errors are found, auto-fix them:

```bash
find . -name "*.md" -type f | xargs markdownlint --fix
```

**Why**: Ensures consistent markdown formatting and style across all
documentation files.

### 2. YAML Syntax Validation

Validate YAML syntax using kubectl dry-run for Kubernetes manifests:

```bash
find . -name '*.yaml' -o -name '*.yml' | while read file; do
  echo "Validating $file..."
  kubectl apply --dry-run=client -f "$file" || exit 1
done
```

**Why**: Ensures all Kubernetes manifests are valid before deployment.

### 3. YAML Formatting Check

Check YAML formatting with yamllint:

```bash
yamllint .
```

Configuration enforces:

- Default yamllint rules
- Indentation: 2 spaces
- Line length: disabled

**Why**: Maintains consistent YAML formatting across the project.

## Summary

Before committing, verify:

- ✅ All markdown files pass `markdownlint`
- ✅ All YAML files pass `kubectl apply --dry-run=client`
- ✅ All YAML files pass `yamllint`

Only commit to git after all validations pass.
