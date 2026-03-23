

sudo -i (To switch from a vagrant user to a root user)

# 🐚 Basic Shell Knowledge (Linux)

## 🧑‍💻 Prompt Symbols

```text
#  → Superuser (root) prompt, means you are running commands as **root (administrator)** → full system access ⚠️
$  → Normal user prompt, means you are a **regular user** → limited permissions
~  → Refers to the current user's home directory
```

---

## ▶️ Running Executables

```bash
./program_name   You need to use ./program_name to run an program existing on the same directory as you, If you downloaded that program in your current folder but didn’t move it to a PATH directory, typing `beef` alone will NOT work.
```
---

## 🏃‍♂️ Directory Traversal
Absolute Path:
ls /usr/sbin/

Relative Path:
ls sbin/

## 📦 to run without ./ (Why `./` is needed)

```text
move the program to PATH, the list of directories where the system looks for executable files "echo $PATH" to see the paths or move to the following directories
python
ls
nano
```

### Common PATH directories:

```text
/usr/bin
/bin
/usr/local/bin
```

## 📁 File & Directory Basics

```bash
pwd        # Show current directory
ls         # List files
cd         # return to the home directory of the current user)
cd /       # go to the root directory of the OS)
cd ..      # return to the upper directory
cd folder  # Change directory
```

---

## 🔐 Permissions (Very Important)

```bash
ls -l
```

Example output:

```text
-rwxr-xr-x  1 user user  1234 file.sh
```

### Meaning:

```text
r = read
w = write
x = execute
```

### Make a file executable:

```bash
chmod +x file.sh
```

---

## ⚡ Useful Tips

```bash
./script.sh     # Run script in current folder
bash script.sh  # Run using bash interpreter
```

---

# 🐧 Universal Terminal Manipulation Guide

## 📌 Basic Commands (Work on almost all Linux systems)

```bash
clear      # Clear the terminal screen
reset      # Reset terminal (fix broken display)
exit       # Close the terminal session
```

---

## ⌨️ Cursor Movement (Shell-level — works in most shells like Bash)

```text
Ctrl + A   → Move cursor to beginning of line
Ctrl + E   → Move cursor to end of line
Alt + B    → Move backward one word
Alt + F    → Move forward one word
```

---

## ✂️ Text Editing

```text
Ctrl + U   → Delete from cursor to beginning of line
Ctrl + K   → Delete from cursor to end of line
Ctrl + W   → Delete previous word
Ctrl + Y   → Paste (yank) last deleted text
```

---

## 🔄 Screen Control

```text
Ctrl + L   → Clear screen (same as `clear`)
Ctrl + C   → Cancel running command
Ctrl + Z   → Suspend current process
```

---

## 📜 History Navigation

```text
Ctrl + P   → Previous command
Ctrl + N   → Next command
↑ / ↓      → Scroll through command history
Ctrl + R   → Reverse search in history
```

---

## 🧵 Process & Session Control

```text
jobs       # List background jobs
bg         # Resume job in background
fg         # Bring job to foreground
kill %1    # Kill job number 1
```

---

## 📂 Tab & Autocomplete

```text
Tab        → Auto-complete commands/files
Tab (x2)   → Show all possible completions
```

---

## 🔍 Useful Terminal Tricks

```bash
history            # Show command history
!!                 # Run last command again
!n                 # Run command number n
```

---
