# Understanding inodes, I/O redirection, Piping, and Process control commands in Linux

## Introduction

Linux internally manages files using data structures known as inodes, which store metadata about files rather than file names. In addition, Linux provides powerful mechanisms such as input/output redirection, pipes, and process control commands to efficiently manage command execution and system resources. These concepts are fundamental for automation, scripting, system monitoring, and cyber security operations.

The problem is to understand the concept of inodes, practice I/O redirection and piping, and use process control commands to manage running processes in a Linux environment.

---

## Course Outcome Mapping

| CO | Description |
|----|-------------|
| CO1 | Familiarity with Linux system internals and file system concepts |
| CO3 | Execution and manipulation of command output using redirection, piping, and process control |

---

## Learning Outcomes

| LO | Description |
|----|-------------|
| LO1 | Understand and interpret inode information of files |
| LO2 | Use input and output redirection for managing command data |
| LO3 | Combine commands using pipes for advanced output processing |
| LO4 | Monitor and control running processes in Linux |

---

## Theory

### Inodes
An inode is a data structure that stores metadata of a file such as:
- File size
- Ownership
- Permissions
- Timestamps
- Disk location

File names are stored separately in directory entries and point to inodes.

### I/O Redirection
Redirection allows changing the standard input, output, or error streams:
- `>` – Redirect output (overwrite)
- `>>` – Redirect output (append)
- `<` – Redirect input
- `2>` – Redirect error output

### Pipes
Pipes (`|`) allow the output of one command to be used as input to another command.
Example: `ls | grep txt`

### Process Control
Linux supports multitasking. Processes can be monitored and controlled using commands such as:
- `ps`: Display running processes
- `top`: Real-time process monitoring
- `kill`: Terminate a process
- `jobs`: List background jobs
- `bg`, `fg`: Resume job in background/foreground

---

## Commands Reference

| Command | Description |
|---------|-------------|
| `ls -i` | Display inode number of files |
| `stat` | Display file inode details |
| `>` | Output redirection (overwrite) |
| `>>` | Output redirection (append) |
| `<` | Input redirection |
| `ps` | Display running processes |
| `top` | Real-time process monitoring |
| `kill` | Terminate a process |
| `jobs` | List background jobs |
| `bg` | Resume job in background |
| `fg` | Bring job to foreground |

---

## Procedure

### A. Understanding Inodes
1. Create a test file: `touch inode_test.txt`
2. Display inode number: `ls -i inode_test.txt`
3. View inode details: `stat inode_test.txt`

### B. Input / Output Redirection
4. Redirect output to a file: `ls > file_list.txt`
5. Append output: `date >> file_list.txt`
6. Redirect input: `wc -l < file_list.txt`

### C. Using Pipes
7. Combine commands using pipe: `ls -l | grep ".txt"`
8. Count number of text files: `ls | grep ".txt" | wc -l`

### D. Process Control Commands
9. Display running processes: `ps`
10. Monitor processes in real-time: `top`
11. Run a command in background: `sleep 60 &`
12. List background jobs: `jobs`
13. Bring job to foreground: `fg`
14. Terminate a process: `kill <PID>`

---

## Sample Execution

```bash
$ ls -i inode_test.txt
123456 inode_test.txt

$ ls | grep ".txt" | wc -l
3

$ sleep 60 &
[1] 2345
```

---

## Expected Output

- [x] Inode numbers and file metadata displayed correctly.
- [x] Command output redirected and appended successfully.
- [x] Pipes used to filter and process output.
- [x] Processes monitored and controlled successfully.

---

## Results

Inode information, input/output redirection, piping, and process control commands were successfully executed. The student gained practical understanding of Linux file system internals and process management.

---

## Tips

- **Critical Processes:** Do not kill critical system processes.
- **Piping:** Use pipes carefully to avoid unintended outputs.
- **Inodes:** Understand inode concept for file linking and storage.
- **Responsibility:** Practice process control commands responsibly.

---

## Viva Questions

- **What is an inode in Linux?**
  - **Answer:** An inode (index node) is a data structure on a Linux file system that stores all the information about a file except its name and the actual data. It includes metadata like file size, owner, permissions, and timestamps.

- **Does inode store file name? Explain.**
  - **Answer:** No, the inode does not store the file name. File names are stored in directory entries, which map a name to a specific inode number. This allows a single file (inode) to have multiple names (hard links).

- **Difference between > and >>.**
  - **Answer:** The `>` operator redirects output to a file, overwriting the file if it already exists. The `>>` operator redirects output to a file but appends the data to the end of the file instead of overwriting it.

- **What is piping in Linux?**
  - **Answer:** Piping (using the `|` symbol) is a mechanism where the standard output of one command is sent as the standard input to another command, allowing for command chaining and complex data processing.

- **What is the use of ps command?**
  - **Answer:** The `ps` (process status) command is used to display information about currently running processes on the system, such as their PID, user, CPU usage, and memory usage.

- **Difference between background and foreground process.**
  - **Answer:** A foreground process is one that is currently taking up the terminal's input and output, preventing other commands from being run until it finishes. A background process runs independently of the terminal input, allowing the user to continue using the shell while the process executes.

- **How do you terminate a process?**
  - **Answer:** You can terminate a process using the `kill` command followed by the process's PID (Process ID), e.g., `kill 1234`. You can also use `killall` to terminate processes by name or `top` to kill processes interactively.

---

## References

- Linux Man Pages: `man ls`, `man stat`, `man ps`, `man kill`
- Introduction to Linux with Bash Scripting Lab (Dr. Rajesh Kumar)
