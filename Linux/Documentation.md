
A **man page (manual page)** is the official documentation for Linux commands, system calls, configuration files, and programming functions.

# Man Page Conventions:
- Anything between square brackets (“[” and “]”) is optional.
- Anything followed by an ellipsis (“...”) can be repeated.
- Curly braces (“{” and “}”) mean that you should select one of the items separated by vertical bars (“|”).

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

### Exam takeaway

* **Man pages** are the built-in manuals for Linux commands and system components.
* They are stored as compressed source files (for example, `/usr/share/man/man1/ls.1.gz`) written in the **roff** markup language.
* **`nroff`** and **`groff`** are formatting programs that convert roff markup into readable output.
* **Preformatting** means converting the source into display-ready text ahead of time and storing it in a cache, so it doesn't have to be reformatted on every request. Modern Linux systems usually do this caching automatically.
