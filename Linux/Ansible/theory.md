# Automation:
**What is Automation**:
Performing repetative tasks with minimum human intervention.

**Types of Automation:** 
- Infrastructure
- Configuration
- Application
- Cloud
- Network
- Security
- CI/CD


**Automation Tools:**
- Ansible
- Puppet: Configuration Management.
- Terraform: IaC
- Chef: IaC
- Saltstack: Remote execution and configuration management.
- Github Actions: CI/CD Automation.
- AWS System Management: Server management and automation.

# Ansible Automation Platform (Containerized)

## What is Ansible?

Characteristics:
* open-source IT automation tool
* Agentless
* It uses playbook to describe the automation jobs
* It uses hostfile to group the hosts and control actions
* Configuration Management
* Application Deployment
* Infrastructure Provisioning
* Orchestration: Automated configuration, co-ordinating and managing of computer systems and softwares.
* Security Automation

Ansible Automation Platform (AAP) is the **enterprise version of Ansible** provided by Red Hat.
Default Ansible Inventory Path **/etc/ansible/hosts**


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

Contains the list of managed .

Types of Inventory:

### 1. Static Inventory

* A manually created text file.
* Hostnames or IP addresses are specified by the administrator.

Example:

```ini
[name]
192.168.1.10
192.168.1.11

[data]
192.168.10.[2:100]

[data1]
node1.fqdn.address
node2.india.com
node[1:100].india.com

```

### 2. Dynamic Inventory

* Automatically fetches  from cloud providers like:

  * AWS
  * Azure
  * Google Cloud
  * VMware
* Useful when server IP addresses change frequently.


# Inventory Default Groups

1. **all**

   * Contains every host in the inventory.

2. **ungrouped**

   *  that do not belong to any custom group.


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

A collection of tasks executed on one or more .


### Playbook

A collection of one or more plays written in **YAML**.

Extensions:

* `.yml`
* `.yaml`

### Handlers: 
Trgger service status changes like restarting or stopping the service.

### Facts: 
Global variable, which contains all the information about the system.

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
  : web
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

# Native vs External Module
| Feature      | Native Module                                     | External Module                                   |
| ------------ | ------------------------------------------------- | ------------------------------------------------- |
| Meaning      | Module included with Ansible                      | Module developed/maintained outside Ansible core  |
| Installation | Usually available with Ansible package/collection | May require installing a separate collection      |
| Maintenance  | Maintained by Ansible/community                   | Maintained by a vendor, community, or third party |
| Example      | `ansible.builtin.copy`, `ansible.builtin.file`    | Modules from vendor collections                   |
| Namespace    | Often `ansible.builtin.*`                         | Usually `<collection>.<module>`                   |
| Reliability  | Generally well integrated                         | Depends on the collection/vendor                  |

# Types of Automation

## One Time Automation:
```
at now +2 minutes (Run the following commands once, 2 minutes from now)
at> mkdir -p /dir1/dir2 
at> cp -v /etc/* /dir1/dir2/
at> <EOT> (EOT means End Of Text in this context. Usually, you don't literally type 'Ctrl+D')
at> (To check)
```

## Recurring Automation
Crontab:
```
rpm -qa | grep cron-* (To list all installed RPM packages, name starting with cron-)
crontab -e -u test 
10	12	* 	* 	*	mkdir ~/dir3 (Run the command every day at 12:10 PM)
```
