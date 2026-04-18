# Managing Users and Groups in Linux

## Introduction

Linux is a multi-user operating system where multiple users can access system resources simultaneously. Proper user and group management is essential to ensure system security, controlled access to files, and efficient administration. Cyber security professionals must understand how Linux manages users, groups, ownership, and permissions to prevent unauthorized access and enforce security policies.

The goal of this experiment is to create, modify, and manage users and groups in Linux, understand file ownership and group permissions, and practice sharing files securely between users and groups.

---

## Course Outcome Mapping

| CO | Description |
|----|-------------|
| CO1 | Familiarity with Linux environment and system administration commands |
| CO3 | Understanding permission control and ownership for secure operations |

---

## Learning Outcomes

| LO | Description |
|----|-------------|
| LO1 | Create and manage user accounts in Linux |
| LO2 | Create and manage groups and assign users to groups |
| LO3 | Understand file ownership and group-based access control |
| LO4 | Use special permissions such as sticky bit for secure file sharing |

---

## Theory

### Users in Linux

Each user in Linux has a unique username, a user ID (UID), a home directory, and a default shell. Linux supports different types of users:
- **Root user:** Superuser with full system privileges.
- **Normal users:** Regular users with limited privileges.

### Groups in Linux

Groups are collections of users that simplify permission management. Each file or directory belongs to one owner and one group.

### File Ownership

Ownership determines who can read, write, or execute files. The commands `chown` and `chgrp` are used to modify ownership.

### Sticky Bit

The sticky bit is a special permission that prevents users from deleting files owned by others in a shared directory. It is typically applied to directories used for collaboration.
**Example:** `chmod +t directory_name`

---

## Commands Reference

| Command | Description |
|---------|-------------|
| `useradd` | Create a new user |
| `passwd` | Set or change user password |
| `usermod` | Modify user account |
| `userdel` | Delete a user |
| `groupadd` | Create a new group |
| `groupdel` | Delete a group |
| `groups` | Display groups of a user |
| `chown` | Change file owner |
| `chgrp` | Change file group |
| `chmod` | Change permissions |
| `id` | Display user identity |

---

## Procedure

### Step 1: Log in and Open Terminal
Log in to your Linux system and open the terminal emulator.

### Step 2: Create and Verify a New User
Create a new user named `testuser` and set a password.
```bash
sudo useradd testuser
sudo passwd testuser
```
Verify the creation of the user:
```bash
id testuser
```

### Step 3: Manage Groups
Create a new group called `testgroup` and add the previously created user to it.
```bash
sudo groupadd testgroup
sudo usermod -aG testgroup testuser
```
Verify the group membership:
```bash
groups testuser
```

### Step 4: Secure File Sharing with Sticky Bit
Create a shared directory and set appropriate group permissions.
```bash
mkdir shared_dir
sudo chgrp testgroup shared_dir
sudo chmod 770 shared_dir
```
Apply the sticky bit to protect files within the shared directory:
```bash
sudo chmod +t shared_dir
```

### Step 5: Modify File Ownership
Create a file and change its ownership to the new user and group.
```bash
touch shared_file.txt
sudo chown testuser:testgroup shared_file.txt
```

---

## Sample Execution

```bash
$ sudo useradd testuser
$ sudo groupadd testgroup
$ sudo usermod -aG testgroup testuser
$ groups testuser
testuser : testuser testgroup
```

---

## Expected Output

- [x] New users and groups created successfully
- [x] Users added to groups correctly and verified via `groups` or `id`
- [x] File and directory ownership modified using `chown` and `chgrp`
- [x] Shared directory protected using the sticky bit (`+t`)

---

## Results

Linux user and group management operations were successfully performed. The student learned to control access to system resources using users, groups, permissions, and special access bits.

---

## Viva Questions

- What is the difference between root and normal user?
  - **Answer:** The root user (UID 0) is the superuser with full administrative privileges and unrestricted access to all files and commands on the system. Normal users have restricted access, typically limited to their own home directory and specific system resources, and require `sudo` or root permissions to perform administrative tasks.

- What is the purpose of groups in Linux?
  - **Answer:** Groups are used to organize users and simplify permission management. Instead of assigning permissions to each user individually, permissions can be granted to a group, and any user added to that group automatically inherits those permissions.

- Explain `useradd` vs `usermod`.
  - **Answer:** `useradd` is used to create a new user account from scratch, while `usermod` is used to modify the attributes of an existing user account (e.g., changing their home directory, shell, or group memberships).

- What is sticky bit and where is it used?
  - **Answer:** The sticky bit is a special permission (represented by `t`) applied to directories. When set, only the file's owner, the directory's owner, or the root user can delete or rename files within that directory. It is commonly used on shared directories like `/tmp` to prevent users from deleting each other's files.

- Difference between `chown` and `chgrp`.
  - **Answer:** `chown` (change owner) is used to change both the user owner and the group owner of a file or directory. `chgrp` (change group) is specifically used to change only the group ownership of a file or directory.

- How does Linux enforce file ownership?
  - **Answer:** Linux enforces ownership through the filesystem metadata. Each file/directory is associated with a specific User ID (UID) and Group ID (GID). The kernel checks these IDs against the UID/GID of the process attempting to access the file to determine if the requested operation (read, write, or execute) is permitted based on the file's permission bits.

- Why is user management important in cyber security?
  - **Answer:** User management is critical for enforcing the "Principle of Least Privilege," ensuring that users only have the minimum access necessary to perform their jobs. It helps prevent unauthorized access, limits the impact of a compromised account, provides accountability through logging, and secures sensitive system data.

---

## Tips

- Always use `sudo` responsibly.
- Do not modify system users without permission.
- Verify ownership and permissions after making changes.
- Understand the security implications of group access.
- Practice sticky bit usage carefully to ensure collaboration remains secure.

---

## References

- Linux Man Pages: `man useradd`, `man chmod`
- Introduction to Linux with Bash Scripting Lab (Dr. Rajesh Kumar)
