1. Create an inventory called inventory as per the following specification.
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

2. Write a playbook called intranet.yml as per the following specifications.
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
