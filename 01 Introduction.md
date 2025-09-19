# 🚀 Docker Introduction

## 1. What is a Container?

* **Simple Definition:** A container is a lightweight, standalone package that contains everything needed to run an application (code, runtime, system tools, libraries).
* **Technical Definition:** Containers use OS-level virtualization to share the host system’s kernel, isolating applications into separate environments while remaining more efficient than virtual machines.

---

## 2. Containers vs Virtual Machines

| Feature       | Containers 🐳         | Virtual Machines 💻       |
| ------------- | --------------------- | ------------------------- |
| OS Kernel     | Shared with host      | Each VM has its own       |
| Size          | MBs                   | GBs                       |
| Startup Speed | Seconds               | Minutes                   |
| Performance   | Near-native           | Slower (overhead)         |
| Use Case      | Microservices, DevOps | Legacy apps, OS isolation |

📌 Visual Comparison:
![Containers vs VMs](https://user-images.githubusercontent.com/43399466/217262726-7cabcb5b-074d-45cc-950e-84f7119e7162.png)

---

## 3. Why are Containers Lightweight?

* Containers don’t bundle an entire OS; they reuse the host OS kernel.
* Example: An Ubuntu container doesn’t need the whole Ubuntu OS, just required binaries and libraries.

---

## 4. Files/Folders in Containers vs Host OS

* Containers have their own **root filesystem** (isolated from the host).
* But they **share the host kernel**.
* This means multiple containers can run different apps without interfering with each other.

---

## 5. What is Docker?

* **Concept:** A platform to build, run, and ship applications in containers.
* **Implementation:** Docker provides tooling and a runtime to manage containers easily.

📌 Docker Overview:
![Docker Overview](https://user-images.githubusercontent.com/43399466/217507877-212d3a60-143a-4a1d-ab79-4bb615cb4622.png)

---

## 6. Docker Architecture

* **Docker Daemon (dockerd):** Runs on the host, manages containers and images.
* **Docker Client (CLI):** Interface to interact with Docker.
* **Docker Registries:** Stores Docker images (public like Docker Hub, or private).
* **Docker Objects:** Images, containers, networks, volumes.

📌 Architecture Diagram:
![Docker Architecture](https://user-images.githubusercontent.com/43399466/217511949-81f897b2-70ee-41d1-b229-38d0572c54c7.png)

---

## 7. Docker Lifecycle (build → run → push)

1. **Build** an image from a Dockerfile

   ```bash
   docker build -t myapp:1.0 .
   ```
2. **Run** a container from the image

   ```bash
   docker run -d -p 8080:80 myapp:1.0
   ```
3. **Push** the image to Docker Hub

   ```bash
   docker push username/myapp:1.0
   ```

---

## 8. Installing Docker

### On Ubuntu:

```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl enable docker --now
```

### Troubleshooting:

* If daemon not running → `sudo systemctl start docker`
* For non-root usage → `sudo usermod -aG docker $USER`

---

## 9. Hands-on: Your First Docker Image & Container

1. Create a simple `Dockerfile`:

   ```dockerfile
   FROM alpine:latest
   CMD ["echo", "Hello, Docker!"]
   ```
2. Build the image:

   ```bash
   docker build -t hello-docker .
   ```
3. Run the container:

   ```bash
   docker run hello-docker
   ```

---

## 10. Pushing Image to Docker Hub

1. Log in:

   ```bash
   docker login
   ```
2. Tag the image:

   ```bash
   docker tag hello-docker username/hello-docker:1.0
   ```
3. Push the image:

   ```bash
   docker push username/hello-docker:1.0
   ```

---

✅ You now have a complete **Docker Introduction** with theory, visuals, and practical examples.
