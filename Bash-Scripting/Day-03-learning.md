# Day 03 - Mathematical Operations and Conditional Statements in Bash

## Overview

Today I learned how to perform mathematical operations in Bash, use variables in calculations, write conditional statements using `if-else`, and check whether files or commands exist on the system.

---

# Mathematical Operations

Bash provides the `expr` command for performing arithmetic operations.

### Addition

```bash
expr 30 + 10
```

Output:

```text
40
```

---

### Subtraction

```bash
expr 30 - 10
```

Output:

```text
20
```

---

### Division

```bash
expr 30 / 10
```

Output:

```text
3
```

---

### Multiplication

```bash
expr 100 \* 4
```

Output:

```text
400
```

> The `*` symbol must be escaped using `\` because Bash treats it as a wildcard character.

---

# Using Variables in Calculations

Variables can also be used with arithmetic operations.

```bash
mynum1=100
mynum2=200

expr $mynum1 + $mynum2
```

Output:

```text
300
```

---

# Conditional Statements

Conditional statements allow scripts to make decisions based on conditions.

---

## Simple If Statement

```bash
#!/bin/bash

mynum=200

if [ $mynum -eq 200 ]
then
    echo "The condition is true."
fi
```

Output:

```text
The condition is true.
```

---

## If-Else Statement

```bash
#!/bin/bash

mynum=300

if [ $mynum -eq 200 ]
then
    echo "This condition is true."
else
    echo "The variable does not equal 200."
fi
```

Output:

```text
The variable does not equal 200.
```

---

# Comparison Operators

### Equal To

```bash
-eq
```

Example:

```bash
if [ $mynum -eq 200 ]
```

---

### Not Equal To

```bash
-ne
```

Example:

```bash
if [ $mynum -ne 200 ]
```

Meaning:

> Execute the condition if the value is not equal to 200.

---

### Greater Than

```bash
-gt
```

Example:

```bash
if [ $mynum -gt 200 ]
```

Meaning:

> Execute the condition if the value is greater than 200.

---

# Checking Whether a File Exists

Bash can check if a file is present in the filesystem.

```bash
#!/bin/bash

if [ -f ~/myfile ]
then
    echo "The file exists."
else
    echo "The file does not exist."
fi
```

### Explanation

* `-f` checks whether a file exists.
* If the file is found, the first message is displayed.
* Otherwise, the second message is displayed.

---

# Checking Whether a Command Exists

A script can verify whether a command is installed on the system.

Example:

```bash
#!/bin/bash

command=/usr/bin/htop

if [ -f $command ]
then
    echo "$command is available."
else
    echo "$command is unavailable. Install it."

    sudo apt update && sudo apt install -y htop
fi
```

---

## Why Use `&&`?

```bash
sudo apt update && sudo apt install -y htop
```

The second command runs only if the first command executes successfully.

This helps prevent installation attempts when the update process fails.

---

# Using command -v

Another way to check whether a command exists:

```bash
command -v htop
```

Output Example:

```text
/usr/bin/htop
```

### Purpose

* Checks whether a command is available.
* Returns the path of the executable if found.

# Day 03 Status

Completed learning arithmetic operations, conditional statements, comparison operators, file checks, and command validation in Bash scripting.
