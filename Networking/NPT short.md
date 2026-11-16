# SNMP Enumeration
SNMP (Simple Network Management Protocol) enumeration is used to collect information about network devices such as routers, switches and servers. It may reveal **Network interfaces and IP addresses**, **Routing information**, **Device details and system information**.

# DLL hijacking
An attack in which attacker stores a malicious dll file in the earlier path based on the application's search order and the malicious dll file gets executed with the trusted application's privilege.

# HTTP Tunneling
Encapsulates other traffic inside HTTP/HTTPS.	

# SOCKS proxy 
**allows network traffic to pass through another system**. In an authorized penetration-testing laboratory, Metasploit can use a compromised lab machine as a pivot point to reach an isolated internal network.

# WMIC (Windows Management Instrumentation Command-line) 
A Windows administration utility used to **retrieve system and service information.**

# HAL
HAL stands for Hardware Abstraction Layer. It is a component of Windows that provides an interface between the operating system kernel and the computer hardware.
Main Functions:
1. Hides hardware-specific details from the operating system.
2. Provides a standard interface for hardware communication.
3. Helps Windows operate on different hardware platforms.
4. Manages hardware-related operations such as interrupts and input/output communication.

- NetBIOS: Reveals computer names and workgroups.
- SMB: Reveals shared folders, permissions and accessible resources.
- NFS: Reveals exported directories and their access permissions.

# Important concepts to memorize for the exam

| Topic | Remember |
|--------|--------|
| SMB | TCP 445 |
| NetBIOS Name Service | UDP 137 |
| SNMP | UDP 161 |
| NFS | TCP/UDP 2049 |
| HTTP | TCP 80 |
| HTTPS | TCP 443 |
| SSH | TCP 22 |
| Nmap `-sn` | Host discovery |
| Nmap `-sV` | Service/version detection |
| Nmap `-O` | OS detection |
| Nmap `-Pn` | Skip host discovery |
| Nmap `-A` (Aggressive Scan) | Service Banner, Authentication Requirements, Enables OS detection, version detection, script scanning and traceroute to collect detailed information about the target|
| DLL Hijacking | Malicious DLL loaded from an unsafe location |
| HTTP Tunneling | Carries other traffic through HTTP/HTTPS |
| Lateral Movement | Moving from one compromised system to another |

# Defense for Port Forwarding and Lateral Movement if a system gets compromised
- Firewall Rules: Block unnecessary incoming and outgoing connections.
- Network Segmentation: Separate critical systems into different network zones.
- Access Control: Apply least-privilege permissions.
- Monitoring: Monitor unusual network connections and port-forwarding activities.
- MFA: Implement Multi-Factor Authentication for remote access.
- Regular Auditing: Identify and remove unnecessary port-forwarding rules.

# Legacy FTP alternatives
| Protocol | Purpose |
|---|---|
| SFTP | Secure file transfer over SSH |
| FTPS | FTP secured using TLS encryption |
| SCP | Secure file copying over SSH |

# Metasploit-based workflow to set up a SOCKS proxy and pivot into an internal network:
One Windows machine that is connected to both networks your and company's network.
1. Initial Access: Establish a test session with the compromised windows machine.
2. Network Discovery: Identify the internal network accessible through that machine.
3. SOCKS Proxy Setup: Configure a SOCKS proxy through Metasploit session.
4. Traffic Routing: Configure tools to communicate through the proxy.
5. Internal Enumeration: Identify internal hosts and services.
6. Documentation: Record the discovered systems and security weaknesses.

# Three Primary Zones:
1. External Zone: The untrusted network, usually the internet.
2. DMZ (Demilitarized Zone): A separate network **containing publicly accessible services** such as web and mail servers.
3. Internal Zone: The trusted private network containing sensitive systems, databases and organizational resources.
