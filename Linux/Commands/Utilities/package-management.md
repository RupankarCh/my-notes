| Command / Tool    | Meaning                                        | Example                     | Result                                              |
| ----------------- | ---------------------------------------------- | --------------------------- | --------------------------------------------------- |
| `.rpm`            | RPM package file used in Red Hat-based systems | `package.rpm`               | Installable software package for **Fedora/RHEL/CentOS** |
| `apt`             | Package manager for **Debian**-based distros   | `sudo apt update`           | Updates package lists                               |
| `pacman`          | Package manager for **Arch** Linux             | `sudo pacman -Syu`          | Sync + update system                                |
| `dnf`             | **Modern RPM** package manager                 | `sudo dnf install htop`     | Installs package                                    |
| `yum`             | **Legacy RPM** package manager                 | `sudo yum update`           | Updates packages                                    |
| `mandb`           | Update manual page database                    | `sudo mandb`                | Rebuilds man page index                             |
| `go` / Go Modules | Go dependency/package manager                  | `go install package@latest` | Installs Go package                                 |

Note: Use Go when creating software, especially fast CLI tools, servers, cloud tools, or portable binaries.
Use APT/Pacman/DNF when installing software.
---

# APT (Debian / Kali / Ubuntu)

| Command                 | Meaning                       | Example                      | Result                            |
| ----------------------- | ----------------------------- | ---------------------------- | --------------------------------- |
| `apt update`            | Refresh package list          | `sudo apt update`            | Downloads latest package metadata |
| `apt upgrade`           | Upgrade installed packages    | `sudo apt upgrade`           | Updates installed software        |
| `apt search text`       | Search package                | `apt search editor`          | Finds matching packages           |
| `apt list`              | List packages                 | `apt list`                   | Shows all known packages          |
| `apt list --upgradable` | Show upgradeable packages     | `apt list --upgradable`      | Lists outdated installed packages |
| `apt install pkg`       | Install package               | `sudo apt install tree`      | Installs `tree`                   |
| `apt remove pkg`        | Remove package                | `sudo apt remove tree`       | Removes package                   |
| `apt purge pkg`         | Remove package + config files | `sudo apt purge tree`        | Deletes package fully             |
| `apt source pkg`        | Download source code          | `apt source bash`            | Downloads source package          |
| `apt download pkg`      | Download `.deb` only          | `apt download htop`          | Saves package file locally        |
| `apt show pkg`          | Show package info             | `apt show tree`              | Displays version/details          |
| `apt install golang-go` | Install Go language           | `sudo apt install golang-go` | Installs Go compiler              |

---

# DPKG (Local Debian Packages)

| Command            | Meaning                   | Example                  | Result                          |
| ------------------ | ------------------------- | ------------------------ | ------------------------------- |
| `dpkg -i file.deb` | Install local `.deb` file | `sudo dpkg -i opera.deb` | Installs package                |
| `dpkg -r pkg`      | Remove package            | `sudo dpkg -r opera`     | Removes package                 |
| `dpkg -P pkg`      | Purge package             | `sudo dpkg -P opera`     | Removes package + config        |
| `dpkg -l`          | List installed packages   | `dpkg -l`                | Shows installed packages        |
| `dpkg -l pkg`      | Show package info         | `dpkg -l tree`           | Shows installed package details |

---

# Snap Package Manager

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

# Downloading Packages

| Command    | Meaning                     | Example                          | Result                 |
| ---------- | --------------------------- | -------------------------------- | ---------------------- |
| `wget URL` | Download file from internet | `wget https://site.com/file.deb` | Downloads package file |

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

