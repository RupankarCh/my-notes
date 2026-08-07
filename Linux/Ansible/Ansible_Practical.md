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


---

# Become (Privilege Escalation)

**Frequently Used Become Options**

| Option | Description |
|---------|-------------|
| `-b` | Enable privilege escalation |
| `-K` | Ask for sudo password |
| `--become-user USER` | Become another user (usually root) |
| `--become-method sudo` | Use sudo as the escalation method |
| `become=true` | Enable become by default in `ansible.cfg` |

**Used when typically owned by root and a normal user cannot write there**
---

# System Configuration and Debugging: 

## Create a System-Wide Inventory 
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

## Configure Sudo Privileges
This allows the `ansible` user to execute commands as another user using sudo.

On All Three Machines, Create a sudoers file:

```
echo "ansible ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/ansible
```

Or edit the sudoers file:

```
vim /etc/sudoers
```

Add:

```
ansible ALL=(ALL) ALL
```

## Enable Become by Default
Edit the configuration:

```bash
vim /etc/ansible/ansible.cfg
[privilege_escalation]
become=true
su - ansible
ansible all -m command -a 'id' (Ansible automatically performs privilege escalation)
```

## How to Bypass Become:
```
cd /etc/ansible
vi ansible.cfg
[privilege_escalation]
become=True
become_method=sudo
```

## Check Environment:
su - ansible
ansible all -m ping

---

# 7. Modules

**Quick Module Summary**

| Module       | Purpose                                                 |
| ------------ | ------------------------------------------------------- |
| `file`       | Create/delete files, directories, links, permissions    |
| `copy`       | Copy files or content to managed nodes                  |
| `fetch`      | Copy files from managed node to control node            |
| `command`    | Execute simple commands                                 |
| `shell`      | Execute shell commands, scripts, pipes, redirection     |
| `raw`        | Execute commands without Python                         |
| `stat`       | Get file information                                    |
| `lineinfile` | Add/remove/modify a single line                         |
| `replace`    | Replace all matching text                               |
| `user`       | User administration                                     |
| `group`      | Group administration                                    |
| `filesystem` | Create filesystems (recommended)                        |
| `mount`      | Mount filesystems and manage `/etc/fstab` (recommended) |

---

## 1. File Module

**Used for:** `mkdir`, `touch`, `chmod`, `chown`, `chgrp`, `ln`, `rm`, `rmdir`

```
ansible all -m file -a 'path=/tmp/file20.txt state=touch' (Creates an empty File)

ansible all -m file -a 'path=/tmp/redhat state=directory' (Creates a Directory)

ansible all -m file -a 'path=/tmp/test state=directory mode=0777 owner=root group=root' -b (creates directory apply permission and ownership)

ansible all -m file -a 'path=/tmp/folder state=absent' (File Module doesn't support wildcards like * so to delete recursively delete the parent directory)

ansible all -m file -a 'path=/tmp/redhat.txt state=absent' (Deletes a File)

ansible all -m file -a 'src=/tmp/file100.txt dest=/tmp/link1 state=link' (Creates a symbolic (soft)  Link)

ansible all -m file -a 'src=/tmp/file100.txt dest=/tmp/link2 state=hard' (Creates a Hard Link)
```

---

## 2. Command Module

**Used for:** Execute simple commands (no shell features). 

```
ansible all -m command -a 'ls -l /tmp/file20.txt' (Shows detailed information about file20.txt (permissions, owner, size, timestamp))

ansible all -m command -a 'ls -l /tmp' (Lists all files and directories inside /tmp in long format)

ansible all -m command -a 'ls -ld /tmp/redhat' (Shows detailed information about the redhat directory itself, not its contents)

ansible all -m command -a 'cat /tmp/file100.txt' (Displays the contents of file100.txt)

ansible all -m command -a 'uptime' (Shows how long the system has been running, number of users, and load average)

ansible all -m command -a 'id ansible' (Displays the UID, GID, and group memberships of the specified user ansible)
```

---

## 3. Shell Module

**Used for:** Pipes, redirects, variables, loops, scripts to run on managed nodes.
```
ansible all -m shell -a 'rm -rf /tmp/*' (Delete Files)

ansible all -m shell -a 'touch /tmp/file{1..5}' (Create Multiple Files)

ansible all -m shell -a 'cut -d: -f1 /etc/passwd' (It simply prints the usernames of all local user accounts on the system)

ansible all -m shell -a 'cut -d: -f1 /etc/passwd' > /home/ansible/report.txt

ansible all -m shell -a 'id developer'  (Displays the UID, GID, and group memberships of the specified user ansible)

ansible all -m shell -a 'getent group HR' (searches the system's group database (such as /etc/group, LDAP, or another configured name service) for a group named HR)

ansible all -m shell -a 'passwd -S Rohit'  (Checks the password status of the user Rohit on every host managed by Ansible and prints the results)

ansible all -m shell -a 'chage -l Rohit' (To check password related information)

ansible all -m shell -a 'grep Rohit /etc/passwd' (searches the /etc/passwd file for any line containing the string Rohit)

ansible all -m shell -a 'chage -d 0 Rohit' (After this command runs, the user Rohit will be forced to change their password at the next login)

ansible all -m shell -a 'lsblk'  (list block devices. It displays information about storage devices)

ansible all -m shell -a 'fdisk -l /dev/nvme0n1' (Display the partition table)

ansible all -m shell -a ' (Create a new partition)
cat <<EOF | fdisk /dev/nvme0n1
n
p
1

+10G
w
EOF
'

ansible all -m shell -a 'partprobe /dev/nvme0n2' (Tell the kernel to re-read the partition table)

ansible all -m shell -a 'fdisk -l /dev/nvme0n2' (Verify the new partitions)

ansible all -m shell -a 'blkid /dev/nvme0n2p2' (Display filesystem UUID)

ansible all -m shell -a 'mount -a'

ansible all -m shell -a 'df -h' (Display mounted filesystem)

ansible all -m shell -a '/home/ansible/test.sh' (Display mounted filesystems)
```

---

## 4. Copy Module

**Used for:** Copy files/content from control node to managed nodes and a managed node to the same managed node only.

```
ansible all -m copy -a 'src=file1.txt dest=/tmp/file1.txt'  (Copy File)

ansible all -m copy -a 'content="GOOD" dest=/tmp/file100.txt' (Create File with Content)

ansible all -m copy -a 'src=/tmp/file1.txt dest=/tmp/file10.txt remote_src=yes' (If the file exists on remote hosts it copies as file10.txt)

ansible all -m copy -a 'src=test.sh dest=/home/ansible mode=755' (Copy Script, while configuring permissions)

ansible all -m copy -a 'src=file1.txt dest=/tmp/file10.txt mode=0755 owner=student group=tech' -b -K (Before doing it student user, tech group must exist in all the systems, It will Copy the file, Sets permissions to 755, Changes owner to student, Changes group to tech)

ansible all -m copy -a 'src=file1.txt dest=/tmp backup=yes' (Copies the file to remote hosts and if a file with the same name already exists there, Ansible creates a backup before overwriting it)
```

---

## 5. Fetch Module

**Used for:** Copy files from managed node to control node.

```
ansible node1 -m fetch -a 'src=/tmp/file100.txt dest=backup' 
```

---

## 6. Stat Module

**Used for:** Check file metadata.

```
ansible all -m stat -a 'path=/tmp/file100.txt'
```

---

## 7. Lineinfile Module

**Used for:** Add, remove, or modify a single line.

```
ansible all -m lineinfile -a 'dest=/tmp/file100.txt line="Content"' (Append Line)

ansible all -m lineinfile -a 'dest=/tmp/file100.txt line="Content" insertafter=BOF'  (Insert at Beginning)

ansible all -m lineinfile -a 'dest=/tmp/file100.txt line="Content" insertafter=EOF' (Insert at End)

ansible all -m lineinfile -a 'dest=/tmp/file100.txt line="Content" insertafter="Content"' (Insert After Matching Line)

ansible all -m lineinfile -a 'dest=/tmp/file100.txt line="Content" state=absent' (Remove Line)
```

---

## 8. Replace Module

**Used for:** Replace every occurrence of a pattern.

```
ansible all -m replace -a 'dest=/tmp/file100.txt regexp="AFTERNOON" replace="MORNING"'
```

---

## 9. User Module

**Used for:** User management.

```
ansible all -m user -a 'name=developer state=present'  (Create a user named developer)

ansible all -m user -a 'name=tech home=/home/ram shell=/bin/bash state=present' (Create tech with a specific home directory and shell)

ansible all -m user -a 'name=Rahul uid=2001 group=HR' (Create/modify Rahul with UID 2001, add user to group)

ansible all -m user -a 'name=username groups=HR append=yes' (Add user to HR as a supplementary group)

openssl passwd -6 'rohit@123' (Generate a SHA-512 password hash)
ansible all -m user -a 'name=Rohit password=<hashed_password>' -b -K (Set that hash as Rohit's Linux password)

ansible all -m user -a 'name=Rohit shell=/bin/nologin'  (Change user's Shell)

ansible all -m user -a 'name=Rohit state=absent' (Remove User)

ansible all -m user -a 'name=Rohit state=absent remove=yes' (Delete the Rohit user AND remove the user's home directory and related user files)
```

---

## 10. Group Module

**Used for:** Group management.

```
ansible all -m group -a 'name=HR state=present' (Create Group)

ansible all -m group -a 'name=HR state=absent'  (Remove Group)
```

---

## 11. Raw Module

**Used for:** run a command directly on the remote server without requiring Python or an Ansible module on the remote host.

```
ansible all -m raw -a 'uptime; lsblk'
```

---

## 12. filesystem Module

```
ansible all -m filesystem -a 'fstype=xfs dev=/dev/nvme0n2p1'  (Create Filesystem)

ansible all -m filesystem -a 'fstype=ext4 dev=/dev/nvme0n2p2'
```

## 13. Mount Module

```
ansible all -m mount -a 'path=/data src=/dev/nvme0n2p1 fstype=xfs state=mounted'  (Mounts /dev/nvme0n2p1 as XFS on /data immediately and ensures the mount is configured persistently)

ansible all -m mount -a 'path=/data src=/dev/nvme0n2p1 fstype=xfs opts=defaults state=present'  (Adds/configures the /data mount in /etc/fstab with default options but does not mount it immediately, the mount is configured persistently)
```

---

