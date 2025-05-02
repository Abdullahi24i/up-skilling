# 📦 Docker Volumes: Notes & Examples

Docker volumes are used to persist data and share files between the host and containers, or between multiple containers.

---

## 🔸 Types of Docker Volume Bindings

### 1. **Named Volumes**
Managed by Docker. Good for persistent, isolated data (e.g., databases).

```bash
# Create and run a container with a named volume
docker run -v myvolume:/data busybox

# Inspect volumes
docker volume ls
docker volume inspect myvolume
```

**Dockerfile example:**
```Dockerfile
VOLUME ["/data"]
```

---

### 2. **Bind Mounts**
Mounts a specific directory or file from the host into the container.

```bash
# Mount the current host directory into the container
docker run -v $(pwd):/app my-image

# Mount only specific file
docker run -v $(pwd)/config.json:/app/config.json my-image
```

---

## 🔹 Syntax Summary

```bash
-v <host_path>:<container_path>         # Bind mount
-v <volume_name>:<container_path>       # Named volume
```

---

## 📌 Use Cases & Examples

### Example 1: Mount host code into container

```bash
docker run -it \
  -v $(pwd):/app \
  -w /app \
  node:18 \
  npm install
```

### Example 2: Avoid overwriting node_modules
- essentially telling docker to ignore node-modules and don't try reference it. useful for when you have deleted that file.
```bash
docker run -it \
  -v $(pwd):/app \
  -v /app/node_modules \
  -p 3000:3000 \
  app-image
```

*This avoids overwriting `node_modules` inside the container with an empty host directory.*

---

## 🧹 Volume Cleanup

```bash
# Remove unused volumes
docker volume prune

# Remove specific volume
docker volume rm myvolume
```

---

## 🔄 Docker Compose Volume Example

```yaml
services:
  web:
    image: my-web-app
    volumes:
      - .:/app
      - /app/node_modules
```

---

## 🛠️ Debugging Tips

- Use `ls` in both host and container to check file presence.
- Start the container without mounting (`-v`) to see the original image files.
- Use `docker inspect <container>` to view mount bindings.
