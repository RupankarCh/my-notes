# Linux Package Management Cheat Sheet

🎯 Focus: Debian & Fedora only

> **Easy memory rule:**
> **Debian → APT → `.deb` → `dpkg`**
> **Fedora → DNF → `.rpm` → `rpm`**

---

## 1. Package Manager

| Task                    | Debian / Ubuntu          | Fedora                   |
| ----------------------- | ------------------------ | ------------------------ |
| **Update package list** | `sudo apt update`        | `sudo dnf check-update`  |
| **Upgrade system**      | `sudo apt upgrade`       | `sudo dnf upgrade`       |
| **Install**             | `sudo apt install <pkg>` | `sudo dnf install <pkg>` |
| **Remove**              | `sudo apt remove <pkg>`  | `sudo dnf remove <pkg>`  |
| **Search**              | `apt search <pkg>`       | `dnf search <pkg>`       |
| **Package info**        | `apt show <pkg>`         | `dnf info <pkg>`         |

🧠 Remember

```
Debian  → apt install nginx
Fedora  → dnf install nginx
```

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
sudo systemctl start <service>
sudo systemctl stop <service>
sudo systemctl restart <service>
sudo systemctl reload <service>
systemctl status <service>
sudo systemctl enable <service>
```


🧠 Remember

```
start    → start now
stop     → stop now
restart  → restart
reload   → reload configuration
status   → check
enable   → start automatically at boot
```

---
