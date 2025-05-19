# Day-#2- Phishing Analysis: Investigating a Suspicious Lookalike Email
## Lab Objective:
The objective of this lab was to analyze a real-world phishing email sample using manual investigation techniques. I reviewed email headers, validated the sender’s identity, checked domain and IP reputations, and extracted indicators of compromise (IOCs).

## Lab Setup
- [Download Email Sample (.eml)](https://github.com/KarthikSArkasali/30-Days-SOC-Challenge/blob/main/Files/BRADESCO%20LIVELO.eml)
- Tools Recommended:
    - [MX Toolbox Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx)
    - [EML Analyzer](https://eml-analyzer.herokuapp.com/#/)
    - IP reputation check (e.g., VirusTotal, AbuseIPDB, Cisco Talos)
    - Whois lookup (e.g., whois.domaintools.com)
    - URL and Domain analysis (e.g., urlscan.io, VirusTotal)

## Lab Task: Analyze the Suspicious Email
### Scenario:
You received an email from **BANCO DO BRADESCO LIVELO** claiming that your card has **92,990 points expiring today**, sent from `banco.bradesco@atendimento.com.br`. The sender’s domain looks similar to Bradesco’s official domain.

Investigate and answer the following:

## Questions:
1. What is the full email address of the sender?
2. What domain is used to send this email? (Check Return-Path or From)
3. What is the sender’s IP address from the header?
4. Is the sender IP blacklisted? (Check using AbuseIPDB or VirusTotal – Answer Yes/No)
5. What is the result of SPF authentication? (Pass / Fail / Neutral)
6. What is one suspicious URL or link found in the email body?

## Submit the Following Screenshots:
1. Screenshot of the email header with sender, Return-Path, and IP address highlighted.

   ![1](https://github.com/user-attachments/assets/627d7bb9-89f6-420d-b1a0-9e1df537563d)

   ![1 1](https://github.com/user-attachments/assets/3afa088d-f823-4963-8ab3-de798c58a25f)

2. Screenshot of the IP reputation lookup result (AbuseIPDB or VirusTotal).

    # AbuseIPDB
     ![2](https://github.com/user-attachments/assets/79ebee95-d7c1-4709-87e6-557c9e77220e)

    # VirusTotal
    ![2 2](https://github.com/user-attachments/assets/18f674fe-1f00-4fc8-b4a2-bd98d2faa7a9)

3. Screenshot of the suspicious link found in the email body.

    ![3](https://github.com/user-attachments/assets/d44f6cd1-5053-4365-b635-01088dc0991d)

4. Screenshot of the email content or HTML preview that shows urgency, branding, or spoofing.

    ![4](https://github.com/user-attachments/assets/7baf0c8f-a589-4e99-bf5a-8a6c136612e8)

## Learning Outcome
By the end of this lab, students should be able to:

- Trace email origin
- Validate domains and IPs
- Understand spoofing techniques
- Detect phishing attempts using header and body analysis
