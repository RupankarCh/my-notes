
# Virtualization:
Earlier people used single server for a single service. **A virtual computer system is known as a "virtual machine" (VM)**, a tightly **isolated software container with an operating system and application inside**. Each self-contained VM is completely independent. Putting multiple VMs on a single computer enables several operating systems and applications to run on just one physical server, or "host".

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
