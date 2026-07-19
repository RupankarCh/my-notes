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

# Make Custom inventory file as default inventory file:
```
ansible --version (To see default inventory file)
vim /etc/ansible/ansible.cfg 
[defaults]
inventory = /home/teacher/inventory
:wq
su - teacher
ansible all --list-hosts (To check)
```

# SSH Password Based Authentication: (Delete the custom inventory file)
```
password based authentication
su - teacher
rm -rf inventory/
cd /etc/ansible/hosts
vim hosts
[dev]
node1
node2
su - teacher
ansible all --list-hosts
vim ansible.cfg
[defaults]
inventory = /home/teacher/inventory
host_key_checking = false
:wq
ansible dev -m ping -k 
mkdir inventory 
cd inventory/
vim nodes
[dev]
node1
node2
:wq
exit
vim /etc/ansible/hosts
su - teacher
ansible dev -m ping -k
```

# SSH Passwordless Authentication
