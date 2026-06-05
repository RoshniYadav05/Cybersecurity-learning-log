# Linux Fundamentals - File and Directory Management

## Overview

While learning Linux fundamentals, I practiced working with files and directories. Understanding file and directory management is important because almost every task in Linux involves navigating, creating, modifying, or removing files and folders.

In this lab, I learned how to:

- Create directories
- Navigate between directories
- Work with hidden files and directories
- Copy and move files
- Rename files and directories
- Remove files and directories
- View file contents

---

## Creating Directories

### Create a Single Directory

The `mkdir` command is used to create a new directory.

```bash
mkdir dir1
```

Example:

```bash
mkdir projects
```

This creates a directory named `projects`.

### Create Nested Directories

```bash
mkdir dir2/dir3/dir4
```

This creates the following structure:

```text
dir2
└── dir3
    └── dir4
```

The command works only if the parent directories already exist.

### Create Parent Directories Automatically

```bash
mkdir -p dir2/dir3/dir4
```

The `-p` option creates all missing parent directories automatically.

Example:

```text
dir2
└── dir3
    └── dir4
```

### Create Multiple Directories

```bash
mkdir dir5 dir6 dir7
```

This creates multiple directories at once.

---

## Navigating Directories

### Change Directory

The `cd` command is used to move into a directory.

```bash
cd dir2
```

### Move to the Parent Directory

```bash
cd ..
```

The `..` symbol represents the parent directory.

Example:

```text
/home/user/dir2/dir3
```

After running:

```bash
cd ..
```

Current location becomes:

```text
/ home / user / dir2
```

### Move Multiple Levels Back

```bash
cd ../../..
```

This moves multiple levels upward in a single command.

---

## Finding the Current Location

The `pwd` command stands for Print Working Directory.

```bash
pwd
```

Example Output:

```text
/home/user/dir1/dir2/dir3
```

This command displays the complete path of the current directory.

---

## Hidden Files and Directories

In Linux, files and directories that start with a dot (`.`) are hidden.

### Create a Hidden File

```bash
touch .file1
```

You can also create hidden files using:

```bash
nano .file1
```

or

```bash
vi .file1
```

### View Hidden Files

Normal listing:

```bash
ls
```

Hidden files will not be displayed.

To show hidden files:

```bash
ls -a
```

or

```bash
ls -al
```

Where:

- `-a` shows all files including hidden files
- `-l` displays detailed information

### Create a Hidden Directory

```bash
mkdir .dir1
```

This creates a hidden directory.

---

## Copying Files

The `cp` command is used to copy files.

```bash
cp file1 file2
```

Where:

- `file1` = Source file
- `file2` = Destination file

The contents of `file1` are copied into `file2`.

If `file2` already exists, it will be overwritten.

---

## Moving Files

The `mv` command is used to move files from one location to another.

```bash
mv file1 dir1
```

This moves `file1` into the directory `dir1`.

Example:

```text
dir1/file1
```

The original file is removed from its previous location.

---

## Renaming Files and Directories

The `mv` command can also be used to rename files and directories.

```bash
mv file1 myfile
```

Before:

```text
file1
```

After:

```text
myfile
```

The file content remains unchanged; only the name changes.

---

## Removing Directories

### Remove an Empty Directory

```bash
rmdir dir1
```

This removes an empty directory.

### Remove Parent and Child Directories

```bash
rmdir -p dir1/dir2
```

If both directories are empty, Linux removes them together.

### Remove Directories with Verbose Output

```bash
rmdir -pv dir1/dir2
```

Where:

- `-p` removes parent directories
- `-v` displays detailed output

---

## Removing Files and Non-Empty Directories

### Remove a File

```bash
rm file1
```

Deletes the specified file.

### Remove an Empty Directory

```bash
rm -d dir1
```

Deletes an empty directory.

### Remove a Non-Empty Directory

```bash
rm -r dir1
```

The `-r` option removes:

- Directories
- Subdirectories
- Files inside them

### Force Delete

```bash
rm -rf dir1
```

Where:

- `-r` = Recursive
- `-f` = Force

This removes files and directories without confirmation.

> Be careful while using `rm -rf` because deleted data is difficult to recover.

---

## Viewing File Contents

### View File Contents Using less

```bash
less file1
```

Displays file content page by page.

Press `q` to exit.

### View First 10 Lines

```bash
head file1
```

Displays the first 10 lines of a file.

### View Last 10 Lines

```bash
tail file1
```

Displays the last 10 lines of a file.

### View File Contents Using more

```bash
more file1
```

Displays file content one page at a time.

Useful when working with large files.

---

## Commands Practiced

| Command | Description |
|----------|------------|
| mkdir | Create directory |
| mkdir -p | Create nested directories |
| cd | Change directory |
| pwd | Display current directory |
| ls -a | Show hidden files |
| cp | Copy files |
| mv | Move or rename files |
| rmdir | Remove empty directory |
| rm -r | Remove directory recursively |
| rm -rf | Force remove files/directories |
| less | View file page by page |
| head | Display first 10 lines |
| tail | Display last 10 lines |
| more | Display file content page by page |

---

## What I Learned

Through this Linux fundamentals lab, I learned how to create and manage directories, navigate the Linux file system, work with hidden files, copy and move files, rename resources, safely remove files and directories, and view file contents using different Linux utilities.

These commands form the foundation of working with Linux systems and are widely used in system administration, networking, and cybersecurity.
