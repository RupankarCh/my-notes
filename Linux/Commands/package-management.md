Note: 
**APT / DNF / Pacman / Zypper manage system software** on Linux distros and to manage **application software snap** like package manager is used.
Go Modules manages Go libraries and Go-based tools for Go development.

| Command / Tool    | Meaning                                        | Example                     | Result                                              |
| ----------------- | ---------------------------------------------- | --------------------------- | --------------------------------------------------- |
| `.rpm`            | RPM package file used in Red Hat-based systems | `package.rpm`               | Installable software package for **Fedora/RHEL/CentOS** |
| `apt`             | Package manager for **Debian**-based distros   | `sudo apt update`           | Updates package lists                               |
| `pacman`          | Package manager for **Arch** Linux             | `sudo pacman -Syu`          | Sync + update system                                |
| `dnf`             | **Modern RPM** package manager                 | `sudo dnf install htop`     | Installs package                                    |
| `yum`             | **Legacy RPM** package manager                 | `sudo yum update`           | Updates packages                                    |
| `mandb`           | Update manual page database                    | `sudo mandb`                | Rebuilds man page index                             |
| `go` / Go Modules | Go dependency/package manager                  | `go install package@latest` | Installs Go package                                 |


---

# APT (Debian / Kali / Ubuntu)

| Command                 | Meaning                       | Example                      | Result                            |
| ----------------------- | ----------------------------- | ---------------------------- | --------------------------------- |
| `apt update`            | Refresh package list          | `sudo apt update`            | Downloads latest package metadata |
| `apt upgrade`           | Upgrade installed packages    | `sudo apt upgrade`           | Updates installed software        |
| `apt search <text>`     | Search package                | `apt search editor`          | Finds matching packages           |
| `apt list`              | List packages                 | `apt list`                   | Shows all known packages          |
| `apt list --upgradable` | Show upgradeable packages     | `apt list --upgradable`      | Lists outdated installed packages |
| `apt install <pkg>`     | Install package               | `sudo apt install tree`      | Installs `tree`                   |
| `apt remove <pkg>`      | Remove package                | `sudo apt remove tree`       | Removes package                   |
| `apt purge <pkg>`       | Remove package + config files | `sudo apt purge tree`        | Deletes package fully             |
| `apt source <pkg>`      | Download source code          | `apt source bash`            | Downloads source package          |
| `apt download <pkg>`    | Download `.deb` only          | `apt download htop`          | Saves package file locally        |
| `apt show <pkg>`        | Show package info             | `apt show tree`              | Displays version/details          |
| `apt search <pkg>`      | Search package                | `apt search editor`          | Finds packages                    |
| `apt install golang-go` | Install Go language           | `sudo apt install golang-go` | Installs Go compiler              |

---

# DPKG 
(**Local Debian** Packages, means it can’t access other repositories outside the machine.But it can install packages by downloading the file with a deb extension.)

| Command            | Meaning                   | Example                  | Result                          |
| ------------------ | ------------------------- | ------------------------ | ------------------------------- |
| `dpkg -i file.deb` | Install local `.deb` file | `sudo dpkg -i opera.deb` | Installs package                |
| `dpkg -r pkg`      | Remove package            | `sudo dpkg -r opera`     | Removes package                 |
| `dpkg -P pkg`      | Purge package             | `sudo dpkg -P opera`     | Removes package + config        |
| `dpkg -l`          | List installed packages   | `dpkg -l`                | Shows installed packages        |
| `dpkg -l pkg`      | Show package info         | `dpkg -l tree`           | Shows installed package details |

---

# Snap Package Manager (Manage application softwares in a universal package format across multiple Linux distributions)

| Command             | Meaning              | Example                   | Result                |
| ------------------- | -------------------- | ------------------------- | --------------------- |
| `apt install snapd` | Install Snap utility | `sudo apt install snapd`  | Installs Snap support |
| `snap find pkg`     | Search snap package  | `snap find opera`         | Finds packages        |
| `snap list`         | Show installed snaps | `snap list`               | Lists installed snaps |
| `snap install pkg`  | Install snap package | `sudo snap install opera` | Installs package      |
| `snap remove pkg`   | Remove snap package  | `sudo snap remove opera`  | Removes package       |

---

# Arch Linux (Pacman)

| Command           | Meaning            | Example               | Result           |
| ----------------- | ------------------ | --------------------- | ---------------- |
| `pacman -Syu`     | Full system update | `sudo pacman -Syu`    | Updates packages |
| `pacman -S pkg`   | Install package    | `sudo pacman -S htop` | Installs package |
| `pacman -R pkg`   | Remove package     | `sudo pacman -R htop` | Removes package  |
| `pacman -Ss text` | Search package     | `pacman -Ss editor`   | Searches repo    |
| `pacman -Qi pkg`  | Show package info  | `pacman -Qi bash`     | Package details  |

---

# DNF / YUM (Fedora / RHEL)

| Command           | Meaning               | Example                 | Result           |
| ----------------- | --------------------- | ----------------------- | ---------------- |
| `dnf update`      | Update packages       | `sudo dnf update`       | Updates system   |
| `dnf install pkg` | Install package       | `sudo dnf install tree` | Installs package |
| `dnf remove pkg`  | Remove package        | `sudo dnf remove tree`  | Removes package  |
| `dnf search text` | Search package        | `dnf search editor`     | Finds packages   |
| `yum update`      | Legacy update command | `sudo yum update`       | Updates packages |

---

# Downloading Packages (In your current directory)

| Command    | Meaning                     | Example                          | Result                 |
| ---------- | --------------------------- | -------------------------------- | ---------------------- |
| `wget <URL>` | Download file from internet | `wget https://site.com/file.deb` | Downloads package file |

---

# Repositories

| Command                 | Meaning                   | Example                           | Result                   |
| ----------------------- | ------------------------- | --------------------------------- | ------------------------ |
| `lsb_release -a`        | Show distro info/codename | `lsb_release -a`                  | Shows version + codename |
| `/etc/apt/sources.list` | APT repository file       | `sudo nano /etc/apt/sources.list` | Add/edit repositories    |

---

# Most Used Quick Commands

| Task             | Debian/Ubuntu     | Fedora             | Arch             |
| ---------------- | ----------------- | ------------------ | ---------------- |
| Update repo list | `apt update`      | `dnf check-update` | `pacman -Sy`     |
| Upgrade system   | `apt upgrade`     | `dnf upgrade`      | `pacman -Su`     |
| Install package  | `apt install pkg` | `dnf install pkg`  | `pacman -S pkg`  |
| Remove package   | `apt remove pkg`  | `dnf remove pkg`   | `pacman -R pkg`  |
| Search package   | `apt search pkg`  | `dnf search pkg`   | `pacman -Ss pkg` |

```
curl <link of the package> -o <package_name> (To download the file in the package name itself)
rpm -ivh <package_name> (To install an RPM package)
rpm -qa (To show installed RPM packages)
tree /var/log (To show directory structure)
rpm -e <package_name> (To erase/delete an package)
yum search <package_name> (To find the desired package)
yum install epel-release -y (To install another repository)
yum update (To update all the packages)
yum clean all (Clean the local cache)

Service Mgmt

systemctl start <service_name>
systemctl status <service_name>
systemctl restart <service_name> 
systemctl reload <service_name> 
systemctl enable <service_name> 

When you install a service 

cat /etc/systemd/system/multi-user.target.wants/<package_name> (To see the configuration file of the package)
```
