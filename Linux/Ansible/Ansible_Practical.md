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
:wq
su - teacher
ansible all --list-hosts (To check)
```

# 5. Remote Login
## SSH Password Based Authentication: (Delete the custom inventory file)
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

