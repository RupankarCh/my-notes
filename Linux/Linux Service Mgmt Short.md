# M1
**Disk Quota**: how much disk space and how many files a user or group can use.
Components:
- Block Quota: Controls the amount of disk space a user can consume. 1 Block = 1KB
- File Quota (Inode Quota): Controls the maximum number of files and directories a user can create.
- Grace Period: The allowed time for a user to reduce disk usage below the soft limit.
- Soft Limit: The maximum storage limit that a user can temporarily exceed during the grace period.
- Hard Limit: The absolute maximum storage limit. Users cannot store additional data after reaching this limit.
- Quota Database Files: Store information about current disk usage and assigned quotas.
Configuration:
1. Edit the /etc/fstab file and enable user quotas by adding the usrquota option.
2. quotacheck -cug /home (Create quota database files)
3. edquota username (Assign storage limits)
4. edquota -t (Set the grace period)
5. quota username (Monitor user storage)

---

**Methods available for static IP configuration in Linux**:
- Configuration File Method: using interface configuration files /etc/sysconfig/network-scripts/
- nmcli connection modify "System eth0" ipv4.addresses 192.168.1.10/24
- nmtui (Text User Interface)
- GUI (Graphical User Interface)

nmcli connection show
nmcli connection modify "System eth0" ipv4.method manual

Classful addressing divides IPv4 addresses into fixed classes such as A, B and C. It uses fixed network and host portions.
- Class A: 255.0.0.0
- Class B: 255.255.0.0
- Class C: 255.255.255.0

Classless IP Addressing (CIDR):
It uses variable-length subnet masks (VLSM) to allocate IP addresses according to network requirements.

--- 

# M2

**Berkeley Internet Name** Domain is used to implement DNS (Domain Name System) on Linux systems
Roles:
- Name Resolution (Forward and Reverse Lookup)
- Make the system work as DNS server
- maintains DNS zone files
- It supports primary and secondary DNS servers through zone transfers

- Main configuration file: /etc/named.conf
- Zone files directory: /var/named/
- Service name: named
- DNS port: 53
- Package: bind



