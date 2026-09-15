Prerequisite:

Yum repository configuration
hostname_server: nfsserver.bwu.com
IP_server: 192.168.10.10
hostname_client: nfsclient.bwu.com
IP_client: 192.168.10.11

Server:
```
#yum install nfs-utils -y
#systemctl enable nfs-server.service --now
#systemctl status nfs-server.service
#rpcinfo -p | grep nfs (To see nfs is running on which port)
#mkdir -p /mnt/nsf_server/docs
#chown -R nobody: /mnt/nfs_server/docs/
#chmod -R 777 /mnt/nfs_server/docs/
#vim /etc/exports
/mnt/nfs_server/docs 192.168.10.11(rw,sync,no_all_squash,root_squash)
#systemctl start nfs-server.service
#exportfs -arv
#firewall-cmd --add-service=nfs --permanent
#firewall-cmd --add-service=rpc-bind --permanent
#firewall-cmd --add-service=mountd --permanent
#firewall-cmd --reload 
#firewall-cmd --list-all
```

Client:
```
#yum install nfs-utils nfs4-acl-tools -y
#showmount -e 192.168.10.10
#mkdir -p /mnt/nfs_client/
#mount -t nfs 192.168.10.10:/mnt/nfs_server/docs /mnt/nfs_client/
#cd /mnt/nfs_client
```

Server:
```
#cd /mnt/nfs_server/docs/
#echo Hi > nfs.txt
```
Client:
```
#useradd abc
#su abc
#mkdir folder
```

Server:
```
#ll
#useradd abc
#ll
```



