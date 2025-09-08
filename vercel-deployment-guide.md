# 🚀 Vercel Deployment Guide (Frontend + Backend)

This guide explains how to deploy your **full-stack app (frontend + backend)** on **Vercel**.

---

## 📂 Project Structure
```
project-root/
├── backend/
│   ├── server.js
│   ├── package.json
│   └── vercel.json
├── frontend/
│   ├── index.html
│   ├── package.json
│   └── vercel.json
└── README-VERCEL.md
```

---

## ⚙️ Backend Setup (`backend/vercel.json`)
```json
{
  "version": 2,
  "builds": [
    {
      "src": "./server.js",
      "use": "@vercel/node"
    }
  ],
  "routes": [
    {
      "src": "/(.*)",
      "dest": "/",
      "methods": ["GET", "POST", "PUT", "DELETE", "OPTIONS"]
    }
  ]
}
```
- This tells Vercel to run your backend using `server.js` as the entry point.  
- Supports all HTTP methods (GET, POST, PUT, DELETE, OPTIONS).  

---

## ⚙️ Frontend Setup (`frontend/vercel.json`)
```json
{
  "rewrites": [{ "source": "/(.*)", "destination": "/" }]
}
```
- Fixes React Router / SPA routing issues.  
- Ensures that refreshing on any route still loads `index.html`.  

---

## 🖼️ Add Script in `frontend/index.html`
Insert this before `</body>` tag:
```html
<script type="text/javascript">
  (function (l) {
    if (l.search[1] === "/") {
      var decoded = l.search
        .slice(1)
        .split("&")
        .map(function (s) {
          return s.replace(/~and~/g, "&");
        })
        .join("?");
      window.history.replaceState(
        null,
        null,
        l.pathname.slice(0, -1) + decoded + l.hash
      );
    }
  })(window.location);
</script>
```
- This script solves URL issues when using client-side routing with Vercel.  

---

## 🚀 Deployment Steps
1. Push your repo to GitHub.  
2. Go to [Vercel](https://vercel.com/).  
3. Import your GitHub repo.  
4. Configure projects:  
   - **Frontend → set root directory to `frontend`**  
   - **Backend → set root directory to `backend`**  
5. Deploy both services separately.  

---

## ✅ Notes
- Make sure your backend has a proper `start` script in `backend/package.json`:  
  ```json
  "scripts": {
    "start": "node server.js"
  }
  ```
- Environment variables can be set from Vercel dashboard.  
- Use separate projects for **frontend** and **backend** on Vercel.  

---

🎉 Now your full-stack project will work perfectly on Vercel with routing & backend support.
