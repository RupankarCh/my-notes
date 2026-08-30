# SELinux:
*A Linux security system that controls what users and programs are allowed to access.* 

**DAC(Discretionary Access Control): Permission Based Security**
**MAC(Mandatory Access Contol): Policy/Label-Based Security**

## MODE of SELINUX:
1.Enforcing(default in Redhat): Policy is active and provide highest level of security. **It blocks and logs the unauthorized access.**
2.Permissive: selinux doesn't block unauthorized access but **log file will be generated.**
3.Disabled: selinux is totally **disabled.**

## Two main concepts of SELinux:
- **Labeling (User:role:type:level)**
- Type enforcement


Note: It may crash your system as it automatically relabels file system when changing from the disabled state to permissive or enforcing mode. If it's disabled at first set to permissive mode run the command  'autogenerate .autorelabel file' and set enforcing and then reboot the system.

## Boolean:
Just by setting some **pre-defined properties to either ON or OFF manage what services can accesses**
Ex: Ftp server to access home dir



## Important Directories:
**/etc/selinux/config (selinux configuration file)
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
chcon -t <type> <file_name> (To change the lebel type)
getsebool -a (To check Boolean)
semanage boolean -l (To check Boolean)
setsebool -P <bool_name> on/off (To set boolean)
```
