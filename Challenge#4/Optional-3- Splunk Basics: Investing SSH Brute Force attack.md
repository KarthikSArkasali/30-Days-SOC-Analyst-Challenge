# Day#18- Splunk Basics: Investigating SSH Brute Force attack

## Objective
I learned to use Splunk to detect and investigate an SSH brute-force attack by analyzing failed login logs and identifying suspicious IP addresses using basic SPL queries.

## Lab Setup
- Ubuntu Server (22.04 or later)
- [Download Linux Auth log sample](https://github.com/KarthikSArkasali/30-Days-SOC-Challenge/blob/main/Files/Challenge-4/linux_auth_logs.json)
  
## Pre-requisite
- [Setting up Splunk Server on Ubuntu Server](https://github.com/KarthikSArkasali/30-Days-SOC-Challenge/blob/main/Challenge%234/DAY-%231.md)

## Lab Task
Submit the answers below along with screenshots from your Splunk queries.

- Question 1: Which user has attempted most number of SSH brute attack attempt?

  ![1](https://github.com/user-attachments/assets/c43d7dad-325f-421e-bba1-17a7ab6b50b7)

- Question 2: What is the IP Address of the user “thor”?

  ![2](https://github.com/user-attachments/assets/88db2e3c-b3e9-4d3d-b7f2-af0e0c55bb8f)

- Question 3: How many times user “thor” failed to login?

  ![3  ](https://github.com/user-attachments/assets/0cac3558-4a22-4142-a39f-e3787461fca4)

## Conclusion
You used Splunk to spot repeated SSH login failures, identify attacker IPs, and understand how brute-force attacks appear in log data — a key SOC analyst skill.
