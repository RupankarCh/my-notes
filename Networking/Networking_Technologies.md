# Terminologies:
- Upstream/Uplink: **Data traveling from you → toward the internet/server**. Example: uploading a photo, sending a message, or making a video call.
- Downstream/Downlink: **Data traveling from the internet/server → to you**. Example: downloading a movie or receiving a webpage.
- WAN = the network your router connects to
- LAN = the network your router provides to your devices

# CGNAT(Carrier-Grade NAT): 
**CGNAT allows an ISP to let many customers share a limited number of public IPv4 addresses by performing NAT inside the ISP's network.Hundreds or thousands of customers can potentially share the same public IPv4 address, differentiated by TCP/UDP port numbers.**


## Why ISPs use CGNAT

The main reason is **IPv4 address exhaustion**. There are only about 4.3 billion IPv4 addresses, and ISPs may have millions of customers.
Instead of giving every customer a unique public IPv4 address, an ISP can do:
```
Customer A ─┐
Customer B ─┤
Customer C ─┼── CGNAT ──→ One public IPv4 address
Customer D ─┤
Customer E ─┘
```

The main reason is IPv4 address exhaustion. There are only about 4.3 billion IPv4 addresses, and ISPs may have millions of customers.
With CGNAT, there is an additional NAT layer at the ISP:
```
Your phone/PC
192.168.1.10
     ↓
Home Router NAT
     ↓
ISP private/shared address
100.64.x.x
     ↓
ISP CGNAT
     ↓
Public IPv4
49.x.x.x
     ↓
Internet
```
This is sometimes called double NAT, although CGNAT is specifically the ISP-side NAT.

The CGNAT device maintains a translation table, something like:

**Internal connection	Public connection**
100.64.12.25:40000 ->	49.50.60.70:25000


# Forward Proxy: 
Protects the client while making the request, it hides who is making the request.

# Reverse Proxy: 
A reverse proxy is a server that sits in front of your backend servers and receives requests from users on their behalf. It Protects the server it hides where the request is going.

For example, suppose your app runs internally on port 3000:
```
Internet
   ↓
example.com
   ↓
Nginx (reverse proxy)
   ↓
localhost:3000
   ↓
Your Node.js app
```
Reverse proxies are commonly used for HTTPS/TLS, load balancing, caching, hiding backend servers, routing different URLs to different services, and security/rate limiting.

# CDN: 
Network of Distributed servers, that delivers content to the user from the location closest to them.

# Cache: 
Stores frequently accessed data to reduce latency and application load.

# Load Balancer: 
Decides which server will handle your request.

# API Gateway: 
Checks if you are allowed to make a request and then route it to the right services.

# Monolith: 
Packages all the functionality user/notification in one application

# Microservices: 
Split these services into independent services, no single source of failure.

# DNS: 
Let's you find public services on the internet by name

# Service Discovery: 
Finds dynamic services talking to each other within a distributed system.

# Serverless: 
runs your services when triggers and stops after execution

# Container: 
runs your application continuously on an infrastructure on an infrastructure you manage.

# Bandwidth: 
Maximum capacity of data that can be transferred over a network.

# Throughput: 
Actual amount of data that's successfully transferred.

# Rate Limiting: 
Blocks the request above a defined threshold to protect your system. 

# Throttling: 
Slows the request to manage them without blocking them completely.

# Synchronous Communication: 
Requires the sender and the receiver to be available at the same time.

# Asynchronous Communication: 
A sender fires a request and the receiver processes the request whenever its ready.

# Replication: 
Keeps a live copy of data to serve traffic instantly

# Backup: 
A snapshot of the data you restore when something breaks 

