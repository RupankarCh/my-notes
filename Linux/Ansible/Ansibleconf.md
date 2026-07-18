Ansible Server Configuration
```
nmcli connection modify ens160 ipv4.addresses 192.168.10.1/24 ipv4.gateway 192.168.10.1 ipv4.method manual 
systemctl restart network-online.target 
hostnamectl set-hostname ansible-server.india.com
vim /etc/hostname
vim /etc/hosts
192.168.10.1 ansible-server.india.com ansible
192.168.10.2 node1.india.com node1
192.168.10.3 node2.india.com node2
```

Ansible Node1 Configuration
```
nmcli connection modify ens160 ipv4.addresses 192.168.10.2/24 ipv4.gateway 192.168.10.1 ipv4.method manual 
systemctl restart network-online.target 
hostnamectl set-hostname node1.india.com
vim /etc/hostname
vim /etc/hosts
192.168.10.1 ansible-server.india.com ansible
192.168.10.2 node1.india.com node1
192.168.10.3 node2.india.com node2
```
Ansible Node2 Configuration
```
nmcli connection modify ens160 ipv4.addresses 192.168.10.3/24 ipv4.gateway 192.168.10.1 ipv4.method manual 
systemctl restart network-online.target 
hostnamectl set-hostname node1.india.com
vim /etc/hostname
vim /etc/hosts
192.168.10.1 ansible-server.india.com ansible
192.168.10.2 node1.india.com node1
192.168.10.3 node2.india.com node2
```
