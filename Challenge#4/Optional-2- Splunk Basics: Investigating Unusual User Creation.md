# Day-#4- Splunk Basics: Investigating Unusual User Creation

## Objective:
Use Splunk to detect unusual user creation activity by filtering system logs and identifying unauthorized or suspicious accounts

## Lab Setup
- Ubuntu Server (22.04 or later)
- [Download Linux Auth log sample](https://github.com/KarthikSArkasali/30-Days-SOC-Challenge/blob/main/Files/Linux_UnAuthorized_Auditd_logs.json)

## Pre-requisite

[Setting up Splunk Server on Ubuntu Server](https://github.com/KarthikSArkasali/30-Days-SOC-Challenge/blob/main/Challenge%234/DAY-%231.md)

## Lab Task
- Submit the answers below along with screenshots from your Splunk queries.
     - Question 1: How many users are created in this Auth log file?
     - Question 2: Who changed the password for user 'david_wilson’?
     - Question 3: What is the UID of user "david_wilson”?

## Conclusion
You investigated new user creation events in Splunk, helping detect possible privilege escalation or insider threats
