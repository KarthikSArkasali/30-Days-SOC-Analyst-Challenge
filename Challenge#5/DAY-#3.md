# Day-#3- Threat Intelligence Basics
## Lab Objective:
The objective of this lab was to help SOC Analysts extract Indicators of Compromise (IOCs) from a suspicious email and use threat intelligence tools to investigate their context and assess their maliciousness.

## What is Threat Intelligence?
**Threat Intelligence (TI)** is information about threats, threat actors, and their tactics. It helps SOC analysts investigate alerts faster, make informed decisions, and respond to incidents more effectively.

**Types of Threat Intelligence:**

- **Tactical:** IOCs like IPs, hashes, domains
- **Operational:** Info about campaigns, malware families
- **Strategic:** Big-picture trends, threat groups, geopolitical context

## Scenario:
While triaging a phishing alert, you discovered three suspicious indicators:

- **IP Address:** 18.188.148.80

  ![1](https://github.com/user-attachments/assets/6cc464ba-5040-464b-ad26-fad432de4035)

- **Domain:** aaronthompson.ug

  ![2 2](https://github.com/user-attachments/assets/fa1b9601-725b-4e67-9c31-4eabbcd501ba)

- **File Hash(SHA256):** d45a079c59c2860f9cf4578a8fc9f5fe8009cff8aaa83c572474d6bfe15ba95b

  ![3](https://github.com/user-attachments/assets/5b2d5fdf-f17e-498c-ad90-5e653053345a)

## Lab Setup
- **Download Email Sample:** [sample-1.eml](https://github.com/KarthikSArkasali/30-Days-SOC-Challenge/blob/main/Files/BRADESCO%20LIVELO.eml)
- **Tools You Will Use:**
     - [VirusTotal](https://www.virustotal.com/gui/home/upload)
     - [AbuseIPDB](https://www.abuseipdb.com/)
     - [URLScan.io](https://urlscan.io/)
     - [AlienVault OTX](https://otx.alienvault.com/)
     - [ThreatFox](https://threatfox.abuse.ch/)
     - [MXToolbox Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx)

## Tasks
1. What is the type of the malicious file?
2. What country is this IP registered in?
3. What malware name (if any) is associated with this file on VirusTotal?

## Submission
- IP Lookup
    - Screenshot from VirusTotal or AbuseIPDB showing details of 185.220.101.19

      ![10](https://github.com/user-attachments/assets/550c50fd-1c9a-4b66-b286-dde5fc3c18af)

- Domain Lookup
    - Screenshot from VirusTotal or URLScan showing reputation and scan results of secure-login-verification.com

      ![9](https://github.com/user-attachments/assets/1acc749c-cf5b-4102-804c-1e81c8a5909a)

- Hash Analysis
    - Screenshot from VirusTotal showing file type, detection ratio, and malware name for the hash 44d88612fea8a8f36de82e1278abb02f

      ![8](https://github.com/user-attachments/assets/56905e7c-17e0-4de2-b39d-1ee0cc801cd0)

- Threat Intelligence Feed (Optional Bonus)
     - Screenshot of the IOC found in AlienVault OTX or ThreatFox with campaign name or tags

       ![bonus](https://github.com/user-attachments/assets/853c86de-cb4e-4088-8807-13dfef0e8e3b)

## Expected Outcome
By completing this lab, you will:

- Understand how to extract IOCs from phishing emails
- Use free tools to assess IPs, domains, and links
- Gain confidence in making escalation decisions based on threat intelligence
- Develop investigation habits like documentation and screenshot evidence
