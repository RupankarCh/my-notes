
# Virtualization:

Definition:
**Virtualization is the technology that allows a single piece of hardware to run multiple operating systems simultaneously.**

Description
A Virtual Machine (VM) is a complete, **self-contained operating system (OS) and its applications running on top of a hypervisor**. The **hypervisor is a piece of software that creates and runs VMs**, abstracting the underlying hardware.

# Terms
- Host OS: The main OS my machine uses.
- Guest OS: The OS which my VM uses.
- Snapshot: A **saved copy of a system, file, or data at a specific moment in time**, allowing you to restore it later if needed.
- Hypervisor: The software which let us create a VM.
  - Type 1
    - Bare Metal
    - Runs as a Base OS
    - Production
    - E:g VMware esxi, Xen Hypervisor
  - Type 2
    - Runs a software
    - Learn & test
    - E:g Oracle virtualbox. Vmware server
  
![Types of Hypervisor](https://github.com/RupankarCh/my-notes/blob/main/Images/Hypervisor%20Types.png)

# Containers:
A Container is a lightweight, portable, and self-sufficient **executable package that contains everything needed to run a software application**: the code, runtime, libraries, and settings.

- How They Differ from VMs: Unlike VMs, containers share the host machine's OS kernel. They don't have a separate guest OS. This makes them much smaller (megabytes), faster to start, and more resource-efficient.
- The Analogy: Think of a VM as a full-sized house with its own foundation, plumbing, and electricity. A container is a portable apartment that shares the foundation and infrastructure of a large building, making it much easier to move and scale.
- Docker: Docker is the most popular tool for **creating and managing containers**. It has become the de-facto standard in the industry.

## The VM Challenge: 
VMs are great for isolation but have significant overhead. **Each VM requires its own full operating system, which consumes valuable disk space and memory**. Launching a new VM can take several minutes.

## Containerization as the Solution: 
Containers are an OS-level virtualization technology. They don't have a separate operating system for each container. Instead, **they share the host OS kernel and only package the application code and its dependencies (e.g., libraries, configuration files)**. This makes them incredibly **lightweight, portable, and fast to start** (often in seconds). The consistency of a container ensures that an application will run the same way in a development environment, a testing environment, and in production, eliminating the infamous "it works on my machine" problem.

# Vagrant:
A tool used to create and manage reproducible development environments using virtual machines.

* **Vagrant Box**: A pre-built base image of an operating system used by Vagrant to quickly create virtual machines.

* **Vagrantfile**: A configuration file that defines how the Vagrant environment and virtual machine should be set up.

* **Provisioning**: The process of automatically installing software and configuring the VM after it is created.

**Commands**:
vagrant init <vagrant box name> (To initializes the current directory as a Vagrant environment and creates a configuration file called a Vagrantfile.)
vagrant up (To create, configure, and power on a virtual machine (VM) based on the settings specified in the Vagrantfile)
vagrant ssh (To login the VM using the Vagrant user created automatically)

