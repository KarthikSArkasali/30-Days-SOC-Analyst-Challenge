# Day-#5- Splunk Basics: Investigating Unauthorized Access
## Objective:
To learn how to search and analyze authentication logs using Splunk to detect unauthorized access attempts, extract meaningful insights from fields like user, src_ip, and status, and identify suspicious login behaviors that may indicate compromise.

## Lab Setup
- Ubuntu Server (22.04 or later)
- [Download Linux Auth log sample](https://github.com/KarthikSArkasali/30-Days-SOC-Challenge/blob/main/Files/Linux_UnAuthorized_Auditd_logs.json)

## Pre-requisite
[Setting up Splunk Server on Ubuntu Server]()

## Lab Task
Submit the answers below along with screenshots from your Splunk queries.
- Question 1: What is the total number of success events in this log file?
- Question 2: What is the most common event triggered and captured in this log file?
- Question 3: If a user “jaimin_pathak” with a uid “1010” tried accessing a linux server. What the logfile path accessed by him twice?

## Conclusion
In this lab, you learned how to investigate unauthorized access attempts using Splunk by analyzing authentication logs. You gained hands-on experience with SPL (Search Processing Language) to query login data, detect suspicious activity, and extract valuable insights.
This exercise helped you:
   - Understand patterns of unauthorized access behavior.
   - Use Splunk to identify high-risk user and IP combinations.
   - Strengthen your skills in log analysis and incident investigation.
