# Linux File/Directory Archival and Compression Cheat Sheet

## 1. Archiving vs Compression

| Task                      | Tool                         | Purpose                         |
| ------------------------- | ---------------------------- | ------------------------------- |
| Archive files/directories | `tar`, `cpio`                | Combine multiple files into one |
| Compress files            | `gzip`, `bzip2`, `xz`, `zip` | Reduce file size                |
| Archive + Compress        | `tar` + compressor           | Create compressed archives      |

---

# TAR (Tape Archive)

### Create Archive

```bash
tar -cvf archive.tar file1 file2 dir/
```

* `c` → Create
* `v` → Verbose
* `f` → Archive filename

Example:

```bash
tar -cvf backup.tar Documents/
```

---

### List Contents

```bash
tar -tvf archive.tar
```

---

### Extract Archive

```bash
tar -xvf archive.tar
```

Extract to another directory:

```bash
tar -xvf archive.tar -C /path/to/destination
```

---

### Common TAR Options

| Option | Meaning                |
| ------ | ---------------------- |
| `c`    | Create                 |
| `x`    | Extract                |
| `t`    | List                   |
| `v`    | Verbose                |
| `f`    | File name              |
| `C`    | Extract into directory |

**Mnemonic:**
**CXT + VF**

* **C**reate
* E**X**tract
* Lis**T**
* **V**erbose
* **F**ile

---

# gzip

Compress:

```bash
gzip file.txt
```

Produces:

```text
file.txt.gz
```

Decompress:

```bash
gunzip file.txt.gz
```

or

```bash
gzip -d file.txt.gz
```

Keep original file:

```bash
gzip -k file.txt
```

View compressed file:

```bash
zcat file.txt.gz
```

---

# TAR + GZIP (.tar.gz or .tgz)

### Create

```bash
tar -czvf archive.tar.gz directory/
```

`z` = gzip

Example:

```bash
tar -czvf project.tar.gz project/
```

---

### Extract

```bash
tar -xzvf archive.tar.gz
```

---

### List Contents

```bash
tar -tzvf archive.tar.gz
```

---

# bzip2

Higher compression, slower.

Compress:

```bash
bzip2 file.txt
```

Produces:

```text
file.txt.bz2
```

Decompress:

```bash
bunzip2 file.txt.bz2
```

---

# TAR + BZIP2 (.tar.bz2)

Create:

```bash
tar -cjvf archive.tar.bz2 directory/
```

Extract:

```bash
tar -xjvf archive.tar.bz2
```

`j` = bzip2

---

# xz

Best compression, slower.

Compress:

```bash
xz file.txt
```

Produces:

```text
file.txt.xz
```

Decompress:

```bash
unxz file.txt.xz
```

---

# TAR + XZ (.tar.xz)

Create:

```bash
tar -cJvf archive.tar.xz directory/
```

Extract:

```bash
tar -xJvf archive.tar.xz
```

`J` = xz

---

# zip

### Compress Files

```bash
zip archive.zip file1 file2
```

Compress a directory recursively:

```bash
zip -r archive.zip directory/
```

---

### View Contents

```bash
unzip -l archive.zip
```

---

### Extract

```bash
unzip archive.zip
```

Extract to another directory:

```bash
unzip archive.zip -d destination/
```

---

# cpio

### Create Archive

```bash
find . | cpio -ov > archive.cpio
```

* `o` → output
* `v` → verbose

---

### List Archive

```bash
cpio -it < archive.cpio
```

---

### Extract

```bash
cpio -id < archive.cpio
```

* `i` → input
* `d` → create directories

---

# Quick Reference

| Extension  | Create                        | Extract               |
| ---------- | ----------------------------- | --------------------- |
| `.tar`     | `tar -cvf a.tar dir/`         | `tar -xvf a.tar`      |
| `.tar.gz`  | `tar -czvf a.tar.gz dir/`     | `tar -xzvf a.tar.gz`  |
| `.tar.bz2` | `tar -cjvf a.tar.bz2 dir/`    | `tar -xjvf a.tar.bz2` |
| `.tar.xz`  | `tar -cJvf a.tar.xz dir/`     | `tar -xJvf a.tar.xz`  |
| `.zip`     | `zip -r a.zip dir/`           | `unzip a.zip`         |
| `.gz`      | `gzip file`                   | `gunzip file.gz`      |
| `.bz2`     | `bzip2 file`                  | `bunzip2 file.bz2`    |
| `.xz`      | `xz file`                     | `unxz file.xz`        |
| `.cpio`    | `find . \| cpio -ov > a.cpio` | `cpio -id < a.cpio`   |

---

# Memory Trick

### TAR operation letters

```text
c = Create
x = Extract
t = lisT
v = Verbose
f = File
```

### Compression letters in tar

```text
z = gzip     (.gz)
j = bzip2    (.bz2)
J = xz       (.xz)
```

### Formula

```text
tar - [operation][compression]vf archive_name source

Create:
tar -czvf backup.tar.gz folder/

Extract:
tar -xzvf backup.tar.gz
```

### One-line mnemonic

```text
CXT + zjJ + VF

C = Create
X = Extract
T = lisT
z = gzip
j = bzip2
J = xz
V = Verbose
F = File
```

This covers nearly all archival and compression commands commonly required for Linux administration, RHCSA, CompTIA Linux+, and LPIC exams.
