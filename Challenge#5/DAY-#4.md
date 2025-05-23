# Day-#4- Introduction to Malware Analysis
## Lab Objective:
This lab introduced me to the basics of malware analysis. I learned how to identify malicious files, perform static analysis using free tools, and extract indicators such as file names, hashes, strings, and behavior—all without executing the malware.

## What is Malware Analysis?
**Malware Analysis** is the process of examining malicious software to understand its origin, behavior, impact, and indicators. It helps SOC analysts detect infections, contain threats, and prevent future compromises.

## Types of Malware Analysis:
- **Static Analysis:** Examining a file without executing it
- **Dynamic Analysis:** Observing file behavior during execution (sandboxing)
- **Memory Analysis:** Investigating malware artifacts in memory
- **Reverse Engineering:** Deconstructing the code (advanced)

## Key Objectives:

- Identify the type of malware (e.g., trojan, ransomware, info-stealer)
- Determine how it spreads (email, USB, download, vulnerability)
- Understand its behavior (file modifications, network connections, persistence)
- Extract IOCs (Indicators of Compromise) (hashes, domains, IPs, registry keys)
- Help in detection and prevention (create YARA rules, update AV signatures, SIEM rules)
- Support incident response (understand timeline, impact, and cleanup strategy)

## Static Malware Analysis – Activity, Purpose, and Tools
|Activity|	Purpose	|Tools You Can Use|
|------|------------------------|-----------------|
|🔍 Check File Hash (MD5/SHA256)	|Identify file uniquely and compare with threat intel databases	|VirusTotal, HashCalc, HashMyFiles, PowerShell `Get-FileHash`|
|🛑 Check Antivirus Detections	|See if AV engines detect the file as malicious	|VirusTotal, MetaDefender, Hybrid Analysis|
|📎 Inspect File Metadata	|Gather file details like size, type, timestamps, compile date	|ExifTool, PEStudio, Detect It Easy (DIE), `file` command|
|🧪 Check File Type & Entropy	|Detect packing, encryption, or file manipulation|	Detect It Easy (DIE), PEStudio, binwalk|
|🧵 Extract Strings	Reveal |readable content like domains, URLs, commands	|`strings`, FLOSS (FireEye), BinText|
|🔐 Detect Obfuscation or Packing	|Identify if the file is packed to hide malicious code	|PEiD, Detect It Easy (DIE), PEStudio|
|🌐 Scan Embedded Domains or URLs	|Uncover external connections or phishing links	|VirusTotal, CyberChef, URLScan.io|
|🔁 Analyze Imports/Functions	|Understand what Windows APIs or system calls the file uses	|PEStudio, CFF Explorer, IDA Free, Ghidra|
|🧬 Compare to Known Malware Samples	|Check similarity to known malware families or signatures	|Intezer Analyze, Hybrid Analysis, VirusTotal Behavior|
|📦 Hex & Binary Inspection	|Manually examine binary structure for hidden artifacts	|HxD, Hexed.it, 010 Editor|

## Lab Tasks – Perform Static Malware Analysis
### Lab Setup
You will perform basic static malware analysis using a publicly known test malware file.
> ⚠️ *We will use a safe EICAR test file – not harmful, but detected by AV tools*.

## Tools You’ll Use:
- [EICAR Test Malware Sample FIle](https://secure.eicar.org/eicar.com.txt)
- [VirusTotal](https://www.virustotal.com/gui/home/upload)
- [Hybrid Analysis](https://www.hybrid-analysis.com/)
- [Any.Run (Optional)](https://www.hybrid-analysis.com/)
- [CyberChef](https://gchq.github.io/CyberChef/)
- [Intezer Analyze (Optional)](https://analyze.intezer.com/)
- Strings or Hex Viewer (e.g: [https://hexed.it](https://analyze.intezer.com/))

## Submission Checklist
- Submit the following screenshots:
    - VirusTotal scan result with detection tab

      ![1](https://github.com/user-attachments/assets/92b83dad-f00b-4bd5-ad9b-e3789e15c650)

    - Sandbox result (Hybrid Analysis or Any.Run)

      ![2](https://github.com/user-attachments/assets/09d11b8f-8d02-4eb2-934b-6c96247beda1)

    - CyberChef base64 decoding step
 
      
    - Any other interesting output or IOC
 
      ![4](https://github.com/user-attachments/assets/f59a8f74-0b33-4f84-bada-9c4f3e7be42d)

## Learning Outcome
By completing this lab, you will:

- Understand what static malware analysis involves
- Use free tools to analyze suspicious files
- Learn how to extract hashes, strings, and AV detections
- Practice documenting your findings like a SOC analyst
