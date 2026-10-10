# Instance Creation:
EC2 Launch Instances > Name It, Select RHEL 10 as AMI, Create a key pair (ppk.), Enable Auto-assign Public IP, Configure Storage Add new volume of 30GB  Launch.

# Connecting to Instance:
Add volume after lunch Instances: (If require)
Select the Instances > Action >  Storage > Attach volume > Create New volume (size = 30GB & Make sure Availability zone should be same) > Create volume > Select Created volume > Action > Attach volume > Select Instance & Device name > Attach volume. 
Go to Instance tab > Select the Instance > connect > Copy Public IP. 
Open PuTTY  Session > Host name = Copied public IP paste hare > Expand SSH > Expand auth > Click on Credential > Browse Public key authentication > Select the key > Open > Accept.


Step1: Login
Login as: ec2-user 
Step 2: Essential command for setup 
```
# sudo passwd root  (To change password of user)
# sudo su   (Login as root user)
# lsblk  (To view Partition)
```
Step 3: Create Partition
```
# Fdisk /dev/xvdb  (To manage partition)
   n (New partition)
   p  (Primary partition)
   1  (Partition number)
   Click on Enter  (first sector) 
   Click on Enter  (Second sector)
   w  (Save/Write)
# lsblk  (To ensure)
```
Step 4: Set file system
```
# mkf.ext4 /dev/xvdb1  (Create an ext4 filesystem)
```
Step 5: Mount Partition
```
# mkdir /partition1  (To directory for mount point)
Temporary mount:
# mount /dev/xvdb1 /partition1  (To temporary mount)
Permanent Mount: 
#  vi /etc/mtab  (Edit/view mount table)
Copy the last line (Esc yy) &  exit (q!) /dev/xvdb1 /folder ext4 rw,seclabel,relatime 0 0
 # vi /etc/fstab  (Edit filesystem mount configuration)
Paste in last line ( i Esc p) & Save/Exit (wq)
```
Step 6: Install Disk Quota package 
```
# yum install quota  (Install disk quota package)
# yum list installed quota  (Check installed quota package)
```
Step 7: Create User & Group 
```
# useradd user1  (To create a user)
# groupadd quotagroup  (To create group)
```
Step 8: Add/Change user in quotagroup
```
# usermod -g quotagroup user1  (Change user's primary group)
# ip user1  ( Show user information)
```
Step 9: Enable user and group disk quotas 
```
# vi /etc /fstab  (Edit filesystem mount configuration)
/dev/xvdb1 /folder ext4 rw,seclabel,relatime,usrquota,grpquota 0 0
(usrquota,grpquota → Enable user and group disk quotas)
```
Step 10: Remount Partition & Verify 
```
# systemctl daemon-reload
# mount -o remount /folder (Remount mounted filesystem)
# mount | grep /folder  (Verify filesystem mount)
```
Step 11: 
```
# passwd root
# passwd a
# chmod 777 /folder
# quotacheck -cug /folder
# edquota a (blocks:0 soft:100000 hard:200000 inode:0 soft:10 hard:20)
# quotaon /folder
# su -a
# touch a.user{1..21}.txt
# dd if=/dev/zero of=/data/file bs=1M count=300
```

# Groupquota:
```
# chgrp quota /folder
# edquota -g quota (blocks:4 soft:100000 hard:200000 inode:1 soft:400 hard:500)
# quotaoff /folder
# quotaon /folder
# sudo usermod -aG quota b
# su - b
# cd /folder
# touch abc{1..700}.txt
```

# Modify grace period for a specific user when they exceed their soft disk quota limits:
```
# edquota -T a (Remove the time and add 7 days)
# quotaoff /folder
# quotaon /data
```
