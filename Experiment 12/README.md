# Shell Programming using Bash: Interactive Scripts, Parameters, Arithmetic Operations, Conditional Statements and loops

## Introduction

Manual execution of commands in Linux can be repetitive and inefficient. Bash shell scripting enables users to automate tasks, accept user input, perform arithmetic operations, make decisions using conditional statements, and execute repetitive tasks using loops. These capabilities are essential for system administration, automation, and cyber security workflows.

The problem is to write and execute Bash shell scripts that demonstrate interactive input, positional parameters, arithmetic operations, conditional statements, and loop constructs, thereby automating basic computational and logical tasks.

---

## Course Outcome Mapping

| CO | Description |
|----|-------------|
| CO2 | Ability to write Bash scripts for automation and task execution |
| CO4 | Use of conditional statements and loops for control flow in scripts |

---

## Learning Outcomes

| LO | Description |
|----|-------------|
| LO1 | Create interactive shell scripts using user input |
| LO2 | Use positional parameters in Bash scripts |
| LO3 | Perform arithmetic operations in shell scripts |
| LO4 | Implement conditional statements and loops for decision-making and repetition |

---

## Theory

### Shell Programming
Shell scripting is a method of automating tasks by writing a sequence of Linux commands in a script file executed by the shell.

### Interactive Scripts
Interactive scripts accept input from the user during execution using the `read` command.

### Positional Parameters
Shell scripts accept command-line arguments using:
- `$0` – Script name
- `$1`, `$2`, ... – Positional parameters

### Arithmetic Operations
Arithmetic can be performed using: `$((expression))`

### Conditional Statements
Decision-making constructs include:
- `if`
- `if-else`
- `elif`

### Loops
Loops execute commands repeatedly:
- `for`
- `while`

---

## Commands Reference

| Command | Description |
|---------|-------------|
| `read` | Accept user input |
| `echo` | Display output |
| `$(( ))` | Arithmetic operations |
| `if, elif, else` | Conditional statements |
| `for, while` | Loop constructs |
| `chmod` | Make script executable |

---

## Procedure

### A. Interactive Shell Script
1. Create a script file: `nano interactive.sh`
2. Enter the following code:
   ```bash
   #!/bin/bash
   echo "Enter your name:"
   read name
   echo "Welcome $name"
   ```
3. Save and exit.
4. Make the script executable: `chmod +x interactive.sh`
5. Execute the script: `./interactive.sh`

### B. Script Using Positional Parameters
6. Create another script: `nano params.sh`
7. Enter the following code:
   ```bash
   #!/bin/bash
   echo "Script Name: $0"
   echo "First Argument: $1"
   echo "Second Argument: $2"
   ```
8. Execute: `./params.sh Linux Bash`

### C. Arithmetic Operations
9. Create script: `nano arithmetic.sh`
10. Enter:
    ```bash
    #!/bin/bash
    a=10
    b=5
    sum=$((a + b))
    echo "Sum = $sum"
    ```

### D. Conditional Statement
11. Create script: `nano condition.sh`
12. Enter:
    ```bash
    #!/bin/bash
    echo "Enter a number:"
    read num
    if [ $num -gt 0 ]
    then
    echo "Positive number"
    else
    echo "Zero or Negative number"
    fi
    ```

### E. Loop Constructs
13. Create for-loop script: `nano loop.sh`
14. Enter:
    ```bash
    #!/bin/bash
    for i in 1 2 3 4 5
    do
    echo "Iteration $i"
    done
    ```

---

## Sample Execution

```bash
$ ./interactive.sh
Enter your name:
Rajesh
Welcome Rajesh

$ ./params.sh Linux Bash
First Argument: Linux
Second Argument: Bash

$ ./arithmetic.sh
Sum = 15
```

---

## Expected Output

- [x] Scripts accept user input and display results correctly.
- [x] Positional parameters are accessed successfully.
- [x] Arithmetic operations produce correct output.
- [x] Conditional statements and loops execute as expected.

---

## Result

Bash shell scripts demonstrating interactive input, positional parameters, arithmetic operations, conditional statements, and loops were successfully created and executed.

---

## Tips

- **Display Manager:** Do not stop or disable the display manager without permission.
- **Shebang:** Always include the shebang line (`#!/bin/bash`) in scripts.
- **Spacing:** Use proper spacing inside conditional brackets.
- **Validation:** Validate user input where necessary.
- **Readability:** Comment scripts for readability.

---

## Viva Questions

- **What is a shell script?**
  - **Answer:** A shell script is a text file containing a sequence of commands for a Unix-based operating system's shell to execute.

- **What is the use of read command?**
  - **Answer:** The `read` command is used to take input from the user during the execution of a script.

- **Explain positional parameters in Bash.**
  - **Answer:** Positional parameters are arguments passed to a script when it is invoked. They are represented by `$1`, `$2`, etc., with `$0` being the script's name.

- **How are arithmetic operations performed in shell scripting?**
  - **Answer:** Arithmetic operations can be performed using the `$((expression))` syntax or the `expr` command.

- **Difference between for and while loops.**
  - **Answer:** A `for` loop iterates over a predefined list of items, while a `while` loop continues to execute as long as a given condition remains true.

- **What is the syntax of if statement?**
  - **Answer:** 
    ```bash
    if [ condition ]
    then
      # commands
    fi
    ```

- **Why is shell scripting important for automation?**
  - **Answer:** It allows for the automation of repetitive tasks, reduces human error, and enables the orchestration of complex system workflows efficiently.

---

## References

- Linux Man Pages: `man bash`, `man read`, `man chmod`
- Introduction to Linux with Bash Scripting Lab (Dr. Rajesh Kumar)
