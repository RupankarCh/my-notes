# 1. **IP Address Configuration, Hostname Change:**
<img width="612" height="248" alt="WhatsApp Image 2026-06-11 at 8 27 41 AM" src="https://github.com/user-attachments/assets/dd6ea055-e689-4665-bc29-c4db9c685fe7" />

```
#nmtui (To configure IP address)
```
Edit a connection> Select the interface> IPv4 Address Show> Enter the Content and OK> Back> Activate a connection> deactive and activate and Back> Quit
If connection is not getting active
```
#nmcli connection up
#ifconfig (To check)
#hostnamectl set-hostname newhostname (To change hostname)
```
# 2.**Configure an YUM repository** 
**(remember /etc/yum.repos.d/x.repo is a YUM/DNF repository configuration file that contains definitions of software repositories (repository ID, name, base URL, GPG settings, enable/disable options, etc.) used by the package manager to install and update packages.)**

<img width="736" height="283" alt="WhatsApp Image 2026-06-11 at 8 28 09 AM" src="https://github.com/user-attachments/assets/1bf3685b-22e5-4035-a827-a8138643501c" />

```
#df -Th (To check if /dev/s0 exists on your system means the hardware device (the virtual CD/DVD drive) exists and has a disc inserted/attached inside it, If you see sr0 then start from Part 2, otherwise only disks like sda, vda, nvme0n1, etc., then there is no attached ISO so proceed)
```
Depending on your environment:

VMware Workstation
Power off the VM (or edit settings while powered on if supported).
Go to VM → Settings → CD/DVD.
Select Use ISO image file.
Browse to your RHEL 10 ISO.
Check Connected and Connect at power on.
Start the VM.

VirtualBox
Open Settings → Storage.
Select the empty optical drive.
Choose the RHEL 10 DVD ISO (Only DVD iso contains BaseOS and AppStream)
Start the VM.
After attaching the ISO

Part 2:
```
lsblk
```
You should see something like:
sr0    11:0    1 10G 0 rom
If not then proceed If yes then start from Part 3

Then mount it:
```
mkdir -p /mnt/cdrom
mount /dev/sr0 /mnt/cdrom
```
Verify:
```
ls /mnt/cdrom
```
You should see directories such as:
AppStream
BaseOS
media.repo

Part 3: Configure Local YUM Repository
Check the mount point
```
ls /run/media/rupankar/RHEL-10-2-BaseOS-x86_64
```
You should see: AppStream, BaseOS, EFI, images, media.repo
#mkdir /root/foldername (To keep the main "RHEL installation DVD/ISO" untouched, it contains **operating system installation files, boot loaders, and the entire catalog of software packages**.) 

#cp -rvf /run/media/rupankar/RHEL-10-2-BaseOS-x86_64 /root/foldername 

Create a repository file:
```
#vim /etc/yum.repos.d/filename.repo
```
Add:
```
[BaseOS]
name=This is RHEL 10 BaseOS
baseurl=file:///root/foldername/RHEL-10-2-BaseOS-x86_64/BaseOS 
gpgcheck=0
enabled=1

[AppStream]
name=This RHEL 10 AppStream
baseurl=file:///root/foldername/RHEL-10-2-BaseOS-x86_64/AppStream
gpgcheck=0
enabled=1
```
Save and exit. Esc :wq if you get any error while creating the file E212/E303
rum with root previledge
rm -f /etc/yum.repos.d/.filename.repo.sw* (To cleanup)

```
#yum clean all (To Clean existing metadata)
#yum repolist (The command scans all the configuration files inside /etc/yum.repos.d/)
```
Test package installation
For example:
```
sudo dnf install httpd*
```

# 3.Create users and groups as per the following requirements
<img width="1082" height="213" alt="3" src="https://github.com/user-attachments/assets/7dbcc940-fe41-4cb9-ae6a-ce28b2ca1e42" />

```
#groupadd sysadms
#useradd -G sysadms natasha
#useradd -G sysadms jerry
#useradd -s /sbin/nologin sarah
#passwd natasha
#passwd jerry
#passwd sarah
(Checking)
#cat /etc/passwd
#cat /etc/group
#su <sarah> (user won't be able to login)
```

# 4. Setup collaborative directory
<img width="1259" height="317" alt="4" src="https://github.com/user-attachments/assets/18cf8fb9-30d3-4e15-a26f-e42efaea6fc1" />

```
#mkdir /home/newfolder
#groupadd sysadmin
#chgrp sysadmin /home/newfolder
#chmod 770 /home/newfolder
#chmod g+s /home/newfolder
(Checking)
#ls -ld /home/newfolder
```

# 5. Configure NTP Client
(remember /etc/chrony.conf contains the configuration settings for the Chrony service, including NTP servers and time synchronization options.)
<img width="806" height="209" alt="5" src="https://github.com/user-attachments/assets/c1842752-91fd-4295-8d85-5b1b6e499072" />

Your system should be configured as an NTP client of classromm example.com

```
#timedatectl set-ntp true
#vim /etc/chrony.conf
```
Comment out the third line and write "<domain.com> iburst" and save

# 6.create a user called system with ID number 2026

```
#sudo useradd -u 2026 <username>
```

# 7.Create a tar archive
<img width="1097" height="176" alt="6" src="https://github.com/user-attachments/assets/33ce5d87-f3ed-473b-ab64-ec86c169d7e6" />

Create an archive called archive.tar.bz2 which contains the contents of /usr/local directory using bzip2 compression to perform this task
using bzip2
```
#yum install bzip*
#tar -Jcvf archive.tar.bz2 /usr/local/
```
using gzip
```
#yum install gzip*
#tar -zcvf archive.tar.gz2 /usr/local/
```

Decompress Not needed
# Using gzip
gzip -d file.txt.gz   # or gunzip file.txt.gz

# Using bzip2
bzip2 -d file.txt.bz2 # or bunzip2 file.txt.bz2

# 8.Password Reset RHEL 10
**(/usr/sbin/reboot is the executable command used to safely restart the Linux system.)**
<img width="734" height="123" alt="8" src="https://github.com/user-attachments/assets/37cdcbc1-1818-4d7c-a862-351d91ecf505" />

Restart the machine first go to GRUB menu then press e to enter
```
init=/bin/bash (After the Linux line)
ctrl+x
mount -o remount,rw /
passwd root
touch /.autorelabel
/usr/sbin/reboot -f
```
login with the new passwords.


# 9.Create an Application message while login
<img width="885" height="119" alt="8" src="https://github.com/user-attachments/assets/4b3d8343-379b-4998-b2d6-bf9954128b19" />

Write an application called rhcsa which should display "EX200 Exam whenever the user abid login.

```
vim /usr/local/bin/rhcsa
```
write 
echo "EX200 Exam"
```
chmod +x /usr/local/bin/rhcsa
vim /home/abid/.bash_profile
```
write
/usr/local/bin/rhcsa

Check: su - abid

# 10.

<img width="767" height="187" alt="10" src="https://github.com/user-attachments/assets/a8c33976-987e-4716-8e7a-2aa6c922cb7c" />

```
tuned-adm active (To check Which profile the system has been configured)
tuned-adm recomended (To check the list of profile)
tuned-adm profile virtual-guest (To set the profile)
systemctl enable tuned (To start the profile service)
```

# 11. Default Umask value change

<img width="833" height="195" alt="11" src="https://github.com/user-attachments/assets/e7d4439f-c384-4558-9307-ec5051468c23" />

```
useradd sam
su - sam
touch a1
touch a2
ls -l
umask (To check value of current user)
vim /home/username/.bash_profile (To change umask value for a particular user)
vim /etc/login.defs (To change value for all users)
```
change the umask value, logout and login again

# 12.Password Policy
**(remember /etc/login.defs defines default settings for user account creation, password policies, and system login behavior.)**
<img width="896" height="124" alt="12" src="https://github.com/user-attachments/assets/ba302121-c285-4623-87f5-e46bac579c28" />

```
#vim /etc/login.defs
```
maximum date will be 2 days


# 13. 
<img width="1027" height="211" alt="WhatsApp Image 2026-06-18 at 2 43 50 PM" src="https://github.com/user-attachments/assets/4e588e3f-f209-4c5e-b4ec-392b2e0aa1fe" />

for perticular user
```
useradd sarah
crontab -e -u sarah
*/ * * * * logger "ex200"
```
:wq
crontab -lu sarah

# 14.Criteria Based Search
<img width="1218" height="171" alt="14" src="https://github.com/user-attachments/assets/1ea6607b-0706-4e4e-9e69-b1b3988e9e2f" />

```
grep "command" /usr/share/dict/word >> /root/command.txt
```


# 15.
<img width="490" height="183" alt="15" src="https://github.com/user-attachments/assets/b460110c-e30b-42a6-9d68-5fac72431553" />

```
#fdisk /dev/sda
n
p
Last: +512M
t
82
w
partprobe /dev/sda
mkswap /dev/sda1
vim /etc/fstab
/dev/sda1 swap swap defaults 0 0
swapon /dev/sda1
swapon -s
```

# 16. Search and store files
```
mkdir -p /root/filefound
find / -type f -user sarah -exec cp {} /root/filefound/ \;
```

# 17.
<img width="1705" height="291" alt="image" src="https://github.com/user-attachments/assets/9ef78ce7-ab82-41cd-b979-41f26eaa96b7" />

```
# useradd geo
groupadd dba
passwd geo
visudo
```
write

Allow root to run any commands anywhere
geo ALL=(ALL) NOPASSWD: ALL

Same thing without a passwd
%dba ALL=(ALL) NOPASSWD: ALL

save and exit.

# 18.
