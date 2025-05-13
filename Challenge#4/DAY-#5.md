# Day-#5: Splunk Basics – Zeek Connection Log Analysis

# Objective
In this lab, you will:

- Learn how to upload and search Zeek connection logs in Splunk.
- Find top clients, top servers, and most common services.
- Identify large traffic and long connections.

## Lab Setup
- Splunk: Already installed and accessible.
- Data Source: JSON-formatted Zeek-style connection logs.
- Log File: Download and upload to Splunk using the steps below.

  - [Download Zeek Conn Log File](https://github.com/KarthikSArkasali/30-Days-SOC-Challenge/blob/main/Files/Challenge-4/zeek_conn_logs.json)

# Steps to Upload Conn Log into Splunk

1. Go to **Splunk Web** → `Settings` > `Add Data`.
2. Choose **Upload** and select `zeek_conn_logs.json`.
3. Set **Source type:** `json` or create a new one like `zeek:conn`.
4. Index: Use `main` or create a new one called `conn_lab`.
5. Complete the upload and check that logs are searchable.

# Lab Tasks
Use the following SPL queries to complete each task:

## Task 1: Find the Top 10 Client IPs (id.orig_h)

    index=conn_lab sourcetype="json"
    | stats count by id.orig_h
    | sort -count
    | head 10

## Task 2: List Most Common Services

    index=conn_lab sourcetype="json"
    | stats count by service
    | sort -count

## Task 3: Find Connections with Duration > 1 Second

    index=conn_lab sourcetype="json" duration>1
    | table ts id.orig_h id.resp_h service duration
    | sort -duration

## Task 4: Identify the Most Accessed Internal Servers

    index=conn_lab sourcetype="json"
    | stats count by "id.resp_h"
    | sort -count
    | head 10

## Submission
Submit a screenshot for each of the following:

- Your query and result for Task 1.

  ![1](https://github.com/user-attachments/assets/e9bc4c02-9999-4842-91e4-e27cc78bb141)

- Your query and result for Task 2.

  ![2](https://github.com/user-attachments/assets/95552aaf-cb61-4f4f-a5a5-07956200d793)

- Your query and result for Task 3.

  ![3](https://github.com/user-attachments/assets/1e014246-cc7b-4a4a-859c-620cea9770f0)

  ![3 1](https://github.com/user-attachments/assets/c1a63dde-a15f-483f-9efe-21afe3b8fcc6)

- Your query and result for Task 4.

  ![4](https://github.com/user-attachments/assets/da637f9d-5861-4d4b-8a02-e9bb1e099ffa)

 
