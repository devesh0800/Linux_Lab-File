# Shell Script to Change Date Format and Measure execution time

## Introduction

Date and time manipulation is a common requirement in system administration, logging, and automation scripts. Linux provides powerful utilities to display and format date and time information. Additionally, measuring the execution time of a script helps evaluate performance and efficiency.

The problem is to write a shell script that changes the system date format as required and measures the time taken for execution of the script, thereby demonstrating date handling and performance measurement in Bash scripting.

---

## Course Outcome Mapping

| CO | Description |
|----|-------------|
| CO2 | Ability to write Bash scripts for automation and system utilities |
| CO4 | Application of scripting logic for structured task execution |

---

## Learning Outcomes

| LO | Description |
|----|-------------|
| LO1 | Display date and time in different formats using Linux commands |
| LO2 | Use shell scripts to customize date output |
| LO3 | Measure execution time of a shell script |
| LO4 | Understand the importance of performance measurement in scripting |

---

## Theory

### Date Command in Linux

The `date` command displays or sets the system date and time. It supports format specifiers that allow customized output.

Common format options:
- `%d` – Day
- `%m` – Month
- `%Y` – Year
- `%H` – Hour
- `%M` – Minute
- `%S` – Second

### Execution Time Measurement

The execution time of a command or script can be measured using:
- The `time` command
- Internal timestamps using `date +%s`

### Commands Used

| Command | Description |
|---------|-------------|
| date | Display date and time |
| time | Measure execution time |
| sleep | Delay execution |
| echo | Display output |

---

## Procedure

### A. Writing the Shell Script

1. Open the terminal.
2. Create a script file:
   ```
   nano date_time.sh
   ```
3. Enter the following script:
   ```bash
   #!/bin/bash
   echo "Current Date (DD-MM-YYYY):"
   date +"%d-%m-%Y"
   echo "Current Time (HH:MM:SS):"
   date +"%H:%M:%S"
   start_time=$(date +%s)
   sleep 2
   end_time=$(date +%s)
   execution_time=$((end_time - start_time))
   echo "Execution Time: $execution_time seconds"
   ```
4. Save and exit the editor.
5. Make the script executable:
   ```
   chmod +x date_time.sh
   ```

### B. Executing the Script

6. Run the script with execution time measurement:
   ```
   time ./date_time.sh
   ```

---

## Sample Execution

```bash
$ time ./date_time.sh
Current Date (DD-MM-YYYY):
10-01-2026
Current Time (HH:MM:SS):
10:45:32
Execution Time: 2 seconds

real 0m2.01s
user 0m0.00s
sys 0m0.01s
```

---

## Expected Output

- [x] Date and time displayed in customized format.
- [x] Execution time calculated and displayed correctly.
- [x] Script execution time measured using time command.

---

## Result

A shell script was successfully written and executed to change the date format and measure the execution time, demonstrating date manipulation and performance evaluation in Linux.

---

## Guidelines to Students

- Use correct date format specifiers.
- Do not attempt to modify system date without permission.
- Understand the difference between real, user, and system time.
- Measure execution time for optimization purposes.

---

## Viva Questions

- What is the use of date command?
  - **Answer:** The `date` command is used to display or set the system's date and time. It can show the current date and time in various formats using format specifiers like `%d`, `%m`, `%Y`, `%H`, `%M`, `%S`, etc.

- How do you change the date format in Linux?
  - **Answer:** By using format specifiers with the `date` command. For example, `date +"%d-%m-%Y"` displays the date in DD-MM-YYYY format, and `date +"%H:%M:%S"` displays time in HH:MM:SS format.

- What does the time command measure?
  - **Answer:** The `time` command measures the execution time of a command or script. It reports three types of time: real (wall clock time), user (CPU time spent in user mode), and sys (CPU time spent in kernel mode).

- Difference between real, user, and system time.
  - **Answer:** 
    - **Real time:** The actual elapsed time from start to finish (wall clock time).
    - **User time:** The CPU time spent executing in user mode (processing user-level code).
    - **System time:** The CPU time spent executing in kernel mode (operating system calls).

- Why is execution time measurement important?
  - **Answer:** Execution time measurement is important for analyzing script performance, identifying bottlenecks, optimizing code, and ensuring efficient resource utilization. It helps in comparing different implementations and improving overall script efficiency.

- What does %Y represent in date format?
  - **Answer:** `%Y` represents the full 4-digit year (e.g., 2026). Lowercase `%y` represents the 2-digit year (e.g., 26).

- Can scripts modify system date? Why or why not?
  - **Answer:** Scripts can potentially modify system date using `date -s` or similar commands, but typically root/sudo privileges are required. Modifying system date without proper permission is discouraged as it can cause logging issues, certificate problems, and other system inconsistencies.

---

## References

- Linux Man Pages: `man date`, `man time`, `man sleep`
- Introduction to Linux with Bash Scripting Lab (Dr. Rajesh Kumar)
