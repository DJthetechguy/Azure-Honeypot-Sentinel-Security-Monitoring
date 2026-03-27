# 🛡️ Azure-Honeypot-Sentinel-Security-Monitoring


## Description
Building and Visualizing a Cloud-Based Security Operations Center Using Azure Sentinel and a Honeypot VM

---

## Introduction
This project simulates a real-world Security Operations Center (SOC) environment by deploying an intentionally vulnerable Windows 11 honeypot in Microsoft Azure. The virtual machine is exposed to the internet by allowing all inbound traffic and disabling the firewall, enabling it to attract and capture unauthorized access attempts such as brute-force logins. These failed authentication (event ID 4625) events are collected and forwarded to a centralized Log Analytics Workspace, where they are monitored and analyzed using Azure Sentinel. To enhance visibility, logs are enriched with GeoIP data, allowing attacker IP addresses to be mapped to geographic locations. The results are visualized through a custom Sentinel workbook, providing an interactive view of global attack patterns. This project demonstrates hands-on experience with cloud security, SIEM configuration, log analysis using KQL, and threat visualization.

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









<h2>Actions and Observations</h2>

🖥️ Azure Environment Setup
<p>
<img <img width="1920" height="971" alt="image" src="https://github.com/user-attachments/assets/13aad036-1680-4869-a2eb-93222c50e73b" />
This screenshot confirms that the cloud environment has been successfully initialized in Microsoft Azure. It shows the active subscription, which is required to provision and manage resources such as virtual machines, networking, and monitoring services.


<p>
<img width="1916" height="964" alt="image" src="https://github.com/user-attachments/assets/0dacdd0d-702e-469d-b0e1-e90b249874a7" />
This page displays the virtual machine overview and shows the VM (honeypot) fully deployed and running, with a public IP that exposes it to the internet. This deliberate exposure allows real-world attack traffic, such as automated scans and brute-force login attempts, to reach the VM. The Azure region indicates its datacenter location, which can affect the source of incoming attacks. 


</p>
<p>

</p>
<br />

🔐 Honeypot Configuration
<p>
<img <img width="1919" height="861" alt="image" src="https://github.com/user-attachments/assets/257b3803-65b6-4c63-8e66-05a84c18e81c" />
This screenshot shows the completed NSG rule applied to the honeypot VM, allowing all inbound traffic from any source IP, on any port, using any protocol. By removing network-level restrictions, the VM is fully exposed to the internet, enabling automated scans and brute-force login attempts to generate real-world security logs for analysis.


</p>
<p>

</p>
<br />

<p>
<img <img width="1295" height="961" alt="image" src="https://github.com/user-attachments/assets/fe4ee9a8-e557-4512-aa25-28f3fb74c92f" />
The Windows 10 VM is fully exposed as a honeypot. The NSG allows all inbound traffic and the Windows Firewall is disabled on all profiles, ensuring that all attack attempts reach the system. This setup creates a realistic attack surface for capturing and analyzing real-world malicious activity.


<p>
<p>
🚫 Attack Simulation


<p>
<img <img width="1908" height="1023" alt="image" src="https://github.com/user-attachments/assets/1c0cdbc2-012b-469b-8a58-8f1ad7d6641b" />
 The honeypot VM intentionally received failed login attempts to generate security logs. Event Viewer records these as Event ID 4625, capturing the attempted username, source IP, and timestamp. This simulates real-world attacks, providing data for analysis in the SIEM.

</p>
<p>


</p>
<br />



<p>
<img <img width="1920" height="966" alt="image" src="https://github.com/user-attachments/assets/ebc5c571-dd89-48d9-887a-a6a817ace4c3" />
Microsoft Sentinel was deployed and connected to the Log Analytics Workspace. Sentinel is a cloud-native SIEM (Security Information and Event Management) solution used for threat detection and analysis. It allows correlation of logs, creation of alerts, and visualization of attack data. By integrating Sentinel, I transformed raw logs into actionable security insights. This step completes the core monitoring architecture.


</p>
<p>





</p>
<br />


<p>
<img <img width="1920" height="972" alt="image" src="https://github.com/user-attachments/assets/8543bad4-b6fa-4d14-b0e4-f125b7712a88" />
The Data Collection Rule (DCR) defines which security events are collected from the virtual machine and forwarded to Microsoft Sentinel via the Azure Monitor Agent. This screenshot shows the DCR configuration with the associated VM and enabled data streams for Windows Security Events. It confirms the data ingestion setup is correctly linked to the VM, enabling centralized security monitoring and analysis.
 

</p>
<p>






</p>
<br />



<p>
<img <img width="1920" height="968" alt="image" src="https://github.com/user-attachments/assets/6eddf8b2-05d6-47a5-b2d6-c14a7e61e773" />
I imported a GeoIP dataset as a Sentinel watchlist to enrich log data with geographic information. This dataset maps IP addresses to locations such as country and city. By joining this data with security logs, I can identify where attacks originate. Enrichment adds valuable context to raw log data. This is commonly used in real-world SOC environments for threat intelligence.
</p>
<p>


</p>
<br />



<p>
<img <img width="1920" height="966" alt="image" src="https://github.com/user-attachments/assets/58efb376-cc38-44d0-b248-21ff44b0411a" />
In this step, I enriched Windows Security Event logs with geographic data by integrating a GeoIP watchlist into a KQL query. The query filters failed login attempts (Event ID 4625) from a specific attacker IP and uses the ipv4_lookup function to match the IP address against known geographic ranges. This process appends location details such as city, country, latitude, and longitude to each log entry. I then used the project operator to format the output into a clean, analyst-friendly view. This enrichment transforms raw security logs into actionable intelligence, allowing identification of where attacks are originating from.

</p>
<p>


</p>
<br />




<p>
<img />

</p>
<p>


</p>
<br />
