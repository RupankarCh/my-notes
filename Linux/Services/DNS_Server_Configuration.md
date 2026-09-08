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
#systemctl start NetworkManager
#vim /etc/resolve.conf
search tata.com
nameserver 192.168.10.10
#vim /etc/named.comf
11 Change the IP to our IP
12 Comment out this line as we don't need IPv6
19 Change localhost to any
#vim /etc/named.rfc1912.zones
17 Change the domain name to tata.com
19 Change file name as forward.zone
35 Change the IP as 10.168.192
37 Change the file name as reverse.zone
#cd /var/named/
#ll
#cp named.localhost forward.zone
#cp named.lookup reverse.zone
#vim forward.zone
2 @ IN SOA srv.tata.com. root.srv.tata.com. (
8 IN NS srv.tata.com.
9 srv IN A 192.168.10.10
10 Remove
#vim reverse.zone
2 @ IN SOA srv.tata.com. root.srv.tata.com. (
8 IN NS srv.tata.com.
9 Remove A record <10(IP)> IN PTR srv.tata.com.
#chgrp named forward.zone
#chgrp named reverse.zone
#systemctl start named
#dig srv.tata.com
#nslookup <192.168.10.10>
```
