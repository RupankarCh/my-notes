
# Virtualization:

Definition:
Virtualization is the **technology that allows a single piece of hardware to run multiple operating systems simultaneously**.

Description
A Virtual Machine (VM) is a complete, **self-contained operating system (OS) and its applications running on top of a hypervisor**. The **hypervisor is a piece of software that creates and runs VMs, abstracting the underlying hardware.**

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
