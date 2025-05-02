
# 🐳 Docker Commands Cheat Sheet

## 📋 Basic Docker Information
```bash
docker --version          # Show installed Docker version
docker info                # Display Docker system-wide info
docker help                # List Docker commands and options
```

---

## 📦 Image Management
```bash
docker pull <image>        # Download an image
docker build -t <name> <path>  # Build an image from a Dockerfile
docker build -f Dockerfile.dev . # Build an image form a specific file
docker images              # List all images
docker rmi <image>         # Remove an image
```

---

## 🚢 Container Management
```bash
docker run <image>         # Run a container from an image
docker run -d <image>      # Run a container in detached mode (background)
docker run -p <host>:<container> <image>  # Map host port to container port
docker ps                  # List running containers
docker ps -a               # List all containers (running and stopped)
docker stop <container>    # Stop a running container
docker start <container>   # Start a stopped container
docker restart <container> # Restart a container
docker rm <container>      # Remove a container
docker exec -it <container> <command>  # Run a command inside a container (interactive)
docker logs <container>    # Fetch logs from a container
```

---

## 🛠️ Volumes and Networks
```bash
docker volume create <volume-name>  # Create a new volume
docker volume ls           # List volumes
docker volume rm <volume-name>  # Remove a volume

docker network create <network-name>  # Create a new network
docker network ls          # List networks
docker network rm <network-name>  # Remove a network
```

---

## 🗂️ Docker Compose Commands
```bash
docker-compose up          # Start services defined in docker-compose.yml
docker-compose up -d       # Start services in detached mode
docker-compose down        # Stop and remove services
docker-compose build       # Build or rebuild services
```

---

## 🧹 Cleanup Commands
```bash
docker system prune        # Remove unused data (containers, networks, images)
docker container prune     # Remove all stopped containers
docker image prune         # Remove unused images
docker volume prune        # Remove unused volumes
```

---

> 🔥 Tip: Add `-f` (`--force`) to prune commands to skip confirmation prompts.
