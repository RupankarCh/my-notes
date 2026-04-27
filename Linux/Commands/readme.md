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

## File Usage Tips:

1. If a filename is '-' then 'cat ./-' can open it meaning you are telling cat to search for a file name '-' in the current directory './'
2. To exit from ssh shell "exit"
3. file ./-* (This command can be used for finding human readable text in a bunch of files where which file contains text is not specified because, ./-* means all files whose names start with -, The file command tells you the type of each file, e.g., ASCII text (human-readable), binary data.)
4. find . -type f -size 1033c ! -executable -exec file {} + | grep "text" (find . (searches in the current directory and all subdirectories), -type f (looks for regular files only), -size 1033c (looks for files that are exactly 1033 bytes (c = bytes)), ! -executable (keep non executables files), -exec (lets you run a command on each file that found), file (determines file type), {} (is a placeholder that gets replaced with the current file's path/name for each match), + (passes multiple files at once), | grep "text" (filters the output to only show lines containing "text" i.e., human-readable files.)


sudo -i (To switch from a vagrant user to a root user)
mkdir folder1 folder2 folder3 (To make multiple directories at a time)
touch file{1..5}.txt (To make multiple files at a time)
cd /tmp/ (To move to temp directory from anywhre)
cp <coping_file_path> <destination_directory> (To copy, paste a file from one directory to another while not being present to the coping file directory)
cp -r <coping_directory_name> <destination_directory_name> (To copy a directory recursively)
mv <moving_directory_name> <destination_directory_name> (To move a directory from one place to another)
mv <file_name.txt> <file_new_name.txt> (To rename a file)
rm <file_name.txt> (To remove a file)
rm -r <directory_name> (To remove a directory)

