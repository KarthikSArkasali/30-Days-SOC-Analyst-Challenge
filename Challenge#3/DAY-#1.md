# Day-#1: Introduction to Incident Response

# Objective:
The objective of this lab was to understand the core concepts of incident response and become familiar with the incident response lifecycle. I learned how basic threats on Windows systems are detected, analyzed, and responded to by SOC Analysts.

## What is Incident Response?
**Incident Response (IR)** is the structured approach to handle and manage the aftermath of a **security breach or cyberattack**, also known as an incident. It includes steps to:

- Detect the incident
- Contain the damage
- Investigate the root cause
- Recover normal operations
- Report and document findings

## Incident Response Process (NIST SP 800-61 Rev. 2)
The NIST Incident Response Lifecycle includes **4 main phases**:

|Phase|	Description|
|------|--------|
|1. Preparation	|Establish policies, train team, and set up tools and logging mechanisms.|
|2. Detection and Analysis	|Identify potential incidents using logs, alerts, and anomaly detection systems.|
|3. Containment, Eradication, and Recovery	|Isolate threats, remove malware/artifacts, and restore systems securely.|
|4. Post-Incident Activity	|Conduct lessons learned, create reports, and improve incident response plans.|

## Common Types of Incidents Across Platforms:

### Common Types of Incidents on Windows:
|Platform	  |Incident Type	|Description|
|------------|-----|-------|
|Windows  |Unauthorized Login Attempts	| Multiple failed logins or brute-force via RDP or local access.|
|        |PowerShell-based Attacks	| Obfuscated or encoded PowerShell commands for exploitation or lateral movement.|
 |       |Malware/Ransomware Execution	| Malicious EXE/DLL files executed, causing encryption or data theft.|
|        |Credential Dumping |	Use of tools like Mimikatz to extract credentials from LSASS memory.|
|       |Lateral Movement via WMI or RDP	| Internal system traversal using Windows services and accounts.|  

### Common Types of Incidents on Linux:
|Platform	  |Incident Type	|Description|
|------------|-----|-------|
|Linux	|SSH Brute Force or Unauthorized Access	|Repeated login attempts or access from unknown IPs via SSH.|
|          |Malicious Cron Jobs for Persistence	|Scheduled tasks created by attackers to maintain access.|
 |         |Sudo Abuse / Privilege Escalation	|Exploiting weak sudo rules or known vulnerabilities to gain root privileges.|
|          |Web Shell Upload	|Attackers upload backdoors via vulnerable web applications.|
 |         |Crypto Miner Installation	|Hidden mining software running under compromised user accounts.|

### Common Types of Incidents on AWS:
|Platform	  |Incident Type	|Description|
|------------|-----|-------|
|AWS	|IAM Credential Misuse	|Leaked API keys used from unknown geographies.|
 |    |Root User Console Access|	Suspicious login or activity from the AWS root account.|
|     |Unusual S3 Bucket Access|	Public or unauthorized access to private storage.|
|    |CloudTrail or Logging Disabled	|Logging service turned off to hide attacker activity.|
|    |EC2 Abuse for Command and Control	|EC2 instances being used as a staging point or C2 server.|

### Common Types of Incidents on GCP:

|Platform	|Incident Type|	Description|
|------------|-----|-------|
|GCP |GCP	IAM Key Misuse	|Leaked or exposed service account keys used from suspicious IPs or regions.|
|    |GCP	Root/Owner Role Abuse	|Unusual activity from users with Owner/Editor roles, especially outside hours.|
|    |GCP	Unusual Cloud Storage Access	|Public or unauthorized access to private Cloud Storage buckets.|
|    |GCP	Cloud Audit Logs Disabled	|Cloud Audit Logs or Admin Activity logs are disabled to evade detection.|
|    |GCP	Compute Engine Abuse for C2	|Compute Engine VMs used as command and control or data exfiltration nodes.|
|    |GCP	API Abuse or Overuse	|Unexpected spikes in API usage, potentially indicating abuse or bot activity.|
|    |GCP	Deployment of Unauthorized Services	|Unapproved services like Kubernetes clusters or App Engine apps deployed.|
|    |GCP	Firewall Rule Changes	|Suspicious modifications to firewall rules exposing internal services.|
|    |GCP	Identity Federation Misuse	|Abuse of external identity providers to gain unauthorized access.|


### Common Types of Incidents on Network:
|Platform	  |Incident Type	|Description|
|------------|-----|-------|
|Network	|DDoS Attack	|Flood of traffic targeting public-facing services.|
  |        |Port Scanning / Reconnaissance	|Continuous scanning of open ports across network segments.|
 |        |ARP Spoofing / Man-in-the-Middle (MitM)	|Tampering with traffic flows for interception.|
|      |DNS Tunneling	|Covert data exfiltration using DNS queries.|
|       |Unauthorized VPN Access	|Compromised VPN credentials used for internal access.|

### Common Types of Incidents on Email:
|Platform	  |Incident Type	|Description|
|------------|-----|-------|
|Email	|Phishing / Credential Harvesting |	Fake emails with links to steal user credentials.|
|         |Malware via Attachments	|Office or ZIP files with embedded malware.|
|           |Business Email Compromise (BEC)	|Attacker impersonates an executive to trick employees.|
|          |Spoofed Email Domains	|Sending emails from domains that look like legitimate ones.|
|            |Internal Account |Compromise	Compromised internal mailbox used to spread phishing internally.|
 
## How SOC Analysts Respond to Incidents:
- Monitor logs and alerts (via SIEM)
- Investigate suspicious behavior
- Contain and isolate infected systems
- Coordinate with other teams
- Document and report the incident

## Lab Task: Detect and Respond: Windows Server RDP Brute Force Attack
### Lab Setup and Requirements
#### Machines Required:
- Windows Server 2019 or 2022
   - RDP enabled
   - Event Viewer access
   - One local user account with known username
- Kali Linux VM
   - Hydra pre-installed
   - Connected to same LAN or Virtual Network
## Network:
- Ensure both machines are on the same network
- Verify RDP (TCP/3389) is open on Windows Server

## Preparation Steps
### On Windows Server:
1. Enable RDP:<br>
   `System Properties → Remote → Enable Remote Desktop`
2. Allow RDP in Firewall:<br>
    `Windows Defender Firewall → Advanced Settings → Inbound Rules → Remote Desktop (TCP-In) → Enable`
3. Create Test User:

       net user attackerlab Password123 /add
4. Open Event Viewer: Windows Logs → Security Filter for **Event ID 4625** (Failed Logon)

## Simulate the Attack
1. On Kali Linux: Install Hydra (if not installed):

        sudo apt update && sudo apt install hydra
   
3. Prepare Wordlist: Use the existing list or create a custom one, e.g.: /usr/share/wordlists/rockyou.txt 2. Run this command on Kali Linux:

       hydra -t 4 -V -f -l attackerlab -P /usr/share/wordlists/rockyou.txt rdp://<Windows_Server_IP>
> *Replace <Windows_Server_IP> with actual IP of Windows Server*

## Visualize the Alert in Event Viewer
1. On Windows Server: Open `Event Viewer → Windows Logs → Security`
2. Look for **Event ID 4625** with:

> *Logon Type: 10 (RemoteInteractive / RDP)*<br>
> Failure Reason: "Unknown user name or bad password"<br>
> Caller IP Address: IP of Kali machine<br>

## Incident Response Steps
1. Identify Repeated Failed Logons:
   - Spot Event ID 4625 from same IP
2. Correlate IP Address:
   - Confirm repeated failures from attacker’s IP
3. Lock the User Account (Optional):

       net user attackerlab /active:no

4. Block Attacker IP:

       New-NetFirewallRule -DisplayName "Block Attacker" -Direction Inbound -RemoteAddress <Kali_IP> -Action Block

5. Collect Evidence:
   - Export relevant Event Logs
      
      - [RDP Brute Force Attack Evidence - Event Viewer logs](https://github.com/KarthikSArkasali/30-Days-SOC-Challenge/blob/main/Files/RDP-Attack.evtx)

      - [RDP Brute Force Attack - Wireshark PCAP Evidence](https://github.com/KarthikSArkasali/30-Days-SOC-Challenge/blob/main/Files/RDP%20Bruteforce.pcapng)
     
6. Report Incident:
   - Create a brief report with findings and actions taken

      - [Incident Response Report](https://github.com/KarthikSArkasali/30-Days-SOC-Challenge/blob/main/Files/RDP%20Incident%20Report.pdf)
  
## Submission Requirements
Submit the following:

- Screenshot of Hydra attack in Kali Linux

![1](https://github.com/user-attachments/assets/c00ce689-063f-42fa-97a1-c0ccf9b30f0a)

- Screenshot of Event Viewer showing multiple 4625 events

![2](https://github.com/user-attachments/assets/cb2fc0f5-1038-49e2-a78c-72567148035d)

- Firewall rule

![3](https://github.com/user-attachments/assets/1461e0a2-f171-400a-a274-6097531ed782)

## Conclusion
This lab demonstrated how to:

- Simulate an RDP brute-force attack using Hydra
- Detect suspicious logons via Windows Event Viewer
- Respond with basic IR steps without using Sysmon




















