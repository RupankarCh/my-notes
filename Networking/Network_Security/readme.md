# Router Privilege Levels and Their Configuration:
**Privilege levels control what commands a user can execute**. They are part of Cisco IOS’s basic access-control mechanism. Level 2-14 can be customized to create role-based access, while level 15 provides full administrative access.

## 1.Configure passwords for privilege levels:
```
Router(config)# enable secret level 5 <password>
Router(config)# enable secret level 10 <password>
```
now 'Router> enable 5' and 'Router> enable 10' will ask for different passwords for different privileges 

## 2.Assign required commands to a lower privilege level
```
Router(config)# privilege exec level 5 configure terminal (Allows privilege level 5 users to enter global configuration mode using configure terminal)
Router(config)# privilege configure level 5 interface (Allows level 5 users to use the interface command from global configuration mode)
Router(config)# privilege interface level 5 shutdown (Allows level 5 users to use the shutdown command inside interface configuration mode)
Router(config)# privilege exec level show running-config (Allows level 5 users to run show running-config from EXEC mode)
```

## 3.Create users and assign them a privilege level
```
Router(config)# username <user_name> privilege 5 secret <Password>
Router(config)# username <user_name> privilege 15 secret <password> (Creates a local user with privilege level 15, giving that user full administrative privileges)
```
After this when you login 'Router(config)# line console 0, Router(config-line)# login local' you will be prompted for username and password.
The privilege level of those users will be predefined

# Access Control List:
**set of filter rules placed on routers, switches, or firewalls to permit or deny data packets.**

## Standard ACL (Close to destination)
**Filter traffic using only the source IP address, They block or allow an entire protocol suite, Numbered 1–99** and 1300–1999.
```
#access-list 10 deny host <src_IP>
access-list 10 permit any
int 
ip access_group 10 out
```

## Extended ACL (Close to Source)
**Filter traffic using source and destination IPs, specific protocols (TCP/UDP), and port numbers. They offer precise traffic control. (Numbered 100–199** and 2000–2699).
```
#access-list 100 deny icmp host <src_IP> host <dst_IP>
access-list 101 permit ip any any
int <Interface_name>
ip access-group 101 in
```

## Name Based ACL
**Use alphanumeric names** instead of numbers for easier identification and management.
```
#ip access-list extended <Name>
deny tcp host <src_IP> host <dst_IP> eq 80
permit tp any any
int <Interface_name>
ip access-group <Name> out
```


# AAA Authentication
**Authentication, Authorization and Accounting. A framework to control and monitor access to network devices.**

1. Authentication "Who are you": Verifies the identity of a user using credentials.
2. Authorization "What you can do": Determines the commands privileges and resources that an authenticated user is allowed to access.
3. Accounting "What did you do": It records and tracks user's activities.

