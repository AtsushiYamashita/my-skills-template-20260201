---
description: Merge a feature branch into develop
---

# Merge to Develop Workflow

This workflow guides you through merging a completed feature branch into the develop branch.

## Pre-Merge Checklist

Before merging, ensure:

- [ ] All changes are committed
- [ ] Code has been tested (manually or automated)
- [ ] Documentation is updated (if applicable)
- [ ] No conflicts with develop branch
- [ ] Branch is pushed to remote

## Steps

### 1. Ensure all changes are committed

// turbo

```bash
git status
```

If there are uncommitted changes, commit them:

```bash
git add .
git commit -m "feat: your commit message"
```

### 2. Update your branch with latest develop

```bash
git fetch origin develop
```

```bash
git merge origin/develop
```

If there are conflicts, resolve them, then commit the merge.

### 3. Push your branch to remote

```bash
git push origin HEAD
```

### 4. Create Pull Request

**Option A: Using GitHub CLI (if installed)**

```bash
gh pr create --base develop --head $(git branch --show-current) --title "Your PR title" --body "Description of changes"
```

**Option B: Using GitHub Web Interface**

1. Go to your repository on GitHub
2. Click "Pull requests" → "New pull request"
3. Set base: `develop`, compare: `your-feature-branch`
4. Add title and description following conventional commits format
5. Click "Create pull request"

**Option C: Manual merge (for solo projects)**

// turbo

```bash
git checkout develop
```

```bash
git merge --squash feature/<your-branch-name>
```

```bash
git commit -m "feat: add your feature description"
```

// turbo

```bash
git push origin develop
```

### 5. Delete the feature branch (after successful merge)

// turbo

```bash
git checkout develop
```

// turbo

```bash
git branch -d feature/<your-branch-name>
```

```bash
git push origin --delete feature/<your-branch-name>
```

## Examples

### Full workflow example

```bash
# Ensure everything is committed
git status

# Update with develop
git fetch origin develop
git merge origin/develop

# Push to remote
git push origin HEAD

# Merge to develop (manual merge)
git checkout develop
git merge --squash feature/user-auth
git commit -m "feat: add user authentication system"
git push origin develop

# Clean up
git branch -d feature/user-auth
git push origin --delete feature/user-auth
```

## Troubleshooting

### Merge conflicts

If you encounter conflicts during merge:

1. Open conflicting files
2. Resolve conflicts (look for `<<<<<<<`, `=======`, `>>>>>>>` markers)
3. Stage resolved files: `git add <file>`
4. Complete merge: `git commit`

### PR not showing on GitHub

- Ensure your branch is pushed to remote: `git push origin HEAD`
- Check repository permissions
- Verify branch names are correct

## Next Steps

- After merge, you can start a new feature using **create-feature** workflow
- When ready for production, use **release-to-main** workflow
