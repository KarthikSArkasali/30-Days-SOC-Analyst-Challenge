# Day-#5- Splunk Basics: Investigating Unauthorized Access
## Objective:
I learned how to search and analyze authentication logs using Splunk to detect unauthorized access attempts. I extracted meaningful insights from fields such as user, src_ip, and status, and identified suspicious login behaviors that could indicate potential compromise.

## Lab Setup
- Ubuntu Server (22.04 or later)
- [Download Linux Auth log sample](https://github.com/KarthikSArkasali/30-Days-SOC-Challenge/blob/main/Files/Linux_UnAuthorized_Auditd_logs.json)

## Pre-requisite
[Setting up Splunk Server on Ubuntu Server](https://github.com/KarthikSArkasali/30-Days-SOC-Challenge/blob/main/Challenge%234/DAY-%231.md)

## Lab Task
Submit the answers below along with screenshots from your Splunk queries.
- Question 1: What is the total number of success events in this log file?

  ![1](https://github.com/user-attachments/assets/4b9c1fac-102c-49c5-9792-73e870038800)

- Question 2: What is the most common event triggered and captured in this log file?

  ![2](https://github.com/user-attachments/assets/f7329018-ae14-4c46-9ae7-ab8df558b9fd)

- Question 3: If a user “jaimin_pathak” with a uid “1010” tried accessing a linux server. What the logfile path accessed by him twice?

  ![3](https://github.com/user-attachments/assets/e2f17e4a-004e-423c-a92f-98cd7004f901)

  ![3 1](https://github.com/user-attachments/assets/5847661f-e2b3-4cc9-b7b1-d92b6f7b8d82)

## Conclusion
In this lab, you learned how to investigate unauthorized access attempts using Splunk by analyzing authentication logs. You gained hands-on experience with SPL (Search Processing Language) to query login data, detect suspicious activity, and extract valuable insights.
This exercise helped you:
   - Understand patterns of unauthorized access behavior.
   - Use Splunk to identify high-risk user and IP combinations.
   - Strengthen your skills in log analysis and incident investigation.
