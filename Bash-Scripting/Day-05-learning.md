# Bash Scripting - Day 5
# While Loops

## What is a While Loop?

A **while loop** executes a block of code repeatedly **as long as the specified condition is TRUE**.

It is mainly used when:
- You don't know how many times the loop will run.
- You want to repeat a task until a condition becomes false.
- You want to continuously monitor something (logs, files, services, etc.).

---

# Syntax

```bash
while [ condition ]
do
    commands
done
```

---

# Flow

```
Start
   │
Check Condition
   │
True ─────► Execute Commands
   │             │
   └─────────────┘
False
   │
  End
```

---

# Example 1 - Print Numbers 1 to 10

```bash
#!/bin/bash

myvar=1

while [ $myvar -le 10 ]
do
    echo $myvar
    myvar=$((myvar+1))
done
```

### Output

```
1
2
3
4
5
6
7
8
9
10
```

---

# Explanation

### Step 1

```bash
myvar=1
```

Initializes the variable with value **1**.

---

### Step 2

```bash
while [ $myvar -le 10 ]
```

Checks whether the value of `myvar` is **less than or equal to 10**.

- `-le` → Less than or Equal

If the condition is **TRUE**, the loop executes.

If **FALSE**, the loop stops.

---

### Step 3

```bash
echo $myvar
```

Prints the current value of the variable.

---

### Step 4

```bash
myvar=$((myvar+1))
```

Increments the variable by **1**.

Without this statement, the loop would become an **Infinite Loop**.

---

# Example 2 - Check Until a File Exists

```bash
#!/bin/bash

while [ ! -f ~/testfile ]
do
    echo "The test file doesn't exist."
    sleep 2
done

echo "The test file exists."
```

### Explanation

```bash
-f
```

Checks whether the file exists.

```bash
!
```

Means **NOT**.

```bash
! -f
```

Means the file **does not exist**.

The loop keeps checking every 2 seconds until the file is created.

---

# Example 3 - Countdown Timer

```bash
#!/bin/bash

count=5

while [ $count -gt 0 ]
do
    echo $count
    count=$((count-1))
done

echo "Done!"
```

### Output

```
5
4
3
2
1
Done!
```

---

# Example 4 - Read User Input Until Correct Password

```bash
#!/bin/bash

password="linux"

while true
do
    read -p "Enter Password: " userpass

    if [ "$userpass" = "$password" ]
    then
        echo "Access Granted"
        break
    fi

    echo "Wrong Password"
done
```

---

# Important Keywords

## break

Immediately exits the loop.

```bash
break
```

---

## continue

Skips the current iteration and starts the next iteration.

```bash
continue
```

---

## sleep

Pauses the script for a specific number of seconds.

```bash
sleep 5
```

Waits for **5 seconds**.

---

## true

Always returns TRUE.

```bash
while true
do
    echo "Running..."
done
```

This creates an **Infinite Loop** until stopped manually (`Ctrl + C`).

---

# Numeric Comparison Operators

| Operator | Meaning |
|----------|---------|
| `-eq` | Equal |
| `-ne` | Not Equal |
| `-lt` | Less Than |
| `-le` | Less Than or Equal |
| `-gt` | Greater Than |
| `-ge` | Greater Than or Equal |
