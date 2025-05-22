---
layout: default
---
Hello,

My name is Mark Leventhal, an aspiring Cyber Security professional actively looking for a cyber security role. I am a Technical Support leader with 
5 years of experience in Hardware Repair, IT User Support, Leading and Managing Teams, and Customer Service.  

Training and Certifications 

CompTIA Security+ : Confidently explain and define general security concepts. Navigate the complexities 
of secure systems and network design. Explore threats, vulnerabilities, and mitigation tactics. Document 
security operations and architectures 

TryHackMe SOC Level 1 : Provided hands on experience with Cyber Defense Frameworks, Cyber Threat 
Intelligence, Network Security and Traffic Analysis, Endpoint Security, SIEM, Digital Forensics, Incident 
Reporting, and Phishing Techniques.

[LinkedIn](https://www.linkedin.com/in/maleventhal/)

# SOC Analyst Projects

## Cybersecurity Detection Lab: End-to-End SOC Simulation Environment

### Objective
To build a functional detection lab replicating real-world blue-team environments. The setup simulates an internal corporate network with endpoint activity, centralized log collection, and adversarial threat emulation using Kali Linux. This lab enables the development and testing of detection logic using Splunk and Sysmon.

### Lab Architecture

I have 4 Virtual Machines in my Home SOC Lab. These were all setup using Oracle Virtual Box.

| VM            | Purpose                     | OS            | Tools Inside
|:--------------|:----------------------------|:--------------|:--------------------------------------|
| Splunk        | Main SIEM + network monitor | Ubuntu-based  | Zeek, Suricata, Wazuh, Kibana
| Kali Linux    | Attacker machine            | Debian-based  | Metasploit, Nmap, Wireshark
| Victim PC     | Victim endpoint             | Windows		    | Sysmon, SysInternals, Splunk Forwarder
| Analyst PC    | Analyst endpoint            | Windows		    | Wireshark, Sysinternals, VSCode, Notepad++, Python, Git

#### 1. Victim PC (Windows 10)
##### Purpose: Simulates a typical enterprise workstation.
Tools Installed:
*  Sysmon (System Monitor) with custom configuration
*  Splunk Universal Forwarder
  
Logging Setup:
*  Sysmon logs written to Microsoft-Windows-Sysmon/Operational
*  Windows Security, Application, and System Event logs forwarded
*  Logs sent to index=winlogs on central Splunk server

Configuration Highlights:
*  Custom inputs.conf to enable WinEventLog and XmlWinEventLog ingestion
*  Troubleshooting included tuning indexing behavior and ensuring full event visibility
*  Tested and validated Event ID collection (e.g., 1, 11 for Sysmon, 4663 for Windows auditing)
  
#### 2. Splunk Core Instance
##### Purpose: Acts as centralized log aggregation, search, and detection engine
Role:
*  Receives logs from Universal Forwarder
*  Contains dashboards for live detection analytics
  
Dashboards Created:
*  Sysmon Event Summary
*  Windows EventCode Analysis
*  Host Activity Tracker
   
#### 3. SOC Analyst Workstation (Windows)
##### Purpose: Emulates the workflow of a blue-team analyst
Tools Installed:
*  Splunk Web (for investigation)
*  Sysinternals Suite (e.g., Process Explorer, Autoruns, etc.)
*  Sysmon Config Validator
*  PowerShell & Log Parser Tools
  
Rationale: Chosen for compatibility with common enterprise tools and Windows-based event investigation workflows

#### 4. Kali Linux Attacker VM
##### Purpose: Simulates external or insider threat actor
Configuration:
*  Dual NIC setup (NAT + Host-only)
*  IP verified and tested for internal reachability (ping, nmap)

#### Technologies Used

| Component             | Technology                          | 
|:----------------------|:------------------------------------|
| Logging Agent         | Splunk Universal Forwarder          | 
| Endpoint Telemetry	  | Sysmon                              | 
| SIEM                  | Splunk Enterprise                   | 
| Threat Emulation	    | Kali Linux                          | 
| Network Tooling		    | VirtualBox (Host-only Networking)   | 
| Log Forwarding Config	| inputs.conf, outputs.conf           | 
| Auditing Enhancements	| auditpol, PowerShell ACL Scripting  | 

## PowerShell Obfuscation Detection via Sysmon & Splunk
#### Overview
Simulated an obfuscated PowerShell attack using -enc (encoded command), then detected the behavior using Splunk and Sysmon Event ID 1. Created a dashboard to alert on such activity.

#### Simulated Attack
```ps
// This encoded string represents a PowerShell payload — often seen in phishing and red team activity.
powershell -enc SQBFAFgAIAAoAE4AZ...
}
```
