
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

# Vagrant:
A tool used to create and manage reproducible development environments using virtual machines.

* **Vagrant Box**: A pre-built base image of an operating system used by Vagrant to quickly create virtual machines.

* **Vagrantfile**: A configuration file that defines how the Vagrant environment and virtual machine should be set up.

* **Provisioning**: The process of automatically installing software and configuring the VM after it is created.

**Commands**:
vagrant init <vagrant box name> (To initializes the current directory as a Vagrant environment and creates a configuration file called a Vagrantfile.)
vagrant up (To create, configure, and power on a virtual machine (VM) based on the settings specified in the Vagrantfile)
vagrant ssh (To login the VM using the Vagrant user created automatically)

# Orchestration: 
Manage and control many containers, e.g., Kubernetes is Orchastration tool, Kubernetes (often used with Docker containers) → uses .yaml files for deployments, services, etc.
