02/08/26
## 1. Git (Version Control System - VCS)

* Used to track changes in code.
* Helps multiple developers work together.
* Stores different versions of a project.
* Allows rollback to previous versions if needed.

**Example:**

* BGMI v1.1 → Initial version
* BGMI v1.2 → New update
* If v1.2 has bugs, Git can **roll back** to v1.1.

---

## 2. GitHub

* A cloud platform owned by **Microsoft**.
* Used to store Git repositories online.
* Supports collaboration, backup, and code sharing.

**Flow:**

```
Local Repository → git push → GitHub Repository
```

---

## 3. Git Rollback

If the latest version has issues:

```
v1.1 → v1.2 (Bug)
        ↓
    Roll back to v1.1
```

---

## 4. Terraform

**IaC = Infrastructure as Code**

* Used to create cloud infrastructure using code.
* Supports AWS, Azure, GCP, and more.
* Automates infrastructure creation.

**Example:**
Instead of creating an EC2 instance manually, write Terraform code to create it automatically.

---

## 5. Ansible

**Automation Tool**

* Used to automate server configuration and management.
* Agentless (uses SSH).
* Executes tasks on multiple servers.

### Playbook

A Playbook is a YAML file containing a list of tasks.

**Example:**

```
Playbook
   ├── Task 1
   ├── Task 2
   └── Task 3
```

---

## 6. nmcli

`nmcli` = Network Manager Command Line Interface

Used to manage network settings in Linux.

Example command:

```bash
nmcli con mod ipv4.addresses
```

There are **100+ nmcli commands** available for different networking tasks.

---

## 7. Inventory File (Ansible)

Stores the list of target machines.

Contains:

* Hostname
* IP Address

Example:

```ini
[web]
192.168.1.10

[db]
192.168.1.20
```

---

## 8. Network Flow

### Normal Internet

```
Client
   ↓
ISP
   ↓
Destination Server (aws.com)
```

---

### VPN Architecture

```
Client
   ↓
Encryption
   ↓
ISP
   ↓
VPN Server
   ↓
Decryption
   ↓
Destination Server
```

**Benefits of VPN:**

* Encrypts data
* Protects privacy
* Secures communication

---

# Quick One-Line Revision

* **Git** → Version Control System (VCS)
* **GitHub** → Microsoft's cloud platform for Git repositories
* **Push** → Upload local code to GitHub
* **Rollback** → Return to a previous working version
* **Terraform** → Infrastructure as Code (IaC)
* **Ansible** → Automation and configuration management tool
* **Playbook** → YAML file containing automation tasks
* **Inventory File** → List of hostnames/IP addresses
* **nmcli** → Linux network management command-line tool
* **VPN** → Encrypts data before sending it over the internet
ai topic gulo kalke hoyeche, mone rakhar jnno akta notes er moto bania dilam pore jate revise korte paris
