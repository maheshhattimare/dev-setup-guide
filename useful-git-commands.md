# 🔁 First Time Git Push

```bash
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin <your-repo-link>
git push -u origin main
```

---

## 📂 Daily Git Workflow

```bash
git add .
git commit -m "your commit message"
git push origin main
```

---

## 📅 Pull Code into Editor

```bash
git pull origin main --allow-unrelated-histories
```

---

## ❌ If you want the copied folder to be fresh, not linked to the old repo:

```bash
rm -rf .git
```

---


# 🌿 Git Branch Workflow Guide

A universal guide for working with Git branches — from creating a branch to merging and deleting it.

---

## 1️⃣ Create a New Branch

```bash
git checkout -b feature/your-feature-name
```
Example:
```bash
git checkout -b feature/show-birthday-banner
```

---

## 2️⃣ Work on the Branch

Make your code changes and check status:
```bash
git status
```

Stage changes:
```bash
git add .
```

Commit changes:
```bash
git commit -m "Added birthday banner feature"
```

---

## 3️⃣ Push the Branch to Remote

```bash
git push -u origin feature/your-feature-name
```
Example:
```bash
git push -u origin feature/show-birthday-banner
```

---

## 4️⃣ Create a Pull Request (PR)

1. Go to your repository on GitHub.
2. You will see a prompt to create a pull request for the new branch.
3. Review changes and create the PR.

---

## 5️⃣ Merge the Branch

Once reviewed and approved:
```bash
git checkout main
git pull origin main
git merge feature/your-feature-name
git push origin main
```

---

## 6️⃣ Delete the Branch

### Local:
```bash
git branch -d feature/your-feature-name
```

### Remote:
```bash
git push origin --delete feature/your-feature-name
```

---

## 📝 Sample Commit Messages

- `feat: add birthday banner`
- `fix: resolve banner display issue`
- `refactor: clean up banner component code`
- `docs: update README with banner info`
- `style: improve banner UI`

---

## ⚠️ Important Notes

- If you **delete a branch without merging**, your changes will be lost unless they were pushed to remote.
- Always merge your branch before deleting if you want to keep the changes.
- Branch names should be short, descriptive, and use `-` for spaces.

---
