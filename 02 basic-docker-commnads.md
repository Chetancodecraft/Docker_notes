# Section 3.1: Basic Docker Commands

Docker provides a rich set of commands to manage **containers**, **images**, **networks**, and **volumes**. This section covers the **most commonly used basic commands** with explanations, examples, and notes.

---

## 🔹 1. Check Running Containers
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

## 🔹 2. List Docker Images
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
- **Note:** Each image has a **repository name**, **tag**, and **unique ID**.

---

## 🔹 3. Remove Containers
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

## 🔹 4. Remove Images
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
- **Force remove (if container exists):**
  ```bash
  docker rmi -f <image_id>
  ```

---

## 🔹 5. Start & Stop Containers
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

## 🔹 6. Execute Commands Inside Container
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

## 🔹 7. View Logs of a Container
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

## 📌 Summary Cheat Sheet
| Command             | Description                           | Example |
|---------------------|---------------------------------------|---------|
| `docker ps`         | List running containers              | `docker ps` |
| `docker ps -a`      | List all containers                  | `docker ps -a` |
| `docker images`     | List all images                      | `docker images` |
| `docker rm`         | Remove stopped container             | `docker rm my_container` |
| `docker rmi`        | Remove image                         | `docker rmi ubuntu:latest` |
| `docker start`      | Start a stopped container            | `docker start my_container` |
| `docker stop`       | Stop a running container             | `docker stop my_container` |
| `docker exec`       | Run command inside a container       | `docker exec -it my_container /bin/bash` |
| `docker logs`       | View container logs                  | `docker logs my_container` |

---
