# 🚀 Docker Introduction


## 2.1 What is a Container?

A container is a **standard unit of software** that packages up code and all its dependencies so the application runs reliably from one computing environment to another.

* **Simple definition:** A container is a bundle of your application, required libraries, and minimal system dependencies.
* **Technical definition:** A Docker container image is a **lightweight, standalone, executable package** of software that includes everything needed to run an application: code, runtime, system tools, system libraries, and settings.

Containers solve the classic problem: "It works on my machine!" by providing consistent behavior across different environments.

---

## 2.2 Containers vs Virtual Machines (VMs)

Containers and VMs are both used to isolate applications, but they have important differences:

| Feature              | Containers 🐳                                 | Virtual Machines 💻                           |
| -------------------- | --------------------------------------------- | --------------------------------------------- |
| Resource Utilization | Share host OS kernel → lightweight & fast     | Full OS + hypervisor → heavy & slower         |
| Portability          | Can run on any system with compatible host OS | Less portable, needs hypervisor compatibility |
| Security             | Less isolation, shares host OS                | Strong isolation, each VM has its own OS      |
| Management           | Easier to create, destroy, and move           | Heavier to manage                             |
| Size                 | MBs (Ubuntu base \~22 MB)                     | GBs (Ubuntu VM \~2.3 GB)                      |
| Startup Time         | Seconds                                       | Minutes                                       |

**Visual Comparison:**
![Containers vs VMs](https://user-images.githubusercontent.com/43399466/217262726-7cabcb5b-074d-45cc-950e-84f7119e7162.png)

👉 **Conclusion:** Containers are lighter, faster, and portable, whereas VMs are more isolated and secure.

---

## 2.3 Why are Containers Lightweight?

* Containers use **OS-level virtualization** instead of full hardware virtualization.
* They **share the host OS kernel** and only package necessary libraries and binaries.
* **Example:**

  * Ubuntu container base image → \~22 MB
  * Ubuntu VM image → \~2.3 GB
* This means containers are **\~100 times smaller** than VM images.
* Minimalism is the key: containers only include what is required for the app to run.

---

## 2.4 Files/Folders in Containers vs Host OS

**Inside container base images:**

* `/bin` → common executables like ls, cp, ps
* `/sbin` → system executables like init, shutdown
* `/etc` → configuration files
* `/lib` → library files for executables
* `/usr` → applications, documentation, libraries
* `/var` → variable data like logs and temp files
* `/root` → root user home directory

**Resources from the host OS:**

* **File system:** Accessed via bind mounts for reading/writing files
* **Networking stack:** Shared for connectivity
* **System calls:** Handled by host kernel for CPU, memory, I/O
* **Namespaces:** Isolate resources like process IDs, file systems, and networks
* **Cgroups:** Limit resources like CPU, memory, I/O

Containers remain isolated while efficiently using host resources.

---

## 2.5 What is Docker?

* Docker is a **containerization platform** that implements the concept of containers.
* Provides tools to **build images, run containers, and share them** on registries.
* Components include:

  * Docker Engine (core runtime)
  * Docker CLI (commands like `docker run`)
  * Docker Hub (image registry)
  * Docker Compose, Swarm, Kubernetes integration

**Docker Overview Diagram:**
![Docker Overview](https://user-images.githubusercontent.com/43399466/217507877-212d3a60-143a-4a1d-ab79-4bb615cb4622.png)

---

## 2.6 Docker Architecture

* **Docker Daemon (dockerd):** Manages containers, images, networks, and volumes; listens for Docker API requests.
* **Docker Client (docker CLI):** User interface to interact with daemon via commands.
* **Docker Registries:** Store and distribute Docker images (public Docker Hub or private registry).
* **Docker Objects:** Images, containers, networks, volumes.

**Architecture Diagram:**
![Docker Architecture](https://user-images.githubusercontent.com/43399466/217511949-81f897b2-70ee-41d1-b229-38d0572c54c7.png)

---

## 2.7 Docker Lifecycle

1. **docker build** → Create an image from Dockerfile
2. **docker run** → Run a container from the image
3. **docker push** → Push the image to a registry (public/private)

Each step ensures containers can be **built, executed, and shared consistently**.

---

## 2.8 Installing Docker (Ubuntu)

```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl enable docker --now
```

### Verify installation:

```bash
docker run hello-world
```

### Common Issues:

* **Permission Denied:** Add your user to Docker group:

```bash
sudo usermod -aG docker $USER
```

* **Daemon not running:** Start it with:

```bash
sudo systemctl start docker
```

---

## 2.9 Hands-on: Your First Docker Image & Container

```bash
# Clone example repo
git clone https://github.com/iam-veeramalla/Docker-Zero-to-Hero
cd examples

# Build your first Docker image (replace username)
docker build -t username/my-first-docker-image:latest .

# Verify images
docker images

# Run the container
docker run -it username/my-first-docker-image
```

Output: `Hello World`

---

## 2.10 Push Image to Docker Hub

```bash
# Login to Docker Hub
docker login

# Tag image
docker tag username/my-first-docker-image:latest username/my-first-docker-image:latest

# Push image
docker push username/my-first-docker-image:latest
```

✅ You now have a **full, detailed Docker introduction** with theory, examples, images, and hands-on commands.
