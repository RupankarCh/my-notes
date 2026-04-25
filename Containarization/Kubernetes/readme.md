
# KUBERNETES TAKES CARE OF THE ...
- Automatic **deployment of the containerized applications across different servers.**
- Distribution of the **load** across multiple servers
- Auto-**scaling** of the deployed applications
- **Monitoring** and health check of the containers
- **Replacement** of the failed containers

# Supported Container Runtimes:
- Docker
- CRI-O
- Containerd

# PODS
Smalles possible unit in the Kubernetes world:

## PODS Anatomoy:
one or more Containers, Shared Network Resources (Shared Volumes, Shared IP Address etc.)

# Kuberenetes Cluster:
It consists of Nodes, Nodes are servers either bare metal or virtual, Nodes can be located anywhre in the world.

<img width="819" height="536" alt="image" src="https://github.com/user-attachments/assets/939d8355-ccf6-4389-b3f9-296ff6779e56" />

# Kubernetes creates Pods inside different Nodes automatically.
# We create such Nodes and Kubernetes Cluster based on that nodes.

# Master Node features
- distribute tasks to other nodes (e.g., Load Balancing)
- runs only system pods which are responsible for actual work of the Kubernetes cluster in general. 

# Worker Node features
- All pods related to your application are deployed to worker nodes
