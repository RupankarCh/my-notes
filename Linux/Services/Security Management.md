# SELinux:
*A Linux security system that controls what users and programs are allowed to access.* 

**DAC(Discretionary Access Control): Permission Based Security**
**MAC(Mandatory Access Contol): Policy/Label-Based Security**

## MODE of SELINUX:
1.Enforcing(default in Redhat): Policy is active and provide highest level of security. **It blocks and logs the unauthorized access.**
2.Permissive: selinux doesn't block unauthorized access but **log file will be generated.**
3.Disabled: selinux is totally **disabled.**

## Types of SELinux:
1.STRICT (Every service/daemon)
2.TARGETED (For a perticular service/daemon)
3.MLS=> MULTI LEVEL SECURITY

## Two main concepts of SELinux:
- **Labeling (User:role:type:level)**
- Type enforcement


Note: It may crash your system as it automatically relabels file system when changing from the disabled state to permissive or enforcing mode. If it's disabled at first set to permissive mode run the command  'autogenerate .autorelabel file' and set enforcing and then reboot the system.

## Boolean:
Just by setting some **pre-defined properties to either ON or OFF manage what services can accesses**. selinux boolean allows administrator to enable or disable certain policy or behaviour without creating a complete new selinux policy. 
Ex: Ftp server to access home dir



## Important Directories:
**/etc/selinux/config (selinux configuration file, change selinux mode permanently)
etc/selinux/targeted/contexts/files/file_contexts (Context storage)**

## Commands:
```
sestatus (To check current status)
getenforce (To check current mode)
setenforce 0 (set mode to Permissive/Disable temporarily)
setenforce 1 (set mode to Enable temporarily)
vim /etc/selinux/config (Edit SELINUX=<Mode_name> change mode permanently)
ls -lZ (To check lebel of directory/file)
ps axZ | grep httpd (To check lebel of a perticular process)
netsat -taZ | grep httpd (To check the label of a socket (ex: httpd))
cd /var/www/html 
journalctl -b 0 (To check for errors on selinux)
/sbin/restorecon -v /var/www/html/index.html (to change the lebel type)
chcon -t <label_type> <file_name> (To change the lebel type)
semanage fcontext -a -t httpd_sys_content_t "/web(/.*)?" (Create a permanent context rule)
restorecon -Rv /web/ (Apply the permanent rule)
getsebool -a (To See all booleans)
semanage boolean -l (To check Boolean)
setsebool <Policy_name> on (To turn a policy on, Temporarily)
setsebool -P <bool_name> on/off (To set boolean)

```
## SELinux and Apache Practical:
Apache wants to serve /web/index.html, but SELinux may block it unless the file has the correct SELinux context.
```
1. Create website 
#mkdir /web
#vim /web/index.html

2. Configure Apache
#yum install httpd -y
#systemctl enable --now httpd
#vim /etc/httpd/conf/httpd.conf
Listen 82
DocumentRoot "/web"
<Directory "/web">
#systemctl restart httpd

Document
3. Check SELinux context
#ls -Zld /var/www/html
#ls -Zl /web/index.html

4. Create permanent SELinux rule
#semanage fcontext -a -t httpd_sys_content_t "/web(/.*)?"
(semanage fcontext Manage SELinux file-context rules, -a Add a rule, -t httpd_sys_content_t Assign the SELinux type httpd_sys_content_t, "/web(/.*)?" Apply it to /web and everything inside /web.)

5. Apply the rule
#restorecon -Rv /web/ (It applies the SELinux context rule you just created.)

6. Verify
#ls -Zl /web/index.html

7. Restart Apache
#systemctl restart httpd

8. Test
#curl localhost:82
```

# Firewalld Commands Using Two Zones

Managing the Linux firewall using `firewalld` and `firewall-cmd`. We will use two zones: `public` and `internal` as examples.

- public zone: For network interfaces connected to an untrusted or public network.
- internal zone: For a trusted internal network.

## 1. Check the Firewalld service

### Command 1

bash

```
systemctl status firewalld.service
```

Purpose: Checks whether the firewalld service is running, stopped, or failed.

### Command 2

bash

```
systemctl enable --now firewalld
```

Purpose: Enables firewalld to start automatically at boot and starts it immediately.

## 2. View available and active zones

### Command 3

bash

```
firewall-cmd --get-zones
```

Purpose: Displays all available firewall zones.

Example output:

text

```
block dmz drop external home internal public trusted work
```

### Command 4

bash

```
firewall-cmd --get-active-zones
```

Purpose: Displays currently active zones and the interfaces or source addresses assigned to them.

Example:

text

```
public
  interfaces: ens160
internal
  interfaces: ens192
```

Here, `ens160` belongs to the `public` zone, while `ens192` belongs to the `internal` zone.

### Command 5

bash

```
firewall-cmd --get-default-zone
```

Purpose: Shows the default zone used for connections or interfaces that have not been assigned to another zone.

Example:

text

```
public
```

### Command 6

bash

```
firewall-cmd --set-default-zone=public
```

Purpose: Sets `public` as the default zone.

To set `internal` as the default instead:

bash

```
firewall-cmd --set-default-zone=internal
```

## 3. View the firewall configuration of both zones

### Command 7 — Public zone

bash

```
firewall-cmd --zone=public --list-all
```

Purpose: Displays the complete runtime configuration of the public zone, including interfaces, services, ports, and rich rules.

### Command 8 — Internal zone

bash

```
firewall-cmd --zone=internal --list-all
```

Purpose: Displays the complete runtime configuration of the internal zone.

### Command 9 — List all configured zones

bash

```
firewall-cmd --list-all-zones
```

Purpose: Displays configuration details for every zone.

## 4. Allow HTTP service in the public zone

### Command 10

bash

```
firewall-cmd --zone=public --add-service=http --permanent
```

Purpose: Permanently allows the HTTP service, normally using TCP port 80, in the public zone.

The `--permanent` option saves the change but does not immediately apply it to the running configuration.

### Command 11

bash

```
firewall-cmd --reload
```

Purpose: Applies permanent firewall changes to the runtime configuration.

### Command 12

bash

```
firewall-cmd --zone=public --list-services
```

Purpose: Lists the services currently allowed in the public zone.

Example:

text

```
cockpit dhcpv6-client http ssh
```

## 5. Allow a port directly

### Command 13

bash

```
firewall-cmd --zone=public --add-port=80/tcp
```

Purpose: Opens TCP port 80 in the runtime configuration of the public zone.

Important: This command is not permanent. It will not survive a reload unless the port is also added permanently.

To make the change permanent:

bash

```
firewall-cmd --zone=public --add-port=80/tcp --permanent
firewall-cmd --reload
```

You normally need either the HTTP service rule or the port rule for HTTP traffic, not both.

## 6. Assign network interfaces to the two zones

### Command 14 — Assign interface to public

bash

```
firewall-cmd --zone=public --add-interface=ens160
```

Purpose: Assigns the `ens160` network interface to the public zone in the runtime configuration.

### Command 15 — Assign interface to internal

bash

```
firewall-cmd --zone=internal --add-interface=ens192
```

Purpose: Assigns the `ens192` interface to the internal zone in the runtime configuration.

To make both assignments permanent:

bash

```
firewall-cmd --permanent --zone=public --add-interface=ens160
firewall-cmd --permanent --zone=internal --add-interface=ens192
firewall-cmd --reload
```

Replace `ens160` and `ens192` with the actual interface names on your system.

## 7. Configure rich rules

Rich rules allow you to apply more specific firewall policies based on source IP addresses, services, ports, and actions.

### Command 16 — Allow HTTP from one IP address

bash

```
firewall-cmd --permanent --zone=public \
  --add-rich-rule='rule family="ipv4" source address="192.168.10.30" service name="http" accept'
```

Purpose: Allows HTTP traffic from `192.168.10.30` in the public zone.

- `family="ipv4"` — applies to IPv4 traffic.
- `source address="192.168.10.30"` — matches the specified source IP.
- `service name="http"` — matches HTTP service traffic.
- `accept` — allows matching traffic.
- `--permanent` — saves the rule persistently.

Apply the rule:

bash

```
firewall-cmd --reload
```

### Command 17 — Display rich rules

bash

```
firewall-cmd --zone=public --list-rich-rules
```

Purpose: Lists rich rules in the runtime configuration of the public zone.

### Command 18 — Reject traffic from a specific IP

bash

```
firewall-cmd --permanent --zone=public \
  --add-rich-rule='rule family="ipv4" source address="192.168.10.60" reject'
```

Purpose: Rejects traffic matching source IP `192.168.10.60` in the public zone.

Apply the rule:

bash

```
firewall-cmd --reload
```

`reject` normally sends a rejection response to the sender, unlike `drop`, which silently discards the traffic.

### Command 19 — Allow TCP port 8080 from a specific IP

Your original command used `apublic`, which appears to be a typo. Use `public` or `internal` as appropriate.

For the public zone:

bash

```
firewall-cmd --permanent --zone=public \
  --add-rich-rule='rule family="ipv4" source address="192.168.10.30" port port="8080" protocol="tcp" accept'
```

Purpose: Allows TCP port 8080 traffic from `192.168.10.30` in the public zone.

For the internal zone, change `--zone=public` to `--zone=internal`.

Apply and verify:

bash

```
firewall-cmd --reload
firewall-cmd --zone=public --list-rich-rules
```

### Command 20 — Correct the rich-rule listing command

Your original command was `firewal-cmd`, missing an `l`.

Correct command:

bash

```
firewall-cmd --zone=public --list-rich-rules
```

To check the internal zone:

bash

```
firewall-cmd --zone=internal --list-rich-rules
```

## 8. Open the graphical firewall configuration tool

### Command 21

bash

```
yum install firewall-config -y
```

Purpose: Installs the graphical firewalld configuration utility on compatible RHEL-based systems.

- `yum install` — installs the package.
- `firewall-config` — the graphical firewall management application.
- `-y` — automatically confirms installation prompts.

On newer RHEL-based systems, you can also use:

bash

```
dnf install firewall-config -y
```

Launch the graphical utility from a desktop terminal:

bash

```
firewall-config
```

The GUI lets you manage zones, services, ports, interfaces, and rich rules.

## 9. Final verification commands

Run these commands after configuring both zones.

bash

```
# Check the service
systemctl status firewalld

# Check active zones and assigned interfaces
firewall-cmd --get-active-zones

# Check the default zone
firewall-cmd --get-default-zone

# Check public zone
firewall-cmd --zone=public --list-all

# Check internal zone
firewall-cmd --zone=internal --list-all

# Check all rich rules in public
firewall-cmd --zone=public --list-rich-rules

# Check all rich rules in internal
firewall-cmd --zone=internal --list-rich-rules

# Display permanent configuration for public
firewall-cmd --permanent --zone=public --list-all

# Display permanent configuration for internal
firewall-cmd --permanent --zone=internal --list-all
```

## Quick reference: Two-zone example

| Configuration | Public zone | Internal zone |
| --- | --- | --- |
| Network interface | `ens160` | `ens192` |
| HTTP service | Allow | Not explicitly allowed |
| TCP port 8080 | Allow from `192.168.10.30` | Not explicitly allowed |
| Blocked source | Reject `192.168.10.60` | No rule specified |
| Intended network | Public/untrusted | Trusted/internal |

The table describes the example policy, not the complete effective firewall state. Other services, rules, and zone defaults can affect the final result.

Remember these three concepts:

- Runtime: Changes that take effect immediately but may be lost after reload or reboot.
- Permanent: Changes saved for future use; apply them with `firewall-cmd --reload`.
- Zone: A collection of firewall policies assigned to network interfaces or source addresses.
