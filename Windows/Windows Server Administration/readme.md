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

## DNS Name Space: 
organized structure of all domain names
www.example.com Domain name
- . → Root
- com → TLD (2 Types Basic and Country code)
- example → Second-Level Domain 
- www → Subdomain (For Web)/ Child Domain (For Active Directory environment)



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

