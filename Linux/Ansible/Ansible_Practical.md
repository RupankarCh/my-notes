# 1. Create an inventory called inventory as per the following specification.

a. Create a hostgroup called webservers with 2 host.
i. web1.example.com
ii. web2.example.com

b. Create a hostgroup called appservers with 2 host.
i. host1.example.com
ii. host2.example.com

c. Create a nested group called servers which include both groups webservers and appservers

```
[webservers]
web1.example.com
web2.example.com

[appservers]
host1.example.com
host2.example.com

[servers:children]
webservers
appservers
```

# 2. Write a playbook called intranet.yml as per the following specifications.
a. Install the httpd package on webservers hostgroup.

b. Install the package postfix on appservers host group.

c. Update all servers with latest patches and bug fixes.

```
---
- name: Install and start Apache on webservers
  hosts: webservers
  become: yes   (Installing packages and managing services requires root privileges.)
  tasks:
    - name: Install httpd
      yum:
        name: httpd
        state: latest

    - name: Start and enable httpd
      service:
        name: httpd
        state: started
        enabled: yes

- name: Install and start Postfix on appservers
  hosts: appservers
  become: yes

  tasks:
    - name: Install postfix
      yum:
        name: postfix
        state: latest

    - name: Start and enable postfix
      service:
        name: postfix
        state: started
        enabled: yes

- name: Update all servers
  hosts: servers
  become: yes

  tasks:
    - name: Update all packages to latest version
      yum:
        name: "*"
        state: latest
```

# 3. Ansible Architecture Configuration
**Ansible Control Node Configuration:**

Change IP Address as 192.168.10.1/24 and Gateway address 192.168.10.1 and hostname ansible-server.india.com
```
vim /etc/hostname (To verify hostname)
vim /etc/hosts
192.168.10.1 ansible-server.india.com ansible-server
192.168.10.2 node1.india.com node1
192.168.10.3 node2.india.com node2
```

**Ansible Node1 Configuration:**

Change IP Address as 192.168.10.2/24 and Gateway address 192.168.10.1 and hostname node1.india.com
```
vim /etc/hostname (To verify hostname)
vim /etc/hosts
192.168.10.1 ansible-server.india.com ansible-server
192.168.10.2 node1.india.com node1
192.168.10.3 node2.india.com node2
```

**Ansible Node2 Configuration:**

Change IP Address as 192.168.10.3/24 and Gateway address 192.168.10.1 and hostname node2.india.com
```
vim /etc/hostname (To verify hostname)
vim /etc/hosts
192.168.10.1 ansible-server.india.com ansible-server
192.168.10.2 node1.india.com node1
192.168.10.3 node2.india.com node2
```
**Ansible Server Configuration**

yum repository configuration
```
yum install ansible-core -y
ansible --version
(/usr/lin/python3.9/site-packages/ansible stores ansible modules)
useradd teacher (For 2 nodes also)
passwd teacher (For 2 nodes also)
su - teacher
mkdir inventory
cd inventory/
vim nodes
[dev]
192.168.10.2
192.168.10.3
:wq!
ansible all --list-hosts -i ~/inventory/ (to see particular 2 group replace all with dev:data)
```

# 4. Make Custom inventory file as default inventory file:
```
ansible --version (To see default inventory file)
vim /etc/ansible/ansible.cfg 
[defaults]
inventory = /home/teacher/inventory
host_key_checking = False
:wq
su - teacher
ansible all --list-hosts (To check)
```

# 5. Remote Login
## SSH Password Based Authentication: (Delete the custom inventory file)
SH key-based authentication is the recommended approach for Industry.
```
sudo yum install -y sshpass
su - teacher
rm -rf ~/inventory
mkdir ~/inventory
cd ~/inventory
vim nodes
[dev]
node1
node2
vim ~/ansible.cfg
[defaults]
inventory = /home/teacher/inventory/nodes
host_key_checking = false
ansible all --list-hosts (Test if two nodes appear)
```

On Nodes:
```
vim /etc/ssh/sshd_config 
PasswordAuthentication yes
sudo systemctl restart sshd
```

On Server:
```
ansible dev -m ping -k
```

## SSH Passwordless Authentication
```
sudo useradd ansible
sudo passwd ansible
echo "ansible ALL=(ALL) NOPASSWORD:ALL" | sudo tee /etc/sudoers.d/ansible (Give it passwordless sudo)
cat /etc/sudoers.d/ansible (Verify)
su - ansible
ssh-keygen
```
On Both Managed Nodes:
```
sudo useradd ansible
sudo passwd ansible
echo "ansible ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/ansible (Optional)
```
On Server
```
ssh-copy-id ansible@node1
ssh-copy-id ansible@node2
ssh ansible@node1
ssh ansible@node2
```

## Inventory-Based Authentication 
You **store the SSH username and password in the Ansible inventory file** instead of using SSH keys (passwordless authentication). When Ansible connects to a managed node, it reads the credentials from the inventory and logs in using SSH.
```
mkdir automation
cd automation
vim ansible.cfg
[defaults]
inventory = ./inventory  (Uses the local inventory file by default) 
host_key_checking = false (Disables SSH host key verification)
remote_user = ansible (Uses the ansible user to connect by default)
ask_pass = false (Does not prompt for an SSH password)

[privilege_escalation]
become = true (Automatically uses sudo)
become_method = sudo (Runs tasks as the root user)
become_user = root (Runs tasks as the root user) 
become_ask_pass = false (Does not ask for the sudo password)
vim inventory
[web] 
node1 ansible_user=ansible ansible_password=ansible (**node1** The hostname or IP of the managed node, **ansible_user=ansible** SSH username, **ansible_password=ansible** SSH password)
node2 ansible_user=ansible ansible_password=ansible
ansible web -m ping or ansible web -m ping -i /home/ansible/automation/inventory Test the connection)
```

# 6. Ansible Copy Module & Privilege Escalation Notes

## 1. Create a System-Wide Inventory

```bash
cd /etc/ansible
vim hosts
```

Example inventory:

```ini
[web]
node1
node2
```

> **Note:** If `/etc/ansible/hosts` exists, you can run Ansible commands without specifying the `-i` option.

Example:

```bash
ansible web -m ping
```

---

## 2. Remove Local Inventory

```bash
rm -rf inventory
```

**Purpose:**
- Deletes the local inventory file.
- If `/etc/ansible/hosts` exists, Ansible automatically falls back to using it.

---

## 3. Create a Source File

```bash
echo "Good Afternoon" > file1.txt
```

Creates a text file that will be copied to managed nodes.

---

## 4. Copy an Inventory File

```bash
cp -r /home/teacher/inventory /home/ansible/
```

Copies the inventory directory from the teacher account.

---

## 5. Change Ownership

```bash
chown -R ansible:ansible /home/ansible/inventory
```

Changes ownership recursively to the `ansible` user and group.

---

# Copy Module Examples

## 1. Copy a File from Control Node

```bash
ansible all -i ~/inventory -m copy -a "src=/home/ansible/file1.txt dest=/tmp/file1.txt"
```

Copies `file1.txt` from the control node to `/tmp/file1.txt` on every managed node.

---

## 2. Verify the Copy

```bash
ansible all -m command -a "ls -l /tmp/file1.txt"
```

Checks whether the file exists on all managed nodes.

---

## 3. Create a File Without an Existing Source

```bash
ansible all -m copy -a 'content="Welcome to our Ansible Class" dest=/tmp/file3.txt'
```

Creates a file directly from the provided text without using a local source file.

---

# Preparing the Destination Directory

## On Both Managed Nodes

```bash
cd
mkdir test
chmod 755 test
```

Creates a directory with standard permissions.

---

## Copy File into the Directory

On the control node:

```bash
ansible all -m copy -a "src=file1.txt dest=/home/ansible/test/"
```

Copies `file1.txt` into `/home/ansible/test/` on every managed node.

---

# Configure Sudo Privileges

## On All Three Machines

Create a sudoers file:

```bash
echo "ansible ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/ansible
```

Or edit the sudoers file:

```bash
vim /etc/sudoers
```

Add:

```text
ansible ALL=(ALL) ALL
```

This allows the `ansible` user to execute commands as another user using sudo.

---

# Using Become (Privilege Escalation)

Switch to the Ansible user:

```bash
su - ansible
```

---

## Copy a File Using Sudo

```bash
ansible all -m copy -a 'src=file1.txt dest=/test/file2.txt' -b -K --become-method sudo
```

### Options

| Option | Meaning |
|---------|---------|
| `-b` | Enable privilege escalation (become) |
| `-K` | Prompt for sudo password |
| `--become-method sudo` | Use sudo for privilege escalation |

---

## Verify File

```bash
ansible all -m command -a 'ls -l /test'
```

---

## Check Current User (Root)

```bash
ansible all -m command -a 'id' -b -K
```

Runs the command as root.

---

## Read `/etc/passwd`

```bash
ansible all -m command -a 'cat /etc/passwd'
```

Displays the passwd file.

---

## Become Another User

```bash
ansible all -m command -a 'id' -b --become-user ansible
```

Runs the command as the `ansible` user instead of root.

---

# Enable Become by Default

Edit the configuration:

```bash
vim /etc/ansible/ansible.cfg
```

Add:

```ini
[privilege_escalation]
become=true
```

> **Note:** The correct section name is **`[privilege_escalation]`**, not `priveledge_escalation`.

Now simply run:

```bash
su - ansible

ansible all -m command -a 'id'
```

Ansible automatically performs privilege escalation.

---

# Create User and Group

## On All Three Machines

```bash
useradd student
passwd student
groupadd tech
```

Creates:
- User: `student`
- Group: `tech`

---

# Copy Module with Permissions

## Copy While Setting Owner, Group and Mode

```bash
ansible all -m copy -a 'src=file1.txt dest=/tmp/file10.txt mode=0755 owner=student group=tech' -b -K
```

This command:

- Copies the file
- Sets permissions to **755**
- Changes owner to **student**
- Changes group to **tech**

---

# Copy File Normally

```bash
ansible all -m copy -a 'src=file1.txt dest=/tmp'
```

Copies the file into `/tmp`.

---

## Verify Contents

```bash
ansible all -m command -a 'cat /tmp/file1.txt'
```

---

# Update a File

Edit locally:

```bash
vim file1.txt
```

Contents:

```text
Welcome
```

Copy again:

```bash
ansible all -m copy -a 'src=file1.txt dest=/tmp'
```

Verify:

```bash
ansible all -m command -a 'cat /tmp/file1.txt'
```

---

Edit once more:

```bash
vim file1.txt
```

Add:

```text
New Line
```

Copy again with backup enabled:

```bash
ansible all -m copy -a 'src=file1.txt dest=/tmp backup=yes'
```

---

## Verify Backup

```bash
ansible all -m command -a 'ls -l /tmp'
```

Ansible creates a timestamped backup of the previous file before replacing it.

---

# Copy a File Already Present on the Remote Host

```bash
ansible all -m copy -a 'src=/tmp/file1.txt dest=/tmp/file10.txt remote_src=yes'
```

### `remote_src=yes`

Indicates that the source file is already located on the managed node, so Ansible copies it locally on that remote machine instead of transferring it from the control node.

---

# Remove Test Files

## On Both Managed Nodes

```bash
rm -rf file10.txt
rm -rf file1.txt.backup
```

Deletes the copied file and its backup.

---

# Copy Only to a Specific Host

```bash
ansible node2 -m copy -a 'src=/tmp/file1.txt dest=/tmp/file10.txt remote_src=yes'
```

Copies the remote file only on **node2**.

---

# Summary of Important Copy Module Parameters

| Parameter | Purpose |
|-----------|---------|
| `src=` | Source file |
| `dest=` | Destination path |
| `content=` | Create file from text |
| `owner=` | File owner |
| `group=` | File group |
| `mode=` | File permissions |
| `backup=yes` | Backup existing file before overwrite |
| `remote_src=yes` | Source file already exists on the managed node |

---

# Frequently Used Become Options

| Option | Description |
|---------|-------------|
| `-b` | Enable privilege escalation |
| `-K` | Ask for sudo password |
| `--become-user USER` | Execute as another user |
| `--become-method sudo` | Use sudo as the escalation method |
| `become=true` | Enable become by default in `ansible.cfg` |
