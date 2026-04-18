# Cross Platform Linux Package Management

## Introduction

Linux systems rely on software packages to install, update, and manage applications and system utilities. Manually compiling software from source is time-consuming and prone to errors. To address this, Linux provides automated package management systems. This experiment focuses on understanding the operation of both Red Hat-based (RPM/YUM) and Debian-based (DPKG/APT) systems, including dependency resolution and the role of language-specific managers like NPM.

---

## Course Outcome Mapping

| CO | Description |
|----|-------------|
| CO1 | Familiarity with Linux system utilities and package management tools |

---

## Learning Outcomes

| LO | Description |
|----|-------------|
| LO1 | Understand the role of package management in Linux |
| LO2 | Master low-level (dpkg, rpm) and high-level (apt, yum) tools |
| LO3 | Differentiate between System Managers (OS level) and Language Managers (Application level like NPM) |
| LO4 | Differentiate between low-level and high-level package managers |

---

## Theory

### Package Management in Linux

Linux distributions generally fall into two packaging "ecosystems." A package is a compressed archive containing:
- **Software binaries**
- **Configuration files**
- **Metadata** (version, dependencies, scripts)

Package managers simplify software management by automating installation, upgrade, removal, and dependency handling.

| Feature | Debian/Ubuntu Family | Red Hat/Fedora Family |
|---------|----------------------|-----------------------|
| Package Format | .deb | .rpm |
| Low-Level Tool | `dpkg` (Installs local files) | `rpm` (Installs local files) |
| High-Level Tool | `APT` (Automates dependencies) | `YUM` / `DNF` (Automates dependencies) |

### System vs. Language Managers

- **System Managers (APT/YUM):** Manage the Operating System and shared utilities.
- **Language Managers (NPM/Pip):** Manage libraries for a specific programming language (e.g., JavaScript/Node.js). They usually reside "on top" of the system manager.

---

## Commands Reference

### General Comparison
| Action | Ubuntu (Lab Environment) | Red Hat (Theory/Manual) |
|--------|--------------------------|-------------------------|
| Search | `apt search <package>` | `yum search <package>` |
| Install | `sudo apt install <package>` | `sudo yum install <package>` |
| Query (Local) | `dpkg -l <package>` | `rpm -qi <package>` |
| Remove | `sudo apt remove <package>` | `sudo yum remove <package>` |
| Update List | `sudo apt update` | `yum check-update` |

### DPKG & APT (Debian/Ubuntu)
| Command | Description |
|---------|-------------|
| `dpkg -l` | List all installed Debian packages |
| `dpkg -s` | Display status and information of a specific package |
| `dpkg -i` | Install a local .deb package |
| `apt install` | Install a package and its dependencies |
| `apt update` | Update the local database of available packages |
| `apt search` | Search for a package in the repositories |

### RPM & YUM (Red Hat)
| Command | Description |
|---------|-------------|
| `rpm -qa` | List all installed RPM packages |
| `rpm -qi` | Display package information |
| `yum install` | Install a package and resolve dependencies |
| `yum remove` | Remove a package |
| `yum update` | Update packages |

---

## Procedure

### Step 1: Working with Ubuntu (Hands-on)
1. **Update Repository Index:** `sudo apt update`
2. **Search for a utility (e.g., tree):** `apt search tree`
3. **Install the utility:** `sudo apt install tree`
4. **Verify Installation:** `tree --version`
5. **View Package Details:** `dpkg -s tree`
6. **Remove the utility:** `sudo apt remove tree`

### Step 2: Using YUM (Red Hat)
1. **Search for a package:** `yum search nano`
2. **Install a package:** `sudo yum install nano`
3. **Verify installation:** `nano --version`
4. **List installed packages:** `yum list installed`
5. **Remove a package:** `sudo yum remove nano`
6. **Update system packages:** `sudo yum update`

---

## Sample Execution

```bash
$ yum search nano
$ sudo yum install nano
Installed:
 nano.x86_64 0:5.6.1-1.el8
$ nano --version
GNU nano, version 5.6.1
```

---

## Expected Output

- [x] Successful navigation of both dpkg and apt commands.
- [x] Identification of the differences between .deb and .rpm files.
- [x] Understanding that yum and apt perform the same role for different "families."

---

## Results

Linux package management operations were successfully performed across Ubuntu and Red Hat environments. The student learned to manage OS utilities and understood the distinction between system and language-level managers (NPM).

---

## Viva Questions

- **What is a package in Linux?**
  - **Answer:** A package is a compressed archive containing software binaries, configuration files, and metadata (like version and dependencies) required for an application to be installed and run correctly on a Linux system.

- **Difference between rpm and yum.**
  - **Answer:** `rpm` is a low-level package manager that works with individual `.rpm` files but does not automatically resolve dependencies. `yum` is a high-level tool that works on top of `rpm`, automatically fetching packages from repositories and resolving all dependencies.

- **Why is dependency management important?**
  - **Answer:** Software often relies on other libraries or tools. Dependency management ensures that all required components are installed in the correct versions, preventing software failures and manual installation overhead.

- **What is a repository?**
  - **Answer:** A repository is a centralized storage location (usually on a remote server) where software packages are hosted and maintained, allowing package managers to download and install them easily.

- **Why should yum be preferred over manual RPM installation?**
  - **Answer:** `yum` handles dependency resolution automatically. If an RPM package requires other files to work, `yum` will find and install them, whereas `rpm` will simply report an error and stop.

- **What command updates all system packages?**
  - **Answer:** On Debian-based systems, `sudo apt upgrade` (after `apt update`). On Red Hat-based systems, `sudo yum update`.

---

## Tips

- **Preference:** Always prefer high-level managers (`apt`/`yum`) for automatic dependency resolution.
- **Safety:** Avoid removing packages marked as essential or system-critical.
- **Currency:** Always run `update` before `install` to avoid version conflicts.

---

## References

- Linux Man Pages: `man apt`, `man yum`, `man rpm`, `man dpkg`
- Introduction to Linux with Bash Scripting Lab (Dr. Rajesh Kumar)
