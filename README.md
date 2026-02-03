# internship-12-elevate-labs
Log Monitoring &amp; Analysis
# Log Monitoring & Analysis using Splunk Free

## 📌 Project Overview
This project demonstrates **log monitoring, analysis, anomaly detection, and alerting** using **Splunk Free** and **Windows Security Logs**.  
It simulates real-world **SOC (Security Operations Center)** activities such as detecting brute-force attacks and documenting security incidents.

---

## 🛠 Tools & Technologies
- **Operating System:** Windows 10  
- **Log Source:** Windows Security Logs  
- **SIEM Tool:** Splunk Enterprise (Free)  
- **Log Viewer:** Windows Event Viewer  

---

## 📂 Log Sources Used
- Windows Event Viewer → **Security Logs**
- Key Event IDs:
  - **4624** – Successful logon
  - **4625** – Failed logon
  - **4672** – Special privileges assigned (Admin)

---

## 🎯 Objectives
- Understand different types of logs  
- Monitor authentication activity  
- Detect anomalies in login behavior  
- Correlate security events  
- Learn SIEM fundamentals  
- Create alerts in Splunk  
- Document security findings  

---

## 🔍 Steps Performed

### 1. Log Collection
- Collected Windows Security Logs using Splunk
- Verified events in Event Viewer before ingestion

### 2. Log Analysis
- Analyzed successful and failed login attempts
- Identified repeated authentication failures

### 3. Anomaly Detection
- Detected multiple failed login attempts for a single user
- Identified abnormal login patterns

### 4. Event Correlation
- Correlated failed logins followed by successful login events
- Analyzed potential brute-force behavior

### 5. Alert Creation
- Created Splunk alerts for:
  - Multiple failed logins
  - Suspicious authentication activity

### 6. Documentation
- Documented findings in a SOC-style incident report

---

## 🚨 Sample Detection (Splunk Query)
```spl
index=main EventCode=4625
| stats count by Account_Name
| where count > 3
