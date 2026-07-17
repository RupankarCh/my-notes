

# Ansible Automation Platform (Containerized)

## What is Ansible?

Ansible is an **open-source IT automation tool** used for:

* Configuration Management
* Application Deployment
* Infrastructure Provisioning
* Orchestration
* Security Automation

Ansible Automation Platform (AAP) is the **enterprise version of Ansible** provided by Red Hat.



# Features

1. **Agentless**

   * No software (agent) needs to be installed on managed nodes.
   * Uses **SSH** for Linux/Unix systems.
   * Uses **WinRM** (Windows Remote Management) for Windows systems.

2. **Infrastructure as Code (IaC)**

   * Infrastructure is managed using code (YAML files), making it version-controlled and repeatable.

3. **Modular**

   * Uses **modules** to perform tasks such as installing packages, copying files, managing services, creating users, etc.
   * Ansible provides thousands of built-in modules.

4. **Push-Based Model**

   * The control node pushes configurations and commands to managed nodes.
   * Managed nodes do not initiate communication.

5. **Idempotent**

   * Running the same playbook multiple times will produce the same result.
   * If a task is already in the desired state, Ansible skips making unnecessary changes.



# Ansible Architecture

## Control Node

* The machine where Ansible is installed.
* Executes playbooks and ad-hoc commands.

## Managed Nodes

* Target servers managed by Ansible.
* Can be Linux, Unix, Windows, or network devices.

Communication:

* Linux → SSH
* Windows → WinRM



# Important Components

## Inventory

Contains the list of managed hosts.

Types of Inventory:

### 1. Static Inventory

* A manually created text file.
* Hostnames or IP addresses are specified by the administrator.

Example:

```ini
[web]
192.168.1.10
192.168.1.11

[db]
192.168.1.20
```

### 2. Dynamic Inventory

* Automatically fetches hosts from cloud providers like:

  * AWS
  * Azure
  * Google Cloud
  * VMware
* Useful when server IP addresses change frequently.


# Inventory Default Groups

1. **all**

   * Contains every host in the inventory.

2. **ungrouped**

   * Hosts that do not belong to any custom group.


# Ansible Modules

A **module** is a reusable unit that performs a specific task.

Examples:

* `ping`
* `copy`
* `yum`
* `dnf`
* `apt`
* `service`
* `user`
* `file`

Modules are executed by tasks.


# Important Terms

### Module

Performs a specific action.

Example:

```yaml
ansible.builtin.copy
```


### Task

A single action performed using a module.

Example:

```yaml
- name: Install Apache
  yum:
    name: httpd
    state: present
```


### Play

A collection of tasks executed on one or more hosts.


### Playbook

A collection of one or more plays written in **YAML**.

Extensions:

* `.yml`
* `.yaml`


# Ad-hoc Commands

Ad-hoc commands are **one-line commands** used for quick, simple tasks without creating a playbook.

### When to use Ad-hoc Commands

Use ad-hoc commands when you want to:

* Check connectivity (`ping`)
* Restart a service
* Copy a single file
* Gather quick information
* Reboot servers
* Execute one-time commands
* Perform quick troubleshooting

Example:

```bash
ansible all -m ping
```

Example:

```bash
ansible web -m service -a "name=httpd state=restarted"
```

**Best suited for:**

* One-time tasks
* Testing
* Quick administration
* Troubleshooting


# Playbooks

Playbooks are YAML files used to automate multiple tasks in a structured and repeatable way.

### When to use Playbooks

Use playbooks when you need to:

* Install software on many servers
* Configure applications
* Provision infrastructure
* Deploy applications
* Configure multiple services
* Automate complete server setup
* Execute tasks in a specific order

Example:

```yaml
---
- name: Install Apache
  hosts: web
  become: true

  tasks:
    - name: Install package
      yum:
        name: httpd
        state: present

    - name: Start service
      service:
        name: httpd
        state: started
```

**Best suited for:**

* Repetitive tasks
* Complex automation
* Production deployments
* Infrastructure as Code
* Version-controlled automation


# Difference Between Ad-hoc Commands and Playbooks

| Ad-hoc Commands       | Playbooks                        |
| --------------------- | -------------------------------- |
| One-time execution    | Reusable automation              |
| Single command        | Multiple tasks                   |
| No YAML file required | Written in YAML                  |
| Quick administration  | Complex automation               |
| Good for testing      | Good for production              |
| Not reusable          | Easily reusable and maintainable |

# YAML Basics

YAML stands for **YAML Ain't Markup Language**.

Rules:

* Uses **spaces** for indentation (do not use tabs).
* Data is written as **key: value** pairs.
* Lists start with a hyphen (`-`).
* Files use `.yml` or `.yaml` extension.

Example:

```yaml
name: Web Server
port: 80
enabled: true
```


# Structure of a Playbook

A playbook generally starts with:

```yaml
---
```

Main (top-level) components:

* `name` → Describes the play
* `hosts` → Target systems
* `become` → Runs tasks with elevated (root/administrator) privileges
* `vars` → Variables
* `tasks` → List of tasks
* `handlers` → Triggered only when notified by tasks

Example:

```yaml
---
- name: Configure Web Server
  hosts: web
  become: true

  tasks:
    - name: Install Apache
      yum:
        name: httpd
        state: present
```

# Return Codes

| Code | Meaning                                            |
| ---- | -------------------------------------------------- |
| 0    | Successful execution                               |
| 1    | General error                                      |
| 2    | One or more hosts failed                           |
| 3    | Some hosts were unreachable                        |
| 4    | Parser or syntax error (varies by command/context) |


