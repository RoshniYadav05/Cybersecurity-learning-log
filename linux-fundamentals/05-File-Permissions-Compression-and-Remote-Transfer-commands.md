# Linux File Permissions, Compression, and Remote File Transfer

## Overview

Linux provides powerful commands for managing file ownership, permissions, file compression, and transferring files between systems. These concepts are fundamental for Linux administration, cybersecurity, cloud environments, and penetration testing.

In this guide, we will cover:

* File Compression Commands
* Secure File Transfer
* File Ownership
* File Permissions
* chmod (Numeric & Symbolic Modes)
* chown
* Shebang (`#!`)
* Executing Shell Scripts

---

# File Compression Commands

Compression reduces file size and makes it easier to store or transfer files.

---

## ZIP Command

The `zip` command is used to compress multiple files or folders into a single ZIP archive.

### Syntax

```bash
zip archive.zip file1 file2 file3
```

### Example

```bash
zip backup.zip file1.txt file2.txt file3.txt
```

### Result

A file named `backup.zip` will be created containing all specified files.

---

## Listing ZIP Contents

```bash
ls
```

Example Output:

```text
backup.zip
file1.txt
file2.txt
file3.txt
```

---

## Extracting ZIP Files

The `unzip` command extracts files from a ZIP archive.

### Syntax

```bash
unzip backup.zip
```

### Example

```bash
unzip backup.zip
```

### Result

All files inside the archive will be extracted into the current directory.

---

# TAR Command

The `tar` command is widely used in Linux to archive and compress files.

---

## Creating a Compressed Archive

### Syntax

```bash
tar -cvzf archive.tar.gz folder/
```

### Example

```bash
tar -cvzf cloud.tar.gz cloud/
```

### Understanding the Options

| Option | Meaning              |
| ------ | -------------------- |
| c      | Create archive       |
| v      | Verbose output       |
| z      | Use gzip compression |
| f      | Specify filename     |

### Result

Creates a compressed archive named:

```text
cloud.tar.gz
```

---

## Extracting a TAR Archive

### Syntax

```bash
tar -xvzf archive.tar.gz
```

### Example

```bash
tar -xvzf cloud.tar.gz
```

### Understanding the Options

| Option | Meaning                |
| ------ | ---------------------- |
| x      | Extract archive        |
| v      | Verbose output         |
| z      | Use gzip decompression |
| f      | Archive filename       |

---

## Quick Summary

### Compress

```bash
tar -cvzf filename.tar.gz directory/
```

### Extract

```bash
tar -xvzf filename.tar.gz
```

---

# Secure File Transfer

## SCP (Secure Copy)

SCP stands for **Secure Copy Protocol**.

It is used to securely transfer files between local and remote systems using SSH.

---

## Why Use SCP?

* Encrypted transfer
* Uses SSH authentication
* Secure file copying
* Commonly used in cloud servers

---

## Syntax

```bash
scp source_file username@remote_host:/destination/path
```

### Example

```bash
scp secret-file.txt ubuntu@192.168.1.10:/home/ubuntu/
```

### Explanation

| Component       | Purpose             |
| --------------- | ------------------- |
| scp             | Secure Copy Command |
| secret-file.txt | Source File         |
| ubuntu          | Remote Username     |
| 192.168.1.10    | Remote Host         |
| /home/ubuntu/   | Destination Path    |

### Result

The file is copied from the local machine to the remote machine securely.

---

# RSYNC Command

`rsync` is used for synchronizing files and directories between systems.

Unlike SCP, it only transfers changed data, making it faster and more efficient.

---

## Features

* Local to Remote Sync
* Remote to Local Sync
* Incremental Transfer
* Directory Synchronization
* Backup Operations

---

## Syntax

```bash
rsync -av source/ destination/
```

### Example

```bash
rsync -av project/ backup/
```

---

# File Ownership

In Linux, every file has:

1. Owner (User)
2. Group
3. Permissions

Ownership determines who controls the file.

---

# Understanding ls -l Output

Consider the following output:

```bash
-rw-rw-r-- 1 labex labex 0 Jun 8 22:47 example.txt
```

---

## Breaking It Down

### File Type

```text
-
```

The first character indicates file type.

| Symbol | Meaning       |
| ------ | ------------- |
| -      | Regular File  |
| d      | Directory     |
| l      | Symbolic Link |

---

### Owner Permissions

```text
rw-
```

Owner can:

* Read
* Write
* Cannot Execute

---

### Group Permissions

```text
rw-
```

Members of the group can:

* Read
* Write
* Cannot Execute

---

### Others Permissions

```text
r--
```

Everyone else can:

* Read Only

---

### Link Count

```text
1
```

Represents the number of hard links.

---

### Owner Name

```text
labex
```

Current owner of the file.

---

### Group Name

```text
labex
```

Current group assigned to the file.

---

### File Size

```text
0
```

Size in bytes.

Since the file is empty, the size is zero.

---

### Modification Time

```text
Jun 8 22:47
```

Last modified date and time.

---

### Filename

```text
example.txt
```

Actual file name.

---

# Changing Ownership Using chown

The `chown` command is used to change ownership of files and directories.

---

## Syntax

```bash
sudo chown owner:group file
```

### Example

```bash
sudo chown root:root example.txt
```

### Explanation

| Component   | Purpose                  |
| ----------- | ------------------------ |
| sudo        | Run with root privileges |
| chown       | Change Ownership         |
| root:root   | Owner and Group          |
| example.txt | Target File              |

---

## Recursive Ownership Change

To change ownership of a directory and everything inside it:

```bash
sudo chown -R root:root new-dir
```

### Meaning of -R

Recursive mode.

Changes ownership of:

* Directory
* Subdirectories
* Files inside them

---

# Creating Directories

## mkdir -p

Creates nested directories.

### Example

```bash
mkdir -p new-dir/subdir
```

### Result

```text
new-dir/
└── subdir/
```

### Why Use -p?

Without `-p`, directory creation would fail if parent directories do not already exist.

---

# Creating Files with echo

## Example 1

```bash
echo "Hello World" > new-dir/file.txt
```

Creates:

```text
new-dir/file.txt
```

with content:

```text
Hello World
```

---

## Example 2

```bash
echo "Another File" > new-dir/subdir/file2.txt
```

Creates:

```text
new-dir/subdir/file2.txt
```

---

# Recursive Listing

```bash
ls -R new-dir
```

### Purpose

Lists:

* Files
* Directories
* Subdirectories

Recursively.

---

# Linux File Permissions

Linux permissions determine who can access or modify files.

Permissions are divided into:

1. Owner
2. Group
3. Others

---

## Permission Symbols

| Symbol | Meaning                |
| ------ | ---------------------- |
| r      | Read                   |
| w      | Write                  |
| x      | Execute                |
| -      | Permission Not Granted |

---

## Permission Breakdown

Example:

```text
-rwxr-xr-x
```

### Owner

```text
rwx
```

Can:

* Read
* Write
* Execute

---

### Group

```text
r-x
```

Can:

* Read
* Execute

Cannot write.

---

### Others

```text
r-x
```

Can:

* Read
* Execute

Cannot write.

---

# Numeric Permission System

Linux uses numbers to represent permissions.

| Permission    | Value |
| ------------- | ----- |
| Read          | 4     |
| Write         | 2     |
| Execute       | 1     |
| No Permission | 0     |

---

## Common Calculations

### Full Access

```text
4 + 2 + 1 = 7
```

```text
rwx
```

---

### Read + Execute

```text
4 + 1 = 5
```

```text
r-x
```

---

### Read + Write

```text
4 + 2 = 6
```

```text
rw-
```

---

### No Permission

```text
0
```

```text
---
```

---

# chmod Command

`chmod` stands for **Change Mode**.

Used to modify file permissions.

---

## Example: 700

```bash
sudo chmod 700 example.txt
```

### Meaning

| User Type | Value | Permission |
| --------- | ----- | ---------- |
| Owner     | 7     | rwx        |
| Group     | 0     | ---        |
| Others    | 0     | ---        |

Result:

```text
-rwx------
```

Only the owner has access.

---

## Directory Permission Example

```bash
mkdir ~/test-dir
chmod 755 ~/test-dir
```

### Understanding 755

| User Type | Value | Permission |
| --------- | ----- | ---------- |
| Owner     | 7     | rwx        |
| Group     | 5     | r-x        |
| Others    | 5     | r-x        |

Result:

```text
drwxr-xr-x
```

---

## Viewing Directory Permissions

```bash
ls -ld ~/test-dir
```

### Why Use -d?

Without `-d`, `ls` displays directory contents.

With `-d`, it displays information about the directory itself.

---

# Symbolic Permission Mode

Instead of numbers, permissions can also be modified symbolically.

---

## User Categories

| Symbol | Meaning      |
| ------ | ------------ |
| u      | User (Owner) |
| g      | Group        |
| o      | Others       |
| a      | All Users    |

---

## Operators

| Symbol | Meaning              |
| ------ | -------------------- |
| +      | Add Permission       |
| -      | Remove Permission    |
| =      | Set Exact Permission |

---

## Example

Add execute permission to owner:

```bash
chmod u+x script.sh
```

### Meaning

* u → User (Owner)
* * → Add
* x → Execute Permission

---

# Understanding Shebang (#!)

A Shebang tells Linux which interpreter should execute a script.

Example:

```bash
#!/bin/bash
```

This tells Linux:

> Run this script using Bash.

---

# Creating a Simple Shell Script

```bash
echo '#!/bin/bash' > script.sh
echo 'echo "Hello World"' >> script.sh
```

View the script:

```bash
cat script.sh
```

Output:

```bash
#!/bin/bash
echo "Hello World"
```

---

# Permission Denied Error

Attempting to run:

```bash
./script.sh
```

may produce:

```text
Permission denied
```

### Why?

The script lacks execute permission.

---

# Grant Execute Permission

```bash
chmod u+x script.sh
```

Verify:

```bash
ls -l script.sh
```

Output:

```text
-rwxrw-r--
```

Now the owner has execute permission.

---

# Execute the Script

```bash
./script.sh
```

Output:

```text
Hello World
```

---

# Key Takeaways

* `zip` and `unzip` are used for ZIP archives.
* `tar` is commonly used for Linux backups and compression.
* `scp` securely transfers files using SSH.
* `rsync` synchronizes files efficiently.
* `chown` changes file ownership.
* `chmod` changes permissions.
* Linux permissions are divided into Owner, Group, and Others.
* Numeric permissions use values 4, 2, and 1.
* Symbolic permissions use `u`, `g`, `o`, and `a`.
* Shebang (`#!/bin/bash`) tells Linux which interpreter should run a script.
* Scripts require execute permission before they can run.

---

## Lab Practice

```bash
# Create directories
mkdir -p new-dir/subdir

# Create files
echo "Hello World" > new-dir/file.txt
echo "Another File" > new-dir/subdir/file2.txt

# Compress directory
tar -cvzf backup.tar.gz new-dir

# Extract archive
tar -xvzf backup.tar.gz

# Change ownership
sudo chown -R root:root new-dir

# Set permissions
chmod 755 new-dir
chmod 700 file.txt

# Create script
echo '#!/bin/bash' > script.sh
echo 'echo "Hello World"' >> script.sh

# Add execute permission
chmod u+x script.sh

# Run script
./script.sh
```
