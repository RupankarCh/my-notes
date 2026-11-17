# SNMP Enumeration
SNMP (Simple Network Management Protocol) enumeration is used to collect information about network devices such as routers, switches and servers. It may reveal **Network interfaces and IP addresses**, **Routing information**, **Device details and system information**.

# DLL hijacking
An attack in which attacker stores a malicious dll file in the earlier path based on the application's search order and the malicious dll file gets executed with the trusted application's privilege.

# HTTP Tunneling
Encapsulates other traffic inside HTTP/HTTPS.	

# SOCKS proxy 
**allows network traffic to pass through another system**. In an authorized penetration-testing laboratory, Metasploit can use a compromised lab machine as a pivot point to reach an isolated internal network.

# PowerShell Execution Policy 
A feature that controls the conditions under which PowerShell scripts can run. e.g., Restricted, AllSigned, RemoteSigned, Unrestricted. Execution Policy is designed mainly to prevent accidental script execution, not to prevent determined attackers from executing malicious code.

# Micro-segmentation 
A security technique that divides a network into very small, **isolated segments and applies individual access-control policies to each segment**.

# Sysmon Event ID 3
Network Connection records network connections made by processes.

# Object Manager 
Helps manage the corresponding object and its access. When an application opens a file, Windows creates or provides a handle that allows the application to access that file.
Main Functions:
1. Creates and manages system objects.
2. Maintains object names and directories.
3. Controls object handles.
4. Manages object security and access permissions.
5. Handles object references and resource management.

# BITS (Background Intelligent Transfer Service) 
A Windows service used to transfer files between computers in the background.
Why attackers misuse BITS:
1. It supports background file transfers.
2. Transfers can continue even when applications are closed.
3. It can operate using normal Windows service mechanisms.
4. Attackers may abuse BITS jobs to download malicious files.
5. Unauthorized BITS jobs can help maintain access or persistence.

# Dirty COW (Copy-On-Write) 
A privilege-escalation vulnerability discovered in the Linux kernel in 2016. Its root cause was a race condition in the kernel's Copy-On-Write (COW) memory-management mechanism.
Working:
1. Linux uses Copy-On-Write to avoid unnecessary memory duplication.
2. When a process attempts to modify shared memory, the kernel should create a private copy.
3. Due to a race condition, the kernel could incorrectly handle simultaneous memory operations.
4. This could allow an unprivileged user to modify read-only memory under certain conditions.


# Data exfiltration 
unauthorized transfer of files or sensitive information from a compromised system to another machine.
Three common methods are:
1. Netcat: Transfers data through TCP network connections.
2. HTTP/HTTPS: Transfers files through web-based communication.
3. SCP/SFTP: Transfers files using encrypted SSH-based communication.

# Bridged Networking 
A network configuration in virtualization where a virtual machine connects directly to the physical network through the host computer's network adapter.

| TCP SYN Scan | TCP Connect Scan |
|---|---|
| Uses the TCP three-way handshake partially. | Completes the full TCP three-way handshake. |
| Does not normally establish a complete connection. | Establishes a complete connection. |
| Also called a half-open scan. | Also called a full-connect scan. |
| Generally faster. | Generally slower. |
| Uses `-sS`. | Uses `-sT`. |
| Usually requires raw-packet privileges. | Can work without raw-packet privileges. |

# Reverse shell 
allows a remote system to initiate a connection back to another machine, through which commands may be communicated.
| Netcat | PowerShell TCP Socket |
|---|---|
| Uses the Netcat utility. | Uses built-in PowerShell networking capabilities. |
| Requires Netcat to be available. | Can use .NET TCP socket classes. |
| Supports network communication through TCP. | Supports TCP communication through native Windows functionality. |
| May be detected as an unauthorized network utility. | May be monitored through PowerShell logging and endpoint security. |

# WMIC (Windows Management Instrumentation Command-line) 
A Windows administration utility used to **retrieve system and service information.**
How it can be abused:
1. Identify services using WMIC.
2. Examine their executable paths.
3. Find paths containing spaces without quotation marks.
4. Check whether an earlier interpreted location is writable by an unprivileged user.
5. If exploitable, an attacker may place an unauthorized executable in that location.

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

# cron
*/15 9-17 * * 1-5
| Field | Value | Meaning |
|---|---|---|
| Minute | `*/15` | Every 15 minutes |
| Hour | `9-17` | From 9 AM to 5 PM |
| Day of Month | `*` | Every day |
| Month | `*` | Every month |
| Day of Week | `1-5` | Monday to Friday |
