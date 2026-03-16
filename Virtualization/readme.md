
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
  
![Types of Hypervisor](Images/Hypervisor Types.png)
