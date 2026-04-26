# Network Scanning and Device Information Retrieval using Bash Script and Nmap

## Introduction

In cyber security and network administration, understanding the devices connected to a network is essential for monitoring, vulnerability assessment, and incident response. Network scanning helps identify active hosts, open ports, and services running on connected systems. Automating this process using Bash scripting enhances efficiency and reduces manual effort.

The problem is to develop a Bash shell script that scans a given network and displays information about connected devices such as IP addresses, MAC addresses, and open ports, using the Nmap network scanning tool.

---

## Course Outcome Mapping

| CO | Description |
|----|-------------|
| CO1 | Familiarity with Linux environment and system utilities |
| CO2 | Ability to write Bash scripts for automation |
| CO4 | Application of scripting logic for real-world problem solving |

---

## Learning Outcomes

| LO | Description |
|----|-------------|
| LO1 | Understand basic network scanning concepts |
| LO2 | Use Nmap to identify live hosts and open ports |
| LO3 | Automate network scanning using Bash scripting |
| LO4 | Interpret scan results for cyber security analysis |

---

## Theory

### Network Scanning

Network scanning is the process of discovering devices, services, and open ports in a network. It is commonly used for:
- Network inventory
- Vulnerability assessment
- Security auditing
- Intrusion detection support

### Nmap (Network Mapper)

Nmap is a powerful open-source tool used for network discovery and security auditing. It supports:
- Host discovery
- Port scanning
- Service/version detection
- OS fingerprinting

### Ethical Note

Network scanning must only be performed on authorized networks.

### Software / Tool Requirements

- Linux Operating System
- Bash Shell
- Nmap tool installed
- Network connectivity

To install Nmap:
```
sudo yum install nmap
```
or
```
sudo apt install nmap
```

### Commands and Constructs Used

| Command | Description |
|---------|-------------|
| nmap | Network scanning tool |
| grep | Filter output |
| awk | Process text output |
| read | Accept user input |
| echo | Display output |
| chmod | Make script executable |

---

## Procedure

### A. Writing the Network Scanning Script

1. Open the terminal.
2. Create a script file:
   ```
   nano network_scan.sh
   ```
3. Enter the following script:
   ```bash
   #!/bin/bash
   echo "Enter network range (e.g., 192.168.1.0/24):"
   read network
   echo "Scanning network: $network"
   echo "--------------------------------"
   nmap -sn $network > scan_result.txt
   echo "Active devices in the network:"
   grep "Nmap scan report" scan_result.txt | awk '{print $5}'
   echo "--------------------------------"
   echo "Detailed scan of active hosts:"
   for ip in $(grep "Nmap scan report" scan_result.txt | awk '{print $5}')
   do
     echo "Scanning $ip..."
     nmap $ip
   done
   ```
4. Save and exit the editor.
5. Make the script executable:
   ```
   chmod +x network_scan.sh
   ```

### B. Executing the Script

6. Run the script:
   ```
   ./network_scan.sh
   ```
7. Enter the authorized network range when prompted.

---

## Sample Execution

```bash
$ ./network_scan.sh
Enter network range (e.g., 192.168.1.0/24):
192.168.1.0/24
Active devices in the network:
192.168.1.1
192.168.1.5
192.168.1.10
--------------------------------
Scanning 192.168.1.5...
PORT STATE SERVICE
22/tcp open ssh
80/tcp open http
```

---

## Expected Output

- [x] List of active IP addresses in the network.
- [x] Open ports and services for each detected host.
- [x] Script runs without errors and displays structured output.

---

## Result

A Bash shell script was successfully developed and executed to scan a network using Nmap and display information about connected devices, including IP addresses and open ports.

---

## Guidelines to Students

- Perform scans only on authorized networks.
- Do not use aggressive scan options without permission.
- Document findings clearly.
- Understand ethical and legal implications of scanning.

---

## Viva Questions

- What is network scanning?
  - **Answer:** Network scanning is the process of systematically probing a network to discover active devices, open ports, running services, and other network information. It helps in identifying live hosts, understanding network topology, and assessing security posture.

- What is Nmap and why is it used?
  - **Answer:** Nmap (Network Mapper) is a powerful open-source tool used for network discovery and security auditing. It is used to discover hosts and services on a computer network, identify open ports, detect operating systems, and gather information about network infrastructure for security assessments.

- Difference between -sn and port scanning.
  - **Answer:** The `-sn` option (previously `-sP`) performs a ping scan, which only discovers live hosts without scanning ports. Port scanning (without `-sn`) goes further to discover open ports and services on identified hosts, providing more detailed information about each device.

- What information does a port scan reveal?
  - **Answer:** A port scan reveals open ports on a target system, the services running on those ports (like SSH, HTTP, FTP), the state of ports (open, closed, filtered), and sometimes version information about the services, which can help identify potential vulnerabilities.

- Why is network scanning important in cyber security?
  - **Answer:** Network scanning is important in cyber security for asset discovery, vulnerability assessment, security auditing, incident response, penetration testing, and maintaining network inventory. It helps identify exposed services and potential entry points that attackers might exploit.

- What are ethical considerations while scanning?
  - **Answer:** Ethical considerations include: only scanning networks you have explicit permission to test, respecting privacy, not causing disruption to services, following responsible disclosure practices, understanding legal boundaries (like computer fraud laws), and using scanning results only for legitimate security purposes.

- How can this script be extended further?
  - **Answer:** The script can be extended by: adding service version detection (`-sV`), OS fingerprinting (`-O`), saving results to a file with timestamps, adding options for different scan types (SYN, UDP), filtering specific ports, generating HTML reports, adding parallel scanning for faster results, and implementing input validation.

---

## References

- Linux Man Pages: `man nmap`
- Nmap Official Documentation: https://nmap.org/book/man.html
- Introduction to Linux with Bash Scripting Lab (Dr. Rajesh Kumar)
