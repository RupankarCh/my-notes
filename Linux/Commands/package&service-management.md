# Linux Package Management Cheat Sheet

🎯 Focus: Debian & Fedora only

> **Easy memory rule:**
> **Debian → APT → `.deb` → `dpkg`**
> **Fedora → DNF → `.rpm` → `rpm`**

---

## 1. Package Manager

| Purpose                       | Debian / APT             | Fedora / DNF                     |
| ----------------------------- | ------------------------ | -------------------------------- |
| Refresh repositories          | `sudo apt update`        | `sudo dnf makecache`             |
| Upgrade packages              | `sudo apt upgrade`       | `sudo dnf upgrade`               |
| Install                       | `sudo apt install <pkg>` | `sudo dnf install <pkg>`         |
| Remove                        | `sudo apt remove <pkg>`  | `sudo dnf remove <pkg>`          |
| Remove + config               | `sudo apt purge <pkg>`   | `sudo dnf remove <pkg>`*         |
| Search                        | `apt search <pkg>`       | `dnf search <pkg>`               |
| Show information              | `apt show <pkg>`         | `dnf info <pkg>`                 |
| List installed                | `apt list --installed`   | `dnf list installed`             |
| List available                | `apt list`               | `dnf list available`             |
| Show upgradable               | `apt list --upgradable`  | `dnf check-update`               |
| Clean cache                   | `sudo apt clean`         | `sudo dnf clean all`             |
| Download package              | `apt download <pkg>`     | `dnf download <pkg>`**           |
| Find package providing a file | `apt-file search <file>` | `dnf provides <file>`            |
| Package dependencies          | `apt depends <pkg>`      | `dnf repoquery --requires <pkg>` |
| Package files                 | `dpkg -L <pkg>`          | `rpm -ql <pkg>`                  |

---

### 2. Local Package Files

 Debian → `.deb` → `dpkg`

```bash
sudo dpkg -i package.deb    # Install
sudo dpkg -r package         # Remove
sudo dpkg -P package         # Remove + config
dpkg -l                      # List installed packages
```

 Fedora → `.rpm` → `rpm`

```bash
sudo rpm -ivh package.rpm    # Install
rpm -qa                      # List installed RPMs
sudo rpm -e package          # Erase/remove
```

**Prefer APT/DNF for normal package installation** because they handle dependencies and repositories for you.

---

## 3. Download Files

### `wget`

```bash
wget <URL>
```

Downloads a file into the current directory.

### `curl`

```bash
curl -O <URL>
```

Download while keeping the original filename.

```
curl <URL> -o package.deb
```

Download and choose the filename.

---

## 4. Application Management

If you mean **universal application packages**, remember **Snap**:

```
snap find <app>          # Search
sudo snap install <app> # Install
snap list                # Installed apps
sudo snap remove <app>  # Remove
```

Example:

```bash
sudo snap install opera
```

> **APT/DNF = normal distro packages**
> **Snap = universal application packages**

---

## 5. Service Management

Both Debian and Fedora commonly use **systemd**, so the commands are basically identical.

```
sudo systemctl start <service> (start now)
sudo systemctl stop <service> (stop now)
sudo systemctl restart <service> (restart)
sudo systemctl reload <service> (reload configuration)
systemctl status <service> (check current status)
sudo systemctl enable <service> (start automatically at boot)
```
---
