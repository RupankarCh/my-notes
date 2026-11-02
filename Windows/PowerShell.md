# 🛡️ PowerShell Cybersecurity Cheatsheet

A handy reference guide for security professionals, SOC analysts, and system administrators using PowerShell for Windows security auditing, incident response, and system administration.

---

## 📑 Table of Contents

1. [Core & Navigation Commands](https://www.google.com/search?q=%23-core--navigation-commands)
2. [Execution Policies & Script Security](https://www.google.com/search?q=%23-execution-policies--script-security)
3. [Process & Service Monitoring (Incident Response)](https://www.google.com/search?q=%23-process--service-monitoring-incident-response)
4. [Network Connections & Configuration](https://www.google.com/search?q=%23-network-connections--configuration)
5. [User & Group Management](https://www.google.com/search?q=%23-user--group-management)
6. [Event Logs & Auditing](https://www.google.com/search?q=%23-event-logs--auditing)
7. [Useful Built-in Security Cmdlets](https://www.google.com/search?q=%23-useful-built-in-security-cmdlets)

---

## 🧭 Core & Navigation Commands

| Command / Cmdlet | Description | Example |
| --- | --- | --- |
| `Get-Help` | View help documentation for any cmdlet | `Get-Help Get-Process` |
| `Get-Command` | Find cmdlets, functions, and scripts | `Get-Command -Module NetTCPIP` |
| `Get-Member` | Inspect properties and methods of an object | `Get-Process | Get-Member` |
| `Get-Location` | Display current working directory (like `pwd`) | `Get-Location` |
| `Set-Location` | Change directory (like `cd`) | `Set-Location C:\Windows\System32` |
| `Get-ChildItem` | List files and folders (like `ls` or `dir`) | `Get-ChildItem -Path C:\ -Force` |

---

## 🔒 Execution Policies & Script Security

PowerShell execution policies are designed to prevent the accidental execution of unscripted or malicious files.

```powershell
# View the current execution policy settings across scopes
Get-ExecutionPolicy -List

# Set execution policy for the current user (e.g., to run local scripts safely)
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser

# Bypass execution policy for a single session (common for administrative tasks)
PowerShell.exe -ExecutionPolicy Bypass -File .\script.ps1

```

---

## 🔍 Process & Service Monitoring (Incident Response)

Quickly triage running processes, loaded modules, and background services during an investigation.

```powershell
# List all running processes sorted by CPU usage
Get-Process | Sort-Object CPU -Descending

# Find a specific process and inspect its path and command line arguments
Get-CimInstance Win32_Process -Filter "Name='powershell.exe'" | Select-Object ProcessId, CommandLine, Path

# Stop a suspicious process by its Process ID (PID)
Stop-Process -Id 1234 -Force

# List all running services and their status
Get-Service | Where-Object {$_.Status -eq 'Running'}

```

---

## 🌐 Network Connections & Configuration

Assess active network sockets, interfaces, and open ports.

```powershell
# View active network connections and listening ports
Get-NetTCPConnection | Select-Object LocalAddress, LocalPort, RemoteAddress, RemotePort, State

# Display active connections tied to their owning process ID
Get-NetTCPConnection | Select-Object LocalPort, RemotePort, State, OwningProcess

# Retrieve IP address configurations
Get-NetIPAddress | Where-Object {$_.AddressFamily -eq 'IPv4'}

# Quick ping test to check network reachability
Test-Connection -ComputerName 8.8.8.8 -Count 4

```

---

## 👥 User & Group Management

Audit local accounts, groups, and privileges.

```powershell
# List all local user accounts
Get-LocalUser

# Check members of the local Administrators group
Get-LocalGroupMember -Group "Administrators"

# Check details of a specific user account
Get-LocalUser -Name "Administrator"

```

---

## 📜 Event Logs & Auditing

Query the Windows Event Log for security events, failed logins, and process executions.

```powershell
# Search the Security event log for recent failed logon attempts (Event ID 4625)
Get-WinEvent -FilterHashtable @{LogName='Security'; ID=4625} -MaxEvents 10

# View PowerShell script block logging events (Event ID 4104)
Get-WinEvent -FilterHashtable @{LogName='Microsoft-Windows-PowerShell/Operational'; ID=4104} -MaxEvents 5

```

---

## 🛠️ Useful Built-In Security Cmdlets

* **`Get-MpComputerStatus`**: Check Windows Defender status, real-time protection, and signature versions.
* **`Find-Module` / `Install-Module**`: Manage extensions from the PowerShell Gallery (requires administrative privileges).

---

> **Disclaimer:** This cheatsheet is intended for authorized administrative tasks, security hardening, and defensive lab practice. Always follow your organization's security policies.
