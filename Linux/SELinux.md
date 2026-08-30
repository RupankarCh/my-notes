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
# 1. Create website 
#mkdir /web
vim /web/index.html

# 2. Configure Apache
yum install httpd -y
systemctl enable --now httpd
vim /etc/httpd/conf/httpd.conf
# DocumentRoot "/web"
systemctl restart httpd

# 3. Check SELinux context
ls -Zld /var/www/html
ls -Zl /web/index.html

# 4. Create permanent SELinux rule
semanage fcontext -a -t httpd_sys_content_t "/web(/.*)?"
(semanage fcontext Manage SELinux file-context rules, -a Add a rule, -t httpd_sys_content_t Assign the SELinux type httpd_sys_content_t, "/web(/.*)?" Apply it to /web and everything inside /web.)

# 5. Apply the rule
restorecon -Rv /web/ (It applies the SELinux context rule you just created.)

# 6. Verify
ls -Zl /web/index.html

# 7. Restart Apache
systemctl restart httpd

# 8. Test
curl localhost
```

