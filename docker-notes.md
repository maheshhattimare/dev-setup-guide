# 🚀 Docker Notes for Full-Stack Development

---

## 🐳 What is Docker?

Docker is a tool to **package, ship, and run applications** in
lightweight, isolated containers.\
Think of containers like **mini virtual machines** but faster and
lighter.

---

## 🔑 Why Docker?

- Avoids the "works on my machine" problem 🖥️ → 🚫\
- Ensures the **same environment everywhere** (dev, test,
  production).\
- Lets you run services (Node.js, MongoDB, Nginx, etc.) without
  installing them on your host.\
- Easy scaling and deployment with Docker Compose & orchestration
  tools (Kubernetes).

---

## 📚 Important Terms

---

Term Meaning

---

**Image** A snapshot (blueprint) of an
app/environment (e.g., Node.js, MongoDB).

**Container** A running instance of an image (like an
app started from a blueprint).

**Dockerfile** Instructions to build your own image.

**Volume** A way to persist data outside the
container (e.g., MongoDB data).

**Port mapping** Exposing container ports to host
(`-p 3000:3000`).

**-d** Run container in **detached mode**
(background).

**-it** Run container in **interactive mode** with
a terminal.

**docker ps** List running containers.

**docker ps -a** List all containers (including stopped).

**docker exec -it Open shell inside a running container.
`<container>`{=html} bash**

---

---

## ⚡ Command Structure

Always remember the format:

    docker run [OPTIONS] IMAGE [COMMAND] [ARG...]

- OPTIONS = things like `--name`, `-p`, `-e`\
- IMAGE = the base image (`node:18`, `mongo`, `nginx`)\
- COMMAND = what to run inside the container (e.g., `bash`,
  `npm start`)

---

## 🛠️ Core Commands

### 🔹 Images & Containers

```bash
# Pull an image
docker pull <image>

# Run a container (basic)
docker run <image>

# Run interactively with terminal
docker run -it <image> bash

# Run in background with port mapping
docker run -d -p 3000:3000 <image>

# Give a custom name to container
docker run -d --name mycontainer <image>

# List running containers
docker ps

# List all containers (including stopped)
docker ps -a

# Stop a container
docker stop <container_id>

# Start a container
docker start <container_id or name>

# Remove a container
docker rm <container_id>

# Remove an image
docker rmi <image_id>
```

### 🔹 Debugging & Cleanup

```bash
# View logs of a container
docker logs <container_id>

# Inspect container details
docker inspect <container_id>

# Remove unused containers/images/networks
docker system prune -a
```

---

## 📝 Full-Stack Project Workflow with Docker

Imagine a **MERN app** with **frontend, backend, and MongoDB**.

### 1. Create Dockerfile for backend (Node.js)

```dockerfile
# backend/Dockerfile
FROM node:18
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 5000
CMD ["npm", "start"]
```

### 2. Create Dockerfile for frontend (React)

```dockerfile
# frontend/Dockerfile
FROM node:18
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build
# Use nginx to serve React build
FROM nginx:alpine
COPY --from=0 /app/build /usr/share/nginx/html
EXPOSE 80
```

### 3. Docker Compose for all services

```yaml
# docker-compose.yml
version: "3"
services:
  mongo:
    image: mongo
    container_name: mongo
    ports:
      - "27017:27017"
    volumes:
      - mongo_data:/data/db
    environment:
      MONGO_INITDB_ROOT_USERNAME: admin
      MONGO_INITDB_ROOT_PASSWORD: qwerty

  backend:
    build: ./backend
    container_name: backend
    ports:
      - "5000:5000"
    depends_on:
      - mongo

  frontend:
    build: ./frontend
    container_name: frontend
    ports:
      - "3000:80"
    depends_on:
      - backend

volumes:
  mongo_data:
```

### 4. Useful Commands for Full-Stack Dev

```bash
# Start all services (frontend, backend, mongo)
docker compose up -d

# Stop all services
docker compose down

# Rebuild containers after code changes
docker compose up --build -d

# See logs of all services
docker compose logs -f

# Open a shell inside a container
docker exec -it backend bash
```

---

## 📦 Volumes & Data Persistence

Example with MongoDB:

```yaml
volumes:
  mongo_data:
services:
  mongo:
    image: mongo
    volumes:
      - mongo_data:/data/db
```

👉 Even if container is removed, data persists.

---

## 🌐 Networking

- Each Compose project has a default network.
- Containers talk to each other by service name.\
  Example: backend connects to MongoDB using `mongo:27017`.

---

## ☁️ Pushing to Docker Hub

```bash
# Login
docker login

# Tag your image
docker tag backend maheshattimare/backend:v1

# Push to Docker Hub
docker push maheshattimare/backend:v1
```

Later, on another machine:

```bash
docker pull maheshattimare/backend:v1
docker run -p 5000:5000 maheshattimare/backend:v1
```

---

## ✅ Professional Tips

- Always use **.dockerignore** to avoid copying `node_modules`:

      node_modules
      npm-debug.log
      .env

- Use **volumes** for data persistence.\

- Use **multi-stage builds** for production (smaller images).\

- Tag your images with versions (`:v1`, `:v2`) instead of always
  `:latest`.\

- Use `docker logs` for debugging.\

- Prefer `docker compose` (new syntax) over `docker-compose` (old
  binary).

---

🎯 With this workflow, you can run your entire MERN app with just:

```bash
docker compose up -d
```

Welcome to the **real-world developer workflow** 🚀
