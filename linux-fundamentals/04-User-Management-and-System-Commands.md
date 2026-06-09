# Linux User Management and System Commands

## Overview

Linux provides various system-level commands that help administrators manage the operating system, users, groups, services, and software packages. Understanding these commands is essential for Linux administration, cybersecurity, cloud computing, and troubleshooting.

---

# System Information Commands

## 1. uname

The `uname` command displays information about the operating system and kernel.

### Syntax

```bash
uname
```

### Example Output

```bash
Linux
```

### Common Usage

```bash
uname -a
```

Displays detailed system information, including:

* Kernel Version
* Hostname
* Architecture
* Operating System Details

### Use Case

Used to identify the platform and operating system currently running.

---

## 2. uptime

The `uptime` command shows how long the system has been running.

### Syntax

```bash
uptime
```

### Information Displayed

* Current system time
* System uptime
* Number of logged-in users
* System load average

### Example

```bash
uptime
```

Output:

```bash
14:25:10 up 5 days, 3:15, 2 users, load average: 0.10, 0.20, 0.30
```

### Use Case

Useful for checking system stability and workload.

---

## 3. who

The `who` command displays information about users currently logged into the system.

### Syntax

```bash
who
```

### Use Cases

* Check active users
* Monitor login sessions
* View terminal activity

---

## 4. whoami

Displays the username of the currently logged-in user.

### Syntax

```bash
whoami
```

### Example

```bash
student
```

### Use Case

Used to verify the account currently being used.

---

## 5. date

Displays the current system date and time.

### Syntax

```bash
date
```

### Example

```bash
Mon Jun 08 14:30:25 IST 2026
```

---

## 6. which

Displays the location of an executable command.

### Syntax

```bash
which <command>
```

### Example

```bash
which bash
```

Output:

```bash
/usr/bin/bash
```

### Use Case

Used to find where a command is installed on the system.

---

## 7. id

Displays information about a user and the groups they belong to.

### Syntax

```bash
id
```

### Example Output

```bash
uid=1000(student) gid=1000(student) groups=1000(student),27(sudo)
```

### Information Displayed

* User ID (UID)
* Group ID (GID)
* Supplementary Groups

---

# Privilege Management

## 8. sudo

`sudo` stands for **Super User Do**.

It allows a normal user to execute commands with administrative (root) privileges.

### Example

```bash
sudo apt update
```

### Benefits of sudo

* Temporary root access
* Improved security
* User activity logging
* Prevents direct root login

---

# System Control Commands

## 9. shutdown

Used to safely power off the system.

### Syntax

```bash
sudo shutdown now
```

### Example

```bash
sudo shutdown now
```

### Note

Root privileges are required to shut down the system.

---

## 10. reboot

Used to restart the system.

### Syntax

```bash
sudo reboot
```

### Example

```bash
sudo reboot
```

---

# Package Management

## 11. apt

APT (**Advanced Package Tool**) is the package manager used in Debian-based distributions such as Ubuntu and Kali Linux.

### Install a Package

```bash
sudo apt install docker.io
```

### Remove a Package

```bash
sudo apt remove docker.io
```

### Update Package Lists

```bash
sudo apt update
```

### Upgrade Installed Packages

```bash
sudo apt upgrade
```

### Functions of APT

* Install software
* Remove software
* Update repositories
* Upgrade packages
* Search packages

---

## Package Managers in Different Linux Distributions

| Distribution             | Package Manager |
| ------------------------ | --------------- |
| Ubuntu / Debian          | apt             |
| CentOS                   | yum             |
| Fedora                   | dnf             |
| Arch Linux               | pacman          |
| Gentoo                   | portage         |
| Red Hat Enterprise Linux | rpm             |

---

# User Management

## 12. useradd

Used to create a new user account.

### Syntax

```bash
sudo useradd -m jethalal
```

### Explanation

* `useradd` → Creates a new user
* `-m` → Creates a home directory automatically

### Result

```bash
/home/jethalal
```

A new user account and home directory will be created.

---

## 13. passwd

Used to set or reset a user's password.

### Syntax

```bash
sudo passwd jethalal
```

### Example

```bash
sudo passwd jethalal
```

The system will prompt for a new password.

---

## 14. su

`su` stands for **Switch User**.

Used to switch from one user account to another.

### Syntax

```bash
su jethalal
```

### Example

```bash
su jethalal
```

After entering the correct password, the session switches to the specified user.

### Exit Current Session

```bash
exit
```

Returns to the previous user session.

---

## 15. userdel

Used to delete a user account.

### Syntax

```bash
sudo userdel jethalal
```

### Delete User Along with Home Directory

```bash
sudo userdel -r jethalal
```

### Explanation

* `-r` removes the user's home directory and mail files.

---

# Group Management

Linux uses groups to manage permissions efficiently and control access to resources.

---

## 16. groupadd

Creates a new group.

### Syntax

```bash
sudo groupadd cyber
```

### Example

```bash
sudo groupadd tester
```

---

## 17. View Group Information

Displays all groups configured on the system.

### Syntax

```bash
cat /etc/group
```

### Example

```bash
cat /etc/group
```

---

## 18. Add a User to a Group

### Syntax

```bash
sudo gpasswd -a jethalal cyber
```

### Example

```bash
sudo gpasswd -a jethalal cyber
```

### Explanation

* `-a` → Add user
* `jethalal` → Username
* `cyber` → Group name

---

## 19. Remove a User from a Group

### Syntax

```bash
sudo gpasswd -d jethalal cyber
```

### Example

```bash
sudo gpasswd -d jethalal cyber
```

### Explanation

* `-d` → Delete user from the group

---

## 20. Add Multiple Users to a Group

### Syntax

```bash
sudo gpasswd -M iyer,tapu,bhide,tester cyber
```

### Explanation

The `-M` option replaces the group's member list with the specified users.

### Example

```bash
sudo gpasswd -M iyer,tapu,bhide,tester cyber
```

---

# Quick Command Reference

| Command          | Purpose                               |
| ---------------- | ------------------------------------- |
| `uname`          | Display OS information                |
| `uptime`         | Show system uptime                    |
| `who`            | Show logged-in users                  |
| `whoami`         | Display current user                  |
| `date`           | Show date and time                    |
| `which`          | Find command location                 |
| `id`             | Show UID, GID, and group membership   |
| `sudo`           | Execute commands with root privileges |
| `shutdown`       | Power off the system                  |
| `reboot`         | Restart the system                    |
| `apt`            | Package management                    |
| `useradd`        | Create a user                         |
| `passwd`         | Set or reset a password               |
| `su`             | Switch user                           |
| `userdel`        | Delete a user                         |
| `groupadd`       | Create a group                        |
| `cat /etc/group` | View groups                           |
| `gpasswd -a`     | Add user to group                     |
| `gpasswd -d`     | Remove user from group                |
| `gpasswd -M`     | Add multiple users to a group         |

---

# Key Takeaways

* Linux uses users and groups to control access to system resources.
* Administrative tasks require elevated privileges through `sudo`.
* Package management is handled using tools such as `apt`.
* User management commands include `useradd`, `passwd`, `su`, and `userdel`.
* Group management commands include `groupadd` and `gpasswd`.
* These commands are widely used in Linux administration, cybersecurity, cloud environments, and penetration testing labs.

---

## Lab Practice Commands

```bash
# Create a group
sudo groupadd cyber

# Create users
sudo useradd -m jethalal
sudo useradd -m tapu
sudo useradd -m iyer

# Set passwords
sudo passwd jethalal
sudo passwd tapu
sudo passwd iyer

# Add users to group
sudo gpasswd -a jethalal cyber
sudo gpasswd -a tapu cyber
sudo gpasswd -a iyer cyber

# Verify group membership
cat /etc/group

# Switch user
su jethalal

# Return back
exit
```
