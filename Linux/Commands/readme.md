whoami
pwd
ls
mkdir -p /path/ (To 
cat <file/path>
clear
sudo -i (To switch from a vagrant user to a root user)
cd (To return to the home directory)
cd / (To go to the root directory of the OS)
cd .. (To return to the upper directory)

Absolute Path:
ls /usr/sbin/
Relative Path:
ls sbin/

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
