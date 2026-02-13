---
description: Create a new feature branch and start development
---

# Create Feature Branch Workflow

This workflow guides you through creating a new feature branch for isolated development.

## Steps

### 1. Ensure you're on the latest develop branch

// turbo

```bash
git checkout develop
```

// turbo

```bash
git pull origin develop
```

### 2. Create a new feature branch

Determine the appropriate prefix:

- `feature/` - For new features or enhancements
- `fix/` - For bug fixes
- `experiment/` - For experimental work that may be discarded
- `docs/` - For documentation-only changes
- `refactor/` - For code refactoring without functionality changes

// turbo

```bash
git checkout -b feature/<descriptive-name>
```

**Replace `<descriptive-name>` with a concise description using lowercase and hyphens.**

### 3. Verify you're on the new branch

// turbo

```bash
git branch --show-current
```

### 4. Start development

You can now begin making changes. Remember to:

- Commit frequently with clear messages using conventional commits format
- Push to remote regularly to backup your work

### 5. Initial push to remote

After your first commit, push the branch to remote:

```bash
git push -u origin feature/<descriptive-name>
```

## Examples

### Creating a feature branch

```bash
git checkout develop
git pull origin develop
git checkout -b feature/user-authentication
git push -u origin feature/user-authentication
```

### Creating a fix branch

```bash
git checkout develop
git pull origin develop
git checkout -b fix/login-timeout
git push -u origin fix/login-timeout
```

### Creating an experiment branch

```bash
git checkout develop
git pull origin develop
git checkout -b experiment/ml-integration
git push -u origin experiment/ml-integration
```

## Next Steps

- Make your changes and commit regularly
- When ready, follow the **merge-to-develop** workflow
