
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
Creates Kubernetes cluster with single node and that node will work like both the worker node and master node.

