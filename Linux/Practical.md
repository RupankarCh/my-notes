# 1.Disk Quota
**Instance Creation:**
EC2> Launch Instance> Name it> Select RHEL 10 as AMI> Create key pair with .ppk extension> Enable auto-assign public IP> Launch Instance.

**Connecting to Instance:**
Open PuTTy paste the public IP of the instance> THen SSH, Auth, Credentials and Browse the key and press open, enter ec2-user> sudo -i

**Adding the Volume:**
EBS> Volumes> Create volume> Select Size, Availability zone will be same as instance> Create volume.

Select the instance, Actions> Storage> Attach volume> Select Volume> Attach Volume.

**Configuration of Disk Quota:**
```
fdisk /dev/nvme1n1 (Opens the disk partitioning utility to create, delete, or modify partitions on the new EBS volume.)
mkfs.ext4 /dev/nvme1n1p1 (Formats the first partition with the ext4 filesystem.)
mkdir /data 
mount /dev/nvme1n1p1 /data (Mounts the partition at /data.)
vi /etc/mtab (Opens the list of currently mounted filesystems (usually not edited manually).)
```
Go to last line enter Esc yy  (Copies(yanks) the current line in vi)
Esc:n /etc/fstab (Opens the /etc/fstab file in vi, filesystem table for permanent mount configuration)
Esc p (Pastes the copied line below the current line.)
Esc: wq
```
yum install quota (Installs the disk quota management package.)
yum list installed quota (Verifies that the quota package is installed.)
useradd a
useradd b
useradd c
useradd d
groupadd quota
usermod -g quota b (Changes user b's primary group to quota.)
vi /etc/fstab 
```
Write realtime, usrquota, grpquota 
Esc: wq
```
(**usrquota** Enables user disk quotas on the filesystem, **grpquota** Enables group disk quotas on the filesystem)
systemctl daemon-reload (Reloads systemd configuration after configuration changes.)
mount -o remount /data (Remounts /data with the updated mount options.)
mount | grep /data (Displays the mount information for /data.)
passwd root
passwd a
chmod 777 /data
quotacheck -cug /data (Creates and initializes user and group quota database files for /data.)
edquota a (Opens the quota editor to set disk limits for user a.)
```
blocks soft 100000, hard 200000
inodes soft 10, hard 20
```
(blocks Sets a soft limit of 100000 KB and hard limit of 200000 KB for disk space, indoes Limits the user to 10 files before warning and a maximum of 20 files.)
quotaon /data (Enables quota enforcement on the mounted filesystem.)
su - a
cd /data/
touch a.user{1..21}.txt
```

17.07.26
```
passwd root
passwd user
chgrp quota /data (Changes the group ownership of /data to the quota group.)
edquota -g quota (Opens the quota editor to configure group quotas for the quota group.)
quotaoff /data (Disables quota enforcement on /data.)
quotaon /data (Re-enables quota enforcement on /data.)
su - a
cd /data
touch abc{1..700} (Creates 700 empty files to test group or inode quota limits.)
```
