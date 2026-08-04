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

## Lab Architecture
                                                              
```mermaid
2
flowchart LR
3
 
4
subgraph Data_Sources["Data Sources"]
5
A[🖥️ Windows Security Logs]
6
B[🌐 Web Host Logs]
7
end
8
 
9
subgraph SIEM["Splunk Enterprise SIEM"]
10
C[📊 Centralized Log Collection & Analysis]
11
end
12
 
13
subgraph Analytics["Security Analytics"]
14
D[🔍 SPL Queries]
15
E[📈 Dashboards]
16
F[🕵️ Investigations]
17
end
18
 
19
subgraph Detection["Threat Detection"]
20
G[⚠️ Detection of Suspicious Activity]
21
end
22
 
23
subgraph Response["Incident Response"]
24
H[🚨 Incident Response Process]
25
end
26
 
27
A --> C
28
B --> C
29
 
30
C --> D
31
C --> E
32
C --> F
33
 
34
D --> G
35
E --> G
36
F --> G
37
 
38
G --> H
39
 
40
classDef source fill:#dbeafe,stroke:#2563eb,stroke-width:2px,color:#000;
41
classDef siem fill:#dcfce7,stroke:#16a34a,stroke-width:3px,color:#000;
42
classDef analytics fill:#fef3c7,stroke:#d97706,stroke-width:2px,color:#000;
43
classDef detect fill:#fee2e2,stroke:#dc2626,stroke-width:3px,color:#000;
44
classDef response fill:#ede9fe,stroke:#7c3aed,stroke-width:3px,color:#000;
45
 
46
class A,B source;
47
class C siem;
48
class D,E,F analytics;
49
class G detect;
50
class H response;
51
```

flowchart LR

    subgraph Data_Sources["Data Sources"]
        A[🖥️ Windows Security Logs]
        B[🌐 Web Host Logs]
    end

    subgraph SIEM["Splunk Enterprise SIEM"]
        C[📊 Centralized Log Collection & Analysis]
    end

    subgraph Analytics["Security Analytics"]
        D[🔍 SPL Queries]
        E[📈 Dashboards]
        F[🕵️ Investigations]
    end

    subgraph Detection["Threat Detection"]
        G[⚠️ Detection of Suspicious Activity]
    end

    subgraph Response["Incident Response"]
        H[🚨 Incident Response Process]
    end

    A --> C
    B --> C

    C --> D
    C --> E
    C --> F

    D --> G
    E --> G
    F --> G

    G --> H

    classDef source fill:#dbeafe,stroke:#2563eb,stroke-width:2px,color:#000;
    classDef siem fill:#dcfce7,stroke:#16a34a,stroke-width:3px,color:#000;
    classDef analytics fill:#fef3c7,stroke:#d97706,stroke-width:2px,color:#000;
    classDef detect fill:#fee2e2,stroke:#dc2626,stroke-width:3px,color:#000;
    classDef response fill:#ede9fe,stroke:#7c3aed,stroke-width:3px,color:#000;

    class A,B source;
    class C siem;
    class D,E,F analytics;
    class G detect;
    class H response;

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
