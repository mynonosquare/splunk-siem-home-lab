# Splunk SIEM Home Lab

## Overview

This project documents a home lab built to gain hands-on experience with Splunk Enterprise as a Security Information and Event Management (SIEM) platform. The lab collects Windows event logs, enables log analysis through Splunk Processing Language (SPL), and demonstrates basic detection and investigation of security-related events.

The project focuses on understanding how security analysts monitor systems, investigate suspicious activity, and develop searches to identify common attack techniques.

By referencing frameworks such as MITRE ATT&CK and the NIST Cybersecurity Framework (CSF), I can approach security incidents using established industry practices while continuing to improve my investigation and incident response skills.


## Objectives

The objectives of this lab are to:

- Gain hands-on experience deploying and using Splunk Enterprise as a SIEM platform.
- Import and analyze security-related logs from multiple sources.
- Develop SPL queries to investigate authentication events, account activity, and suspicious web activity.
- Practice identifying indicators of compromise through log analysis.
- Apply security frameworks such as MITRE ATT&CK and the NIST Cybersecurity Framework (CSF) to guide investigation and response processes.

## Technologies Used

- Splunk Enterprise
- Splunk Processing Language (SPL)
- Windows Event Logs
- Web Server Logs
- Virtualization Platform (VirtualBox/VMware)
- MITRE ATT&CK Framework
- NIST Cybersecurity Framework (CSF)

## Data Sources

The lab analyzes security logs from multiple sources:

### Windows Security Logs

Used for investigating:
- Failed authentication attempts
- Successful logins
- User account creation
- Process activity

Relevant Event IDs:
- 4624 - Successful logon
- 4625 - Failed logon attempt
- 4720 - User account created
- 4688 - Process creation

### Web Host Logs

Used for investigating:
- Suspicious HTTP requests
- Potential directory traversal attempts
- Encoded traversal patterns

Examples of indicators searched:
- ../
- %2e%2e

## Detection Use Cases

- Monitored Windows authentication events to identify failed login attempts.
- Used SPL searches to quickly locate failed authentication events for investigation.
- Reviewed usernames, timestamps, and source hosts to determine whether activity appeared normal or suspicious.
- Utilized SPL to search web host logs for potential directory traversal attempts
- Investigated requests containing path traversal patterns such as `../` and encoded traversal sequences

## SPL Queries Summary

- Filtering Windows authentication events
- Searching for failed login activity
- Investigating specific hosts and users
- Reviewing events over a selected time range

## SPL Queries Plain-txt

- index=main EventCode=4625
- index=main EventCode=4720
- index=web_logs "../"
- index=main "%2e%2e"

## Dashboards

The lab includes dashboards designed to visualize security events and assist with investigation.

- Failed login attempts over time
- Successful login activity
- Top usernames generating authentication events

### Web Security Dashboard
- Suspicious HTTP requests
- Directory traversal indicators
- Source IP activity

### Security Event Overview
- Event volume over time
- Most common Event IDs
- Timeline of detected activity

## Lessons Learned

- Learned how Splunk indexes and searches log data using SPL.
- Improved my understanding of Windows authentication events.
- Practiced investigating suspicious activity by reviewing event logs instead of relying solely on alerts.
- Became familiar with common indicators such as repeated failed logins and network anomalies.
