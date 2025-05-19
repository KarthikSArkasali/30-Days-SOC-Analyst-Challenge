# Day-4: Log Analysis Basics – Network-Based Attack Detection Using UFW

## Objective:

The objective of this lab was to simulate a network-based port scan attack and demonstrate how to detect it using `ufw.log` on a Linux system. I launched an HTTP scan probe from a Kali Linux (attacker) machine and successfully detected the scan attempts on the victim machine using UFW logs.

## Lab Setup
### System Requirements
- Attacker Machine:: Kali Linux
- Target Machine: Ubuntu Linux
### Tools Needed
- `nmap` (on attacker machine)
- `ufw` or `iptables` (on target machine)
### Log Files
- `/var/log/ufw.log` on Ubuntu Server– Captures system and network-related messages

## What is a Network Port Scan?
A **port scan** is a technique used by attackers to probe a system for open ports and active services. Tools like nmap are commonly used to map a system’s network surface.

### Why It’s Dangerous
- Port scans are often a precursor to exploitation
- They help attackers identify vulnerable services like open SSH, FTP, or outdated web servers

## What is Nmap?
- Nmap (Network Mapper) is an open-source network scanning tool.
- Used to discover hosts and services on a network.
- Helps in identifying open ports, running services, and OS detection.
- Commonly used for network inventory and vulnerability scanning.

### Nmap Popular Scan Types
- **SYN Scan (-sS):** Fast and stealthy port scan.
- **TCP Connect Scan (-sT):** Full TCP connection, less stealthy.
- **UDP Scan (-sU):** Scans UDP ports for services.
- **Ping Scan (-sn):** Checks which hosts are up, no port scan.

## What is UFW?
- UFW stands for Uncomplicated Firewall, a frontend for iptables.
- Simplifies firewall management for Linux users.
- Used to allow, deny, and manage traffic rules easily.
- Logs are stored in `/var/log/ufw.log`.
- Rule file `/etc/ufw/before.rules`
- To check ufw status `ufw status`
- To check the rule number `ufw status numbered`

### UFW Rule Syntax

- **Basic allow rule:** ufw allow
- **Deny a port:** ufw deny
- **Allow by service:** ufw allow (e.g., ufw allow ssh)
- **Allow by IP:** ufw allow from
- **Allow specific port from IP:** ufw allow from to any port
- **Delete rule:** ufw delete allow

## Lab Task: Explore and Analyze Linux Syslog for Network Scans

## Step 1: Attack Simulation – Perform a Port Scan
 > *Only scan systems you own or are authorized to test*.

### On the Attacker Machine:

     nmap -p80 TARGET-IP

![1](https://github.com/user-attachments/assets/d93db2c1-25cc-46ad-b457-feba86034500)

## Step 2: Detection and Analysis – Analyze Syslog

1. Installing UFW firewall<br>
      
       sudo apt install ufw
       sudo ufw enable
       sudo ufw logging on
       sudo ufw logging high

2. Create a Firewall rule to drop HTTP traffic from Attack machine<br>
     
       sudo ufw deny from 69.62.84.69 to any port 80 proto tcp

3. Reload the firewall rules to take effect<br>
      
       sudo ufw reload

4. Detect the HTTP Scanning traffic<br>
       
       sudo tail -f /var/log/ufw.log | grep "Attcker IP"

![3](https://github.com/user-attachments/assets/685c1d04-405e-4c48-addf-44038a76d492)

## Conclusion
- ufw.log, combined with firewall logs, is powerful for detecting early-stage reconnaissance
- Port scanning is often the first indicator of an attacker mapping your system
- Detecting and blocking IPs performing scans is a crucial step in proactive defense

## Submission
Submit a screenshot of a syslog entry showing blocked network traffic due to a port scan. Include:

- Source IP of scan
- Targeted port
- Timestamp
