# Day 02 - Variables in Bash

## Overview

Today I learned about variables in Bash scripting, how to store values, print them, and use built-in environment variables provided by the shell.

---

## Declaring Variables

Variables can store different types of data such as:

* Text
* Numbers
* Strings

Example:

```bash
myname="Roshni"
```

Here:

* `myname` is the variable name.
* `"Roshni"` is the value stored in the variable.

> Variable names in Bash are case-sensitive.

For example:

```bash
name="Roshni"
Name="Cybersecurity"
```

Both variables are treated as different.

---

## Printing Variable Values

To access a variable's value, use `$`.

Example:

```bash
echo $myname
```

Output:

```text
Roshni
```

The `$` symbol tells Bash that the value of the variable should be printed.

---

## Why Use `$`?

Example:

```bash
ls="Hello"
echo $ls
```

Output:

```text
Hello
```

Without `$`, Bash may interpret `ls` as the Linux command instead of the variable.

Using `$` helps avoid confusion between variables and commands.

---

## Variables in Terminal vs Script

Variables created directly in the terminal exist only for that session.

Example:

```bash
myname="Roshni"
```

If the terminal is closed, the variable is lost.

To keep variables and reuse them, they can be stored inside a Bash script.

---

## Using Variables Inside a Bash Script

Example:

```bash
#!/bin/bash

myname="Roshni"
myage="22"

echo "Hello my name is $myname."
echo "I am $myage years old."
```

Output:

```text
Hello my name is Roshni.
I am 22 years old.
```

---

## Double Quotes vs Single Quotes

### Double Quotes

Variables are expanded.

```bash
echo "Hello $myname"
```

Output:

```text
Hello Roshni
```

### Single Quotes

Variables are not expanded.

```bash
echo 'Hello $myname'
```

Output:

```text
Hello $myname
```

---

## Reusing Variables

Example:

```bash
#!/bin/bash

word="fun"

echo "Love should be $word"
echo "Life should be $word"
echo "Person should be $word"
```

Output:

```text
Love should be fun
Life should be fun
Person should be fun
```

This demonstrates how one variable can be reused multiple times.

---

## Command Substitution

Variables can also store command output.

Example:

```bash
files=$(pwd)
```

Print the value:

```bash
echo $files
```

Output:

```text
/current/path
```

Here, the output of `pwd` is stored inside the variable.

---

## Environment Variables

Bash provides several predefined environment variables.

List all environment variables:

```bash
env
```

Some commonly used variables:

| Variable | Purpose                           |
| -------- | --------------------------------- |
| USER     | Current username                  |
| HOME     | User home directory               |
| PWD      | Present working directory         |
| OLDPWD   | Previous working directory        |
| PATH     | Directories searched for commands |
| SHELL    | Current shell                     |
| HOSTNAME | System hostname                   |
| TERM     | Terminal type                     |
| LANG     | Language and locale settings      |
| UID      | User ID                           |
| RANDOM   | Generates random numbers          |

Examples:

```bash
echo $USER
echo $HOME
echo $PWD
```

---

## Special Bash Variables

| Variable | Meaning                          |
| -------- | -------------------------------- |
| $$       | Current shell process ID (PID)   |
| $?       | Exit status of the last command  |
| $0       | Script or shell name             |
| $*       | All arguments as a single string |
| $@       | All arguments separately         |
| $#       | Number of arguments passed       |

---

## Key Learnings

✅ Declared variables in Bash

✅ Printed variable values using `$`

✅ Learned variable scope in terminal sessions

✅ Used variables inside Bash scripts

✅ Understood single vs double quotes

✅ Stored command output in variables

✅ Explored environment variables

✅ Learned special Bash variables

---

## Day 02 Status

Completed learning Bash variables, variable expansion, command substitution, environment variables, and special shell variables.
