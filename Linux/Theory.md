# Intro
Linux is an open source software.Based on unix and initially developed by Linus Torvalds in 1991. When people say "**Linux", they often mean** a system that combines:
- **The Linux kernel (developed by Linus Torvalds)**
- **GNU software (shell, compiler, tools, etc.)**
In 2005 the source code for Linux was managed under a version control system Bitkeeper. Linus Torvalds created Git to manage the Linux kernel development. The community needed a new tool after losing their free access to BitKeeper, a proprietary version control system.
- Everything is a file (Including Hardware, Configuration data etc.)
- Small Single purpose Programs creates the Ability to chain programs together and perform complex operations.
- Avoid Captive User Interface (avoid GUI)

**Linux Distributions:**
A Linux distribution comprises the **Linux kernel**, which is the core of the operating system, and packages that make up all the commands you can run on the system. but the **format, type, and number of packages differ** quite a bit. 

| Distribution                        | Base Distribution         | Package Manager        | Package Format |
| ----------------------------------- | ------------------------- | ---------------------- | -------------- |
| **Ubuntu**                          | **Debian-based**          | `apt`                  | `.deb`         |
| **RHEL (Red Hat Enterprise Linux)** | **Red Hat/Fedora family** | `dnf` (formerly `yum`) | `.rpm`         |
| **CentOS**                          | **Red Hat/Fedora family** | `dnf` (formerly `yum`) | `.rpm`         |
| **Kali Linux**                      | **Debian-based**          | `apt`                  | `.deb`         |


**Knowledge about various distributions of Linux:**
- **Debian** (Ian Murdock and his wife Debra): **non-commercial** project, maintains an ideological commitment to community development and open access, Each release version is labled with Oldstable, Stable, Testing, Unstable (Sid) and it changes as each version gets polished day by day so three releases are maintained simultaneously. stable, targeting production servers; unstable, with current packages that may have bugs and security vulnerabilities; and testing, which is somewhere in between.
- **Ubuntu**: **Based on Debian**, The business behind Ubuntu is Canonical Ltd., founded by entrepreneur Mark Shuttleworth. Offers a variety of editions targeting the cloud, the desktop, bare metal, phones and tablets also. Ubuntu **version numbers derive from the year and month of release**, so version 16.10 is from October, 2016. Each release also has an alternative code name such as Vivid Vervet or Wily Werewolf. **Two versions of Ubuntu are released annually: one in April and one in October**. The April releases in even-numbered years are **long-term support (LTS) editions that promise five years of maintenance updates**. These are the releases recommended for production use.
- **RHEL**: **Based on Fedora**,  RHEL targets **production environments at large enterprises** that require support and consulting services to keep their systems running smoothly. Somewhat paradoxically, **RHEL is open source but requires a license**. If you’re not willing to pay for the license, you’re not going to be running Red Hat. Red Hat also sponsors Fedora, a community-based distribution that serves as an incubator for bleeding-edge software not considered stable enough for RHEL.**Fedora is used as the initial test bed for software and configurations that later find their way to RHEL.**
- **CentOS**: **Based on Fedora**, Virtually **identical to RHEL but free of charge**, except Red Hat's branding and a few proprietary tools, CentOS is an excellent choice for sites that want to deploy a production-oriented distribution. A hybrid approach is also feasible. **Oracle sells a rebranded and customized version of CentOS** to customers of its enterprise database software. **Amazon Linux was initially derived from CentOS** and still shares many of its conventions.

# Term
**Open Source software: is software with source code that anyone can inspect, modify. and enhance.**

# Linux Booting Process:
Power On> CPU (**CPU is hard-wired to start executing instructions from a fixed address** called reset vector **which maps to firmware(BIOS/UEFI) stored in a non-volatile memory like (ROM or Flash memory)**)> **BIOS/UEFI performs POST**, **looks for a bootable device**(SSD/HDD/Pendrive) **once found BIOS will enter the MBR** and **UEFI will enter the ESP** section of the bootable device, **BOOTLOADER executes GRUB** then it reads GRUB config and shows an GUI to the user to **select the OS or kernel**, once the kernel is selected, GRUB locates the kernel binary and **initrd/initramfs(temporary file system) image detects hardware and loads required modules from its temporary filesystem**. Once all required drivers are loaded, the **initramfs mounts the actual root filesystem**. After that, the **temporary filesystem (initramfs) is discarded/unmounted**. **Kernel sets up the environment and launches the first process, typically init or systemd**, which then continues to start all other user-space services. **Init/systemd reads configuration files (e.g., /etc/inittab or systemd unit files) to determine the default runlevel/target.  Runlevel/Target start services and daemons according to the desired system state**. 

**firmware**-a special type of **program stored on the motherboard**, manufacturer does it.

**MBR**-first sector of BIOS bootable device 512Bytes The **MBR contains machine code instructions that help boot the machine**. It consists of 3 sections BOOTLOADER, PARTITION TABLE, BOOT SIGNATURE.

**Bootloader code**: 446 bytes — a small program that acts as the first-stage bootloader, **responsible for loading the second-stage bootloader (such as GRUB)**

**Partition table**: 64 bytes — partition table **tells the bootloader and OS where the partitions are located** on the disk.

**Boot signature**: 2 bytes — serves as a marker to **indicate that the sector contains a valid MBR**.

**ESP-EFI System Partition**, It is a special partition on a GPT-formatted disk used by UEFI firmware.100-500 MB UEFI directly loads an .efi executable (e.g., bootx64.efi or grubx64.efi).

**GRUB2** is the modern, modular, UEFI-compatible version of GRUB with better filesystem support, scripting, and graphical features. It's config files /boot/grub2/grub.cfg (BIOS) /boot/efi/EFl/<distro>/grub.cfg (UEFI)The user sees a text-based or graphical menu listing the OSes/kernels configured to boot.

**Initramfs (Initial RAM File System)** is a small, **temporary filesystem loaded into your computer's RAM during startup. It contains the essential drivers and tools the Linux kernel needs to find and mount your main, permanent filesystem** (the one on your hard drive or SSD e). Once the real filesystem is running, the initramfs is cleared from memory, having completed its mission.

**The Linux kernel** is the core program of the operating system that controls all the computer's hardware and allows software to run.

**SystemD** is the first user-space process, always started with **PID 1** by the kernel to bring the system to usable state. It **initializes all required services and targets according to its configuration**. The default target is usually a symlink: /etc/systemd/system/default.target 
