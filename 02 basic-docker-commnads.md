# Section 3.1: Basic Docker Commands

Docker provides a rich set of commands to manage **containers**, **images**, **networks**, and **volumes**. This section covers the **most commonly used basic commands** with explanations, examples, and notes.

---

## 🔹 1. Run a Container
### `docker run`
- **Purpose:** Creates and starts a new container from an image.
- **Syntax:**
  ```bash
  docker run [options] <image> [command]
  ```
- **Example:** Run an Ubuntu container with interactive shell:
  ```bash
  docker run -it ubuntu /bin/bash
  ```
- **Detached mode:**
  ```bash
  docker run -d nginx
  ```

---

## 🔹 2. Check Running Containers
### `docker ps`
- **Purpose:** Lists all running containers.
- **Syntax:**
  ```bash
  docker ps
  ```
- **Example Output:**
  ```
  CONTAINER ID   IMAGE        COMMAND       STATUS        PORTS   NAMES
  e5c123abc456   ubuntu       "/bin/bash"   Up 2 minutes          my_container
  ```
- **Tip:** To see **all containers** (running + stopped):
  ```bash
  docker ps -a
  ```

---

## 🔹 3. List Docker Images
### `docker images`
- **Purpose:** Displays all images downloaded or built on your system.
- **Syntax:**
  ```bash
  docker images
  ```
- **Example Output:**
  ```
  REPOSITORY      TAG       IMAGE ID       CREATED        SIZE
  ubuntu          latest    1318b700e415   2 weeks ago    72.8MB
  hello-world     latest    feb5d9fea6a5   16 months ago  13.3kB
  ```

---

## 🔹 4. Download an Image
### `docker pull`
- **Purpose:** Pulls an image from Docker Hub or another registry.
- **Syntax:**
  ```bash
  docker pull <image>:<tag>
  ```
- **Example:**
  ```bash
  docker pull nginx:latest
  ```

---

## 🔹 5. Remove Containers
### `docker rm`
- **Purpose:** Removes stopped containers.
- **Syntax:**
  ```bash
  docker rm <container_id or name>
  ```
- **Example:**
  ```bash
  docker rm e5c123abc456
  ```
- **Remove multiple containers:**
  ```bash
  docker rm container1 container2
  ```

---

## 🔹 6. Remove Images
### `docker rmi`
- **Purpose:** Deletes an image from the system.
- **Syntax:**
  ```bash
  docker rmi <image_id or name>
  ```
- **Example:**
  ```bash
  docker rmi ubuntu:latest
  ```

---

## 🔹 7. Start & Stop Containers
### `docker start`
- **Purpose:** Starts a stopped container.
- **Example:**
  ```bash
  docker start my_container
  ```

### `docker stop`
- **Purpose:** Gracefully stops a running container.
- **Example:**
  ```bash
  docker stop my_container
  ```

---

## 🔹 8. Execute Commands Inside Container
### `docker exec`
- **Purpose:** Runs a command inside a running container.
- **Example:** Open interactive shell in container:
  ```bash
  docker exec -it my_container /bin/bash
  ```
- **Example:** Run a simple command:
  ```bash
  docker exec my_container ls /app
  ```

---

## 🔹 9. View Logs of a Container
### `docker logs`
- **Purpose:** Displays logs produced by a container.
- **Syntax:**
  ```bash
  docker logs <container_name>
  ```
- **Example:**
  ```bash
  docker logs my_container
  ```
- **Follow live logs:**
  ```bash
  docker logs -f my_container
  ```

---

## 🔹 10. Inspect Container or Image
### `docker inspect`
- **Purpose:** Shows detailed configuration (in JSON format).
- **Example:**
  ```bash
  docker inspect my_container
  ```

---

## 🔹 11. Show Running Processes in Container
### `docker top`
- **Purpose:** Displays active processes inside a container.
- **Example:**
  ```bash
  docker top my_container
  ```

---

## 🔹 12. Monitor Resource Usage
### `docker stats`
- **Purpose:** Shows live CPU, memory, and I/O usage of containers.
- **Example:**
  ```bash
  docker stats
  ```

---

## 🔹 13. Copy Files Between Host and Container
### `docker cp`
- **Purpose:** Copies files between host system and container.
- **Examples:**
  - Copy from container to host:
    ```bash
    docker cp my_container:/app/file.txt ./file.txt
    ```
  - Copy from host to container:
    ```bash
    docker cp ./config.json my_container:/app/config.json
    ```

---

## 🔹 14. Rename a Container
### `docker rename`
- **Purpose:** Renames a container for easier reference.
- **Example:**
  ```bash
  docker rename old_name new_name
  ```

---

## 🔹 15. Clean Up Unused Data
### `docker system prune`
- **Purpose:** Removes all unused containers, networks, and images.
- **Syntax:**
  ```bash
  docker system prune
  ```
- **Remove everything (caution!):**
  ```bash
  docker system prune -a
  ```

---

## 📌 Summary Cheat Sheet
| Command                 | Description                           | Example |
|-------------------------|---------------------------------------|---------|
| `docker run`            | Create & start a new container       | `docker run -it ubuntu /bin/bash` |
| `docker ps`             | List running containers              | `docker ps` |
| `docker ps -a`          | List all containers                  | `docker ps -a` |
| `docker images`         | List all images                      | `docker images` |
| `docker pull`           | Download image from registry         | `docker pull nginx:latest` |
| `docker rm`             | Remove stopped container             | `docker rm my_container` |
| `docker rmi`            | Remove image                         | `docker rmi ubuntu:latest` |
| `docker start`          | Start a stopped container            | `docker start my_container` |
| `docker stop`           | Stop a running container             | `docker stop my_container` |
| `docker exec`           | Run command inside container         | `docker exec -it my_container /bin/bash` |
| `docker logs`           | View container logs                  | `docker logs my_container` |
| `docker inspect`        | Detailed info on container/image     | `docker inspect my_container` |
| `docker top`            | Show processes inside container      | `docker top my_container` |
| `docker stats`          | Live container resource usage        | `docker stats` |
| `docker cp`             | Copy files between host and container| `docker cp my_container:/app/file.txt ./` |
| `docker rename`         | Rename a container                   | `docker rename old new` |
| `docker system prune`   | Clean up unused Docker data          | `docker system prune -a` |

---
