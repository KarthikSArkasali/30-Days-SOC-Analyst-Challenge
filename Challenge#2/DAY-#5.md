# Day-#5: Wireshark Basics – TLS Protocol Analysis

# Objective:
The objective of this lab was to analyze TLS (Transport Layer Security) traffic using Wireshark. I explored how TLS secures data over the network, understood the TLS handshake process, and identified metadata such as server names and certificate details.

# Lab Setup
## System Requirements
- Operating System: Windows 10/11 (or Linux/macOS)
- Software: Wireshark (latest version)
## Files Needed
- [Download Sample PCAP file](https://github.com/KarthikSArkasali/30-Days-SOC-Challenge/blob/main/Files/Protocol_Analysis_pcap.pcapng)

## TLS Packet Structure and Fields
TLS is a **cryptographic protocol** that provides secure communication over the internet. It runs over **TCP**, commonly on port **443**, and is used in HTTPS, FTPS, SMTPS, etc.

### Key TLS Handshake Messages:
|Message |Type	Description|
|------|-------------------|
|**Client Hello**|	Client initiates secure connection, offers cipher suites|
|**Server Hello**	|Server selects cipher and provides certificate|
|**Certificate**	|Server provides digital certificate (X.509)|
|**Key Exchange**|	Client and server exchange keys for session|
|**Finished**	|Secure session begins|

## Most Common TLS Display Filters
Use these filters in Wireshark’s **Display Filter** bar:

|Filter	|Description|
|------|-------------|
|`tls`|	Show all TLS traffic|
|`tcp.port == 443`|	TLS over HTTPS|
|`tls.handshake.type == 1`	|Client Hello messages|
|`tls.handshake.type == 2`	|Server Hello messages|
|`tls.record.version == 0x0303`	|TLS 1.2 traffic|
|`tls.record.version == 0x0304`	|TLS 1.3 traffic|

## Conclusion

- TLS secures communication using encryption, making traffic unreadable without keys.
- Wireshark can't decrypt TLS by default but can reveal.
- Server name (SNI)
- Certificate chain
- TLS versions and cipher suites
- Analyzing TLS metadata helps detect:
- Outdated TLS versions (e.g., TLS 1.0)
- Suspicious or self-signed certificates
- Malicious domain encryption abuse

## Submission
Submit a screenshot showing:

- Show all TLS traffic

![1](https://github.com/user-attachments/assets/00e51179-5766-4048-89d7-dc0bbcc09c00)

- Show Client Hello messages

![2](https://github.com/user-attachments/assets/5b37bbb6-5338-4ecb-867a-c463039af820)

- Show TLS 1.2 traffic

![4](https://github.com/user-attachments/assets/da3953a0-fb98-4d74-9546-7e3604897557)
