# 🛡️ Azure-Honeypot-Sentinel-Security-Monitoring


## Description
Building and Visualizing a Cloud-Based Security Operations Center Using Azure Sentinel and a Honeypot VM

---

## Introduction
This project simulates a real-world Security Operations Center (SOC) environment by deploying an intentionally vulnerable Windows 11 honeypot in Microsoft Azure. The virtual machine is exposed to the internet by allowing all inbound traffic and disabling the firewall, enabling it to attract and capture unauthorized access attempts such as brute-force logins. These failed authentication events (Event ID 4625) are collected and forwarded to a centralized Log Analytics Workspace, where they are monitored and analyzed using Azure Sentinel. To enhance visibility, logs are enriched with GeoIP data, allowing attacker IP addresses to be mapped to geographic locations. The results are visualized through a custom Sentinel workbook, providing an interactive view of global attack patterns. This project demonstrates hands-on experience with cloud security, SIEM configuration, log analysis using KQL, and threat visualization.

---

## Project Goals

- Deploy a honeypot VM in Azure to capture unauthorized login attempts.
- Centralize and analyze security logs using Azure Log Analytics and Sentinel.
- Enrich logs with GeoIP data to determine the geographic origin of attacks.
- Visualize attack patterns on an interactive attack map.
- Gain hands-on experience with KQL queries, SIEM workflows, and security monitoring.

---

## Tools & Technologies

- Azure Virtual Machines – Windows 10 honeypot deployment
- Network Security Groups (NSG) – Inbound traffic management
- Windows Event Viewer – Failed login event logging
- Azure Log Analytics Workspace – Centralized log repository
- Azure Sentinel – SIEM platform for threat monitoring
- KQL (Kusto Query Language) – Querying logs in Sentinel
- GeoIP Watchlist CSV – Log enrichment with geographic data
- Sentinel Workbooks – Attack map visualization


<h2>Operating Systems Used </h2>

- Windows 11 (Windows Virtual Machine)
- Windows (Host Machine)
  

<h2>Short Steps Taken </h2>

- Azure Subscription Setup – Created a free or paid Azure subscription.
- Honeypot VM Deployment – Deployed Windows 11 VM and configured credentials.
- Network & Firewall Configuration – Allowed all inbound traffic and disabled Windows Firewall.
- Failed Login Simulation – Attempted 3 failed logins with a test username (“employee”).
- Event Logging – Captured failed login events (Event ID 4625) in Windows Event Viewer.
- Log Analytics Workspace & Sentinel Setup – Created a central log repository and connected Sentinel.
- Forward Security Events – Configured Windows Security Event forwarding to Sentinel.
- KQL Queries – Queried failed login events and filtered relevant data.
- GeoIP Enrichment – Imported GeoIP watchlist CSV and enriched logs with attacker location.
- Attack Map Visualization – Created a custom Sentinel workbook to visualize attacks on a world map.


