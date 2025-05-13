# Day-#4: Splunk Basics – HTTP Log Analysis

## Objective
In this lab, you will:
- Learn how to ingest and analyze HTTP logs using Splunk.
- Detect client errors, server errors, and suspicious web activity.
- Identify large file transfers and suspicious URI access attempts.

## Lab Setup
- **Splunk:** Already installed and accessible.
- **Data Source:** JSON-formatted Zeek-style HTTP logs.
- **Log File:** Download and upload to Splunk using the steps below.

  - [Download HTTP Log file](https://github.com/KarthikSArkasali/30-Days-SOC-Challenge/blob/main/Files/Challenge-4/http_logs.json)

# Steps to Upload HTTP Log into Splunk
1. Go to Splunk `Web` → `Settings` > `Add Data`.
2. Choose `Upload` and select `synthetic_zeek_http.json`.
3. Set Source type: `json` or create a new one `zeek:http`.
4. Index: Choose `main` or create a new index like `http_lab`.
5. Finish the upload and confirm indexing.

## Lab Tasks
Use SPL queries to complete the following analysis:

✅ **Task 1: Find the top 10 endpoints generating web traffic**<br>
      
    index=http_lab sourcetype="json" 
    | stats count by "id.orig_h" 
    | sort -count 
    | head 10

✅**Task 2: Count the number of server errors (5xx) observed**
      
    index=http_lab sourcetype="json" status_code>=500 status_code<600 
    | stats count as server_errors

✅**Task 3: Identify User-Agents associated with possible scripted attacks**
   
    index=http_lab sourcetype="json" user_agent IN ("sqlmap/1.5.1", "curl/7.68.0", "python-requests/2.25.1", "botnet-checker/1.0") 
    | stats count by user_agent

✅**Task 4: Find large file transfers (greater than 500 KB)**
     
    index=http_lab sourcetype="json" resp_body_len>500000 
    | table ts "id.orig_h" "id.resp_h" uri resp_body_len 
    | sort -resp_body_len

## Submission
Submit a screenshot for each of the following:

- Your query and result for Task 1.

  ![1](https://github.com/user-attachments/assets/03a9193c-6847-42dd-960c-f220f0348022)

- Your query and result for Task 2.

  ![2](https://github.com/user-attachments/assets/5d2d2e33-f0e5-4add-8842-adc544f3f72b)

- Your query and result for Task 3.

  ![3](https://github.com/user-attachments/assets/ad23ae30-00f9-4e60-a9a1-43479d8619cc)

- Your query and result for Task 4.

 ![3 1](https://github.com/user-attachments/assets/9bcac422-4850-4389-9c99-04cacea09dd6)

 ![3 2](https://github.com/user-attachments/assets/4e9d9a3d-2991-43c7-acd2-97c85b1969ac)

