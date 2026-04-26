# Shell Script for User Login Count, File Listing and Job Control

## Introduction

Linux provides powerful utilities to monitor user activity, manage files, and control process execution priorities. System administrators and cyber security professionals often need to determine how many users are currently logged in, list files in structured formats, and manage jobs running in foreground or background with controlled priorities.

The problem is to write shell scripts that display the number of users logged into the system, list files in a columnar format, and manage job execution using priority and background execution, thereby demonstrating system monitoring and job control through Bash scripting.

---

## Course Outcome Mapping

| CO | Description |
|----|-------------|
| CO2 | Ability to write Bash scripts for system monitoring and automation |
| CO3 | Execution and control of processes and jobs in Linux |

---

## Learning Outcomes

| LO | Description |
|----|-------------|
| LO1 | Determine the number of users currently logged into the system |
| LO2 | Display files in a formatted column list |
| LO3 | Manage job execution priority using nice |
| LO4 | Continue running jobs in the background after logout |

---

## Theory

### User Login Monitoring

Linux supports multiple users simultaneously. Commands such as who and users help administrators monitor logged-in users.

### File Listing

The ls command can display files in multiple formats. Using options such as -l and -C, files can be displayed in a structured column layout.

### Job Control

Linux allows processes to run:
- In the foreground
- In the background

The nice command adjusts the scheduling priority of a process, and nohup allows a process to continue running after logout.

---

## Commands Reference

| Command | Description |
|---------|-------------|
| who | Display logged-in users |
| wc -l | Count number of lines |
| ls -C | Display files in columns |
| nice | Run command with priority |
| nohup | Run command immune to hangup |
| jobs | List background jobs |
| bg | Resume job in background |
| fg | Resume job in foreground |

---

## Procedure

### A. Writing the Shell Script

1. Open the terminal.
2. Create a script file:
   ```
   nano system_info.sh
   ```
3. Enter the following script:
   ```bash
   #!/bin/bash
   echo "Number of users currently logged in:"
   who | wc -l
   echo "Files in home directory (column format):"
   ls -C $HOME
   echo "Running a job with lower priority:"
   nice -n 10 sleep 60 &
   echo "Running a background job that survives logout:"
   nohup sleep 120 &
   ```
4. Save and exit the editor.
5. Make the script executable:
   ```
   chmod +x system_info.sh
   ```

### B. Executing the Script

6. Run the script:
   ```
   ./system_info.sh
   ```

---

## Sample Execution

```bash
$ ./system_info.sh
Number of users currently logged in:
2
Files in home directory:
Desktop Documents Downloads
[1] 3456
[2] 3457
```

---

## Expected Output

- [x] Number of logged-in users displayed correctly.
- [x] Files listed in column format.
- [x] Background jobs started with specified priorities.
- [x] Jobs continue to run independently.

---

## Result

A shell script was successfully written and executed to display logged-in user count, list files in column format, and manage job execution using priority and background processing.

---

## Guidelines to Students

- Avoid running long background jobs unnecessarily.
- Use nice values carefully; lower values mean higher priority.
- Monitor background jobs using jobs or ps.
- Terminate jobs after completion to free system resources.

---

## Viva Questions

- How do you count logged-in users in Linux?
  - **Answer:** Using the `who | wc -l` command. The `who` command lists all logged-in users and `wc -l` counts the number of lines (users).

- What is the purpose of ls -C?
  - **Answer:** The `ls -C` command lists files in a multi-column format, displaying them arranged in columns from left to right.

- What does the nice command do?
  - **Answer:** The `nice` command runs a command with a modified scheduling priority. It allows users to set the priority of a process using the `-n` option (e.g., `nice -n 10` sets a lower priority, where higher nice values mean lower priority).

- Difference between foreground and background jobs.
  - **Answer:** Foreground jobs run in the terminal and block user input until they complete. Background jobs run simultaneously with other processes and don't block the terminal, allowing the user to continue working.

- What is nohup and when is it used?
  - **Answer:** `nohup` (no hangup) is used to run a command that continues running even after the user logs out or closes the terminal. It ignores the hangup signal, useful for long-running processes.

- How do you list background jobs?
  - **Answer:** Using the `jobs` command, which displays all background jobs running in the current terminal session along with their job numbers and status.

- How can you stop a background job?
  - **Answer:** Use `kill %job_number` (e.g., `kill %1`) or find the process ID with `ps` and use `kill PID`. Also, `kill $(jobs -p)` can terminate all background jobs.

---

## References

- Linux Man Pages: `man who`, `man wc`, `man ls`, `man nice`, `man nohup`, `man jobs`
- Introduction to Linux with Bash Scripting Lab (Dr. Rajesh Kumar)
