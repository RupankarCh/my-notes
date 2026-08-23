# Terminologies:
- Upstream/Uplink: **Data traveling from you → toward the internet/server**. Example: uploading a photo, sending a message, or making a video call.
- Downstream/Downlink: **Data traveling from the internet/server → to you**. Example: downloading a movie or receiving a webpage.

# CGNAT(Carrier-Grade NAT): 
**CGNAT allows an ISP to let many customers share a limited number of public IPv4 addresses by performing NAT inside the ISP's network.**

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
Hundreds or thousands of customers can potentially share the same public IPv4 address, differentiated by TCP/UDP port numbers.

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

Internal connection	Public connection
100.64.12.25:40000 ->	49.50.60.70:25000

How to identify CGNAT

Look at the WAN/Internet IP address shown by your router.

If it is in:

100.64.0.0 – 100.127.255.255

that's the address range specifically reserved for Carrier-Grade NAT.



