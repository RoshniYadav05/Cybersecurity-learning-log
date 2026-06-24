# Day 4 - Exit Codes and Script Status in Bash

## Overview

Today I learned about **Exit Codes** in Bash and how they are used to determine whether a command or script executed successfully or failed.

Linux commands always return an exit status after execution. Bash stores this status in a special variable called `$?`.

Understanding exit codes is important for writing scripts that can automatically verify whether a task completed successfully before proceeding to the next step.

---

# Exit Codes in Bash

An exit code is a numeric value returned by a command after it finishes execution.

### Common Exit Codes

| Exit Code | Meaning       |
| --------- | ------------- |
| 0         | Success       |
| Non-Zero  | Failure/Error |

---

# The `$?` Variable

Bash provides a special variable:

```bash
$?
```

It stores the exit code of the **previously executed command**.

---

## Example 1: Successful Command

```bash
ls -l /etc/passwd
echo $?
```

### Output

```text
0
```

### Explanation

The file exists and the command executed successfully.

Exit Code:

```text
0
```

---

## Example 2: Failed Command

```bash
ls -l /misc
echo $?
```

### Output

```text
2
```

### Explanation

The directory does not exist, therefore the command failed.

Any exit code other than `0` generally indicates failure.

---

# Checking Exit Codes Inside a Script

Exit codes are commonly used with `if` statements.

## Example: Package Installation Verification

```bash
#!/bin/bash

package=htop

sudo apt install $package

if [ $? -eq 0 ]
then
    echo "The installation of $package was successful."
    echo "The new command is available here:"
    which $package
else
    echo "$package failed to install."
fi
```

### What Happens?

1. Bash attempts to install the package.
2. `$?` stores the installation result.
3. If exit code is `0`, success message is displayed.
4. Otherwise, failure message is displayed.

---

# Saving Results to Log Files

Exit codes can also be used to maintain installation logs.

```bash
#!/bin/bash

package=htop

sudo apt install $package >> package-install-results.log

if [ $? -eq 0 ]
then
    echo "Installation successful."
    which $package
else
    echo "Failed to install." >> package-failed-install.log
fi
```

### Benefits

* Keeps installation history.
* Stores failed installation attempts.
* Useful for automation and troubleshooting.

---

# Checking if a Directory Exists

The `-d` option checks whether a directory exists.

```bash
#!/bin/bash

directory=/etc

if [ -d $directory ]
then
    echo "The directory $directory exists."
else
    echo "The directory $directory doesn't exist."
fi
```

---

# Important Observation About `$?`

Consider the following script:

```bash
directory=/notexist

if [ -d $directory ]
then
    echo "Directory exists"
else
    echo "Directory doesn't exist"
fi

echo $?
```

### Output

```text
Directory doesn't exist
0
```

Many beginners expect the output to be `1`, but it shows `0`.

### Why?

Because `$?` stores the exit code of the **last command executed**.

The last command was:

```bash
echo "Directory doesn't exist"
```

Since `echo` executed successfully, it returned:

```text
0
```

Therefore `$?` becomes `0`.

---

# The `exit` Command

The `exit` command is used to terminate a script and return a custom exit code.

Syntax:

```bash
exit <code>
```

---

## Example

```bash
#!/bin/bash

echo "Hello World"

exit 199
```

The script terminates immediately with exit code:

```text
199
```

Any code written below `exit` will not execute.

---

# Using `exit` in Conditions

```bash
#!/bin/bash

directory=/etc

if [ -d $directory ]
then
    echo "The directory exists."
    exit 0
else
    echo "The directory doesn't exist."
    exit 1
fi
```

### Explanation

* `exit 0` → Script completed successfully.
* `exit 1` → Script completed with an error.

The script stops immediately after executing the corresponding `exit` statement.

---

# Key Learnings

* Every Linux command returns an exit code.
* `0` means success.
* Any non-zero value indicates failure.
* `$?` stores the exit status of the previous command.
* Exit codes can be used with `if` conditions.
* `exit` can be used to manually return a status code from a script.
* Commands written after `exit` are not executed.
* Always check `$?` immediately after the command whose status you want to verify.

---

# Commands Learned

```bash
$?
exit
which
if
then
else
fi
-d
```

---

# Day 4 Summary

Today I learned how Bash uses exit codes to indicate whether commands succeed or fail. I explored the `$?` variable, used exit codes inside conditional statements, verified package installations, checked directory existence, worked with log files, and understood how the `exit` command terminates a script while returning a custom status code.
