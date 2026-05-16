
# KUBERNETES TAKES CARE OF THE ...
- Automatic **deployment of the containerized applications across different servers.**
- Distribution of the **load** across multiple servers, It can also create container.
- Auto-**scaling** of the deployed applications.
- **Monitoring** and health check of the containers.
- **Replacement** of the failed containers.
- **Self-healing** automatically restarts failed containers, reschedules crashed pods, replaces unhealthy instances, and maintains the desired state via health checks/controllers.
- **rolling updates** gradually replaces old pod versions with new ones while keeping the application available and enabling easy rollback if issues occur.

# Kubernetes Behaviour
Kubernetes uses layered controllers, a **Deployment defines the desired app version/state**, it creates and manages a ReplicaSet, and the **ReplicaSet ensures the required number of Pods are always running**. So You don't manage pods deployment does. You usually manage Pods indirectly through a Deployment, and the **Deployment automatically creates, replaces, scales, and updates Pods for you instead of managing Pods manually.**

# Supported Container Runtimes:
- Docker
- CRI-O
- Containerd

# Terms:
- **Control Plane** – The brain of Kubernetes; **makes scheduling and cluster management decisions**.
- **Deployment** – **Manages app updates, scaling, and desired number of Pods**.
- **Service** – Provides stable **networking/load balancing** so Pods can be reached.
- **Pod** – **Smallest deployable unit**; runs one or more containers for your app.
- **Node** – Worker machine (VM or physical server) **where Pods run**.
- **Cluster** – **Entire Kubernetes environment**: Control Plane + worker Nodes.

# PODS
Smalles possible unit in the Kubernetes world:

## PODS Anatomoy:
one or more Containers, Shared Network Resources (Shared Volumes, Shared IP Address etc.)

# Kuberenetes Cluster:
It consists of Nodes, Nodes are servers either bare metal or virtual, Nodes can be located anywhre in the world.

<img width="819" height="536" alt="image" src="https://github.com/user-attachments/assets/939d8355-ccf6-4389-b3f9-296ff6779e56" />

# Kubernetes creates Pods inside different Nodes automatically.
# We create such Nodes and Kubernetes Cluster based on that nodes.

# Master Node Features 
- distribute tasks to other nodes (e.g., Load Balancing)
- runs only system pods which are responsible for actual work of the Kubernetes cluster in general. 

# Worker Node Features 
- All pods related to your application are deployed to worker nodes

# Node Anatomy

# Services running on Nodes
- **kebelet** services on each Worker Node communicates with API Server on the Master Node (Master Node, Worker Node)
- **Kube-Proxy** is responsible for network communication inside of each nodes and each node (Master Node, Worker Node)
- **Scheduler** is responsible for planning and distribution of load between different nodes in the cluster. (Master Node)
- **API Server** helps to establish communication between Nodes (Master Node)
- **Kube Controller Manager** controlls everything in the Kubernetes cluster on each Nodes.
- **Cloud Controller Manager** helps to interact with cloud service provider where you run your kubernetes cluster.
- **etcd** stores all logs related to operation of entire cluster as key value pairs.
- **DNS** provides name resolution in the entire kubernetes cluster.

## Command Line Tools
- kubectl/kubecontrol allows you to connect to a specific kubernetes cluster and manage it remotely (It uses REST API to connect to master node using HTTPS 

# Minikube 
Minikube automates cration of local Kubernetes cluster with single node and that node will work like both the worker node and master node.

## Docker vs Virtualization Technologies for using Minikube
Minikube creates a local Kubernetes cluster, but the driver decides where that cluster runs: **Docker runs nodes as containers**, while **VMware/VirtualBox run nodes as full virtual machines.** Docker driver = **lighter, faster, lower resource usage**; VM drivers = **heavier, slower, but stronger isolation** and more full-OS-like environment.

# kubectl
The Kubernetes CLI tool used to communicate with the cluster’s API server to deploy apps, inspect resources, scale workloads, and manage the cluster.**manage and interact with any Kubernetes cluster**.
