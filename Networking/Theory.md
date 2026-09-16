NFS Enumeration
nmap -p 111,2049 -sV 192.168.9.129
nmap -p 111,2049 --script=nfs-ls,nfs-showmount,nfs-statfs 192.168.9.129

##### **Automatic Private IP Addressing (APIPA):**
a networking feature that **automatically assigns an IP address (range 169.254.0.1 - 169.254.255.254) to a device when it cannot connect to a DHCP server.** It acts as a failover to enable **local network communication** when automatic address assignment fails. Useful for temporary or emergency connectivity.


# Subnetting
Subnetting in seconds https://cidr.xyz/

# Defence in Depth:
- Switch: VLAN
- Router: ACL
- Firewall

**When data arrives over a network, the IP address identifies the computer, while the port number identifies the application/service that should receive the data.**

Port numbers range from **0 to 65,535**.

### 1. Well-known ports: 0–1023 

These **ports are traditionally assigned to common, fundamental network services**.

|  Port | Protocol/Service | Purpose                 |
| ----: | ---------------- | ----------------------- |
| 20/21 | FTP              | File transfer           |
|    22 | SSH,SFTP         | Secure remote login, Secure File Transfer Protocol |
|    23 | Telnet           | Remote login (insecure) |
|    25 | SMTP             | Sending email           |
|    53(TCP+UDP) | DNS              | Domain-name resolution  |
|    80 | HTTP             | Web traffic             |
|   110 | POP3             | Receiving email         |
|   143 | IMAP             | Receiving email         |
|   443 | HTTPS            | Secure web traffic      |

DNS uses both TCP and UDP on port 53:
- UDP 53 → normally used for **regular DNS queries because it's fast and has low overhead**.
- TCP 53 → used **when the response is too large for the UDP exchange, for zone transfers, and in other situations requiring TCP**.

---

### 2. Registered ports: 1024–49151

These ports are commonly **used by particular applications or vendors**. They can be **registered with IANA**, but unlike well-known ports, they aren't reserved only for fundamental system services.

Examples include:

| Port | Common use                              |
| ---: | --------------------------------------- |
| 1433 | Microsoft SQL Server                    |
| 3306 | MySQL                                   |
| 3389 | Remote Desktop Protocol (RDP)           |
| 5432 | PostgreSQL                              |
| 8080 | Common alternative HTTP/web server port |

---

### 3. Ephemeral ports: 49152–65535

These are temporary ports typically used by a computer when it **initiates an outgoing connection**.

For example, suppose you open:

```text
https://example.com
```

Your computer might create a connection like:

```text
Your computer                    Web server
192.168.1.10:52341  ---------->  93.184.216.34:443
       ↑                                  ↑
 ephemeral port                      HTTPS port
```

Here:

* `192.168.1.10` → your computer's IP address
* `52341` → temporary/ephemeral source port
* `93.184.216.34` → web server's IP
* `443` → destination HTTPS port

The operating system chooses an available ephemeral port, such as `52341`. When the connection finishes, that port can later be reused.


---

# IPv4 Addresses:
- **32bit** long
- **Dotted Decimal Format**, consists of four octets (8 bits each, 4 octets)
- Classes **Total addresses -1 network address, -1 broadcast address, 1 Gateway address.**  IP Addresses are divided into classes to determine the size of the network.
  - Class A IP Address can produce **16 Million Hosts**, It gives us 126 networks and highest host/network
  - Class B IP Address can produce **65,534 Hosts**.
  - Class C IP Address can produce **254 Hosts** It gives us the most network and smaller hosts per network.
-  **Subnet Mask helps identify which portion of IPv4 is Network and Host**. e.g., Class C Default Subnet Mask: 255.255.255.0
  - **Network Portion**: Identifies the specific **network to which the device is connected. The number of bits used for the network portion depends on the subnet mask.**
  - **Host Portion**: Identifies the specific **device (or host) within that network**. The remaining bits after the network portion make up the host portion. 
- Special IPv4 Addresses 
  - **Loopback Address: 127.0.0.1, used for testing and troubleshooting on the local machine**.
  - **Broadcast Address**: An address used to **send data to all possible destinations within a network** (e.g., 192.168.1.255).
  - **Private Addresses**: Used for **local communications within a private network** and not routable on the internet.
  - **Unicast IP Address**: **A single sender and a single recipient**. Each unicast address uniquely identifies a device on the network. Usage: Commonly used for typical network communication, such as between a **client and a server**.
  - **Broadcast IP Address**: Sends data from **one sender to all possible recipients within the network segment**. Usage: **ARP requests or DHCP discovery messages**.
  - **Multicast IP Address**: **One sender to multiple specified recipients**. Example: 224.0.0.0 to 239.255.255.255 are reserved for multicast addresses in IPv4. Usage: Commonly used in **streaming media, online gaming**, and applications where data needs to be delivered to multiple devices simultaneously. 
- CIDR(**Classless Inter Domain Routing**): It means **taking a class of IP and dividing it**. So thats how a class less network it made. e.g., Class C Default CIDR Value: The CIDR notation = /24

 <img width="554" height="289" alt="image" src="https://github.com/user-attachments/assets/14c4be89-6a9c-493b-a864-1a07eed0fe14" />



## Must Remember Chart
| IPv4 Class  | First Octet Range | IP Address Range              | Default Subnet Mask | CIDR    | Private IP Range                                   | Typical Use                 |
| ----------- | ----------------: | ----------------------------- | ------------------- | ------- | -------------------------------------------------- | --------------------------- |
| **Class A** |           `1–126` | `1.0.0.0 – 126.255.255.255`   | `255.0.0.0`         | `/8`    | `10.0.0.0 – 10.255.255.255` (`10.0.0.0/8`)         | **Large networks**          |
| **Class B** |         `128–191` | `128.0.0.0 – 191.255.255.255` | `255.255.0.0`       | `/16`   | `172.16.0.0 – 172.31.255.255` (`172.16.0.0/12`)    | **Medium-sized networks**   |
| **Class C** |         `192–223` | `192.0.0.0 – 223.255.255.255` | `255.255.255.0`     | `/24`   | `192.168.0.0 – 192.168.255.255` (`192.168.0.0/16`) | **Small networks**          |
| **Class D** |         `224–239` | `224.0.0.0 – 239.255.255.255` | **N/A**             | **N/A** | **None**                                           | **Multicast**               |
| **Class E** |         `240–255` | `240.0.0.0 – 255.255.255.255` | **N/A**             | **N/A** | **None**                                           | **Experimental / Reserved** |

## IPv4 Subnetting

Subnetting a /24:
**Original Network**: 192.168.1.0/24
**Network bits** = 24, Host bits = 8
**Hosts per network** = 2⁸ – 2 = 254 (minus 2 for network & broadcast)
So we have Only 1 network.

Subnet into /26:
Now **Network bits** = 26, Host bits = 6
**Hosts per subnet** = 2⁶ – 2 = 62
**Number of subnets** created = 2^(26-24) = 4 networks
So now instead of 1 network with 254 hosts You have:
**4 networks with 62 hosts each**

**Terms**:
- FLSM (**Fixed Length Subnet Mask**): Subnetting method where **all subnets use the same subnet mask and have equal size**.
- VLSM (**Variable Length Subnet Mask**): Subnetting method where **subnets use different subnet masks to create subnets of varying sizes**.
