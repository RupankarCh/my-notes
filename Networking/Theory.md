##### **Automatic Private IP Addressing (APIPA):**
a networking feature that **automatically assigns an IP address (range 169.254.0.1 - 169.254.255.254) to a device when it cannot connect to a DHCP server.** It acts as a failover to enable local network communication when automatic address assignment fails.


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
