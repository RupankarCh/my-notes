# Standard ACL (Close to destination)
```
#access-list 10 deny host <src_IP>
access-list 10 permit any
int 
ip access_group 10 out
```

# Extended ACL (Close to Source)
```
#access-list 100 deny icmp host <src_IP> host <dst_IP>
access-list 101 permit ip any any
int <Interface_name>
ip access-group 101 in
```

# Name Based ACL
```
#ip access-list extended <Name>
deny tcp host <src_IP> host <dst_IP> eq 80
permit tp any any
int <Interface_name>
ip access-group <Name> out
```
