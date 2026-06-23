# File Structure:
<img width="495" height="211" alt="image" src="https://github.com/user-attachments/assets/50af0dd8-e654-42c1-9e81-5b99d7c50f03" />
<img width="521" height="403" alt="image" src="https://github.com/user-attachments/assets/c55d1d38-7647-4368-90da-8a2ea8000f8e" />
<img width="523" height="388" alt="image" src="https://github.com/user-attachments/assets/4dcbbc7c-49ea-4f8f-84b5-86c1eb333e0b" />

## Some Important Directories
- Home Directories: /root, /home/username
- User Executable: /bin, /usr/bin, /usr/local/bin (Binaries or the user executable commands)
- System Executables: /sbin, /usr/sbin, /usr/local/sbin (Binaries or the user executable commands)
- Other Mountpoints: /media, /mnt (External Physical Media)
- Configuration: /etc (System Config)
- Temporary Files: /tmp (Temporary data which will get deleted when system boots)
- Kernels and Bootloader: /boot 
- Server Data: /var, /srv (Running server's data)
- System Information: /proc, /sys (Current System Utilzation details)
- Shared Libraries: /lib, /usr/lib, /usr/local/lib (Installed Programming Language Library)

# Important files to remember:


---

### Path: `/dev/sda`

**Data:**
A device file representing the **first physical disk on the system**. Additional disks are ordered as `/dev/sdb`, `/dev/sdc`, etc.

It does not contain files like a regular directory. Instead, it refers to the raw disk and its partitions (for example, `/dev/sda1`, `/dev/sda2`).

---

### Path: `/etc/fstab`

**Data:**
Used to permanently mount filesystems.

Defines disk partitions and mount points.

Example:

```text
UUID=xxxx-xxxx  /mnt/mydata  ext4  defaults  0 2
```

---

### Path: `/etc/mtab`

**Data:**
Contains information about all currently mounted filesystems.

---

## Package Management

---

### Path: `/etc/yum.repos.d/x.repo`

**Data:**
A YUM/DNF repository configuration file.

Contains:

* Repository ID
* Repository name
* Base URL
* GPG settings
* Enable/disable options

Used by the package manager to install and update packages.

---

### Path: `/etc/apt/sources.list`

**Data:**
Contains a list of repositories (URLs or paths) from which APT retrieves packages and updates on Debian-based systems.

---

## Time Synchronization

---

### Path: `/etc/chrony.conf`

**Data:**
Contains configuration settings for the Chrony service, including:

* NTP servers
* Time synchronization options

---

## User and Group Management

---

### Path: `/etc/passwd`

**Data:**
Contains basic information about user accounts.

* Plain-text file.
* Readable by all users.
* Writable only by the system administrator.

Format:

```text
Ananya:x:1001:1001::/home/Ananya:/bin/bash
```

Contains **7 fields separated by colons**:

```text
username:password:UID:GID:comment:home_directory:login_shell
```

Example:

```text
Ananya:x:1001:1001::/home/Ananya:/bin/bash
```

Field explanation:

* `Ananya` → Username.
* `x` → Masked password (actual password stored in `/etc/shadow`).
* `1001` → UID.

  * `0` → root.
  * `1–999` → system/reserved accounts.
  * `1000+` → regular users.
* `1001` → GID.
* Empty field → Comment (usually full name or description).
* `/home/Ananya` → Home directory.
* `/bin/bash` → Login shell.

Notes:

* New users are added to the bottom of the file.
* If the last field contains `/bin/bash`, the user can log in.

---

### Path: `/etc/shadow`

**Data:**
Contains encrypted password information and password aging policies.

Readable only by root or privileged processes.

Contains **9 fields separated by colons**:

```text
username:password:last_changed:min_days:max_days:warn_days:inactive_days:expire_date:reserved
```

Field explanation:

* **username** → User's login name.
* **password** → Encrypted password (`!` or `*` means account is locked).
* **last_changed** → Days since January 1, 1970 when password was last changed.
* **min_days** → Minimum days before changing password again.
* **max_days** → Maximum password validity period.
* **warn_days** → Days before expiration when user receives warning.
* **inactive_days** → Days after expiration before account becomes inactive.
* **expire_date** → Account expiration date (days since Jan 1, 1970).
* **reserved** → Reserved for future use.

---

### Path: `/etc/group`

**Data:**
Contains group information.

Groups allow permissions to be shared among users for files, directories and resources.

Contains **4 fields separated by colons**:

```text
group_name:password:GID:member_list
```

Field explanation:

* `group_name`
* `password`
* `GID`
* `member_list` → Comma-separated list of users belonging to the group.

---

### Path: `/etc/login.defs`

**Data:**
Defines default settings for:

* User account creation
* Password policies
* System login behavior

Example:

```bash
vim /etc/login.defs

PASS_WARN_AGE 7
PASS_MIN_DAYS 7
PASS_MAX_DAYS 90
```

Explanation:

* `PASS_WARN_AGE 7`

  * Users are warned 7 days before password expiration.

* `PASS_MIN_DAYS 7`

  * Users must wait 7 days before changing password again.

* `PASS_MAX_DAYS 90`

  * Password expires after 90 days.

---

### Path: `/etc/sudoers`

**Data:**
Defines which users or groups can execute commands as root.

Edit using:

```bash
sudo visudo
```

Example:

```text
username ALL=(ALL) NOPASSWD:/bin/systemctl restart
```

Allows the user to execute:

```bash
/bin/systemctl restart
```

without entering a password.

---

## PAM (Pluggable Authentication Modules)

---

### Path: `/etc/pam.d/system-auth`

**Data:**
Controls:

* Authentication (Who can log in?)
* Account management
* Password policies
* Session management

Used for:

* Local login
* Remote login
* `su`
* `sudo`
* `gdm`
* SSH

Example:

```text
password requisite pam_pwquality.so minlen=12
```

Explanation:

* `password`

  * Password-related rule.

* `requisite`

  * If the rule fails, password change immediately stops.

* `pam_pwquality.so`

  * Enforces password strength.

* `minlen=12`

  * Minimum password length is 12 characters.

---

### Path: `/etc/pam.d/password-auth`

**Data:**
Used mainly for remote authentication such as:

* SSH
* SFTP

Example:

```text
password requisite pam_pwquality.so retry=3 minlen=8 minclass=4
```

Explanation:

* `retry=3`

  * Allows 3 attempts.

* `minlen=8`

  * Minimum length is 8.

* `minclass=4`

  * Requires:

  * Uppercase letters

  * Lowercase letters

  * Numbers

  * Special characters

Example:

```text
password sufficient pam_unix.so remember=5
```

Explanation:

* `pam_unix.so`

  * Uses passwords from `/etc/shadow`.

* `remember=5`

  * Prevents reuse of the previous five passwords.

---

## Shell Configuration

---

### Path: `/etc/bashrc`

**Data:**
Executed whenever a new interactive Bash shell starts.

Contains:

* Environment variables
* Aliases
* Functions
* Startup configurations

Example:

```bash
umask o-r
```

Changes default file permissions globally and affects all users.

Apply changes without reopening terminal:

```bash
source .bashrc
```

---

### Path: `/etc/shells`

**Data:**
Contains the list of available shells installed on the system.

---

### Path: `~/.zshrc`

**Data:**
Main configuration file for Zsh.

Executed every time a new interactive shell starts.

Common contents:

* Environment variables

```bash
export PATH="$PATH:/home/kali/go/bin"
```

* Aliases
* Prompt customization
* Plugin settings
* Shell options
* Functions
* Terminal appearance tweaks

---

### Path: `/home/username/.bash_profile`

**Data:**
Executed when a user logs in.

Examples:

* SSH login
* Login shell startup

Used to configure:

* Environment variables
* PATH
* Startup commands

---

### Path: `/root/.bash_history`

**Data:**
Stores command history executed by the root user.

---

# Bootloader (GRUB)

---

### Path: `/etc/default/grub`

**Data:**
Contains default GRUB settings.

---

### Path: `/boot/grub/grub.cfg`

**Data:**
Contains GRUB boot menu entries and kernel parameters.

Each menu entry defines how a particular OS is booted.

Although manual editing is possible, regenerating using:

```bash
grub2-mkconfig
```

is recommended.

Common scenarios:

* Installing a new kernel.
* Adding or removing operating systems.
* Modifying `/etc/default/grub`.

Example:

```bash
sudo nano /etc/default/grub
```

Modify:

```text
GRUB_DEFAULT=0
```

Save:

```text
Ctrl+X
Y
Enter
```

Generate configuration:

```bash
sudo grub2-mkconfig -o /boot/grub2/grub.cfg
```

Reboot:

```bash
sudo reboot
```

---

### Command:

```bash
ls -l /boot/grub2/
```

**Data:**
The `user.cfg` file stores user-specific GRUB settings, including encrypted passwords used to protect bootloader operations.

---

## Networking

---

### Path: `/etc/resolv.conf`

**Data:**
Specifies DNS servers used to resolve domain names into IP addresses.

---

### Path: `/etc/hosts`

**Data:**
Checked before DNS servers when resolving names.

Example:

```text
127.0.0.1 facebook.com
```

Redirects requests for Facebook to localhost, effectively blocking access.

After editing, clear DNS cache or restart the browser.

---

### PATH Environment Variable

**Data:**
A list of directories searched for executables.

Example:

```text
/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin
```

When you type:

```bash
command_name
```

the shell searches these directories in order.

---

## Cron

---

### Path: `/etc/crontab`

**Data:**
Stores system-wide cron jobs.

Format:

```text
MIN HOUR DOM MON DOW USER COMMAND
```

Field meanings:

* MIN → 0–59
* HOUR → 0–23
* DOM → Day of month
* MON → Month
* DOW → Day of week
* USER → User executing the command
* COMMAND → Command to execute

A mistake in this file may prevent cron from functioning.

---

### Path: `/var/spool/cron/crontabs`

**Data:**
Stores user-specific crontab files.

Requires root access.

---

### Path: `/tmp/crontab.rwMlhv/crontab`

**Data:**
Temporary backup file created while editing crontab.

Can be used to recover unsaved changes or identify syntax errors.

---

## Logging Configuration

---

### Path: `/etc/rsyslog.d/50-default.conf`

**Data:**
Defines default logging rules and specifies where various log messages are stored.

---

## Log Files

---

### Path: `/var/log/syslog`

**Data:**

Contains:

* Startup and shutdown messages
* Service and daemon messages
* Network messages
* Errors and status messages
* Hardware events
* CRON messages (on some systems)

---

### Path: `/var/log/messages`

**Data:**
General system activity logs.

View:

```bash
cat /var/log/messages
```

---

### Path: `/var/log/secure`

**Data:**
Security-related events:

* Successful and failed logins
* SSH logins
* sudo usage
* PAM activity

View:

```bash
cat /var/log/secure
```

Audit password changes:

```bash
grep 'passwd' /var/log/secure
```

---

### Path: `/var/log/boot.log`

**Data:**
Boot-related messages.

View:

```bash
cat /var/log/boot.log
```

---

### Path: `/var/log/dmesg`

**Data:**
Kernel ring buffer messages generated during boot.

View:

```bash
cat /var/log/dmesg
```

---

### Path: `/var/log/cron`

**Data:**
Cron job logs.

View:

```bash
cat /var/log/cron
```

---

### Path: `/var/log/audit/audit.log`

**Data:**
Security audit logs.

View:

```bash
cat /var/log/audit/audit.log
```

---

### Path: `/var/log/rhsm/rhsm.log`

**Data:**
Red Hat Subscription Management logs.

View:

```bash
cat /var/log/rhsm/rhsm.log
```

---

### Path: `/var/log/firewalld`

**Data:**
Logs generated by firewalld.

View:

```bash
cat /var/log/firewalld
```

---

### Path: `/var/log/Xorg.0.log`

**Data:**
X server startup and hardware configuration logs.

View:

```bash
cat /var/log/Xorg.0.log
```

---

### Path: `/var/log/lastlog`

**Data:**
Most recent login information.

View:

```bash
lastlog
```

---

### Path: `/var/log/btmp`

**Data:**
Failed login attempts.

View:

```bash
last -f /var/log/btmp
```

---

### Path: `/var/log/wtmp`

**Data:**
Login and logout history.

View:

```bash
last
```

---

### Path: `/var/log/tuned/tuned.log`

**Data:**
Performance tuning logs.

View:

```bash
cat /var/log/tuned.log
```

---

### Path: `/var/log/maillog`

**Data:**
Mail server logs.

Examples:

* Sendmail
* Postfix

View:

```bash
cat /var/log/maillog
```

---

### Path: `/var/log/apache2/`

**Data:**
Apache web server logs (if installed).

---

### Path: `/var/log/nginx/`

**Data:**
Nginx web server logs (if installed).

---

## Metasploit

---

### Path: `/usr/share/metasploit-framework/modules/exploits`

**Data:**
Contains Metasploit exploit modules.

---

### Path: `/usr/share/metasploit-framework/modules/payloads`

**Data:**
Contains payload modules used after successful exploitation to gain control over the target.

---

## Password and Security Notes

---

### Password Aging Files

* `/etc/shadow`
* `/etc/login.defs`

---

### Authentication Logs

* `/var/log/secure`
* `/var/log/audit/audit.log`

---

### GRUB Passwords

```bash
ls -l /boot/grub2/
```

`user.cfg` stores encrypted bootloader passwords.

---


# Environment Variable: PATH

Data:
PATH is an environment variable containing a list of directories that the shell searches for executable files when you type a command.

The directories are searched from left to right.

Example:

/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin

When you type:

ls

the shell searches in the following order:

/usr/local/bin
/usr/bin
/bin
/usr/sbin
/sbin

The first matching executable found is executed.

View the current PATH:

echo $PATH

Temporarily add a directory to PATH (current session only):

export PATH="$PATH:/home/user/bin"

Permanently add a directory:

For the current user:

nano ~/.bashrc

Add:

export PATH="$PATH:/home/user/bin"

Apply changes:

source ~/.bashrc

For all users:

sudo nano /etc/profile

or

sudo nano /etc/bashrc

Add:

export PATH="$PATH:/opt/scripts"



