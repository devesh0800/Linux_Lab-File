# Shell Script to Print File Names with Creation Date and Serial Number

## Introduction

In Linux systems, administrators often need to list files along with their metadata such as creation or modification time in an organized and readable format. Displaying file names with serial numbers and timestamps is useful for auditing, reporting, backup verification, and log management. Automating this task using shell scripting improves efficiency and consistency.

The problem is to write a shell script that lists all files in a directory along with a serial number and their creation (or last modification) date, demonstrating file metadata handling and formatted output in Bash scripting.

---

## Course Outcome Mapping

| CO | Description |
|----|-------------|
| CO2 | Ability to write Bash scripts for automating file-related tasks |
| CO3 | Extraction and formatting of command output for meaningful presentation |

---

## Learning Outcomes

| LO | Description |
|----|-------------|
| LO1 | Access file metadata such as timestamps in Linux |
| LO2 | Generate serial numbers programmatically in a shell script |
| LO3 | Format output for readability using Bash scripting |
| LO4 | Automate directory listing tasks using scripts |

---

## Theory

### File Timestamps in Linux

Linux maintains multiple timestamps for files:
- **Access time (atime)** – Last access
- **Modification time (mtime)** – Last content modification
- **Change time (ctime)** – Last metadata change

Note: Traditional Linux file systems do not always store true creation time. Therefore, mtime or ctime is commonly used to represent file creation or update information.

### Listing Files Programmatically

Using commands such as `ls`, `stat`, and loops, file information can be extracted and formatted within shell scripts.

### Commands Used

| Command | Description |
|---------|-------------|
| ls | List directory contents |
| stat | Display detailed file information |
| awk | Text processing |
| date | Format timestamps |
| echo | Display formatted output |

---

## Procedure

### A. Writing the Shell Script

1. Open the terminal.
2. Create a script file:
   ```
   nano file_info.sh
   ```
3. Enter the following script:
   ```bash
   #!/bin/bash
   count=1
   echo "S.No File Name Date"
   for file in *
   do
     if [ -f "$file" ]; then
       mod_date=$(stat -c %y "$file" | cut -d'.' -f1)
       echo "$count $file $mod_date"
       count=$((count + 1))
     fi
   done
   ```
4. Save and exit the editor.
5. Make the script executable:
   ```
   chmod +x file_info.sh
   ```

### B. Executing the Script

6. Run the script in a directory containing files:
   ```
   ./file_info.sh
   ```

---

## Sample Execution

```bash
$ ./file_info.sh
S.No File Name Date
1 file1.txt 2026-01-10 10:30:12
2 report.doc 2026-01-09 14:20:05
3 script.sh 2026-01-08 18:10:44
```

---

## Expected Output

- [x] Files listed with serial numbers.
- [x] File names displayed correctly.
- [x] Corresponding date and time displayed for each file.

---

## Result

A shell script was successfully written and executed to list file names along with their serial number and modification date, demonstrating file metadata extraction and formatted output using Bash scripting.

---

## Guidelines to Students

- Understand the difference between atime, mtime, and ctime.
- Run the script in directories with sample files for clarity.
- Modify formatting if long file names exist.
- Use quotes around variables to avoid errors with spaces.

---

## Viva Questions

- What are virtual terminals in Linux?
  - **Answer:** Virtual terminals (VTs) are virtual console devices that provide text-based terminal interfaces in Linux. They allow multiple independent terminal sessions to run concurrently, accessible via key combinations like Ctrl+Alt+F1 through F6. However, this question appears to be unrelated to the experiment topic.

- What are file timestamps in Linux?
  - **Answer:** File timestamps are metadata that track when a file was accessed (atime), modified (mtime), or had its metadata changed (ctime). They are stored as part of the file's inode information.

- Does Linux store actual file creation time?
  - **Answer:** Traditional Linux file systems (ext2, ext3, ext4) do not store the true creation time (birth time). Only atime, mtime, and ctime are available. Some modern file systems like Btrfs and XFS may store creation time, but it's not widely accessible.

- Difference between mtime and ctime.
  - **Answer:** 
    - **mtime (modification time):** The last time the file's content was modified.
    - **ctime (change time):** The last time the file's metadata (permissions, ownership, etc.) was changed. It also updates when content is modified.

- What is the use of stat command?
  - **Answer:** The `stat` command displays detailed information about a file, including size, permissions, ownership, access/modification/change times, and inode information. `stat -c` allows custom formatting of output.

- How are serial numbers generated in the script?
  - **Answer:** Serial numbers are generated using a counter variable (`count`) that starts at 1 and increments by 1 (`count=$((count + 1))`) for each file processed in the loop.

- Why is output formatting important?
  - **Answer:** Output formatting makes data easier to read and understand. Proper alignment, headers, and structured presentation are essential for auditing, reporting, and automation tasks where scripts generate logs or reports.

- How can this script be extended for directories?
  - **Answer:** The script can be extended by passing a directory path as a command-line argument (`$1`), allowing it to process any specified directory. It can also be modified to recursively list files in subdirectories using `find` or by adding options like `-r` for recursion.

---

## References

- Linux Man Pages: `man ls`, `man stat`, `man date`
- Introduction to Linux with Bash Scripting Lab (Dr. Rajesh Kumar)
