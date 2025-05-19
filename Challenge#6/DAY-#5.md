# Day-#5- EDR Basics: Vulnerability Detection using Wazuh
## Objective:
To detect system vulnerabilities using Wazuh’s built-in vulnerability detection module and understand how a SOC Analyst can identify and mitigate vulnerabilities using alert data.

## What is a Vulnerability?
A vulnerability is a weakness or flaw in software, hardware, or system configuration that could be exploited by attackers to gain unauthorized access or perform malicious actions.

Types of Vulnerabilities
|Type|	Example|
|------|-----------|
|**Software Bugs**	|Buffer overflow in Apache|
|**Misconfigurations**	|SSH root login enabled|
|**Outdated Software**	|Unpatched Windows or Linux packages|
|**Default Credentials**	|Admin:admin on routers or web apps|
|**Open Ports/Services**	|FTP open with anonymous access|

## How Are Vulnerabilities Discovered?

- Vulnerability Scanners like OpenVAS, Nessus, or Wazuh's built-in modules
- Threat Intelligence Feeds
- Manual Testing and Penetration Testing
- Bug Bounty Programs
- Exploit Databases (e.g., NVD, Exploit-DB)

## How Do SOC Analysts Mitigate Vulnerabilities?
- Prioritize based on CVSS score and asset criticality
- Coordinate with IT to apply patches or updates
- Disable or restrict vulnerable services
- Monitor for exploit attempts (IDS/EDR)
- Document and track remediation through ticketing systems

## Lab Setup
|Component	|Description|
|-----|----|
|Wazuh Server|	Ubuntu with Wazuh Manager + Dashboard|
|Wazuh Agent	|Ubuntu machine with agent installed|

## Task: Detecting and Visualizing System Vulnerabilities using Wazuh

**Step 1: Setting up Vulnerability Detection on Wazuh Agent**
1. Ensure the Wazuh agent is already installed and connected to the manager.
2. On the Wazuh server, enable vulnerability-detector module:
- Edit the Wazuh configuration file:

       sudo nano /var/ossec/etc/ossec.conf

- Enable and configure the module:

       <vulnerability-detector>
         <enabled>yes</enabled>
         <interval>12h</interval>
         <providers>
            <provider name="canonical">yes</provider>  <!-- For Ubuntu -->
         </providers>
       </vulnerability-detector>

3. Restart the Wazuh manager to apply changes:

        sudo systemctl restart wazuh-manager

4. Wazuh agent will now scan installed packages and compare them against vulnerability databases like NVD and Canonical Security Tracker.

**Step 2: Visualizing Vulnerability Alerts in Wazuh Dashboard**

1. Go to the **Wazuh Dashboard**.
2. Navigate to: `Security Events → Rule Groups → vulnerability-detector`
3. **Filter by alert level** ≥ 10 to find high-severity vulnerabilities.
4. View detailed data:
   - CVE ID (e.g., CVE-2023-####)
   - Affected package
   - CVSS score
   - Recommendation to patch or update

## Submission
### Submit:

- Screenshot of at least one vulnerability alert on the dashboard

  ![1](https://github.com/user-attachments/assets/147a6e07-d675-454a-9bf1-3240d0a2f600)

- Description of the vulnerable package, CVE, and CVSS score

  ![2](https://github.com/user-attachments/assets/316899f0-a0bd-4b2a-8c52-b0d4f4934e63)

- Suggested mitigation step
  - CVE-2025-27516 – Mitigation Steps:
   - Upgrade Jinja to version 3.1.6 or later to fix the sandbox bypass issue.
   - Avoid processing untrusted templates in your application.
   - Review and sanitize template inputs to prevent injection.
   - Monitor for suspicious activity related to template rendering.
   - Keep dependencies updated and follow secure coding practices.

## Learning Outcome
- After completing this lab, you will:
   - Understand how vulnerabilities are detected by Wazuh EDR.
   - Enable and configure Wazuh’s vulnerability detector.
   - View and interpret CVE alerts on the dashboard.
   - Learn how SOC analysts triage and respond to system vulnerabilities.
   - Strengthen your endpoint detection and response (EDR) fundamentals.
