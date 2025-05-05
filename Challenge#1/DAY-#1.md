# Day-1: Introduction to Log Analysis

**Objective:** The goal of this lab is to gain hands-on experience with the fundamentals of log analysis. This project demonstrates how logs from both Windows and Linux systems can be generated, collected, and analyzed for security monitoring. The objective is to understand how SOC analysts utilize logs to detect and respond to security incidents, building a strong foundation in threat detection and incident analysis.<br>

## What is a Log?

A log is a record of events in a system that captures important actions like errors, warnings, or user activities. These logs contain key information such as:<br>

- Timestamp
- Event Description
- Severity (Critical, Error, Warning, Information)
- Source (User, Process, Service)<br>

Logs are essential for understanding system behavior, detecting security incidents, and conducting forensic investigations.

## Example logs

🐧Linux auth.log Example

    Apr  7 10:42:15 ubuntu sshd[12345]: Failed password for invalid user admin from 192.168.1.100 port 54321 ssh2

Explanation:

- `Apr 7 10:42:15` — Timestamp
- `ubuntu` — Hostname
- `sshd[12345]` — Service name and process ID
- `Failed password for invalid user admin` — Failed login attempt
- `from 192.168.1.100` — Source IP address
- `port 54321` — Source port
- `ssh2` — Protocol version

## Log Sources on Linux:

- **System Logs:** Stored in `/var/log/`, including files like `syslog` (system messages), `auth.log` (authentication attempts), and `kern.log` (kernel-related logs).
- **Application Logs:** Application-specific logs like Apache (`/var/log/apache2/access.log`) or MySQL (`/var/log/mysql/error.log`).

## Log Sources on Windows:
- **Event Viewer:** Provides access to logs such as:
  - **System Logs:** Logs related to operating system events.
  - **Security Logs:** Logs related to login attempts, permission changes, etc.
  - **Application Logs:** Logs for system applications.
  - **PowerShell Logs:** Logs for PowerShell commands, including suspicious execution.
    
## How Does a SOC Analyst Use Log Analysis?

- **Incident Detection:** SOC Analysts review logs to detect unusual or unauthorized activities, such as failed login attempts or suspicious processes.
- **Forensics:** Logs are used to trace back the actions taken by an attacker during or after an incident.
- **Security Monitoring:** Continuous log analysis helps detect potential security threats in real-time.
- **Compliance:** Logs assist in maintaining compliance with regulatory standards (e.g., GDPR, HIPAA).
  
## Popular Tools for Log Analysis:

- **ELK Stack (Elasticsearch, Logstash, Kibana):** A powerful suite for log collection, storage, and visualization.
- **Splunk:** A leading tool for searching, analyzing, and visualizing machine-generated data.
- **Graylog:** An open-source log management solution.
- **Wazuh:** An open-source security monitoring platform that integrates well with ELK for log analysis and threat detection.
  
## Lab Task: Simulating and Detecting Windows Powershell events
## Requirements:
- Systems: Windows 10/11 or Windows Server 2019/2022, Linux (Ubuntu or CentOS)
- Tools:
 - Windows Event Viewer
 - PowerShell (Pre-installed on Windows)
## Preparation:
For this lab, you will need to set up log collection on both Windows and Linux systems. Follow these steps to ensure everything is ready:

## On Windows:
 1. Open **Group Policy Editor** (`gpedit.msc`):

![1  ](https://github.com/user-attachments/assets/b4b267cd-c9fc-486f-8162-4c28806f1917)

- Navigate to `Computer Configuration > Administrative Templates > Windows Components > Windows PowerShell`.
- Ensure that **Module Logging**, **Script Block Logging**, and **Script Execution** are enabled.

     ![2  ](https://github.com/user-attachments/assets/48b9de5e-7e75-47cb-96f2-847d365ea25a)

 2. Open **Event Viewer:**

     - Go to **Applications and Services Logs → Microsoft → Windows → PowerShell → Operational**.
## **Step 1:** Simulate a Suspicious PowerShell Command
To simulate a suspicious activity, open an elevated PowerShell session and run the following command:

    Get-LocalUser | Select-Object Name, Enabled

![2 1](https://github.com/user-attachments/assets/018b03fd-c413-4f99-943d-7186aa24a257)

This command lists all local user accounts on the system, which could be used by attackers to enumerate users post-exploitation.

## Step 2: Detect the Log in Windows Event Viewer
1. Press `Win + R`, type `eventvwr.msc`, and press Enter.
2. Navigate to: `Applications and Services Logs → Microsoft → Windows → PowerShell → Operational`.
3. Click **Filter Current Log**, and filter for **Event ID 4104** (which logs PowerShell script execution).
4. Look for an entry that shows the execution of the **Get-LocalUser command**.
5. Take a screenshot of the event details.

   ![3 1](https://github.com/user-attachments/assets/fa9aa5ea-0f66-41a5-a992-e286bee388b5)

## Conclusion:
- **Understanding Log Analysis:** Logs are crucial for detecting, investigating, and responding to security incidents. Through the use of Windows Event Viewer and Linux log files, you can 
  monitor system activity and identify potential security issues.
- **SOC Analyst Role:** SOC Analysts use log analysis to detect threats, investigate incidents, and ensure system compliance.









