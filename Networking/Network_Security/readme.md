# Router Privilege Levels and Their Configuration:


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

