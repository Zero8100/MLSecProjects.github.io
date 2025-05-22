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
##### Tools Installed:
*  Sysmon (System Monitor) with custom configuration
*  Splunk Universal Forwarder
##### Logging Setup:
*  Sysmon logs written to Microsoft-Windows-Sysmon/Operational
*  Windows Security, Application, and System Event logs forwarded
*  Logs sent to index=winlogs on central Splunk server
##### Configuration Highlights:
*  Custom inputs.conf to enable WinEventLog and XmlWinEventLog ingestion
*  Troubleshooting included tuning indexing behavior and ensuring full event visibility
*  Tested and validated Event ID collection (e.g., 1, 11 for Sysmon, 4663 for Windows auditing)
  
#### 2. Splunk Core Instance
##### Purpose: Acts as centralized log aggregation, search, and detection engine
##### Role:
*  Receives logs from Universal Forwarder
*  Contains dashboards for live detection analytics
##### Dashboards Created:
*  Sysmon Event Summary
*  Windows EventCode Analysis
*  Host Activity Tracker
   
#### 3. SOC Analyst Workstation (Windows)
##### Purpose: Emulates the workflow of a blue-team analyst
##### Tools Installed:
*  Splunk Web (for investigation)
*  Sysinternals Suite (e.g., Process Explorer, Autoruns, etc.)
*  Sysmon Config Validator
*  PowerShell & Log Parser Tools
##### Rationale: Chosen for compatibility with common enterprise tools and Windows-based event investigation workflows

#### 4. Kali Linux Attacker VM
##### Purpose: Simulates external or insider threat actor
##### Configuration:
*  Dual NIC setup (NAT + Host-only)
*  IP verified and tested for internal reachability (ping, nmap)

## Header 2

> This is a blockquote following a header.
>
> When something is important enough, you do it even if the odds are not in your favor.

### Header 3

```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# Ruby code with syntax highlighting
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

#### Header 4

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

##### Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### Environment

| VM            | Purpose                     | OS            | Tools Inside
|:--------------|:----------------------------|:--------------|:--------------------------------------|
| Splunk        | Main SIEM + network monitor | Ubuntu-based  | Zeek, Suricata, Wazuh, Kibana
| Kali Linux    | Attacker machine            | Debian-based  | Metasploit, Nmap, Wireshark
| Windows 10/11 | Victim endpoint             | Windows		    | Sysmon, SysInternals, Splunk Forwarder


### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![Octocat](https://github.githubassets.com/images/icons/emoji/octocat.png)

### Large image

![Branching](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
