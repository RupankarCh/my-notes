# OSI Model:
A seven-layer framework that standardizes network communication: 
1 Physical – Hardware components (cables, signals)  
2 Data Link – MAC addresses, switches  
3 Network – IP addressing, routing  
4 Transport – TCP/UDP protocols for reliable transmission  
5 Session – Manages session interactions between applications  
6 Presentation – Translates, encrypts, compresses data 
7 Application – Provides direct network services (web browsers, emails) 

# TCP/IP Model:
TCP/IP Model The standard protocol suite for internet communication, divided into four layers: 
Link Layer – Handles physical connectivity (Ethernet, Wi-Fi)  
Internet Layer – Manages IP addressing and routing  
Transport Layer – Ensures reliable delivery via TCP/UDP  
Application Layer – Enables web browsing, email, file transfers 


# Internet Architecture
The **Internet isn't a single centralized entity; it is a global "network of networks" held together by shared physical infrastructure, routing protocols, and open governance standards**.

---

## The Physical & Architectural Hierarchy

The physical Internet functions as a multi-tiered hierarchy that moves data across the globe in milliseconds:

* **Subsea Cables & Fiber Backbones:** The physical foundation. High-capacity fiber-optic cables running across ocean floors and continents carry over 95% of international data traffic.
* **Tier 1 ISPs:** Global backbone providers (such as Level 3/Lumen, Telia, NTT, AT&T) that own or lease massive transcontinental infrastructure. They connect directly to each other via non-monetary agreements called **peering**.
* **Internet Exchange Points (IXPs):** Physical locations where different networks, Tier 1/2 ISPs, and major content delivery networks (CDNs like Cloudflare, Akamai, Google) meet to exchange traffic directly to shorten data paths and reduce latency.
* **Tier 2 ISPs:** Regional providers that buy wholesale internet access (transit) from Tier 1 ISPs and peer with each other at IXPs to cover specific countries or regions.
* **Tier 3 ISPs (Local ISPs):** Consumer-facing providers that buy access from Tier 2/1 providers to connect end-users (homes, businesses).

```
[ Your Device ] ──> [ Tier 3 ISP ] ──> [ Tier 2 ISP ] ──> [ IXP / Tier 1 Backbone ] ──> [ Server / CDN ]

```

---

## What an ISP (Internet Service Provider) Does

An ISP acts as your gateway to this global infrastructure. Its primary functions include:

* **Last-Mile Access:** **Delivering physical connectivity to your home/business via Fiber, Coaxial Cable, DSL, 5G, or Satellite.**
* **Addressing & Configuration:** Assigning your network or router a public IP address (via DHCP) so other devices on the internet can find you.
* **Routing Traffic:** Directing your outgoing packets toward their destination using dynamic routing protocols like **BGP (Border Gateway Protocol)**.
* **DNS Resolution:** Providing default Domain Name System servers to translate human-readable domain names (like `google.com`) into numeric IP addresses (`142.250.190.46`).
* **Bandwidth Management:** Allocating speed limits, managing network congestion, and providing firewall security at the edge.

---

## The Governing & Standards Authorities

Because no single entity owns the Internet, key non-profit and technical organizations maintain order across hardware, protocols, and address assignment.

| Organization | Full Name | Primary Role & Function |
| --- | --- | --- |
| **IEEE** | Institute of Electrical and Electronics Engineers | **Physical & Data Link Standards (Layers 1 & 2):** Defines hardware-level protocols. Famous for the **IEEE 802** standards, including **802.3 (Ethernet)** and **802.11 (Wi-Fi)**. |
| **IETF** | Internet Engineering Task Force | **Network Protocols (Layers 3 & 4):** An open standards organization that develops core Internet protocols (IP, TCP, UDP, HTTP, BGP, TLS). Outputs standards as **RFCs** (Request for Comments). |
| **IANA** | Internet Assigned Numbers Authority | **Global Resource Allocation:** Responsible for the global coordination of IP address allocation (IPv4/IPv6), Autonomous System Numbers (ASNs), and root zone management in the Domain Name System (DNS). *Managed operationally by ICANN.* |
| **ICANN** | Internet Corporation for Assigned Names and Numbers | **DNS & Domain Names:** Oversees IANA and coordinates the global DNS root server network, generic Top-Level Domains (gTLDs like `.com`, `.org`), and country-code TLDs (`.in`, `.us`). |
| **IAB** | Internet Architecture Board | **Technical Oversight:** Operates as a committee of the Internet Society (ISOC) to provide structural oversight of IETF activities and guide long-term internet architecture. |
| **ITU** | International Telecommunication Union | **Global Telecom Standards:** A specialized agency of the United Nations that sets international telecommunications regulations, radio spectrum allocations, and satellite orbits. |

### How They Work Together (An Example)

When you connect your phone to Wi-Fi and load a webpage:

1. **IEEE** standards (`802.11ax`) govern the radio wave communication between your phone and router.
2. Your **ISP** routes your request across the Tier 2/1 networks using IP addresses managed globally by **IANA**.
3. **IETF** protocols (`TCP`, `TLS 1.3`, `HTTP/2`) package, encrypt, and deliver the web content reliably.
4. **ICANN** ensures that when you typed the website domain, the DNS system properly mapped it to the right server address.
