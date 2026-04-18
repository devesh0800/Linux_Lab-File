# Deleting, Copying, Moving and Renaming Files in Linux

## Introduction

Efficient file management is a critical requirement in Linux-based systems, especially for system administrators and cybersecurity professionals. Linux provides powerful command-line utilities that allow users to create, copy, move, rename, view, and delete files efficiently. Understanding these commands is essential for organizing data, managing logs, and automating tasks using scripts.

This experiment practices Linux commands for deleting, copying, moving, renaming, and displaying files, and understanding the use of input/output redirection for managing command outputs.

---

## Learning Outcomes

| LO | Description |
|----|-------------|
| LO1 | Create and manage files using Linux commands |
| LO2 | Copy, move, rename, and delete files safely |
| LO3 | Display file contents using command-line tools |
| LO4 | Use input/output redirection to store command output in files |

---

## Theory

### File Management Commands

Linux offers several commands to manage files:

| Command | Description |
|---------|-------------|
| `touch` | Create empty files |
| `cp` | Copy files or directories |
| `mv` | Move or rename files |
| `rm` | Delete files or directories |
| `cat` | Display file contents |

### Input/Output Redirection

Redirection allows command outputs to be redirected to files instead of the terminal:

| Operator | Description |
|----------|-------------|
| `>` | Redirect output (overwrite) |
| `>>` | Redirect output (append) |
| `<` | Redirect input |

These features are essential for scripting and automation.

---

## Commands Reference

| Command | Description |
|---------|-------------|
| `touch` | Create empty file |
| `cp` | Copy files |
| `mv` | Move or rename files |
| `rm` | Remove files |
| `cat` | Display file contents |
| `>` | Output redirection (overwrite) |
| `>>` | Append output |

---

## Procedure

### Step 1: Create Working Directory

```bash
mkdir file_ops           # Create a new directory
cd file_ops              # Change into the directory
pwd                      # Verify current location
```

### Step 2: Create Files

```bash
touch file1.txt           # Create an empty file
touch file2.txt           # Create another empty file
touch file3.txt file4.txt # Create multiple files at once
ls                       # List created files
```

### Step 3: Add Content Using Redirection

```bash
echo "This is file1" > file1.txt
echo "This is file2" > file2.txt
cat file1.txt             # Display content of file1
```

### Step 4: Copy a File

```bash
cp file1.txt copy_file1.txt    # Create a copy of file1
ls -l                              # Verify copy was created
```

### Step 5: Rename a File

```bash
mv file2.txt renamed_file2.txt   # Rename file2
ls                                 # Verify rename
```

### Step 6: Move a File

```bash
mkdir backup                      # Create backup directory
mv copy_file1.txt backup/         # Move file to backup directory
ls backup/                         # Verify file moved
```

### Step 7: Append Content to a File

```bash
echo "Additional content" >> file1.txt  # Append to file1
cat file1.txt                          # Display updated content
```

### Step 8: Delete a File

```bash
rm renamed_file2.txt             # Delete a single file
rm file3.txt                    # Delete another file
ls                              # Verify deletion
```

### Step 9: Delete a Directory

```bash
rm -r backup/                   # Remove directory and contents
ls                              # Verify directory removed
```

---

## Expected Output

- [x] Files created, copied, renamed, and deleted successfully
- [x] File contents displayed correctly
- [x] Output redirection works as expected
- [x] Understanding of input/output redirection

---

## Results

Linux file operations including copying, moving, renaming, deleting files, and output redirection were successfully performed using command-line utilities. The student gained practical understanding of file management operations and redirection in Linux.

---

## Viva Questions

- Difference between cp and mv.
- What is the use of rm command?
- Explain output redirection in Linux.
- Difference between > and >>.
- How do you safely delete a file?
- What does cat command do?
- Can mv be used to rename files? Explain.

**Answers:**

**Difference between cp and mv:**
- `cp` (copy) duplicates a file, leaving the original intact
- `mv` (move) relocates a file, removing it from the original location

**What is the use of rm command?**
`rm` removes files and directories permanently from the filesystem. Common options include `-r` for recursive deletion of directories and `-f` to force deletion without confirmation.

**Explain output redirection in Linux:**
Output redirection sends command results (stdout) to a file instead of displaying on the terminal. This allows saving command output for later use, logging, or piping to other commands.

**Difference between > and >>:**
- `>` overwrites the file with new content
- `>>` appends content to the existing file

**How do you safely delete a file?**
Use `rm -i` for interactive confirmation before deletion, or create backups before deletion. The `-i` flag prompts before every removal.

**What does cat command do?**
`cat` displays the contents of a file(s) on the terminal. It can also concatenate multiple files and create new files using redirection.

**Can mv be used to rename files? Explain.**
Yes, `mv` can rename files by moving a file to a new name in the same directory. Example: `mv oldname.txt newname.txt` renames the file.

---

## Tips

- Use `rm` carefully, as deleted files cannot be recovered easily
- Verify file names before executing copy or delete commands
- Use redirection cautiously to avoid overwriting important data
- Maintain backups of important files
- Use `rm -i` for interactive mode when unsure
- Check current directory with `pwd` before operations
- Use `ls` frequently to verify changes

---

## References

- rm Manual: `man rm`
- cp Manual: `man cp`
- mv Manual: `man mv`
- Shell Redirection: https://www.gnu.org/software/bash/manual/html_node/Redirections.html
