# my-skills-template-20260201

Template repository for AI-assisted skill development.

## Branch Strategy

This project follows a **simplified 3-tier branch model** optimized for AI-assisted parallel development:

```
feature/xxx → develop → main
```

- **`main`** - Production-ready code (stable, tagged releases)
- **`develop`** - Integration and testing (all features merge here first)
- **`feature/xxx`** - Short-lived feature branches (AI sessions work here)

### Quick Start

Start a new feature:

```bash
git checkout develop
git pull origin develop
git checkout -b feature/your-feature-name
```

For detailed workflows, see:

- [Branch Strategy Rules](.agent/rules/branch-strategy.md)
- [Create Feature Workflow](.agent/workflows/create-feature.md)
- [Merge to Develop Workflow](.agent/workflows/merge-to-develop.md)
- [Release to Main Workflow](.agent/workflows/release-to-main.md)

---

**AI Agents**: Always start new tasks with `/create-feature` workflow.
