---
description: Release develop branch to production (main)
---

# Release to Main Workflow

This workflow guides you through releasing the develop branch to the production main branch.

## Pre-Release Checklist

Before releasing to main, ensure:

- [ ] All features in develop are tested and verified
- [ ] Documentation is up-to-date
- [ ] No known critical bugs
- [ ] Changelog is prepared (if applicable)
- [ ] Version number is decided (semantic versioning: MAJOR.MINOR.PATCH)

## Steps

### 1. Ensure develop is up-to-date and clean

// turbo

```bash
git checkout develop
```

// turbo

```bash
git pull origin develop
```

// turbo

```bash
git status
```

### 2. Update main branch

// turbo

```bash
git checkout main
```

// turbo

```bash
git pull origin main
```

### 3. Merge develop into main

**Option A: Using Pull Request (Recommended for teams)**

1. Create PR: develop → main on GitHub
2. Review changes
3. Merge pull request
4. Pull the updated main locally:
   ```bash
   git checkout main
   git pull origin main
   ```

**Option B: Direct merge (For solo projects)**

```bash
git checkout main
git merge develop -m "Release: merge develop to main"
```

```bash
git push origin main
```

### 4. Tag the release

Determine version number using [Semantic Versioning](https://semver.org/):

- **MAJOR**: Breaking changes
- **MINOR**: New features (backward compatible)
- **PATCH**: Bug fixes (backward compatible)

```bash
git tag -a v1.0.0 -m "Release 1.0.0: Initial production release"
```

```bash
git push origin v1.0.0
```

### 5. Sync develop with main (if needed)

If you made any hotfixes directly on main, sync them back to develop:

// turbo

```bash
git checkout develop
```

```bash
git merge main
```

```bash
git push origin develop
```

## Examples

### Full release workflow

```bash
# Prepare develop
git checkout develop
git pull origin develop

# Prepare main
git checkout main
git pull origin main

# Merge develop to main
git merge develop -m "Release: v1.2.0"
git push origin main

# Tag the release
git tag -a v1.2.0 -m "Release 1.2.0: Add user authentication and API improvements"
git push origin v1.2.0

# Return to develop
git checkout develop
```

### Hotfix release workflow

```bash
# Fix directly on main
git checkout main
git pull origin main
# Make fixes...
git add .
git commit -m "fix: critical security patch"
git push origin main

# Tag hotfix
git tag -a v1.2.1 -m "Release 1.2.1: Security hotfix"
git push origin v1.2.1

# Sync to develop
git checkout develop
git merge main
git push origin develop
```

## Post-Release Tasks

After successful release:

1. **Update documentation** (if hosted separately)
2. **Notify stakeholders** (if applicable)
3. **Monitor production** for any issues
4. **Create release notes** on GitHub (optional)

### Creating GitHub Release Notes

```bash
gh release create v1.0.0 --title "Version 1.0.0" --notes "Release notes here"
```

Or use GitHub web interface:

1. Go to repository → Releases
2. Click "Draft a new release"
3. Select tag, add title and description
4. Publish release

## Versioning Guide

### When to increment version numbers

**MAJOR (v2.0.0)**

- Breaking API changes
- Major architectural changes
- Non-backward compatible updates

**MINOR (v1.1.0)**

- New features added
- Backward compatible improvements
- Deprecated (but not removed) functionality

**PATCH (v1.0.1)**

- Bug fixes
- Security patches
- Minor improvements

## Troubleshooting

### Merge conflicts during release

- Review conflicts carefully
- Prioritize main branch code for production stability
- Test thoroughly after resolving conflicts

### Accidental push to main

```bash
# Revert the last commit (if not shared yet)
git revert HEAD
git push origin main
```

## Next Steps

- Monitor production for any issues
- Start new development cycle with **create-feature** workflow
- Document lessons learned for next release
