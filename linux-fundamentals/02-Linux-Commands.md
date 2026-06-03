# Linux Commands Fundamentals

## Overview

One of the biggest strengths of Linux is its Command Line Interface (CLI). While graphical interfaces are convenient, Linux administrators, system engineers, DevOps professionals, and cybersecurity analysts often rely on commands to perform tasks efficiently.

Understanding basic Linux commands is the first step toward becoming comfortable with Linux systems.

---

# Understanding Root User

Linux follows a privilege-based access model.

The most powerful account in Linux is the **root user**, also known as the **superuser**.

The root user has permission to:

* Install software
* Create users
* Modify system configurations
* Access protected files
* Manage services and processes

To switch from a normal user to the root user:

```bash
sudo su
```

### Breakdown

* `sudo` = Execute command with administrative privileges
* `su` = Switch User

After switching successfully, the terminal prompt usually changes from:

```bash
roshni@linux:~$
```

to

```bash
root@linux:~#
```

Notice that the `$` changes to `#`, indicating root access.

---

# Creating Files in Linux

Linux provides multiple ways to create files.

---

## Using the touch Command

The simplest way to create an empty file is:

```bash
touch file1
```

### Example

```bash
touch notes.txt
```

This creates an empty file named `notes.txt`.

---

### Creating Multiple Files

```bash
touch file1 file2 file3
```

This command creates multiple files at once.

---

# Understanding the touch Command

Most beginners think `touch` is used only for creating files.

Its original purpose is actually to update a file's timestamp.

Every Linux file maintains timestamps such as:

### Access Time (atime)

The last time a file was accessed.

### Modify Time (mtime)

The last time file content was modified.

### Change Time (ctime)

The last time file metadata changed.

Examples:

```bash
touch file1
```

Updates file timestamps.

```bash
touch -a file1
```

Updates only the access time.

```bash
touch -m file1
```

Updates only the modification time.

---

# Creating Files with cat

The `cat` command stands for **Concatenate**.

Although it is mainly used to display and combine files, it can also create files.

### Create a File

```bash
cat > file1
```

After running the command:

```text
Hello
How are you?
```

Press:

```text
CTRL + D
```

to save the file.

---

## Limitation

While creating files using `cat`, content must be entered immediately.

Editing existing content is not very convenient compared to text editors.

---

# Viewing File Contents

To display the contents of a file:

```bash
cat file1
```

Example:

```bash
cat notes.txt
```

Output:

```text
Linux is awesome.
```

---

# Appending Data to a File

To add new content without deleting existing content:

```bash
cat >> file1
```

Example:

```bash
cat >> notes.txt
```

Enter new content and press:

```text
CTRL + D
```

The new text will be appended to the existing file.

---

# Combining Multiple Files

One of the most common uses of `cat` is concatenation.

### Display Multiple Files Together

```bash
cat file1 file2
```

---

### Merge Files into a New File

```bash
cat file1 file2 > all
```

Example:

```bash
cat notes.txt tasks.txt > combined.txt
```

This creates a new file containing the contents of both files.

---

# The tac Command

The `tac` command is the reverse version of `cat`.

While `cat` displays content from top to bottom:

```text
Line 1
Line 2
Line 3
```

`tac` displays content from bottom to top:

```text
Line 3
Line 2
Line 1
```

### Example

```bash
tac file1
```

This is useful when reviewing logs or recent entries first.

---

# Text Editors in Linux

Linux provides text editors that allow users to create and modify files.

The two most common editors for beginners are:

* Vi/Vim
* Nano

---

# Vi Editor

Vi (or Vim) is one of the most powerful editors available in Linux.

It is installed by default on most Linux systems.

---

## Opening a File

```bash
vi file1
```

Example:

```bash
vi notes.txt
```

---

## Enter Insert Mode

After opening a file:

Press:

```text
i
```

This switches Vi into Insert Mode and allows typing.

---

## Exit Insert Mode

Press:

```text
ESC
```

---

## Save and Quit

```bash
:wq
```

Meaning:

* `w` = Write (save)
* `q` = Quit

---

## Quit Without Saving

```bash
:q!
```

---

## Navigation Keys

Traditional Vi navigation uses:

```text
h = left
j = down
k = up
l = right
```

These keys are still heavily used by Linux administrators.

---

# Nano Editor

Nano is a beginner-friendly text editor.

Unlike Vi, Nano displays shortcuts at the bottom of the screen, making it easier to learn.

---

## Open a File

```bash
nano file1
```

Example:

```bash
nano notes.txt
```

---

## Save File

Press:

```text
CTRL + O
```

Then press:

```text
ENTER
```

---

## Exit Nano

Press:

```text
CTRL + X
```

---

# Listing Files and Directories

To display files and folders in the current directory:

```bash
ls
```

Example:

```bash
ls
```

Output:

```text
Documents
Downloads
notes.txt
```

This command is one of the most frequently used Linux commands.

---

# Key Takeaways

* Linux commands provide direct interaction with the operating system.
* `sudo su` switches to the root user.
* `touch` creates files and updates timestamps.
* `cat` displays, creates, appends, and combines files.
* `tac` displays file contents in reverse order.
* `vi` is a powerful terminal-based editor.
* `nano` is beginner-friendly and easier to learn.
* `ls` displays files and directories in the current location.

Mastering these basic commands builds a strong foundation for Linux administration, cybersecurity, and system management.
