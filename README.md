# Git and GitHub Workflow Guide

## Standard Daily Workflow

### 1. Pull Latest Changes
[Git Pull Documentation](https://git-scm.com/docs/git-pull)
```bash
git pull origin main
```

### 2. Check Status
[Git Status Documentation](https://git-scm.com/docs/git-status)
```bash
git status
```

### 3. Stage Changes
[Git Add Documentation](https://git-scm.com/docs/git-add)
```bash
git add .
```

### 4. Commit Changes
[Git Commit Documentation](https://git-scm.com/docs/git-commit)
```bash
git commit -m "Describe your changes"
```

### 5. Push to Remote
[Git Push Documentation](https://git-scm.com/docs/git-push)
```bash
git push -u origin main
```

---

## Bug Fix Workflow (Branching)

### 1. Create and Switch to a New Branch
[Git Checkout Documentation](https://git-scm.com/docs/git-checkout)
```bash
git checkout -b fix-bug-description
```

### 2. Make and Test Your Fix

### 3. Stage and Commit Changes
```bash
git add .
git commit -m "Fix: bug description"
```

### 4. Push the Branch
```bash
git push -u origin fix-bug-description
```

### 5. Merge the Fix into Main
```bash
git checkout main
git merge fix-bug-description
git push origin main
```

---

## Troubleshooting Common Errors

### Merge Conflict
- **Cause:** Conflicting edits on the same line from different sources.
- **Resolution:**
  1. Open the conflicting file.
  2. Find conflict markers:
     ```
     <<<<<<< HEAD
     code from your branch
     =======
     code from other branch
     >>>>>>> branch-name
     ```
  3. Edit to keep the correct code and remove the markers.
  4. Save, stage, and commit:
     ```bash
     git add .
     git commit -m "Resolve merge conflict"
     ```
[More on resolving conflicts](https://docs.github.com/en/get-started/using-git/resolving-merge-conflicts)

### fatal: refusing to merge unrelated histories
- **Cause:** Merging unrelated repositories.
- **Resolution:**
  ```bash
  git pull origin main --allow-unrelated-histories
  ```
[More info](https://stackoverflow.com/questions/37937984/git-refusing-to-merge-unrelated-histories)

### src refspec main does not match any
- **Cause:** Local branch is not named main.
- **Resolution:**
  ```bash
  git branch -M main
  git push -u origin main
  ```
[More info](https://stackoverflow.com/questions/51881838/error-src-refspec-master-does-not-match-any)

### Accidentally Staging Large/Untracked Files
- **Cause:** Staging files before setting up .gitignore.
- **Resolution:**
  ```bash
  git rm -r --cached .
  git add .
  git commit -m "Remove untracked files using .gitignore"
  ```
[About .gitignore](https://git-scm.com/docs/gitignore)
