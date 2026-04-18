# Understanding different types of shells in Linux and writing a simple shell script

## Introduction

In Linux, the shell acts as an interface between the user and the operating system kernel. Different types of shells provide varied features, scripting capabilities, and command-line behaviors. Among these, Bash (Bourne Again Shell) is the most widely used shell due to its scripting power and ease of use.

The problem is to identify different types of shells available in Linux, understand their characteristics, and write and execute a simple shell script using Bash, including the use of variables.

---

## Course Outcome Mapping

| CO | Description |
|----|-------------|
| CO1 | Familiarity with Linux environment and shell types |
| CO3 | Execution of commands and manipulation of shell environment |

---

## Learning Outcomes

| LO | Description |
|----|-------------|
| LO1 | Identify and differentiate between various Linux shells |
| LO2 | Switch between different shells |
| LO3 | Write and execute a basic Bash shell script |
| LO4 | Use variables within shell scripts |

---

## Theory

### Shell in Linux
A shell is a command-line interpreter that processes user commands and communicates with the kernel. It allows users to execute commands, manage files, and write scripts for automation.

### Types of Shells
Common shells available in Linux include:

| Shell | Description |
|-------|-------------|
| `sh` | Original Bourne Shell |
| `bash` | Bourne Again Shell (default) |
| `ksh` | Korn Shell |
| `csh` | C Shell |
| `zsh` | Z Shell |

### Bash Shell
Bash is an enhanced version of `sh` that supports:
- Command history
- Job control
- Scripting with variables and control structures

### Shell Scripts
A shell script is a file containing a sequence of commands executed by the shell. It typically starts with a shebang (`#!/bin/bash`) that specifies the interpreter.

---

## Commands Reference

| Command | Description |
|---------|-------------|
| `cat /etc/shells` | List available shells |
| `echo $SHELL` | Display current shell |
| `bash` | Start Bash shell |
| `sh` | Start Bourne shell |
| `chmod +x` | Change file permissions to executable |
| `./script.sh` | Execute shell script |

---

## Procedure

### Step 1: Identifying Different Shells
1. Open the terminal.
2. List available shells: `cat /etc/shells`
3. Check the current shell: `echo $SHELL`

### Step 2: Switching Between Shells
1. Switch to Bourne shell: `sh`
2. Return to Bash: `exit`

### Step 3: Writing a Simple Bash Script
1. Create a new script file: `nano simple.sh`
2. Enter the following script:
```bash
#!/bin/bash
echo "Welcome to Linux Shell Scripting"
name="Student"
echo "Hello $name"
```
3. Save and exit the editor.

### Step 4: Executing the Script
1. Provide execute permission: `chmod +x simple.sh`
2. Run the script: `./simple.sh`

---

## Sample Execution

```bash
$ echo $SHELL
/bin/bash

$ cat /etc/shells
# /etc/shells: valid login shells
/bin/sh
/bin/bash
/usr/bin/bash
/bin/rbash
/usr/bin/rbash
/bin/dash
/usr/bin/dash

$ ./simple.sh
Welcome to Linux Shell Scripting
Hello Student
```

---

## Expected Output

- [x] List of available shells displayed.
- [x] Current shell identified.
- [x] Simple Bash script executed successfully.
- [x] Output displays variable values correctly.

---

## Results

Different types of Linux shells were identified and a simple Bash shell script using variables was successfully written and executed.

---

## Tips

- **Shebang:** Always include the shebang line (`#!/bin/bash`) in scripts.
- **Permissions:** Provide execute permissions before running scripts (`chmod +x`).
- **Naming:** Use meaningful variable names for better readability.
- **Verification:** Verify the current shell environment before starting complex scripting tasks.

---

## Viva Questions

- **What is a shell in Linux?**
  - **Answer:** A shell is a program that acts as an interface between the user and the kernel. It interprets command lines entered by the user and executes them.

- **Difference between sh and bash.**
  - **Answer:** `sh` (Bourne Shell) is the original Unix shell with a limited feature set. `bash` (Bourne Again Shell) is a modern replacement that is backward compatible with `sh` but adds many features like command-line editing, history, and improved scripting capabilities.

- **What is the purpose of shebang?**
  - **Answer:** The shebang (`#!`) at the beginning of a script tells the operating system which interpreter should be used to parse and execute the file (e.g., `#!/bin/bash` or `#!/usr/bin/python3`).

- **How do you check the current shell?**
  - **Answer:** You can check the current shell by running `echo $SHELL`, which prints the value of the SHELL environment variable.

- **What are shell variables?**
  - **Answer:** Shell variables are memory locations used to store data as strings. They can be user-defined (like `name="Student"`) or environment variables (like `$PATH` or `$HOME`).

- **How do you make a script executable?**
  - **Answer:** Use the `chmod` command with the execute flag: `chmod +x filename.sh`.

- **Why is Bash preferred for scripting?**
  - **Answer:** Bash is preferred because it is the default shell on most Linux distributions, offers robust features for automation, and has extensive support for programming constructs like loops, conditionals, and functions.

---

## References

- Linux Man Pages: `man bash`, `man sh`
- Introduction to Linux with Bash Scripting Lab (Dr. Rajesh Kumar)
