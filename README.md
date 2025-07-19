# 🚀 Developer Daily Essentials

A modern and minimal guide for initializing Git projects, setting up React with Vite, and configuring Tailwind CSS — everything you use daily.

---

## 📚 Table of Contents

- [🔁 First Time Git Push](#-first-time-git-push)
- [📂 Daily Git Workflow](#-daily-git-workflow)
- [📅 Pull Code into Editor](#-pull-code-into-editor)
- [⚛️ React App with Vite](#⚛️-react-app-with-vite)
- [🎨 Tailwind CSS Installation](#-tailwind-css-installation)

---

## 🔁 First Time Git Push

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

##❌ If you want the copied folder to be fresh, not linked to the old repo:

```bash
rm -rf .git
```

---

## ⚛️ React App with Vite

> For React boilerplate: type `rfce` in your component (requires ES7+ extension)

```bash
npm create vite@latest . -- --template react
```

⚠️ Use the `.` if you're already inside a folder and want to avoid nested folders.

---

## 🎨 Tailwind CSS Installation

### 1. Install Tailwind

```bash
npm install -D tailwindcss@3 postcss autoprefixer
npx tailwindcss init -p
```

### 2. In `tailwind.config.js`

```js
content: [
  "./index.html",
  "./src/**/*.{js,ts,jsx,tsx}",
],
```

### 3. In `index.css`

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

---

Happy Coding! ⚡️\
Feel free to ⭐️ this repo if it helps you streamline your daily setup!

