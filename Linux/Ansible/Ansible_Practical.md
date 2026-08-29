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
**/etc/ansible/ansible.conf** (Where default inventory file location can be changed)
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

# 6. System Configuration and Debugging: 

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

ansible all -m file -a 'path=/tmp/redhat.txt state=absent' (Deletes a File)

ansible all -m file -a 'path=/tmp/test state=directory mode=0777 owner=root group=root' -b (creates directory apply permission and ownership)

ansible all -m file -a 'path=/tmp/folder state=absent' (File Module doesn't support wildcards like * so to delete recursively delete the parent directory)

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

ansible all -m command -a 'systemctl status httpd' (To check status)

```

---

## 3. Shell Module

**Used for:** Pipes, redirects, variables, loops, scripts to run on managed nodes.
```
ansible all -m shell -a 'ls -ld /data' (It checks the `/data` directory on all Ansible-managed hosts and displays its permissions, owner, group, and directory details.)

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

ansible all -m shell -a ' cat <<EOF | fdisk /dev/nvme0n1  
n → create a new partition
p → create a primary partition
1 → partition number 1
<blank> → accept the default first sector
+10G → make the partition 10 GB
w → write/save the partition table
EOF
'
(On every Ansible-managed server, create partition /dev/nvme0n1p1 with a size of approximately 10 GB and write the changes to disk, cat <<EOF ... EOF → Creates a sequence of input lines and sends them to fdisk.)

ansible all -m shell -a 'partprobe /dev/nvme0n2' (makes Linux kernel re-read the partition table so the new partition becomes visible without rebooting)

ansible all -m shell -a 'blkid /dev/nvme0n2p2' (It runs blkid on /dev/nvme0n2p1 on all Ansible-managed hosts to display its filesystem type, UUID, and other block-device identification information.)

ansible all -m shell -a 'mount -a'

ansible all -m shell -a 'df -Th' (It **displays the disk space usage, filesystem type, total size, used space, available space, and mount points on all Ansible-managed hosts**.)

ansible all -m shell -a '/home/ansible/test.sh' (Display mounted filesystems)

ansible all -m shell -a 'lsblk -f' > report.txt (To save block devices, partitions, filesystems, UUIDs, and mount points to a file of all hosts in your ansible inventory)

ansible all -m shell -a 'lsblk /dev/nvme0n2' (It displays the partition and block-device layout of `/dev/nvme0n2` on all Ansible-managed hosts.)

ansible all -m shell -a 'mount -t ext4 /dev/nvme0n2p1 /data' (It **mounts `/dev/nvme0n2p1` as an `ext4` filesystem on `/data` on all Ansible-managed hosts**, and ensures the mount is active.)

ansible all -m shell -a 'mkfs.ext4 /dev/nvme0n2p1' (Creates an ext4 filesystem on /dev/nvme0n2p1 on every Ansible-managed server.)

ansible all -m shell -a 'umount /data' (It unmounts the filesystem mounted at `/data` on `node1`, without removing its `/etc/fstab` entry.)

ansible all -m shell -a 'findmnt /dev/nvme0n2p1' (It checks where `/dev/nvme0n2p1` is currently mounted on all Ansible-managed hosts and displays its mount details.)


ansible all -m shell -a 'cat <<EOF | fdisk /dev/nvme0n2 
>d
>1
>w
>EOF
'
(It **automatically runs `fdisk` on `/dev/nvme0n2` to delete partition 1 and write/save the partition-table changes on all Ansible-managed hosts**.)

Make a partition persistently mounted:
ansible all -m shell -a 'mkfs.ext4 /dev/nvme0n2p1' (It **formats `/dev/nvme0n2p1` with the `ext4` filesystem on all Ansible-managed hosts**, creating a new filesystem on that partition Copy the UUID)

ansible node1 -m shell -a 'echo "UUID=<paste> /data ext4 defaults 0 0" >> /etc/fstab' (It adds an `/etc/fstab` entry on `node1` to automatically mount the specified UUID-based ext4 filesystem at `/data` during boot.)


ansible node1 -m shell -a 'mount -a' (It mounts all filesystems listed in `/etc/fstab` on `node1`, including the newly configured `/data` filesystem.)

ansible node1 -m shell -a 'findmnt /dev/nvme0n2p1' (It verifies that `/dev/nvme0n2p1` is mounted and shows its mount point and filesystem details on `node1`.)

ansible node1 -m shell -a "grep '/data' /etc/fstab" (It checks `/etc/fstab` on `node1` and displays the line containing `/data`, verifying that the filesystem is configured for persistent mounting.)

ansible node1 -m shell -a 'cp /etc/fstab /etc/fatab.bak' (It creates a backup copy of `/etc/fstab` as `/etc/fatab.bak` on `node1`.)

ansible node1 -m shell -a 'ls -l /etc/fatab.bak' (It checks whether /etc/fastab.bak exists on node1 and displays its file details.)

ansible node1 -m shell "sed -i '\|[[:space]]data[[:space]]|d' /etc/fstab"  ( \|[[:space]]/data means delete only the line containing /data, It **removes the `/data` mount entry from `/etc/fstab` on `node1` using `sed`. to edit a file use sed with -i for interactive shell,)

Package Management:
ansible all -m shell -a 'rpm -qa |grep httpd' (Checks whether the httpd package is installed on all Ansible-managed hosts by listing installed RPM packages and filtering for httpd)

ansible all -m shell -a 'yum info httpd' (Displays detailed information about the httpd package, such as its version, architecture, repository, and installation status)

ansible all -m shell -a 'dnf list --showduplicates httpd' (Displays all available versions of the httpd package, including duplicate/older versions, on all managed hosts)

ansible all -m shell -a 'dnf install httpd-2.3.4'  (To install a particular version of httpd)

ansible all -m shell -a 'dnf update httpd' (To update package)

ansible all -m shell -a 'rpm -qR httpd' (Displays the dependencies required by the installed httpd package on all managed hosts)

ansible all -m shell -a 'yum remove -y  httpd*' (To remove a package)

ansible all -m shell -a 'curl localhost' (Sends an HTTP request to the local web server on each managed host and displays the response/content returned by localhost)

ansible all -m shell -a 'systemctl mask httpd' (Masks the httpd service on all managed hosts, preventing it from being started manually or automatically until it is unmasked)

ansible all -m shell -a 'systemctl unmask httpd' (Unmasks the httpd service on all managed hosts, allowing it to be started manually or automatically again)

ansible all -m shell -a 'systemctl list-units' (Lists the currently loaded and active systemd units (services, sockets, mounts, etc.) on all managed hosts, |grep active)

ansible all -m shell -a 'systemctl --type=service --state=running' (Lists all currently running services on all managed hosts)

ansible all -m shell -a 'systemctl --failed' (Lists all failed systemd units (such as services) on all managed hosts)

ansible all -m shell -a 'systemctl cat httpd' (Displays the httpd systemd unit file and its configuration/drop-in files on all managed hosts)

ansible all -m shell -a 'systemctl show httpd' (Displays detailed properties and runtime configuration of the httpd systemd service on all managed hosts)

ansible all -m shell -a 'systemctl show httpd -p MainPID' (Displays the Main PID (Process ID) of the httpd service on all managed hosts)

ansible all -m shell -a "ss -lntp |grep ':80'" (Checks which process/service is listening on TCP port 80 on all managed hosts)

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

ansible all -m lineinfile -a 'dest=/tmp/file100.txt line="Content" insertafter="Content2"' (Insert After Matching Line)

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

ansible all -m filesystem -a 'fstype=ext4 dev=/dev/nvme0n2p1' (Creates an ext4 filesystem on /dev/nvme0n2p1 on every Ansible-managed server.)

```

## 13. Mount Module

```
ansible all -m mount -a 'path=/data src=/dev/nvme0n2p1 fstype=ext4 state=mounted' (It **mounts `/dev/nvme0n2p1` as an `ext4` filesystem on `/data` on all Ansible-managed hosts**, and ensures the mount is active.)

ansible all -m mount -a 'path=/data src=/dev/nvme0n2p1 fstype=xfs state=mounted'  (Mounts /dev/nvme0n2p1 as XFS on /data immediately and ensures the mount is configured persistently)

ansible all -m mount -a 'path=/data src=/dev/nvme0n2p1 fstype=xfs opts=defaults state=present'  (Adds/configures the /data mount in /etc/fstab with default options but does not mount it immediately, the mount is configured persistently)
```

## 14. Package Module
```
ansible all -m package -a 'name=vsftpd state=present use=yum' (To install a package)

ansible all -m package -a 'name=nfs*,samba state=present use=dnf' (Install multiple services)



```

## 15. Yum Module
```

ansible all -m yum -a 'name=httpd state=present" (To install httpd)

```

## 16. Systemd Module (To manage services, and daemons)
```
ansible all -m systemd -a 'daemon-reload=true' (Reloads the systemd manager configuration on all managed hosts so it recognizes changes to service/unit files)

ansible all -m systemd -a 'name=httpd state=started' (To start the service)

ansible all -m systemd -a 'name=httpd state=started enabled=true' (To restart and enable service)

ansible all -m systemd -a 'name=httpd state=stopped enabled=false' (Stops the httpd service and disables it from starting automatically at boot on all managed hosts)


```
---

22-08-26 1st half


SELINUX: Security Enhanced Linux
selinux is a mendatory access control security mechanism built into RHELL9 beyond traditional Linux permissions such as user and group ownership and rwx permission.

MAC vs DAC

MODE of SELINUX:
1.Enforcing(default): Policy is active and provide highest level of security. It blocks and logs the unauthorized access.
2.Permissive: selinux doesn't block unauthorized access but log file will be generated.
3.Disabled: selinux is totally disabled.


Configuration File: /etc/selinux/config


sestatus (To see current state of selinux)
getenforce (To see current state of selinux)
setenforce 1 (To 
sudo vim /etc/selinux/config (To change selinux mode permanently)
SELINUX=disabled

Types:
1.STRICT (Every service/daemon)
2.TARGETED (For a perticular service/daemon)
3.MLS=> MULTI LEVEL SECURITY

Selinux Contexts
Security Context
Selinux Boolean: selinux boolean allows administrator to enable or disable certain policy or behaviour without creating a complete new selinux policy 

# manual Selinux 
```
ls -zl test.sh 

su - root
mkdir /web
cd /web/
vim index.html
<content>
ls -zl /web/index.html
yum install httpd -y
cd ..
clear 
systemctl restart httpd
systemctl enable httpd
httpd -t
vim /etc/httpd/conf/httpd.conf
DocumentRoot "/web/index.html"
systemctl status httpd.service
ls -lZd /var/www/html/
vim /etc/httpd/conf/httpd.conf
DocumentRoot "/web/index.html"
systemctl restart httpd
systemctl enabled httpd/systemctl restart --now httpd
ls -Zl /web/index.html
#chcon -t httpd_sys_content_t /web/index.html
ls -Zld /web 
#chcon -t httpd_sys_content_t /web
systemctl restart httpd
systemctl enabled httpd
sudo chcon -t system_u /web
ls -Zl /web
ls -Zld /var/www/html
sudo chcon -t system
yum intall semanage* -y
semanage fcontext -a -t httpd_sys_content_t "/web(/.*)?"
restorecon -Rv /web/
exit
#systemctl restart --now httpd
apachectl configtest
curl localhost

getsebool -a (To see all policy status)
setsebool <Policy_name> on (To turn a policy on, Temporarily)
setsebool -P <Policy_name> on (To turn a policy on, Permanently)
```

```
On Server:
ansible all -m command -a 'sestatus' 
ansible all -m command -a 'getenforce' 
ansible all -m command -a 'cat /etc/selinux/config' 
ansible all -m command -a 'sestatus | grep "Loaded policy name"' (To check selinux policy type)
ansible all -m ansible.posix.selinux -a 'setenforce 0" (Change selinux mode to Permissive temporarily)
ansible all -m shell -a "getsebool -a" (To see all policy status)
ansible all -m shell -a "setsebool <boolean_name> 1" (To turn a policy on, Temporarily)

ansible all -m shell -a 'touch /tmp/test_selinux.txt' (to create a file)
ansible all -m command -a 'ls -lZ /tmp/test_selinux.txt' (To see selinux context)

ansible all -m command -a 'ls -lZ /var/www/html' 
ansible all -m shell -a 'dnf install httpd"

ansible all -m shell -a 'echo "THIS IS THE ANSIBLE TEST PAGE" > /var/www/html/index.html'
ansible all -m shell -a "ls -Zl /var/www/html/index.html"
ansible all -m shell -a "chcon -t httpd_sys_content_t /var/www/html/index.html (To set context)
ansible all -m shell -a "systemctl restart --now httpd"
ansible all -m shell -a "curl localhost" 
ansible all -m shell -a "restorecon -Rv var/www/html/index.html" 
ansible all -m shell -a "command -v semanage" (To check semanage tool availability on hosts)
ansible all -m shell -a "semanage fcontext -a -t httpd_sys_content_t "/var/www/html.*)?"' (To set the context permanently)
ansible all -m shell -a "semanage fcontext -d-t httpd_sys_content_t "/var/www/html.*)?"' (To remove the context permanently)
ansible all -m shell -a 'ps -eZ | grep httpd' (To see the context upon a particular process)
ansible all -m shell -a 'semanage port -l | grep http_port_t'(Selinux port context upon certain port)
ansible all -m shell -a 'semanage port -a -t http_port_t -p tcp 8085' (To add a port to the service so the web client can access the web server)
```
2nd half
```
firewalld
ansible all -m shell -a "rpm -qa | grep firewalld" (To check if firewalld is installed)
ansible all -m shell -a "systemctl status firewalld --no-pager" 
ansible all -m shell -a "systemctl start firewalld"
ansible all -m shell -a "firewalld --version"
ansible all -m shell -a "firewall-cmd --get-default-zone"
ansible all -m shell -a "firewall-cmd --get-zone"
ansible all -m shell -a "firewall-cmd --get-active-zone"
ansible all -m shell -a "firewall-cmd --list-all" 
ansible all -m shell -a "firewall-cmd --list-services"
ansible all -m shell -a "firewall-cmd --add-port=80/tcp"
ansible all -m shell -a "firewall-cmd --list-ports"
ansible all -m shell -a "firewall-cmd --reload"
ansible all -m shell -a "firewall-cmd --add-port=8080/tcp --permanent"
ansible all -m shell -a "firewall-cmd --add-port=5000-5010/tcp --permanent"
ansible all -m shell -a "firewall-cmd --remove-port=8080/tcp --permanent"
ansible all -m shell -a "firewall-cmd --zone=public --list-all"
ansible all -m shell -a "firewall-cmd --zone=public --permanent --add-service=http" 
ansible all -m shell -a "firewall-cmd --reload"
ansible all -m shell -a "ip -br addr" (Which interfaces are connected to which zone)
ansible all -b -m shell -a "firewall-cmd --permanent --zone=public --add=interface=ens160"
ansible all -b -m shell -a "firewall-cmd --permanent --set-default-zone=private"
ansible all -m shell -a "firewall-cmd --permanent --add-rich-rule='rule family=ipv4 source address=192.168.10.10 --add-service=http reject'"
ansible all -b -m shell -a "firewall-cmd --list-rich-rules"
ansible all -m shell -a "firewall-cmd --permanent --remove-rich-rule='rule family=ipv4 source address=192.168.10.10 reject'"
ansible all -b -m shell -a "firewall-cmd --list-rich-rules"
ansible all -b -m shell -a "firewall-cmd --permanent --add-rich-rule='rule family=ipv4 source adderss=192.168.10.10 service name=http accept'"
ansible all -b -m shell -a 

AT(One time executable) vs Recurring automation (Re occurring task)
Crontab:Recurring automation
ansible all -m shell -a "rpm -qa | grep crontab"
sudo vim /etc/crontab
ansible all -m shell -a "systemctl start --now crond"
ansible all -m shell -a "touch /home/ansible/test/cron-date.log" 
ansible all -m shell -a "crontab -l"
ansible all -m shell -a '(crontab -l 2>>/dev/null; echo "* * * * * date >> /home/ansible/cron-date.log") | crontab -'
ansible all -m shell -a "crontab -l"
ansible all -m shell -a "cat /home/ansible/cron-date.log"
ansible all -m shell -a "cat /home/ansible/test/cron-date.log"
ansible all -m shell -a '(crontab -l 2>>/dev/null; echo "#ANSIBLE CRON TEST"; echo "* * * * * date >> /home/ansible/cron-date.log") | crontab -'
ansible all -m shell -a '(crontab -l 2>/dev/null df -h;>> echo "45 17 * * * date >> /home/ansible/test/cron-disk-monitor.log") | crontab -'
ansible all -m shell -a "cat /home/ansible/test/cron-disk-monitor.log"
ansible all -m shell -a "cat 
```

29-08-26
One Time Automation

at now +2 minutes 
at> mkdir -p /dir1/dir2
at> cp -v /etc/* /dir1/dir2/
at> <EOT>

at> (To check)

Recurring Automation
rpm -qa | grep cron-* (To check if cron rpm is loaded)
crontab -e -u test 
10	12	* 	* 	*	mkdir ~/dir3

systemctl restart --now crond (Restart cron daemon)
 


ansible all -m shell -a "rpm -qa | grep crontab" (To check current crontab)
ansible all -m shell -a "systemctl is-active crond"
ansible all -m shell -a "systemctl enable --now crond"
ansible all -m shell -a "cat > /tmp/cront-test.sh << "EOF"
>#!/bin/bash
>echo "I am Ironman"
>date
>hostname

ansible all -m shell -a "ls -l /tmp/cron-test.sh"

ansible all -m shell -a "chmod o+x /tmp/cron-test.sh"

ansible all -m shell -a "ls -l /tmp/cron-test.sh"

ansible all -m shell -a "/tmp/cron-test.sh" (Check manually

ansible all -m shell '(crontab -l 2> /dev/null/; echo "* * * * *  /tmp/cron-test.sh 
>> /tmp/cron-output.log 2>&1") | crontab -' 

ansible all -m shell -a "ls -l /tmp/cron-output.log"

An ansible Playbook is a file containing step by step instruction for automating tasks on the managed node.
it is mainly written in .yaml(yet another markup language) language.

*every .yaml file starts with three dash and end with three dot.

```
---
- name:  playbook1
  hosts:  all
  become: true
 
  tasks:
  - name:  mytask
    ansible.builtin.ping:
```

ansible-playbook <palybook_name>.yml (To run a playbook)
```
---
- name: File and Directory Management
  hosts: all
  become: true
  
  tasks:
	- name: Create Directory
	  ansible.builtin.file: 
		path: /opt/ansible
		state: directory
		mode: '0755'

	- name: Create File
	  ansible.builtin.file:
		path: /opt/ansible/file1.txt
		state: touch
		mode: '0644'

	- name: Write content
	  ansible.builtin.copy
		content: "This is my first file\n"
		dest: /opt/ansible.file1.txt
		mode: '0644'
```
Normal Variable
```
---
- name: Normal Variable Example
  hosts: all

  vars:
	student_name: "Rahul"
	course_name: "Ansible"
	operating_system: "RHEL 9"
	
	tasks:
	  
	  - name: Display student name
	    ansible.builtin.debug: 
	      msg: "student Name: {{ student_name }}"
	  
	tasks:
	  - name: Display Student  Course
	    ansible.builtin.debug:
		msg: "Student Course Name: {{ course_name }}"
	
	tasks:
	  - name: Display Operating System
	    ansible.builtin.debug:
		msg: "Working Operating System: {{ operating_system }}"
```


Numeric Variable:
```
---
- name: Numeric Variable Example 
  hosts: all
  vars:
    
    server_count: 2
    port_number: 8080
    
  tasks:
    
    - name: Display Server Count
      ansible.builtin.debug: 
	msg: "Number of Servers: {{ server_count }}"
    
    - name: Display Port
      ansible.builtin.debug:
	msg: " Application Port: {{ port_number }}"
```
 
Boolean Variable:
```
---
- name: Boolean Varible Example 
  hosts: all
  
  vars:
     
    web_server_enabled: true
    testing_enabled: false
   
  tasks:
  
    - name: Display web server status
      ansible.builtin.debug:
	msg: "Web server Enabled: {{ web_server_enabled }}"
	
    - name: Display Testing Status
      ansible.builtin.debug: 
	msg: "Testing Enabled: {{ testing_enabled }}"
```

Array Variable:
```
---
- name: Array Variable Example
  hosts: all

  vars:
  
    students: 

	- Ram
	- Shyam
	- Jadu
	- Madhu

  tasks: 

     - name: Display Complete student list
       ansible.builtin.debug:
	 var: students
	
     - name: Display First student
       ansible.builtin.debug:
	 msg: "Student 1: {{ students[0] }}"

     - name: Display Second Student Details
       ansible.builtin.debug:
 	 msg: "Student 2: {{ students[1] }}"
```
       



