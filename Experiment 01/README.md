# Linux Virtualization Experiment - Installation & Configuration

## Introduction

This experiment covers the installation and configuration of a Linux operating system using virtualization technology. Virtualization allows running multiple isolated operating systems on a single physical machine, which is essential for system administration, cloud computing, and cybersecurity practice environments.

---

## Learning Outcomes

| LO | Description |
|----|-------------|
| LO1 | Understand the concept of virtualization and virtual machines |
| LO2 | Install and configure a virtualization platform (VirtualBox/VMware/KVM) |
| LO3 | Import and configure a Linux operating system using an OVA file |
| LO4 | Verify successful Linux installation and system readiness |

---

## Theory

### What is Virtualization?

Virtualization enables multiple operating systems (guest OS) to run on a single physical machine (host OS) by abstracting hardware resources such as CPU, memory, storage, and networking. It provides:

- **Isolation** - Each VM runs independently
- **Flexibility** - Easy to create, snapshot, and delete VMs
- **Resource Efficiency** - Maximum hardware utilization

### Virtualization Platforms

| Platform | Type | Notes |
|----------|------|-------|
| Oracle VirtualBox | Open-source | Free, widely used in academia |
| VMware Workstation | Commercial | Professional-grade, advanced features |
| KVM/QEMU | Open-source | Linux-native, kernel-level virtualization |

### OVA File

An **OVA (Open Virtual Appliance)** is a pre-configured virtual machine package containing:
- Guest operating system
- Virtual disk image
- Hardware configuration

Using an OVA file simplifies Linux deployment by eliminating manual installation steps.

---

## System Setup

### Host Environment

| Component | Specification |
|-----------|---------------|
| Host OS | Fedora 41 with COSMIC Desktop |
| Hypervisor | KVM/QEMU (via Virt-Manager) |
| RAM Available | 32 GB |
| Storage | SSD |

### Guest Virtual Machines

| VM Name | OS | RAM Allocation | Purpose |
|---------|-----|----------------|---------|
| Debian Server | Debian 12 | 4 GB | Learning Linux administration |
| Kali Linux | Kali Linux | 8 GB | Cybersecurity practice |
| AWS Instance | Debian (AWS) | Remote cloud VM | Cloud computing practice |
| Raspberry Pi | Raspbian | 2 GB (Pi 4) | ARM architecture learning |

### Hardware Allocation Strategy

**My Configuration (not minimum requirements):**
- 4-8 GB RAM per VM
- 2-4 vCPUs 
- 50-100 GB virtual disk

**Minimum Requirements (for reference):**
- 2 GB RAM is sufficient for basic Linux VMs, for Server Installations, even a gigabyte will suffice
- 2 vCPUs
- 20 GB disk space

> **Note:** The higher allocations (4-8 GB) provide smoother performance for development and security tooling, but 2 GB RAM is perfectly adequate for learning basic Linux commands and Bash scripting.

### Network Configuration

**Bridged Networking** is configured for all VMs, placing them on the same LAN as the host machine. This allows:
- VMs to receive IP addresses via DHCP from the local network router
- Direct network access between host and VMs
- VMs to be accessible from other devices on the network
- Internet connectivity through the physical network

---

## Procedure

### Step 1: Enable Virtualization in BIOS/UEFI

Ensure hardware virtualization (Intel VT-x / AMD-V) is enabled in the system BIOS/UEFI settings.

### Step 2: Install Hypervisor

Choose one of the following virtualization platforms based on your host operating system:

#### Option A: KVM/QEMU (Linux Host)

For Linux hosts, **KVM/QEMU** is the native choice with kernel-level virtualization performance.

```bash
# Fedora - KVM is often pre-installed
sudo dnf install @virtualization

# Or use Virt-Manager GUI
sudo dnf install virt-manager
```

#### Option B: Oracle VirtualBox (Windows/Linux/macOS)

VirtualBox is free, open-source, and works across all platforms.

**Windows/macOS:**
1. Download from https://www.virtualbox.org
2. Run the installer
3. Follow the installation wizard
4. Launch VirtualBox

#### Option C: VMware Workstation (Windows/Linux)

VMware Workstation is a professional-grade virtualization platform.

**Windows:**
1. Download VMware Workstation Player (free) or Pro (trial) from https://www.vmware.com
2. Run the installer
3. Restart system if required

> **Note:** Ensure virtualization is enabled in BIOS/UEFI before running any hypervisor.

### Step 3: Import/Create Virtual Machine

**Option A: Using OVA File**
1. Launch Virt-Manager (or VirtualBox/VMware)
2. File → Import Appliance
3. Select the Linux OVA file
4. Review and adjust settings (RAM, CPU, storage)
5. Complete import

**Option B: Using ISO File**
1. Create new virtual machine
2. Select "Install operating system from ISO"
3. Browse to Linux ISO file
4. Configure hardware settings
5. Begin installation

### Step 4: Configure Network

Set network adapter to **Bridged Mode** (or "Bridge" in KVM) to connect VM directly to the physical network.

### Step 5: Start and Verify

1. Power on the virtual machine
2. Verify Linux boots successfully
3. Check network connectivity
4. Log in with credentials, either credentials that you set during installation or default credentials if its a live VM
---

## Expected Output

- [x] Linux operating system boots successfully
- [x] Desktop or terminal interface is accessible
- [x] Network connectivity established (via bridged adapter)
- [x] Virtual machine is ready for Linux commands and Bash scripting

---

## Results

The Linux operating system was successfully installed and configured using KVM/QEMU virtualization with bridged networking. The virtualized Linux environment is now ready for performing Linux and Bash scripting experiments.

Multiple guest systems (Debian, Kali Linux) are running simultaneously on the Fedora 41 host with COSMIC desktop, demonstrating effective resource allocation and network integration.

---

## Viva Questions & Answers

### Q1: What is virtualization?
Virtualization is the process of creating a software-based representation of computing resources (CPU, memory, storage, network) that allows multiple operating systems to run on a single physical machine as isolated virtual machines.

### Q2: Difference between VirtualBox and VMware Workstation?
| Aspect      | VirtualBox            | VMware Workstation |
|-------------|-----------------------|--------------------|
| Cost        | Free (Open-source)    | Commercial         |
| Performance | Good                  | Excellent          |
| Features    | Basic to intermediate | Advanced           |
| Platform    | Cross-platform        | Cross-platform     |

### Q3: What is an OVA file?
An OVA (Open Virtual Appliance) is a pre-packaged virtual machine file containing the guest OS, virtual disk, and hardware configuration in a single archive file.

### Q4: Difference between OVA and ISO installation?
- **OVA**: Pre-configured, ready-to-run appliance - just import and use
- **ISO**: Bootable installer image - requires manual OS installation process

### Q5: What is the role of virtualization in cybersecurity labs?
Virtualization provides isolated, safe environments for:
- Malware analysis
- Penetration testing practice
- Network security experiments
- Safe testing of potentially destructive tools

### Q6: Host OS vs Guest OS?
- **Host OS**: The primary operating system running on the physical hardware
- **Guest OS**: The virtualized operating system running inside the virtual machine

### Q7: Why is Linux preferred for automation and security tasks?
Linux offers:
- Robust command-line utilities
- Powerful scripting capabilities (Bash)
- Excellent permission and security model
- Wide tool availability for automation and security
- Open-source nature allowing customization

---

## Submission Checklist

- [ ] Virtualization platform installed
- [ ] Linux VM imported/created successfully
- [ ] Linux boots and is accessible
- [ ] Network connectivity verified
- [ ] Screenshots captured for documentation

---

## References

- Oracle VirtualBox: https://www.virtualbox.org
- KVM Documentation: https://www.linux-kvm.org
- Fedora Virtualization Guide: https://docs.fedoraproject.org/en-US/
