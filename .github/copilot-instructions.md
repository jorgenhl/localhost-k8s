# Copilot CLI Custom Instructions

## Markdown Linting

Before committing changes to git, ensure that all markdown files have been validated using markdown linting.

### Required Steps Before Commit

1. Run markdown lint on all markdown files:
   ```bash
   find . -name "*.md" -type f | xargs markdownlint
   ```

2. Fix any linting issues found by markdownlint, or use auto-fix if available:
   ```bash
   find . -name "*.md" -type f | xargs markdownlint --fix
   ```

3. Review the changes to ensure markdown formatting is correct and consistent.

4. Only commit to git after all markdown files pass linting validation.

### Configuration

This project uses markdown linting to maintain consistent formatting and style across all markdown documentation files. All changes to `.md` files must pass markdown linting before being committed.

### Pre-commit Hook (Optional)

To automatically enforce markdown linting before commits, consider using a pre-commit hook by creating a `.git/hooks/pre-commit` file or using a tool like husky with a pre-commit hook script.
