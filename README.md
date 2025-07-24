# 🚀 Developer Daily Essentials

A modern and minimal guide for initializing Git projects, setting up React with Vite, and configuring Tailwind CSS — everything you use daily.

---

## 📚 Table of Contents

- [🔁 First Time Git Push](#-first-time-git-push)
- [📂 Daily Git Workflow](#-daily-git-workflow)
- [📅 Pull Code into Editor](#-pull-code-into-editor)
- [⚛️ React App with Vite](#⚛️-react-app-with-vite)
- [🎨 Tailwind CSS Installation](#-tailwind-css-installation)
- [🌐 Deploying to Render](#-deploying-to-render)

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

## ❌ If you want the copied folder to be fresh, not linked to the old repo:

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
```

```bash
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


## 🚀 Deploying Node.js Backend to Render

Follow this step-by-step guide to deploy your **Node.js backend** (inside the `/backend` folder) to **Render**.

---

## 📁 Project Structure

Make sure your folder structure looks like this:

```
project-root/
│
├── backend/
│   ├── server.js
│   ├── package.json
│   └── ...
│
├── frontend/
│   └── ...
```

---

## ⚙️ package.json Configuration

Inside `backend/package.json`, ensure your scripts look like this:

```json
"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1",
  "start": "node server.js",
  "dev": "nodemon server.js"
}
```

---

## 📤 Push to GitHub

Make sure your code is version controlled and pushed to GitHub:

```bash
git add .
git commit -m "Prepare for Render deployment"
git push origin main
```

---

## 🌐 Deploying to Render

1. Go to [https://render.com](https://render.com) and log in using GitHub
2. Click **"New +" → "Web Service"**
3. Connect your GitHub repository
4. Fill the Render setup form with the following details:

| Setting             | Value                                    |
|---------------------|------------------------------------------|
| **Name**            | `portfolio-backend` *(or anything)*      |
| **Root Directory**  | `backend` ✅ *(very important)*          |
| **Environment**     | `Node`                                   |
| **Build Command**   | `npm install` *(or leave blank)*         |
| **Start Command**   | `npm start`                              |
| **Region**          | Closest to your audience *(e.g., Singapore for India)* |

---

### 🔐 Environment Variables

If you're using a `.env` file locally, make sure to manually add those variables under:

> **Render Dashboard → Your Service → Environment tab**

---

### ✅ Final Step

Click **Create Web Service**. Render will install dependencies and start your backend using `server.js`.

Once deployed, your backend will be live at a Render-provided URL. Test it in your browser or with Postman.

---

### 🌟 Done!

Your backend is now successfully deployed to Render 🎉

---

Happy Coding! ⚡️\
Feel free to ⭐️ this repo if it helps you streamline your daily setup!

