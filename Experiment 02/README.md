
# Exploring Linux System Commands, Run Levels & Help Utilities

## Introduction

Efficient use of the Linux operating system requires a strong understanding of basic system commands, system states, and built-in help mechanisms. Unlike graphical operating systems, Linux relies heavily on command-line utilities for system interaction, administration, and automation.

This experiment explores essential Linux system commands, understands system run levels/targets, and effectively uses Linux help utilities such as `man`, `--help`, and auto-completion.

---

## Learning Outcomes

| LO | Description |
|----|-------------|
| LO1 | Execute basic Linux system and user-level commands |
| LO2 | Understand Linux run levels (systemd targets) |
| LO3 | Use Linux help utilities to learn command syntax and options |
| LO4 | Improve efficiency using command auto-completion |

---

## Theory

### Linux Command Line Interface (CLI)

The Linux CLI allows users to interact with the operating system by typing commands. It provides precise control over system operations and is faster and more powerful than graphical interfaces for many tasks.

### System Run Levels / Targets

In modern Linux distributions using systemd, run levels are replaced by targets, which define the system's operating state.

| Target | Description |
|--------|-------------|
| graphical.target | Multi-user mode with GUI |
| multi-user.target | Multi-user mode without GUI |
| rescue.target | Single-user rescue mode |
| poweroff.target | Shutdown system |
| reboot.target | Reboot system |

### Linux Help Utilities

Linux provides built-in documentation tools:

| Utility | Description |
|---------|-------------|
| `man` | Displays the manual page for a command |
| `--help` | Displays brief command usage information |
| Tab auto-completion | Completes commands and file names automatically |

---

## Commands Reference

| Command | Description |
|---------|-------------|
| `pwd` | Display current working directory |
| `ls` | List files and directories |
| `cd` | Change directory |
| `whoami` | Display current user |
| `date` | Show system date and time |
| `uptime` | Show system running time |
| `man` | Display manual pages |
| `systemctl` | Manage system services and targets |
| `runlevel` | Display previous and current run level |
| `clear` | Clear terminal screen |

---

## Procedure

### Step 1: Open the Terminal

Log in to the Linux virtual machine and open the terminal application.

### Step 2: Execute Basic System Commands

```bash
pwd                    # Show current directory
whoami                 # Show current user
date                   # Show current date and time
uptime                 # Show system uptime
ls                     # List files in current directory
ls -la                 # List files with details
```

### Step 3: Navigate Directories

```bash
cd /home               # Navigate to /home directory
cd ~                   # Navigate to home directory
cd ..                  # Go to parent directory
cd -                   # Go to previous directory
```

### Step 4: Use Manual Pages

```bash
man ls                 # View manual for ls command
man cd                 # View manual for cd command
man date               # View manual for date command
man systemctl          # View manual for systemctl
```

> **Note:** Exit the manual using the `q` key.

### Step 5: Use Help Options

```bash
ls --help              # Display ls help
date --help            # Display date help
systemctl --help       # Display systemctl help
```

### Step 6: Check and Change Run Level / Target

```bash
# Check current run level
runlevel
systemctl get-default

# Switch to multi-user mode (text mode)
sudo systemctl isolate multi-user.target

# Switch to graphical mode
sudo systemctl isolate graphical.target
```

#### Classic System V Runlevel Change

```bash
# Switch to runlevel 3 (multi-user text mode)
sudo init 3

# Switch to runlevel 5 (graphical mode)
sudo init 5
```

### Step 7: Practice Auto-Completion

Type partial command names and press `Tab` to complete:
- Type `sys` and press Tab to see available commands
- Type `ls -` and press Tab to see ls options
- Type `cd /h` and press Tab to complete path

### Step 8: Clear Terminal

```bash
clear                  # Clear the terminal screen
```

---

## Expected Output

- [x] Successful execution of basic Linux commands
- [x] Display of manual pages and help documentation
- [x] Identification of current system run level / target
- [x] Improved familiarity with Linux command usage

---

## Results

Basic Linux system commands, run levels, and help utilities were successfully explored and executed. The student gained practical understanding of Linux command-line interaction and documentation mechanisms.

---

## Viva Questions & Answers

### Q1: What is the Linux command-line interface?
The Linux CLI is a text-based interface that allows users to interact with the operating system by typing commands. It provides precise control over system operations through various command-line utilities.

### Q2: What is the purpose of `man` command?
The `man` command displays the manual page for any command, providing detailed documentation including description, syntax, options, and examples for proper command usage.

### Q3: Difference between `man` and `--help`?
| Aspect | man | --help |
|--------|-----|--------|
| Format | Formatted pages (pager) | Simple text output |
| Detail | Comprehensive documentation | Brief summary |
| Navigation | Page-by-page viewing | Scrollable text |
| Exit | Press `q` | End of output |

### Q4: What are run levels or systemd targets?
Run levels (System V) and systemd targets define the system's operating state. They control which services and functionality are available, such as single-user mode, multi-user text mode, or graphical multi-user mode.

### Q5: What is `graphical.target`?
`graphical.target` is a systemd target that starts a multi-user system with graphical display manager. It is equivalent to runlevel 5 in classic System V and provides the full GUI desktop environment.

### Q6: How does auto-completion help users?
Auto-completion (Tab key) helps users by:
- Reducing typing errors
- Saving time on long command/file names
- Discovering available commands and options
- Completing file paths automatically

### Q7: What command shows the current working directory?
The `pwd` (print working directory) command displays the absolute path of the current working directory.

---

## Tips

- Always refer to `man` pages before using unfamiliar commands
- Do not change system targets unless necessary
- Use auto-completion to reduce typing errors

---

## References

- Linux Manual Pages: `man man`
- systemd Documentation: https://www.freedesktop.org/wiki/Software/systemd/
- GNU Coreutils: https://www.gnu.org/software/coreutils/manual/
