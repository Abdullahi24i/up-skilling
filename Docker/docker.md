## ✅ Docker Documentation

### 1. What is docker?
  - Platform or ecosystem around creating and running containers.
  - image - single file - contains dependencies to run a programme 
  - container - programme that has it's own isolated set of hardware resources

### 2. Why do we use docker?
  - make it easy to install and run software on any computer without having to worry about setup or installing dependencies 

### 3. How are containers Isolated?
- Name-spacing- isolating resources per process (or group of processes) 
  - Every time time there's a system call to read Hard-Drive, you are directed to segment of hard-drive where the resources you're looking for is, i.e. python v2  
- Control groups- limit the amount of resources used per process - i.e. memory or cpu usage.
### 4. What is a Docker image?

A Docker image is like a blueprint that creates containers. It includes everything needed to run an application:

- Code  
- Libraries  
- Settings  

When you use a Docker image, Docker turns it into a **container**, which is an isolated environment where the application runs independently.

---

### 5. What is a Docker host?

A Docker host is the system where Docker is installed. It acts as the primary environment that runs and manages Docker containers.

Docker hosts can be:

- Local devices  
- Virtual machines  
- Cloud environments

---

### 6. How is a Docker client different from a Docker daemon? Can you share an example?

- **Docker Client**: The command-line tool that sends user commands.
- **Docker Daemon**: The engine that processes those commands.

📌 **Example:**

When you run `docker run`, the client sends the command to the daemon, which then starts the container.

---

### 7. What is Docker networking, and which commands can create bridge and overlay networks?

Docker networking allows containers to communicate with each other and with external systems.

#### ➤ Bridge Network

- Used for container-to-container communication on the **same host**.
- **Command:**
  ```bash
  docker network create -d bridge my-bridge-network
  ```

#### ➤ Overlay Network

- Enables communication between containers on **different Docker hosts** (e.g., in Docker Swarm).
- **Command:**
  ```bash
  docker network create --scope=swarm --attachable -d overlay my-multihost-network
  ```

---

### 8. Explain how Docker bridge networking works.

- Bridge is Docker's default networking mode.
- Containers connected to the bridge can communicate directly via internal IPs.
- If no custom network is specified, Docker assigns containers to the default `bridge` network.

---

### 9. What is a Dockerfile? How do you write one?

A Dockerfile is a script of instructions to build a Docker image. Each command in the file creates a new image layer.

#### Typical Steps:

1. Choose a base image (e.g., `python:3.9`)
2. Set a working directory using `WORKDIR`
3. Copy files using `COPY . .`
4. Install dependencies using `RUN`
5. Expose a port using `EXPOSE`
6. Define the default command using `CMD`

#### 📝 Example:

```Dockerfile
FROM python:3.9

WORKDIR /app

COPY . .

RUN pip install -r requirements.txt

EXPOSE 5000

CMD ["python", "app.py"]
```

---

### 10. What is Docker Compose, and how is it different from a Dockerfile?

**Docker Compose** is a tool for defining and running multi-container Docker apps using a `docker-compose.yml` file.

#### Key Differences:

| Feature        | Dockerfile                      | Docker Compose                         |
|----------------|----------------------------------|----------------------------------------|
| Purpose        | Builds a single Docker image     | Orchestrates multiple containers        |
| Format         | Uses Dockerfile syntax           | Uses YAML (`.yml`)                     |
| Scope          | Single container                | Multi-container applications           |

#### 📝 Example `docker-compose.yml`:

```yaml
version: '3.9'
services:
  web:
    build: .
    ports:
      - "5000:5000"
    depends_on:
      - db
  db:
    image: postgres
    volumes:
      - db-data:/var/lib/postgresql/data

volumes:
  db-data:
```

---

### 11. Why do we use volumes in Docker?

Docker volumes help persist data outside of containers. They are:

- Safer: Data survives container removal
- Shareable: Used by multiple containers
- Easier to manage and back up

**Use case examples:**

- Persisting database files
- Sharing configuration between services

---
