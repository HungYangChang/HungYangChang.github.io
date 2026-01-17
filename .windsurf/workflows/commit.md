---
description: Review changes, create commit message, and push to repository
---

# General Commit and Push Workflow

## Overview:
This workflow helps you review changes, generate appropriate commit messages, and push to the repository.

## Step 1: Review Current Changes

### Check git status:
```bash
git status
```

### See what files changed:
```bash
git diff --name-only
git diff --stat
```

### Review specific changes:
```bash
git diff filename
```

## Step 2: Stage Changes

### Stage all changes:
```bash
git add .
```

### Stage specific files:
```bash
git add file1.js file2.css
```

## Step 3: Create Commit Message

### Commit Message Guidelines:
- Use present tense ("Add feature" not "Added feature")
- First line should be 50 characters or less
- Include a blank line between title and body
- Body should explain what and why, not how
- Reference issues if applicable

### Commit Message Templates:

#### Feature Addition:
```
feat: add new feature name

Brief description of what the feature does and why it's needed.

- Added component X
- Updated style Y
- Fixed bug Z
```

#### Bug Fix:
```
fix: resolve issue with component behavior

Fixed the problem where X was not working correctly due to Y.
This ensures users can now successfully accomplish Z.

Closes #issue-number
```

#### Documentation:
```
docs: update README with installation instructions

Added comprehensive setup guide and troubleshooting section
to help new users get started quickly.
```

#### Refactoring:
```
refactor: improve code structure in authentication module

Reorganized functions to follow single responsibility principle
and improved readability for future maintenance.
```

#### Style/Formatting:
```
style: format code and fix linting issues

Applied consistent formatting across all JavaScript files
and fixed ESLint warnings.
```

## Step 4: Commit and Push

### Execute the commit:
```bash
git commit -m "Your commit message here"
```

### Push to remote repository:
```bash
git push origin main
```

### Or for other branches:
```bash
git push origin branch-name
```

## Step 5: Verify Push

### Check if push was successful:
```bash
git log --oneline -5
git status
```

### Verify on GitHub/GitLab:
- Check the repository online
- Verify files are updated
- Check if CI/CD pipeline runs (if applicable)

## Quality Checklist:

Before committing, ensure:
- ✅ Code follows project style guidelines
- ✅ Tests pass (if applicable)
- ✅ Documentation is updated
- ✅ No sensitive information is included
- ✅ Changes are properly staged
- ✅ Commit message is clear and descriptive

## Troubleshooting:

### If push fails:
```bash
# Pull latest changes first
git pull origin main

# Resolve any merge conflicts
# Then push again
git push origin main
```

### If commit needs to be amended:
```bash
# Amend last commit (only if not pushed yet)
git commit --amend -m "New commit message"

# Force push (use with caution)
git push --force-with-lease origin main
```

### If you need to undo changes:
```bash
# Unstage all changes
git reset

# Discard all unstaged changes
git checkout -- .

# Discard specific file changes
git checkout -- filename
```

## Branch Workflows:

### Create new branch:
```bash
git checkout -b feature-name
```

### Switch branches:
```bash
git checkout main
git checkout feature-name
```

### Merge branches:
```bash
git checkout main
git merge feature-name
git push origin main
```

## Common Git Commands Reference:

```bash
# History
git log --oneline --graph --all
git log --stat
git log -p filename

# Branching
git branch -a
git branch -d branch-name
git branch -D branch-name

# Remote operations
git remote -v
git remote add origin URL
git fetch origin
git pull origin main

# Stashing
git stash
git stash pop
git stash list

# Tags
git tag -a v1.0.0 -m "Version 1.0.0"
git push --tags
```

## Best Practices:

1. **Commit often** with small, focused changes
2. **Write clear commit messages** following the guidelines
3. **Pull before pushing** to avoid conflicts
4. **Test your changes** before committing
5. **Use branches** for features and bug fixes
6. **Keep your main branch clean** and deployable
7. **Review your changes** before staging
8. **Document significant changes** in commit messages