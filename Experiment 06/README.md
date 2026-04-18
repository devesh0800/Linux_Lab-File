# Virtual Terminals, Display Managers, and Window Managers

## Introduction

Linux operating systems support multiple user sessions and interfaces through the use of virtual terminals and graphical environments. Understanding how Linux manages text-based terminals, graphical display servers, display managers, X clients, and window managers is essential for system administration, troubleshooting, and cyber security operations.

The goal of this experiment is to explore and understand virtual terminals, display managers, X clients, and window managers, and to practice switching between text-based and graphical interfaces in a Linux environment.

---

## Learning Outcomes

| LO | Description |
|----|-------------|
| LO1 | Understand the concept of virtual terminals in Linux |
| LO2 | Switch between multiple virtual terminals |
| LO3 | Understand the role of the display manager and graphical login system |
| LO4 | Identify X clients and window managers in Linux |

---

## Theory

### Virtual Terminals

Linux supports multiple virtual terminals (VTs) that allow users to access several independent terminal sessions simultaneously. These terminals run in text mode and are useful for system recovery and troubleshooting.

**Common key combinations:**
- `Ctrl + Alt + F1` to `Ctrl + Alt + F6` – Text-based virtual terminals
- `Ctrl + Alt + F7` (or `F1` on some systems) – Graphical interface

### Display Manager

A display manager provides the graphical login interface and manages user sessions. It starts the graphical server and handles authentication.

**Common display managers:**
- GDM (GNOME Display Manager)
- LightDM
- SDDM

### X Window System

The X Window System (X11) is responsible for handling graphical display, keyboard, and mouse input. It enables graphical applications (X clients) to run on a Linux system.

### X Clients

X clients are graphical applications that communicate with the X server to display windows. Examples include:
- Terminal emulator
- Web browser
- Text editor

### Window Manager

A window manager controls the placement, appearance, and behavior of windows on the screen. Examples:
- GNOME Shell
- KDE Plasma
- Xfce
- Openbox

---

## Commands Reference

| Command | Description |
|---------|-------------|
| `tty` | Display current terminal name |
| `who` | Show who is logged on |
| `w` | Show who is logged on and what they are doing |
| `startx` | Initialize an X session |
| `systemctl status` | Check status of system services (e.g., display manager) |
| `ps` | Report a snapshot of the current processes |
| `echo $DISPLAY` | Display the value of the X session variable |

---

## Procedure

### Step 1: Check Current Terminal
Open your terminal and check which terminal device you are currently using.
```bash
tty
```

### Step 2: Switch to a Virtual Terminal
Switch to another virtual terminal (text-based) using the following key combination:
- Press `Ctrl + Alt + F2`
- Log in with your credentials to verify terminal access.

### Step 3: Switch Back to Graphical Mode
Return to your graphical desktop environment:
- Press `Ctrl + Alt + F1` or `Ctrl + Alt + F7` (depending on your distribution).

### Step 4: Check Logged-in Users
View active user sessions and their associated terminals.
```bash
who
w
```

### Step 5: Check Display Manager Status
Identify the display manager running on your system.
```bash
systemctl status gdm      # For GNOME
# OR
systemctl status lightdm  # For LightDM
# OR
systemctl status sddm     # For SDDM
```

### Step 6: Verify X Session Variable
Check the `$DISPLAY` environment variable which indicates the current graphical display.
```bash
echo $DISPLAY
```

### Step 7: List Running X-related Processes
Search for processes related to the X Window System.
```bash
ps -e | grep X
```

---

## Expected Output

- [x] Successful switching between virtual terminals and graphical mode
- [x] Identification of the active display manager (e.g., GDM, LightDM)
- [x] Display of active user sessions via `who` or `w`
- [x] Confirmation of graphical environment variables like `:0` or `:1`

---

## Results

Virtual terminals, display managers, X clients, and window managers were successfully explored. The student gained practical understanding of Linux system interfaces, switching between sessions, and graphical session management.

---

## Viva Questions

- What are virtual terminals in Linux?
- How do you switch between virtual terminals?
- What is a display manager?
- Difference between X server and window manager.
- What are X clients?
- What does `$DISPLAY` variable indicate?
- Why are virtual terminals useful for system recovery?

**Answers:**

**What are virtual terminals in Linux?**
Virtual terminals are multiple independent login sessions available on a single Linux machine. They allow a user to have multiple text-based sessions or graphical sessions simultaneously.

**How do you switch between virtual terminals?**
By using `Ctrl + Alt + F[1-7]`. Usually, F1-F6 are for text terminals and F7 (or F1 on newer systems) is for the graphical interface.

**What is a display manager?**
A display manager (or login manager) is a graphical program that handles the login process, authenticates the user, and starts the desktop environment or window manager.

**Difference between X server and window manager:**
The X server manages the hardware (display, mouse, keyboard) and provides the basic framework for drawing windows. The window manager is a client that controls the placement, appearance (borders, title bars), and behavior of those windows.

**What are X clients?**
X clients are graphical applications (like a web browser or a terminal emulator) that run on the X Window System and communicate with the X server to display their GUI.

**What does $DISPLAY variable indicate?**
The `$DISPLAY` variable tells graphical applications which X server and screen they should use to display their output (e.g., `:0` refers to the first local display).

**Why are virtual terminals useful for system recovery?**
If the graphical interface freezes or fails to load, virtual terminals (which run in text mode) allow a technician to log in, diagnose the problem, kill unresponsive processes, or edit configuration files to fix the system.

---

## Tips

- Do not stop or disable the display manager without permission.
- Use virtual terminals carefully on shared systems.
- Practice switching between terminals to build confidence.
- Understand the role of graphical components for troubleshooting.
- If `Ctrl + Alt + F1` doesn't work, try other function keys up to F7.

---

## References

- X.Org Foundation: https://www.x.org/
- systemctl Manual: `man systemctl`
- Virtual Terminal Documentation: `man tty`
- GNOME Display Manager: https://wiki.gnome.org/Projects/GDM
