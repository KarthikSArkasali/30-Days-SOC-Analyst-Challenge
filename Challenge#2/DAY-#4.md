# Day-#4: Wireshark Basics – HTTP Protocol Analysis
# Objective
The objective of this lab was to analyze HTTP (Hypertext Transfer Protocol) packets using Wireshark. I explored HTTP request and response headers, gained an understanding of how web communication works, and learned how to detect common HTTP-based attacks and potential data leaks.
## Lab Setup
### System Requirements
- Operating System: Windows 10/11 (or Linux/macOS)
- Software: Wireshark (latest version)
### Files Needed
- [Download Sample PCAP file](https://github.com/KarthikSArkasali/30-Days-SOC-Challenge/blob/main/Files/Protocol_Analysis_pcap.pcapng)
## HTTP Packet Structure and Fields
**HTTP** is an application-layer protocol used for communication between clients (browsers) and web servers. It typically runs over TCP port 80.

## Key HTTP Fields:
|Field Nam|e	Description|
|------|--------------|
|Request Method	|GET, POST, HEAD, etc.|
|**Host**	|The website being accessed|
|**User-Agent**|	Information about the client/browser|
|**URI**	|Resource path on the server|
|**Status Code**	|Server's response status (e.g., 200 OK)|
|**Content-Type**	|MIME type of the response (e.g., text/html)|
|**Cookie/Header**	|Session or tracking information|
## Most Common HTTP Display Filters
Use these filters in Wireshark’s **Display Filter** bar:

|Filter|	Description|
|------|--------------|
|`http`	|Show all HTTP traffic|
|`tcp.port == 80`	|HTTP traffic by default port|
|`http.request.method == "GET"`	|Show all GET requests|
|`http.request.uri`	|View requested resources|
|`http.set_cookie`	|Show cookies in HTTP responses|
|`ip.addr == 192.168.1.10`|	HTTP traffic to/from specific host|
# Conclusion
- HTTP traffic is readable and easy to analyze in Wireshark.
- Analyzing HTTP helps detect:
- Sensitive data exposure in URLs or headers
- Malware beaconing to C2 servers
- Suspicious file downloads or unauthorized access
## Submission
Submit a screenshot showing:

- Show all HTTP traffic

![1](https://github.com/user-attachments/assets/a92bfe60-9752-4f43-9818-dec296b8152d)

- Show all GET requests

![3](https://github.com/user-attachments/assets/73cc9e24-156f-4e7b-a1be-6c51754fadc1)

- View requested resources

![4](https://github.com/user-attachments/assets/a8d1ba56-7594-4d8b-9066-6ba02af69c17)
