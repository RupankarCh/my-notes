Configure IP Address <192.168.10.10/24>
Configure Hostname <srv.tata.com> 
```
#vim /etc/hosts (192.168.10.10 is mapped with the fqdn and if I only type srv on URL bar it directs to the IP)
192.168.10.10 srv.tata.com srv 
#yum install bind* -y
#dig <IP>
#vim /etc/sysconfig/network (This configuration enables global network functionality (NETWORKING=yes) and explicitly sets the system's persistent fully qualified domain name (HOSTNAME=srv.tata.com).)
NETWORKING=yes
HOSTNAME=srv.tata.com
#systemctl start NetworkManager (NetworkManager daemon automatically configures, monitors, and manages active network interfaces and connections)
#vim /etc/resolve.conf (search tata.com automatically appends .tata.com to any short hostname you type (e.g., typing ping srv automatically queries srv.tata.com), and nameserver 192.168.10.10 directs your system to send all local and internet DNS queries to the DNS server at that IP)
search tata.com
nameserver 192.168.10.10
#vim /etc/named.conf (to listen for requests on your local network interface and allows external clients to query it)
11 Change the IP to our IP
12 Comment out this line as we don't need IPv6
19 Change localhost to any
#vim /etc/named.rfc1912.zones (defines the authoritative forward and reverse lookup zones for your network, telling the BIND DNS server where to find the database files for your specific domain and IP subnet)
17 Change the domain name to tata.com
19 Change file name as forward.zone
35 Change the IP as 10.168.192
37 Change the file name as reverse.zone
#cd /var/named/ (/var/named/ directory contains the actual DNS zone database files that the BIND (named) service uses to resolve hostnames and IP addresses)
#ll
#cp named.localhost forward.zone (Rename)
#cp named.lookup reverse.zone (Rename)
#vim forward.zone (creates the authoritative mapping records for your domain, explicitly telling the DNS server that srv.tata.com points to the IP address 192.168.10.10)
2 @ IN SOA srv.tata.com. root.srv.tata.com. (
8 IN NS srv.tata.com.
9 srv IN A 192.168.10.10
10 Remove
#vim reverse.zone (defines the reverse lookup rule, which allows the DNS server to translate the IP address back into your domain name)
2 @ IN SOA srv.tata.com. root.srv.tata.com. (
8 IN NS srv.tata.com.
9 Remove A record <10(IP)> IN PTR srv.tata.com.
#chgrp named forward.zone (Change group ownership)
#chgrp named reverse.zone
#systemctl start named
#dig srv.tata.com
#nslookup <192.168.10.10>
```
