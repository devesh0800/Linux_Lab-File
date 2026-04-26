# Shell Script to Check Whether a User is Logged In and Recheck Every 30 Seconds Until Success

## Introduction

In multi-user Linux environments, system administrators and security professionals often need to monitor user login status—for example, to detect authorized access, synchronize tasks with user activity, or trigger actions only after a specific user logs in. Automating this monitoring avoids continuous manual checking and ensures timely response.

The problem is to write a shell script that checks whether a specified user is logged in to the system and continues checking at regular intervals (every 30 seconds) until the user logs in, demonstrating looping, conditional checks, and time-based execution in Bash scripting.

---

## Course Outcome Mapping

| CO | Description |
|----|-------------|
| CO2 | Ability to write Bash scripts for automation and monitoring tasks |
| CO3 | Execution and control of commands for system-level monitoring |

---

## Learning Outcomes

| LO | Description |
|----|-------------|
| LO1 | Check the login status of a user using Linux commands |
| LO2 | Implement conditional logic to evaluate login status |
| LO3 | Use looping constructs for repeated checks |
| LO4 | Introduce time delays in scripts using sleep intervals |

---

## Theory

### User Login Monitoring in Linux

Linux provides commands such as `who`, `users`, and `w` to display information about currently logged-in users. By filtering the output of these commands, scripts can determine whether a particular user is active.

### Looping with Delay

A `while` loop combined with the `sleep` command enables periodic checks at fixed intervals. This approach is widely used in monitoring scripts, cron jobs, and security checks.

### Commands Used

| Command | Description |
|---------|-------------|
| who | Display logged-in users |
| grep | Search for a specific user |
| while | Loop until condition is met |
| sleep | Pause execution for a fixed time |
| echo | Display messages |

---

## Procedure

### A. Writing the Shell Script

1. Open the terminal.
2. Create a script file:
   ```
   nano check_login.sh
   ```
3. Enter the following script:
   ```bash
   #!/bin/bash
   echo "Enter the username to check:"
   read username
   while true
   do
     if who | grep -w "$username" > /dev/null
     then
       echo "User $username is now logged in."
       break
     else
       echo "User $username is not logged in. Checking again in 30 seconds..."
       sleep 30
     fi
   done
   ```
4. Save and exit the editor.
5. Make the script executable:
   ```
   chmod +x check_login.sh
   ```

### B. Executing the Script

6. Run the script:
   ```
   ./check_login.sh
   ```
7. Enter a valid username when prompted.
8. Log in as that user (from another terminal or system) to observe script behavior.

---

## Sample Execution

```bash
$ ./check_login.sh
Enter the username to check:
student
User student is not logged in. Checking again in 30 seconds...
User student is not logged in. Checking again in 30 seconds...
User student is now logged in.
```

---

## Expected Output

- [x] Script repeatedly checks login status at 30-second intervals.
- [x] Status messages displayed during each check.
- [x] Script terminates automatically once the user logs in.

---

## Result

A shell script was successfully written and executed to monitor a user's login status and recheck every 30 seconds until the user logged in, demonstrating effective use of loops, conditions, and time delays in Bash scripting.

---

## Guidelines to Students

- Ensure the username entered exists on the system.
- Avoid running multiple monitoring scripts simultaneously.
- Modify the sleep interval carefully if required.
- Terminate the script manually using Ctrl + C if needed.

---

## Viva Questions

- How does Linux identify logged-in users?
  - **Answer:** Linux identifies logged-in users by checking active terminal sessions (ttys), pseudo terminals (pts), and remote connections. Commands like `who`, `w`, and `users` query the utmp database to list users currently logged in.

- What is the purpose of the sleep command?
  - **Answer:** The `sleep` command pauses script execution for a specified duration. It's used to introduce delays between repeated operations, preventing excessive CPU usage and allowing time for external events (like user login) to occur.

- Why is a loop required in this script?
  - **Answer:** A loop is required because the script needs to check continuously until the user logs in. A single check would only show the current status at that moment, whereas a loop ensures ongoing monitoring until the target event occurs.

- What does grep -w do?
  - **Answer:** The `grep -w` command matches whole words only. In `grep -w "$username"`, it ensures that the username is matched as a complete word, preventing false matches like "student" matching within "student123".

- How can this script be stopped manually?
  - **Answer:** The script can be stopped manually by pressing Ctrl + C (SIGINT signal), which interrupts the running script. Alternatively, from another terminal, you can find the process ID with `ps aux | grep check_login.sh` and terminate it with `kill PID`.

- Where is such a script useful in cyber security?
  - **Answer:** This script is useful in cyber security for detecting unauthorized access, triggering alerts when specific users log in, coordinating tasks that depend on user presence, monitoring admin access, and forensic analysis of user activity patterns.

- How can the checking interval be modified?
  - **Answer:** The checking interval can be modified by changing the value in the `sleep` command. For example, `sleep 60` would check every 60 seconds, or a variable like `interval=30` can be used and modified as needed.

---

## References

- Linux Man Pages: `man who`, `man grep`, `man sleep`
- Introduction to Linux with Bash Scripting Lab (Dr. Rajesh Kumar)
