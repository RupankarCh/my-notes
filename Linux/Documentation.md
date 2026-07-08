
A **man page (manual page)** is the official documentation for Linux commands, system calls, configuration files, and programming functions.

# Man Page Conventions:
- Anything between square brackets (“[” and “]”) is optional.
- Anything followed by an ellipsis (“...”) can be repeated.
- Curly braces (“{” and “}”) mean that you should select one of the items separated by vertical bars (“|”).

| **Term**                             | **Meaning (Simple)**                                                                             | **Example / Notes**                                      |
| ------------------------------------ | ------------------------------------------------------------------------------------------------ | -------------------------------------------------------- |
| **Man page (Manual page)**           | Built-in Linux documentation for commands, system calls, libraries, configuration files, etc.    | `man ls`                                                 |
| **man**                              | Program used to display manual pages.                                                            | `man grep`                                               |
| **manpath**                          | The list of directories that `man` searches for manual pages.                                    | `manpath`                                                |
| **MANPATH**                          | Environment variable that overrides the default man page search path.                            | `export MANPATH=/home/user/man:/usr/share/man`           |
| **Repository (man page repository)** | A directory tree that stores manual pages.                                                       | `/usr/share/man`                                         |
| **Section**                          | Category of manual pages (commands, system calls, libraries, etc.).                              | `man 2 read`, `man 5 passwd`                             |
| **Source man page**                  | The original manual page written in the **roff** markup language.                                | `/usr/share/man/man1/ls.1.gz`                            |
| **roff**                             | A text formatting markup language used to write man pages.                                       | Uses macros like `.TH`, `.SH`, `.B`                      |
| **troff**                            | Original document formatter for typesetting (printer output).                                    | Ancestor of `groff`                                      |
| **nroff**                            | Formatter that converts roff source into text for terminals.                                     | Historically used for terminal output                    |
| **groff**                            | GNU implementation of troff/nroff; formats man pages into readable output.                       | Used internally by modern `man`                          |
| **Macro**                            | A formatting command in roff.                                                                    | `.TH`, `.SH`, `.B`, `.I`                                 |
| **Markup language**                  | A language that describes document formatting instead of plain text.                             | HTML, Markdown, roff                                     |
| **Formatting**                       | Converting marked-up source into readable output.                                                | `groff` formats `.TH` into headings                      |
| **Preformatted page**                | A man page that has already been formatted and saved for quick viewing.                          | Also called a **cat page**                               |
| **Cat page**                         | Cached, preformatted man page that can be displayed directly without reformatting.               | Historically stored in `/var/cache/man/cat1`             |
| **catman**                           | Legacy utility that preformatted all man pages and stored them as cat pages.                     | Rarely used today                                        |
| **Cache**                            | A storage area that keeps computed data so it can be reused quickly.                             | `/var/cache/man`                                         |
| **Persistent cache**                 | A cache stored on disk that survives reboots.                                                    | Historically, cat pages in `/var/cache/man`              |
| **On-demand formatting**             | Formatting a man page only when it is requested, instead of storing a cached copy.               | Used by modern `man-db`                                  |
| **Compression**                      | Reducing file size to save disk space.                                                           | `.gz` files                                              |
| **gzip (.gz)**                       | A common compression format used for man page source files.                                      | `ls.1.gz`                                                |
| **Decompression**                    | Expanding a compressed file back to its original form.                                           | `gunzip -c file.gz`                                      |
| **Pager**                            | A program that lets you scroll through text one screen at a time.                                | `less` (used by `man`)                                   |
| **less**                             | The default pager used by `man` to display long documents.                                       | Scroll with arrow keys, quit with `q`                    |
| **System call**                      | A function through which a program requests services from the Linux kernel.                      | `read()`, `open()`, `fork()`                             |
| **Library function**                 | A function provided by a programming library, not directly by the kernel.                        | `printf()`, `malloc()`                                   |
| **Kernel**                           | The core of the operating system that manages hardware and system resources.                     | Handles system calls                                     |
| **Configuration file**               | A file that stores settings used by programs or the operating system.                            | `/etc/passwd`, `/etc/fstab`                              |
| **MANDB_MAP**                        | A `man-db` configuration directive mapping a man-page directory to its cat-page cache directory. | `MANDB_MAP /usr/share/man /var/cache/man`                |
| **man-db**                           | The modern Linux implementation of the `man` system.                                             | `man --version`                                          |
| **Search path**                      | Ordered list of directories searched for files.                                                  | `manpath` for manuals, `PATH` for executables            |
| **Parallel man-page tree**           | A separate directory hierarchy that mirrors the standard man directory layout.                   | `/opt/company/man/man1`, `/opt/company/man/man5`         |
| **Rendering**                        | Producing the final readable output from formatted source.                                       | `groff` renders roff into terminal text                  |
| **Offline documentation**            | Documentation available locally without an Internet connection.                                  | All standard man pages                                   |
| **`/usr/share/man`**                 | Standard location for source man pages.                                                          | Contains `man1`, `man2`, `man3`, etc.                    |
| **`/var/cache/man`**                 | Traditional location for cached preformatted man pages (cat pages).                              | Often empty on modern Linux distributions like RHEL 10.2 |


### Exam takeaway

- A man page is the official documentation for Linux commands and system interfaces.
- Source man pages are stored under /usr/share/man (or local equivalents) as compressed roff files.
- groff/nroff convert roff source into readable terminal output.
- Historically, formatted output was cached as cat pages in /var/cache/man.Modern Linux distributions such as RHEL 10.2 generally format pages on demand instead of maintaining a persistent cat-page cache.
- Use manpath to see where man searches for source pages.
- Use find /var/cache/man -type f to determine whether the system maintains persistent preformatted man pages.

When you type:

```
man ls
```

you are asking Linux:

> "Show me the documentation for the `ls` command."

Example output:

```
LS(1)

NAME
       ls - list directory contents

SYNOPSIS
       ls [OPTION]... [FILE]...

DESCRIPTION
       List information about the FILEs...
```

Think of it as an **offline encyclopedia** built into Linux.

# 2. Where are Man Pages Stored?

The actual man pages are stored as **text source files**, not as the nicely formatted pages you see.

Usually here:

```
/usr/share/man/
```

Inside this directory you'll find sections.

Example:

```
/usr/share/man/

man1/
man2/
man3/
man4/
man5/
man6/
man7/
man8/
```

Let's see one:

```
/usr/share/man/man1/ls.1.gz
```

Notice:

```
ls.1.gz
```

means

```
ls       -> command
1        -> section
gz       -> compressed
```

It is **not** a normal text file.

---

# 3. Why Different Sections?

Linux documentation is divided into categories.

| Section | Meaning                                           |
| ------- | ------------------------------------------------- |
| 1       | User commands and applications (`ls`, `cp`, `cat`)                 |
| 2       | System calls, Kernel error codes (`open()`, `read()`)                 |
| 3       | Library functions/calls (`printf()`)                    |
| 4       | Device files/drivers and network protocols                                      |
| 5       | Standard file formats and Configuration files                               |
| 6       | Games and Demonstrations                                             |
| 7       | Miscellaneous files and Documents                                     |
| 8       | System administration commands (`mount`, `fdisk`) |
| 9       | Obscure kernel specs and interfaces |

Example:

```
man 5 passwd
```

Shows documentation for

```
/etc/passwd
```

whereas

```
man 1 passwd
```

shows the `passwd` command.

---

# 4. What is Actually Inside `ls.1.gz`?

If you decompress it:

```bash
gunzip -c /usr/share/man/man1/ls.1.gz
```

You'll see something strange:

```
.TH LS 1
.SH NAME
ls \- list directory contents
.SH SYNOPSIS
.B ls
.RI [ OPTION ]...
```

This is **not plain English**.

These are **formatting commands**.

Think of it like HTML.

HTML:

```html
<h1>Title</h1>

<p>Paragraph</p>
```

Man page source:

```
.TH Title
.SH Section
.B Bold
.I Italic
```

So the source is written in a markup language.

---

# 5. What are `nroff` and `groff`?

These are **text formatting programs**.

Their job is:

```
Man source
        ↓
nroff / groff
        ↓
Beautiful formatted manual page
```

Imagine writing Markdown:

```
# Title

**Bold**
```

Before viewing it nicely, a renderer converts it.

Exactly the same happens here.

---

### nroff

Older formatter.

Designed for

```
Terminal output
```

Produces text suitable for a console.

---

### groff

GNU version of troff/nroff.

Much more powerful.

Can produce

* terminal output
* PDF
* PostScript
* HTML

`man` nowadays usually uses **groff** internally.

---

# 6. What Happens When You Run `man ls`?

Internally, something like this happens:

```
man ls
      │
      │
Find file

/usr/share/man/man1/ls.1.gz
      │
      │
Uncompress
      │
      │
Send to groff
      │
      │
Convert formatting commands
      │
      │
Display nicely in terminal
```

So every time, Linux has to:

* unzip
* interpret formatting commands
* render the page

---

# 7. Then What is Preformatting?

Imagine a Word document.

Original:

```
report.docx
```

When you print it,

Windows must:

* read the document
* calculate fonts
* arrange paragraphs
* produce printable pages

Now imagine printing it once and saving the result as a PDF.

Next time you want it,

You just open the PDF.

No formatting work is needed.

That is exactly what **preformatting** means.

---

Without preformatting:

```
Source
↓

groff

↓

Display
```

Every time.

With preformatting:

```
Source
↓

groff

↓

Save formatted version
↓

Display directly
```

No need to run `groff` again.

---

# 8. What Did `catman` Do?

It went through every man page:

```
ls.1.gz

cp.1.gz

mv.1.gz

fdisk.8.gz

...
```

For each one:

```
Read source
↓

Run groff
↓

Save formatted output
```

Example:

```
Source

/usr/share/man/man1/ls.1.gz
```

↓

Generated

```
/var/cache/man/cat1/ls.1
```

Now when you type:

```
man ls
```

Instead of

```
Source

↓

groff

↓

Display
```

it becomes

```
Preformatted page

↓

Display
```

which was much faster on older hardware.

---

# 9. Why Is It Called "cat" Page?

Originally, the preformatted output was plain text that could be displayed directly using the `cat` command.

For example:

```
cat /var/cache/man/cat1/ls.1
```

would show the already formatted manual.

That's why these cached files were called **cat pages**, and the program that generated them was named **`catman`**.

---

# 10. Modern Linux

Today, when you run:

```bash
man ls
```

**after running the command the `man-db` system checks whether a cached formatted version already exists. If not, it formats the page with `groff`, stores the cached result automatically, and displays it. On later accesses, it can reuse the cache.

Because of this automatic caching**, the separate `catman` command is rarely needed on modern Linux distributions.

---

## Complete Flow Diagram

```text
           You type

           man ls
              │
              ▼
Find source file
/usr/share/man/man1/ls.1.gz
              │
              ▼
Decompress (.gz)
              │
              ▼
Man page source
(.TH .SH .B .I ...)
              │
              ▼
groff / nroff
(formatting engine)
              │
              ▼
Formatted text
              │
              ├── Display in terminal
              │
              └── (Modern systems) Cache formatted output for faster future access
```


# To check wether this linux OS contains preformatted man page
```
find /var/cache/man -type f 2>/dev/null
```
If it lists files such as:
```
/var/cache/man/cat1/ls.1.gz
/var/cache/man/cat2/read.2.gz
```
then the system has cached preformatted (cat) man pages.

If it prints nothing, then there are no persistent cached cat pages in the standard cache location.
