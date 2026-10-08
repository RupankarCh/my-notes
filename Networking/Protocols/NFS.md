# Network File System
It allows Linux/Unix computers to share file and directory over a network, so another system can access them. 

## NFS Enumeration:
```
#nmap -sV -p111,2049 <target_IP> (To Check If NFS is running on the target system)
#nmap -p111,2049 --script=nfs* <target_IP> (To run all scripts named nfs from NSE)

