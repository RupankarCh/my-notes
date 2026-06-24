# Read (r), Write (w), and Execute (x) give a user the power to do:

**1. On a FILE (The Standard Behavior)**
Think of a file as a document.

**Read (r):** The power to look inside.
Allows a user to open a file and view its contents.
Commands enabled: cat, less, grep, vi (read-only mode).

**Write (w):** The power to alter contents.
Allows a user to modify, overwrite, or truncate the data inside the file.
Commands enabled: Saving changes in vi, appending text with echo "text" >> file.

**The Catch:** It does not allow a user to delete the file. (More on that below).
Execute (x): The power to run it.
Allows the system to run the file as a program, script, or binary.
Commands enabled: ./script.sh.

**2. On a DIRECTORY (The Structural Behavior)**
Think of a directory not as a container, but as a ledger or an index that lists the names and inode numbers of the files inside it.

**Read (r):** The power to list the ledger.
Allows a user to see the names of the files and folders inside the directory.
Commands enabled: ls.

**The Catch:** If you only have r but not x, you can see the file names, but you will get permission errors if you try to view details like file sizes, timestamps, or ownership.
Write (w): The power to alter the ledger.
Allows a user to modify the directory structure itself. This means they can create new files, rename files, and delete existing files inside that directory.

⚠️ Crucial Rule: In Linux, the power to delete a file comes from the directory it lives in, not the file itself. If a user has w permission on a directory, they can delete any file inside it, even if they have zero permissions on the file itself.
Execute (x): The power to pass through / access.
On a directory, x is often called the search bit. It allows a user to "enter" the directory and pass through it to access files inside.
Commands enabled: cd /path/to/directory, or directly reading a file inside it via cat /directory/file.txt.
