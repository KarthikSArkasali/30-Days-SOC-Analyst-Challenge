# Day-#5: Introduction to Digital Forensics

## Objective:
The objective of this task was to acquire a Linux memory dump using KVML for forensic analysis. I captured live memory from an Ubuntu machine and transferred it to another system for further forensic investigation.

## What is Digital Forensics?
**Digital Forensics** is the science of identifying, preserving, analyzing, and presenting digital evidence in a legally acceptable manner. It involves recovering and examining data from digital devices like computers, servers, networks, and mobile devices — especially after a security breach or criminal incident.

Digital forensics plays a critical role in cybercrime investigations, incident response, insider threat detection, and legal proceedings.

## Goal of Digital Forensics
The main goal of digital forensics is to:

- Identify and preserve digital evidence
- Reconstruct timelines of digital activity
- Determine the root cause of incidents or intrusions
- Support legal or administrative actions with valid findings
- Maintain chain of custody and evidence integrity

## Types of Digital Forensics

|Type	|Description|	Common Tools|
|------|------|------|
|**Linux Forensics**	|Investigation of Linux systems, logs, memory, and file integrity|	`log2timeline`, `auditd`, `grep`, `kape`, `KVML`|
|**Windows Forensics**	|Analysis of registry, Event Logs, prefetch, and file metadata	|`FTK Imager`, `Registry Explorer`, `KAPE`, `PECmd`|
|**Mobile Forensics**	|Recovery of deleted data, call logs, chats, and app artifacts from smartphones	|`Cellebrite`,`Magnet AXIOM`, `MobSF`|
|**Network Forensics**	|Capturing and analyzing packets, logs, and intrusion traces	|`Wireshark`, `tcpdump`, `Zeek`, `Suricata`|
|**Memory Forensics**|	Live RAM acquisition and analysis of volatile artifacts	|`Volatility`, `Rekall`, `LiME`, `KVML`|
|**Cloud Forensics**	|Investigation of cloud logs, APIs, and storage for abnormal activity	|`AWS CloudTrail`, `GCP Logs`, `AZ Sentinel`, `FIR`|
|**IoT Forensics**	|Analyzing embedded devices and sensor data for signs of compromise|	`Autopsy`, `Binwalk`, `Scalpel`, `Firmware-Mod-Kit`|

## Digital Forensics Process (Simplified 5-Step Approach)
|Step	|Description|
|------|------|
|**1. Identification**	|Detect potential sources of evidence (e.g., compromised system, suspicious process)|
|**2. Preservation**	|Isolate and protect the system from tampering or loss of evidence|
|**3. Collection**	|Acquire volatile (memory) and non-volatile (disk) data|
|**4. Analysis**	|Examine the data to uncover malicious activity, indicators, or artifacts|
|**5. Reporting**	|Document findings clearly and support with timelines, screenshots, or logs|

## Preparation: Lab Setup
### Requirements
- **System 1 (Target Machine):** Ubuntu 22.04/20.04 (Machine from which memory will be acquired).
- **System 2 (Analysis Machine):** Ubuntu 22.04/20.04 (Machine where the memory dump will be transferred and analyzed).
- **User Permissions:** Root or sudo privileges on both machines.
- **Tools Required:**
     - **AVML ( by Microsoft)** for memory acquisition
     - **strings & grep** for quick validation
     - **scp or rsync** for transferring the memory dump

## Forensic Acquisition Steps
**Step 1: Download AVML on Target Machine**
1. Open a terminal on the **Target Machine (System 1)**.
2. Download KVML from the official GitHub releases:

       wget https://github.com/microsoft/avml/releases/latest/download/avml

**Step 2: Make AVML Executable**
1. Grant execute permissions:

       chmod +x ./avml

2. Verify execution by running:

       ./avml --help

**Step 3: Create a Memory Dump**

1. Run the following command to acquire a memory dump and save it as linux_memory.mem:

       sudo ./avml linux_memory.mem

2. Confirm the memory dump file has been created:

       ls -lh linux_memory.mem

**Step 4: Validate the Memory Dump**
1. Use `strings` and `grep` to check if known data appears in the dump:

       strings linux_memory.mem | grep "mozilla"

- If strings related to applications, files, or processes appear, the dump is valid.

**Step 5: Transfer the Memory Dump to the Analysis Machine**
1. On the Analysis Machine (System 2), create a directory to store the memory dump:

       mkdir ~/forensics/memory_dumps

2. Transfer the memory dump from the Target Machine to the Analysis Machine using scp:

        scp user@<Target-Machine-IP>:/home/user/linux_memory.mem ~/forensics/memory_dumps/

- Replace with the actual IP of the Target Machine.
- Enter the password when prompted.

3. Verify the file is successfully transferred:

        ls -lh ~/forensics/memory_dumps/

## Conclusion
- Successfully acquired a Linux memory dump using AVML.
- Performed basic validation to confirm the memory dump’s integrity.
- Transferred the memory dump to a forensic workstation for further analysis.
- Learned how SOC analysts and forensic investigators collect volatile memory for incident response.

## Submission
- Share a screenshot showing the successful memory dump creation.

  ![1](https://github.com/user-attachments/assets/7c126cfe-5fbd-45a9-8416-3455e5450337)

- Share a screenshot of the memory dump transfer to the forensic machine.

  ![2](https://github.com/user-attachments/assets/9da5e4b1-e74e-4d7d-85c5-45a6f7ac3f9e)

- Write a short observation on how memory acquisition plays a crucial role in digital forensics investigations.

  **Memory acquisition** is an important step in digital forensics, especially during a live incident. It helps investigators collect valuable data from the system's RAM before it gets lost. This data can give clues about what was happening on the system at the time of the attack.

  1. **Captures Live Data** – Memory acquisition collects real-time data like running processes, open files, and active network connections.

  2. **Finds Hidden Threats** – It can help detect malware or attacks that do not leave traces on the hard disk.

  3. **Volatile Evidence** – Data in RAM is temporary and disappears when the system is shut down, so acquiring it early is important.

  4. **Supports Investigation** – Memory dumps give forensic experts more evidence to analyze and understand the attack.

  5. **Helps in Incident Response** – It allows quick detection and response to cyber incidents while the system is still running.
