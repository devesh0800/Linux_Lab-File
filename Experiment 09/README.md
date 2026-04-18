# Mounting and unmounting devices in Linux

## Introduction

Linux systems use a unified directory structure in which storage devices such as hard disks, USB drives, and external storage must be explicitly attached to the file system to access their contents. Unlike some operating systems where devices are automatically available, Linux requires administrators to understand how devices are identified, mounted, and unmounted.

The problem is to identify storage devices in Linux, mount and unmount file systems manually, and understand the significance of mounting points and device management in system administration and cyber security environments.

---

## Course Outcome Mapping

| CO | Description |
|----|-------------|
| CO1 | Familiarity with Linux system utilities and file system structure |
| CO3 | Understanding system-level operations and resource management |

---

## Learning Outcomes

| LO | Description |
|----|-------------|
| LO1 | Identify storage devices and partitions in Linux |
| LO2 | Create mount points and mount file systems manually |
| LO3 | Unmount devices safely to prevent data corruption |
| LO4 | Understand the importance of mounting in Linux system administration |

---

## Theory

### Linux File System and Mounting
Linux follows a single-rooted directory structure where all files and devices are accessible through `/`. Storage devices must be mounted to a directory (mount point) before their contents can be accessed.

### Device Files
Linux represents hardware devices as files located in the `/dev` directory. Common examples include:
- `/dev/sda`, `/dev/sdb` – Hard disks
- `/dev/sda1`, `/dev/sdb1` – Disk partitions

### Mount Points
A mount point is an empty directory where a device’s file system is attached.
Example: `/mnt`, `/media`

### Unmounting Devices
Unmounting safely disconnects the device from the file system, ensuring all data is written properly and preventing corruption.

---

## Commands Reference

| Command | Description |
|---------|-------------|
| `lsblk` | List block devices |
| `fdisk -l` | Display disk partition information |
| `mount` | Mount a file system |
| `umount` | Unmount a file system |
| `df -h` | Display mounted file systems in human-readable format |
| `mkdir` | Create mount point |
| `blkid` | Display block device attributes (UUID, type, etc.) |

---

## Procedure

### Step 1: Identifying Devices
1. Open the terminal.
2. List available block devices: `lsblk`
3. Display detailed disk information: `sudo fdisk -l`

### Step 2: Creating a Mount Point
1. Create a directory to be used as a mount point: `sudo mkdir /mnt/usb`

### Step 3: Mounting a Device
1. Mount a partition (example `/dev/sdb1`) to the mount point: `sudo mount /dev/sdb1 /mnt/usb`
2. Verify the mount: `df -h` or simply `mount`

### Step 4: Accessing the Mounted Device
1. Navigate to the mounted directory: `cd /mnt/usb`
2. List files: `ls`

### Step 5: Unmounting the Device
1. Exit the mounted directory: `cd ~`
2. Unmount the device: `sudo umount /mnt/usb`
3. Verify unmounting: `df -h`

---

## Sample Execution

```bash
$ lsblk
sda      8:0    0   50G  0 disk 
├─sda1   8:1    0   45G  0 part /
└─sda2   8:2    0    5G  0 part [SWAP]
sdb      8:16   0    8G  0 disk 
└─sdb1   8:17   0    8G  0 part 

$ sudo mkdir /mnt/usb
$ sudo mount /dev/sdb1 /mnt/usb

$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        45G   10G   33G  24% /
/dev/sdb1       8.0G  1.0G  7.0G  15% /mnt/usb
```

---

## Expected Output

- [x] Storage devices and partitions are listed successfully.
- [x] Device is mounted to the specified mount point.
- [x] Files inside the mounted device are accessible.
- [x] Device is safely unmounted without errors.

---

## Results

Storage devices were successfully identified, mounted, accessed, and unmounted in Linux. The student gained practical understanding of Linux file system mounting and device management.

---

## Tips

- **Safety First:** Always unmount devices before removing them physically.
- **Security:** Do not mount unknown or untrusted devices.
- **Accuracy:** Ensure correct device names before mounting.
- **Usage:** Never unmount a device that is currently in use (ensure no terminal or application is open in the mount point).

---

## Viva Questions

- **What is mounting in Linux?**
  - **Answer:** Mounting is the process of making a storage device or file system accessible by attaching it to a specific directory (mount point) in the Linux unified file system hierarchy.

- **What is a mount point?**
  - **Answer:** A mount point is an empty directory (typically under `/mnt` or `/media`) used as the attachment point for a device's file system.

- **Difference between mount and umount.**
  - **Answer:** The `mount` command attaches a device to the file system, whereas `umount` detaches it. Note that the command is `umount` (without an 'n' before the 't').

- **What is /dev directory?**
  - **Answer:** The `/dev` directory contains special device files that represent the system's hardware, allowing the OS and software to interact with devices like disks, terminals, and printers.

- **Why must devices be unmounted safely?**
  - **Answer:** Safe unmounting ensures that any pending data in the system's write cache is flushed to the physical disk and that the file system is marked as clean, preventing data loss or corruption.

- **What does df -h display?**
  - **Answer:** It displays the amount of disk space used and available on all currently mounted file systems, with the `-h` flag making the output human-readable (KB, MB, GB).

- **How does Linux identify storage devices?**
  - **Answer:** Linux identifies devices through device files in `/dev` and uses kernel drivers to recognize block devices. Tools like `lsblk` and `blkid` help identify these devices and their partitions.

---

## References

- Linux Man Pages: `man mount`, `man umount`, `man lsblk`
- Introduction to Linux with Bash Scripting Lab (Dr. Rajesh Kumar)
