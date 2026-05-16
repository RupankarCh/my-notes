# OS:
- Base(Desktop Experience): GUI
- Core: CLI
- Standard Edition: normal gaming PC
- Datacenter Edition: supercomputer running hundreds of systems. It offers unlimited virtualization(You can create as many virtual machines as your hardware can handle). It includes features like Shielded VMs (It protect VMs even from the system administrator It Encrypts VM data, Preventing copying or tampering, Only trusted servers can run them, Protect against insider attacks EVAL(Evaluation): This is a trial version that is free to use for 180 days for testing and development before it must be activated with a full license.
- 14393: The OS Build Number. This identifies the specific build of the operating system.

Workgroup: Windows based peer- to-peer  computer network
Domain: a client/server network in which the security and resource management is  centralized. 
<img width="443" height="599" alt="image" src="https://github.com/user-attachments/assets/8f2c779b-2845-45e5-b9a3-d77b14da031a" />

Server: a computer or system that provides resources, data, services, or programs to  other computers, known as clients,over a network.

<img width="442" height="498" alt="image" src="https://github.com/user-attachments/assets/78afe1e3-c476-4d44-8283-d9d44bfccb2a" />

# History
| Version                 | Key Features (Keywords)                                                  | Easy Meaning                                           |
| ----------------------- | ------------------------------------------------------------------------ | ------------------------------------------------------ |
| **Windows Server 2003** | AD Improvements, IIS 6.0, Firewall, Group Policy, Backup                 | 🔐 Security started improving + basic web & AD support |
| **Windows Server 2008** | Server Manager, IIS 7.0, Hyper-V, PowerShell, RODC, NAP                  | ⚙️ Automation + Virtualization begins                  |
| **Windows Server 2012** | Advanced AD (ADDS, ADCS), BitLocker, IPAM, NIC Teaming, Hyper-V improved | 🚀 Enterprise features + better networking & security  |
| **Windows Server 2016** | Nano Server, Containers, ReFS, Shielded VMs, Nested Virtualization       | ☁️ Cloud-ready + lightweight + strong security         |
| **Windows Server 2019** | Windows Admin Center, ATP Security, Kubernetes, SDN, Storage Services    | 🤖 Hybrid cloud + AI insights + modern security        |

| Version  | Processor        | RAM (Min → Rec) | Disk (Min → Rec) | Display  |
| -------- | ---------------- | --------------- | ---------------- | -------- |
| **2008** | 1.4 GHz → 2+ GHz | 512 MB → 2 GB+  | 10 GB → 40 GB+   | 800×600  |
| **2012** | 1.4 GHz → 2+ GHz | 512 MB → 16 GB+ | 32 GB → 256 GB+  | 800×600  |
| **2016** | 1.4 GHz → 2+ GHz | 512 MB → 2 GB+  | 32 GB → 40 GB+   | 1024×768 |
| **2019** | 1.4 GHz → 2+ GHz | 2 GB → 8 GB+    | 1.5 GB → 2 GB+*  | 1024×768 |



# Name Resolution: 
The process of translating  human-friendly hostnames into IP addresses and vise versa,so that computers and other network devices can  understand.

1. **Host File:** Name Resolution begins at the local level with the hosts file, situated in **%SystemRoot%\system32\drivers\etc**. It contains mappings of IP  addresses to hostnames. Administrators can manually edit this file to add static mappings.
2. **DNS (Domain Name System):** The primary name resolution service used vy microsoft server environments. DNS operates based on a distributed database  system where various DNS servers store information about different domains.
<img width="850" height="529" alt="image" src="https://github.com/user-attachments/assets/195fbcb3-408c-4f16-a94d-cac6b69dac6a" />
  - **Forward Lookup Zone:** A DNS zone that **translates hostnames to IP addresses.** 
  - **Reverse Lookup Zone:** A DNS zone that **translates IP addresses to hostnames.**

3. **NetBIOS (Protocol):** Lets Windows computers find each other by name, Works mainly inside a local network, Uses broadcasts like  “Who is PC-01?”. **NetBIOS name refers to Device Name on This PC> Properties**.
4. **WINS (Windows Internet Name Service):** 
 - legacy name resolution service.
 - only for NetBIOS so other OSs which don't use NetBIOS can’t use WINS.
 - A server that **stores NetBIOS names and IP addresses**, Clients directly query the WINS server, The WINS server responds with the IP address 
 - WINS **uses unicast communication because broadcast can’t cross routers**, Works across different networks/subnets
 - still supported in modern Windows Server versions for backward compatibility.
 - replication process synchronizes the databases across all WINS servers in the network,  In larger networks with multiple WINS servers.

<img width="609" height="309" alt="image" src="https://github.com/user-attachments/assets/5570167b-1909-4223-9bd8-84047259d4c0" />


## **Name Resolution Step-by-step process**: (recursive resolution, **Without Forwarders and without configuring local zones**)
Even if your **Preferred DNS = 127.0.0.1**, your DNS server can still resolve internet names using Root Hints

1. You type google.com
2. Your PC asks DNS server (127.0.0.1)
3. DNS checks local zones → ❌ not found
4. DNS checks cache → ❌ not found (you missed this step)
5. DNS checks forwarders (if configured)
6. If no forwarder / no response → uses Root Hints
7. Contacts root server → gets referral to .com TLD
8. Queries .com TLD server
9. Gets referral to Google’s authoritative DNS server
10. Queries Google’s DNS server
11. Gets IP address → returns to your PC

## Advantages of DNS Server:
- Single point of failure
- Additional DNS servers can be added as needed to handle increased query loads and accommodate  network expansion.
- Caching mechanisms within DNS servers help speed up resolution by storing  previously resolved queries locally. 
- Distributing client requests across multiple servers or providing failover mechanisms in case of  server failures.

## DNS Name Space: 
organized structure of all domain names
www.example.com Domain name
- . → Root
- com → TLD (2 Types Basic and Country code)
- example → **Second-Level Domain **
- www → **Subdomain (For Web)/ Child Domain (For Active Directory environment)**

## DNS Zone:
**A portion of the domain that a DNS server is responsible for managing. Zone name and Domain name are mostly same**

1. A DNS zone is a **portion of the DNS namespace managed by a specific authority**
2. It defines the administrative boundary of control in DNS
3. **Each zone contains DNS records for domains and subdomains**
4. DNS zones are organized in a hierarchical tree structure
5. **A zone can contain one domain or multiple subdomains**
6. Authority over a zone is delegated to an organization or individual
7. **Subdomains can be kept in the same zone or delegated to separate zones**
8. Delegation requires NS records pointing to authoritative servers
9. Each zone has an SOA record defining its core settings
10. Zones allow distributed management of the global DNS system

**Dynamic Updates: DNS records are automatically updated without manual changes**
**DNS Delegation: Giving control of a subdomain to another DNS server**
**DNS Zone File: A file that stores all DNS records (A, MX, NS, etc.) for that zone**

## DNS Zone Types
1. Primary Zone
👉 **Main (original) copy of zone data, First and Single in a zone**
✔ Stored in file or AD DS
✔ Fully **editable**
When the zone is stored in a file, by default the primary zone file is named zone_name.dns and it is located in the %windir%\System32\Dns folder on the server. 

3. Secondary Zone
👉 Read-only copy of primary zone
✔ Data comes from another DNS server
✔ Used for backup & load sharing, Multiple in a zone
❌ Cannot be edited
This DNS server must have network access to the remote DNS server that supplies this server with updated information about the zone.

5. Stub Zone
👉 Contains SOA, NS, A record
✔ Helps locate authoritative DNS servers
✔ Not full data, only references
 This DNS server must have network access to the remote DNS server to copy the authoritative name server information about the zone.

7. Active Directory Integrated Zone
👉 Stored in Active Directory (not in file)
✔ Data replicates automatically
✔ More secure
✔ Works like a primary zone, uses the security feature of active directory.

## DNS Resource Records:
**Zone DNS database is a collection of resource records** and each of the records provides information about a specific object. 

| Record    | Full Form          | Main Purpose             | Easy Meaning                |
| --------- | ------------------ | ------------------------ | --------------------------- |
| **A**     | Address            | Maps domain → IPv4       | 🌐 Name → IPv4              |
| **AAAA**  | IPv6 Address       | Maps domain → IPv6       | 🌐 Name → IPv6              |
| **CNAME** | Canonical Name     | Alias to another domain  | 🔁 whatever.example.com → example.com |
| **MX**    | Mail Exchanger     | Mail server for domain   | 📧 Domain → Mail Server     |
| **NS**    | Name Server        | Authoritative DNS server | 🧭 Domain → DNS Server(Who Manages it) |
| **PTR**   | Pointer            | IP → Domain              | 🔄 Reverse lookup (IP → Domain) |
| **SOA**   | Start of Authority | Lists primary DNS server's info | 🏢 Zone's identity/Information |
| **TXT**   | Text               | Stores text data         | 📝 Info (**SPF**, verification) |
| **SRV**   | Service Record     | Service + port info      | ⚙️ where to find a specific service |
| **HINFO** | Host Info          | CPU & OS details         | 💻obsolete nowdays for sensitive information exposure |
| **ISDN**  | ISDN Address       | Telephone-based address  | ☎️ Rare/legacy              |

**SPF (Sender Policy Framework)** records – define which mail servers are allowed to send email on behalf of your domain.

## DNS Query Types:
**Iterative Query:** The DNS client sends a query to a DNS server and expects either a response with the **requested information or a referral to another DNS server** that might have the information. If the DNS server has the information, it responds with the requested data. 

**Recursive Query:** The DNS client sends a query to a DNS server and expects the DNS server to either provide the **requested information or handle the entire resolution process on behalf of the client**. The DNS server receiving the recursive query is responsible for either providing the requested information **from its cache** or contacting other DNS servers on the client's behalf to resolve the query

## DNS Zone Transfer:
A DNS zone transfer is a process where **data about a specific domain's DNS records is copied from one DNS server to another**. This is primarily used to keep multiple servers **synchronized and maintain redundancy in case one server goes down.**

• **To replicate DNS records across multiple servers for redundancy and improved performance.**
• To allow **changes made on one server (primary) to be automatically reflected on other servers (secondary).** 
• Full Zone Transfer (AXFR): **Transfers all records in the zone**, even if only one record has changed. 
• Incremental Zone Transfer (IXFR): **Transfers only the records that have changed since the last synchronization**. More efficient for frequent updates. 
