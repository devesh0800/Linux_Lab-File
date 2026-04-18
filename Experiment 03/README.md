# Working with Files and Directories in Linux

## Introduction

File and directory management is a fundamental operation in any operating system. In Linux, effective handling of files and directories is essential for system administration, software development, and cybersecurity tasks. Unlike graphical file managers, Linux primarily relies on command-line utilities to create, view, modify, and manage files with precise control over permissions and access rights.

This experiment practices Linux commands for working with files and directories, understanding file and directory permissions, and using basic text editors such as nano and vi to create and edit files.

---

## Learning Outcomes

| LO | Description |
|----|-------------|
| LO1 | Navigate the Linux file system using command-line tools |
| LO2 | Create, list, and organize files and directories |
| LO3 | Understand and interpret Linux file and directory permissions |
| LO4 | Create and edit text files using nano and vi editors |

---

## Theory

### Linux File System

Linux follows a hierarchical file system structure starting from the root directory `/`. All files and directories are organized in a tree-like structure, enabling efficient file management and security control.

### Files and Directories

- **Files** store data such as text, scripts, or binaries
- **Directories** act as containers that organize files and other directories

### File and Directory Permissions

Linux enforces security using a permission model that defines:

| Permission | Symbol | Description |
|------------|--------|-------------|
| Read | `r` | Permission to read file contents or list directory contents |
| Write | `w` | Permission to modify a file or directory |
| Execute | `x` | Permission to execute a file or access a directory |

Permissions are assigned to three categories:

| Category | Description |
|----------|-------------|
| Owner | The user who owns the file |
| Group | A group of users with shared permissions |
| Others | All other users |

### Text Editors

| Editor | Description |
|--------|-------------|
| `nano` | A beginner-friendly, menu-driven text editor |
| `vi` | A powerful modal editor commonly used in Unix/Linux systems |

---

## Commands Reference

| Command | Description |
|---------|-------------|
| `ls` | List files and directories |
| `ls -l` | Display detailed file information |
| `pwd` | Show current directory |
| `cd` | Change directory |
| `mkdir` | Create directory |
| `rmdir` | Remove empty directory |
| `touch` | Create empty file |
| `cat` | Display file content |
| `nano` | Edit files using nano editor |
| `vi` | Edit files using vi editor |
| `chmod` | Change file permissions |
| `stat` | Display file status |

---

## Procedure

### Step 1: Open the Terminal

Log in to the Linux virtual machine and open the terminal application.

### Step 2: Display Current Directory

```bash
pwd                    # Show current working directory
```

### Step 3: List Files and Directories

```bash
ls                     # List files in current directory
ls -l                  # List files with detailed information
ls -la                 # List all files including hidden
```

### Step 4: Create and Navigate a Directory

```bash
mkdir linux_lab        # Create new directory named linux_lab
cd linux_lab           # Change into the new directory
pwd                    # Verify current directory
```

### Step 5: Create Files

```bash
touch file1.txt        # Create an empty file
touch file2.txt        # Create another empty file
touch file3.txt file4.txt  # Create multiple files at once
ls                     # List files to verify creation
```

### Step 6: Edit Files Using nano

`nano` is a beginner-friendly text editor with on-screen menu options.

```bash
nano file1.txt
```

**nano Key Commands:**
- Type your text content
- **Ctrl + O** - Save file (Write Out)
- **Ctrl + X** - Exit editor

### Step 7: Edit Files Using vi

`vi` is a powerful modal editor with three modes: Normal, Insert, and Command.

```bash
vi file2.txt
```

**vi Key Commands:**

| Mode | Key | Action |
|------|-----|--------|
| Insert | `i` | Enter insert mode |
| Insert | `Esc` | Exit insert mode |
| Command | `:wq` | Save and quit |
| Command | `:q!` | Quit without saving |
| Command | `dd` | Delete current line |
| Command | `yy` | Copy current line |
| Command | `p` | Paste |

**vi Workflow:**
1. Open file: `vi file2.txt`
2. Press `i` to enter insert mode
3. Type your text content
4. Press `Esc` to exit insert mode
5. Type `:wq` and press Enter to save and quit

### Step 8: Display File Contents

```bash
cat file1.txt          # Display contents of file1
cat file2.txt          # Display contents of file2
cat file1.txt file2.txt    # Display multiple files
```

### Step 9: Check File Permissions

```bash
ls -l                  # View file permissions in current directory
ls -l file1.txt        # View permissions of specific file
stat file1.txt          # Display detailed file status
```

**Permission Format Example:**
```
-rwxr-xr-- 1 owner group 4096 Jan 20 10:00 file.txt
|---|---|---|  owner  group  filename
| |  |  other permissions
| |  group permissions
| owner permissions
file type (- = regular file, d = directory)
```

### Step 10: Change File Permissions

Use `chmod` to modify file permissions:

```bash
chmod 755 file1.txt     # rwxr-xr-x (owner: rwx, group: rx, others: rx)
chmod 644 file2.txt     # rw-r--r-- (owner: rw, group: r, others: r)
chmod 700 secret.txt    # rwx------ (owner only)
chmod +x script.sh      # Add execute permission
chmod -w file.txt        # Remove write permission
```

**Permission Numeric Values:**

| Number | Permission | Binary |
|--------|------------|--------|
| 4 | Read (r) | 100 |
| 2 | Write (w) | 010 |
| 1 | Execute (x) | 001 |

### Step 11: Remove Files and Directories

```bash
rm file3.txt           # Remove a file
rmdir empty_dir         # Remove an empty directory
rm -r dir_name          # Remove directory and contents recursively
```

---

## Expected Output

- [x] Successful navigation through Linux file system
- [x] Creation of files and directories using command-line tools
- [x] Understanding of file permissions (rwx for owner/group/others)
- [x] Ability to create and edit text files using nano and vi
- [x] Proper modification of file permissions using chmod

---

## Results

File and directory management commands were successfully explored and executed. The student gained practical understanding of Linux file system navigation, file creation and editing using nano and vi editors, and the permission model for secure file access control.

---

## Viva Questions

8. **What is the Linux command-line interface?**
   The Linux CLI is a text-based interface that allows users to interact with the operating system by typing commands. It provides precise control over system operations through various command-line utilities.

9. **What is the purpose of man command?**
   The `man` command displays the manual page for any command, providing detailed documentation including description, syntax, options, and examples for proper command usage.

10. **Difference between man and --help?**
    | Aspect | man | --help |
    |--------|-----|--------|
    | Format | Formatted pages (pager) | Simple text output |
    | Detail | Comprehensive documentation | Brief summary |
    | Navigation | Page-by-page viewing | Scrollable text |
    | Exit | Press `q` | End of output |

11. **What are run levels or systemd targets?**
    Run levels (System V) and systemd targets define the system's operating state. They control which services and functionality are available, such as single-user mode, multi-user text mode, or graphical multi-user mode.

12. **What is graphical.target?**
    `graphical.target` is a systemd target that starts a multi-user system with graphical display manager. It is equivalent to runlevel 5 in classic System V and provides the full GUI desktop environment.

13. **How does auto-completion help users?**
    Auto-completion (Tab key) helps users by reducing typing errors, saving time on long command/file names, discovering available commands and options, and completing file paths automatically.

14. **What command shows the current working directory?**
    The `pwd` (print working directory) command displays the absolute path of the current working directory.

---

## Tips

- Always backup important files before modifying permissions
- Use `ls -l` frequently to verify file permissions after changes
- Practice both nano and vi editors to become proficient with both
- Remember that vi requires specific key sequences to save and exit
- Use `man` pages for detailed command information
- Be careful with `rm -r` as it permanently deletes directories and contents
- Document your work with screenshots

---

## References

- Linux Filesystem Hierarchy: https://www.pathname.com/fhs/
- nano Editor Documentation: https://www.nano-editor.org/docs.php
- vim (vi improved): https://www.vim.org/docs.php
- chmod Manual: `man chmod`
