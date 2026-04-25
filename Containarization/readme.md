# Containers:
A Container is a lightweight, portable, and self-sufficient **executable package that contains everything needed to run a software application**: the code, runtime, libraries, and settings.

- How They Differ from VMs: Unlike VMs, containers share the host machine's OS kernel. They don't have a separate guest OS. This makes them much smaller (megabytes), faster to start, and more resource-efficient.
- The Analogy: Think of a VM as a full-sized house with its own foundation, plumbing, and electricity. A container is a portable apartment that shares the foundation and infrastructure of a large building, making it much easier to move and scale.
- Docker: Docker is the most popular tool for **creating and managing containers**. It has become the de-facto standard in the industry.

## The VM Challenge: 
VMs are great for isolation but have significant overhead. **Each VM requires its own full operating system, which consumes valuable disk space and memory**. Launching a new VM can take several minutes.

## Containerization as the Solution: 
Containers are an OS-level virtualization technology. They don't have a separate operating system for each container. Instead, **they share the host OS kernel and only package the application code and its dependencies (e.g., libraries, configuration files)**. This makes them incredibly **lightweight, portable, and fast to start** (often in seconds). The consistency of a container ensures that an application will run the same way in a development environment, a testing environment, and in production, eliminating the infamous "it works on my machine" problem.

# Container Runtime: 
The software that actually runs containers on a computer or server.

## Workings:
1. Unpacks the container image (gets the app files ready)
2. Creates an isolated environment (So the app thinks it has its own mini-computer)
3. Limits resources (Example: only 1GB RAM, only 1 CPU core)
4. Starts the app process (Keeps it separate from other apps)
