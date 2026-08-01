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
ask_pass = false (Don't prompt for an SSH password)

[privilege_escalation]
become = true (Automatically uses sudo)
become_method = sudo (Runs tasks as the root user)
become_user = root (Runs tasks as the root user) 
become_ask_pass = false (Don't ask for the sudo password)
vim inventory
[web] 
node1 ansible_user=ansible ansible_password=redhat ansible_become_password=ansible (**node1** The hostname or IP of the managed node, **ansible_user=ansible** SSH username, **ansible_password=ansible** SSH password)
node2 ansible_user=ansible ansible_password=redhat ansible_become_password=ansible
```
On All users
```
usermod -aG wheel ansible
id ansible (Verify)
```
On Ansible server
```
ansible web -m ping  (Test the connection)
```

# 6. Create a System-Wide Inventory 
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

# 7. Modules

## Copy a File from Control Node 
**Used to copy file from Ansible server(Control Node) to managed nodes.** `remote_src=yes` Indicates that the source file is already located on the managed node, so Ansible copies it locally on that remote machine instead of transferring it from the control node.

### Summary of Important Copy Module Parameters

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

```bash
echo "Good Afternoon" > file1.txt (Creates a text file that will be copied to managed nodes)
ansible all -i ~/inventory -m copy -a "src=/home/ansible/file1.txt dest=/tmp/file1.txt" (Copies `file1.txt` from the control node to `/tmp/file1.txt` on every managed node)
ansible node2 -m copy -a 'src=/tmp/file1.txt dest=/tmp/file10.txt remote_src=yes' (Copies the remote file only on node2)
ansible all -m command -a "ls -l /tmp/file1.txt" (Checks whether the file exists on all managed nodes)
ansible all -m command -a 'cat /tmp/file1.txt' (Verify contents)
ansible all -m copy -a 'content="Welcome to our Ansible Class" dest=/tmp/file3.txt' (Creates a file directly from the provided text without using a local source file)
ansible all -m copy -a 'src=file1.txt dest=/tmp/file10.txt mode=0755 owner=student group=tech' -b -K (Before doing it student user, tech group must exist in all the systems, It will Copy the file, Sets permissions to 755, Changes owner to student, Changes group to tech)
ansible all -m copy -a 'src=file1.txt dest=/tmp backup=yes' (To Create Backup, Ansible creates a timestamped backup of the previous file before replacing it)
ansible all -m command -a 'ls -l /tmp' (To verify if backup exists)
ansible all -m copy -a 'src=/tmp/file1.txt dest=/tmp/file10.txt remote_src=yes' (this command copies the file named file1.txt which exists on the remote host with copied file named file10.txt on the remote host)
```
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

## Frequently Used Become Options

| Option | Description |
|---------|-------------|
| `-b` | Enable privilege escalation |
| `-K` | Ask for sudo password |
| `--become-user USER` | Become another user (usually root) |
| `--become-method sudo` | Use sudo as the escalation method |
| `become=true` | Enable become by default in `ansible.cfg` |

## Copy a File Using Sudo 
**Used when typically owned by root and a normal user cannot write there**
```bash
su - ansible
ansible all -m copy -a 'src=file1.txt dest=/test/file2.txt' -b -K --become-method sudo
ansible all -m command -a 'ls -l /test' (Verify File)
```
---

## User Administration

```bash
ansible all -m command -a 'id' -b -K (Runs id as root user)
ansible all -m command -a 'id' (Runs id as normal SSH user even if the user got it's name in sudoers file)
ansible all -m command -a 'id' -b --become-user ansible (Runs the command as the `ansible` user instead of root)
```
---

## Enable Become by Default

Edit the configuration:

```bash
vim /etc/ansible/ansible.cfg
[privilege_escalation]
become=true
su - ansible
ansible all -m command -a 'id' (Ansible automatically performs privilege escalation)
```
---
