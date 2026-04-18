# Shell Script for File Creation and Manipulation Using User Directory

## Introduction

In Linux, automation of file and directory operations is a common requirement for system administration and scripting tasks. Bash scripting allows users to create files, copy content between files, extract specific portions of files, and compare files programmatically. These operations are frequently used in log management, data processing, and system maintenance.

The problem is to write a shell script that creates directories and files in the user's home directory, copies content between files, prints content from a specific line onward, and displays differences between two files, thereby demonstrating file manipulation through shell scripting.

---

## Course Outcome Mapping

| CO | Description |
|----|-------------|
| CO2 | Ability to write Bash scripts for automating file and directory operations |
| CO4 | Use of scripting logic for handling files and structured tasks |

---

## Learning Outcomes

| LO | Description |
|----|-------------|
| LO1 | Create directories and files using a shell script |
| LO2 | Copy content from one file to another using scripting commands |
| LO3 | Display file contents from a specified line number |
| LO4 | Compare two files and identify differences using Linux utilities |

---

## Theory

### File Manipulation Using Shell Scripts

Shell scripts can automate complex file operations using standard Linux commands such as `mkdir`, `touch`, `cp`, `sed`, `tail`, and `diff`. Automating these tasks reduces manual effort and minimizes errors.

### Important Commands

- **mkdir** – Create directories
- **touch** – Create empty files
- **cp** – Copy files
- **sed** – Stream editor for filtering text
- **tail** – Display file content from the end
- **diff** – Compare files line by line

---

## Commands Reference

| Command | Description |
|---------|-------------|
| `mkdir` | Create directories |
| `touch` | Create empty files |
| `cp` | Copy file contents |
| `sed` | Print specific lines |
| `tail` | Print content from a line onward |
| `diff` | Display differences between files |
| `chmod` | Change script permissions |

---

## Procedure

### A. Writing the Shell Script

1. Open the terminal.
2. Create a script file:
   ```
   nano file_ops.sh
   ```
3. Enter the following script:
   ```bash
   #!/bin/bash
   mkdir -p $HOME/class/batch
   cd $HOME/class/batch
   echo "This is the original file." > profile.txt
   echo "Welcome to Linux Bash Scripting Lab." >> profile.txt
   cp profile.txt copy_profile.txt
   echo "Printing file content from line 2:"
   tail -n +2 profile.txt
   echo "Differences between files:"
   diff profile.txt copy_profile.txt
   ```
4. Save and exit the editor.
5. Make the script executable:
   ```
   chmod +x file_ops.sh
   ```

### B. Executing the Script

6. Run the script:
   ```
   ./file_ops.sh
   ```

---

## Sample Execution

```bash
$ ./file_ops.sh
Printing file content from line 2:
Welcome to Linux Bash Scripting Lab.
Differences between files:
(no output – files are identical)
```

---

## Expected Output

- [x] Directory structure created in the user's home directory.
- [x] Files created and content copied successfully.
- [x] File content displayed from the specified line.
- [x] File comparison output displayed correctly.

---

## Result

A shell script was successfully written and executed to automate file creation, content copying, selective printing, and file comparison operations in Linux.

---

## Tips

- **Path Usage:** Use absolute or `$HOME` paths carefully to ensure correct directory targeting.
- **Verification:** Verify directory structure after script execution.
- **Commands:** Understand the difference between `tail` and `sed`.
- **Testing:** Always test scripts with sample data before real usage.
- **Permissions:** Ensure scripts have executable permissions before running.

---

## Viva Questions

- **What is the use of $HOME variable?**
  - **Answer:** The `$HOME` variable is an environment variable that stores the path to the current user's home directory (e.g., `/home/username`). It is used in shell scripts to create files and directories relative to the user's home directory, ensuring portability across different systems where usernames may differ.

- **Difference between cp and mv.**
  - **Answer:** `cp` (copy) duplicates a file or directory, leaving the original intact. `mv` (move) relocates a file or directory from one location to another, removing it from the original location. Essentially, `cp` creates a clone while `mv` performs a relocation.

- **How does tail -n +2 work?**
  - **Answer:** The `tail -n +2` command displays the content of a file starting from line 2 to the end. The `+2` argument tells `tail` to begin at the 2nd line (rather than the default last 10 lines), making it useful for skipping the header line of a file.

- **What is the purpose of diff command?**
  - **Answer:** The `diff` command compares two files line by line and displays the differences between them. It shows which lines need to be added, removed, or modified to make the files identical. This is useful for comparing versions of files and identifying changes.

- **How can a shell script automate file operations?**
  - **Answer:** A shell script can automate file operations by combining multiple file manipulation commands (like `mkdir`, `cp`, `cat`, `sed`, `tail`, `diff`) into a single executable script. This eliminates the need to run commands manually one by one, reduces errors, and ensures consistent execution of repetitive file tasks.

- **Why is chmod required before script execution?**
  - **Answer:** `chmod` (change mode) is required to set executable permissions on a script file. By default, files are created without execute permission. Using `chmod +x script.sh` adds the execute permission, allowing the shell to run the script as a program using `./script.sh`.

- **Where are user-specific files usually stored in Linux?**
  - **Answer:** User-specific files are typically stored in the user's home directory (`/home/username`). This includes configuration files (often hidden, starting with `.`), documents, downloads, desktop files, and user-specific application data. The `$HOME` environment variable points to this location.

---

## References

- Linux Man Pages: `man mkdir`, `man touch`, `man cp`, `man tail`, `man diff`, `man chmod`
- Introduction to Linux with Bash Scripting Lab (Dr. Rajesh Kumar)
