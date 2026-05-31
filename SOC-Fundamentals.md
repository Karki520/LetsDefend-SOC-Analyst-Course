

SOC ANALYST COURSE - COMPLETE NOTES IN SEQUENCE

1.**INTRODUCTION TO SOC**
- First step of career as SOC analyst
- This lesson: Structure of SOC + why SOC analyst needs SOC tools + how to use them effectively
- SOC = Security Operations Center

WHAT YOU WILL LEARN IN THIS COURSE
- The structure of a SOC
- Operation of a SOC
- SOC Tools/Products
- How a SOC Analyst should use his tools
- Common mistakes made by SOC Analysts

2. **SOC TYPES AND ROLES**
   
WHAT IS A SOC?
- SOC = Security Operation Center
- Facility where info security team continuously monitors org security
- Primary purpose: Detect, analyze, and respond to cybersecurity incidents
- Uses 3 things: Technology + People + Processes

TYPES OF SOC MODELS
Depends on security needs and budget. Types include:
Details will be covered in next slides - In-house, Virtual, Co-Managed, Command

3. **SOC ANALYST RESPONSIBILITIES**
- Review SIEM alerts throughout the day
- Decide which alerts are real threats vs false positives
- Use tools to confirm: EDR, Log Management, SOAR
- Tools usage explained later in training

4. **SKILLS NEEDED FOR SOC ANALYST**
Goal: Don't depend only on security products. Analyze alerts correctly yourself.

A. Operating Systems
- Must know "normal" vs "abnormal" in system
- Ex: Windows has many services. Can't spot suspicious ones if you don't know normal Windows services
- Learn how Windows/Linux OS work internally

B. Network
- Deal with lot of malicious IPs/URLs daily
- First task: Check if any device in network trying to connect to those addresses
- Sets direction of analysis
- Also need to find potential data leaks on network
- Basics of networking required for all this

C. Malware Analysis
- Most threats = some type of malicious software
- Malware shows different behaviors to fool analysts
- Key task: Find Command & Control center of malicious file
- Check if any device communicating with that C2 address

5. **SIEM - SECURITY INFORMATION & EVENT MANAGEMENT**
- SIEM = Security Information and Event Management
- Combines security info + event management
- Does real-time logging of events in environment
- Purpose: Detect security threats from logs
- Main features for analysts: Collect/filter data + give alerts for suspicious events

SIEM ALERT EXAMPLE
- Windows user enters 20 wrong passwords in 10 seconds
- Suspicious: Normal user won't retry that many times so fast
- Create SIEM rule/filter for this threshold
- When activity exceeds threshold -> alert generated

POPULAR SIEM TOOLS
IBM QRadar, ArcSight ESM, FortiSIEM, Splunk
Check "Monitoring" page on LetsDefend for better picture

6. **LOG MANAGEMENT**
- Access all logs in one place: web logs, OS logs, firewall, proxy, EDR etc
- Manage all logs from single location
- Benefit: Increases efficiency + saves time
- Without central logs: Same request sent to different devices = more errors + more time

EXAMPLE: Want all users on letsdefend.io. Without central logs = check every device.

<img width="1366" height="768" alt="Screenshot (10)" src="https://github.com/user-attachments/assets/58bd4ad7-28da-4c82-919d-b036a4146400" />


LETSDEFEND LOG MGMT
Page shows log sources as "Type": Proxy, Exchange, Firewall etc
All collected in one place. Query once = see output from Proxy, FW, etc together

PURPOSE OF LOG MANAGEMENT
Use 1: Check if any device communicating with particular address
Ex: Malware C2 = "letsdefend.io". Search this in Log Mgmt to see if any device contacted C2

Use 2: SIEM alert says "LetsDefendHost" leaking data to IP 122.194.229.59
You isolated that device. But still search Log Mgmt for that IP
Reason: Alert showed 1 device, but other devices might also be infected and missed by SIEM

7. **EDR - ENDPOINT DETECTION & RESPONSE**
- EDR = Endpoint Detection and Response
- Also called ETDR = Endpoint Threat Detection & Response
- Integrated endpoint security solution
- Features: Continuous real-time monitoring + data collection + rules-based auto response + analysis
- Source: McAfee definition

POPULAR EDR TOOLS
CarbonBlack, SentinelOne, FireEye HX
<img width="1366" height="768" alt="Screenshot (12)" src="https://github.com/user-attachments/assets/347cc413-4498-4eda-a2f4-d035d1e61126" />




EDR ANALYSIS - LETSDEFEND
- Left side: List of accessible endpoint devices
- Search: By endpoint name, or IOC like IP, file hash, process name across all hosts
- Right side: Device info + sections: Browser History, Network Connections, Process List



CONTAINMENT
- Must isolate hacked machine from network
- 2 reasons:
 1. Prevent attacker from connecting to internal network
 2. Prevent lateral movement inside network
- Isolate from internal + external networks till vulnerabilities fixed
- EDR Containment: Device only communicates with EDR center, not network
- Benefit: Even after isolation, analyst can continue investigation

IOC SEARCH IN EDR
Search file hash, filename etc across all hosts
Ex: MD5 hash "ac596d282e2f9b1501d66fce5a451f00" found on 1 device
Search same hash in EDR -> find if file exists/running on other devices
Helps understand scope: who all are affected by attack

8. **SOAR - SECURITY ORCHESTRATION AUTOMATION & RESPONSE**
- SOAR = Security Orchestration Automation and Response
- Makes security products/tools work together automatically
- Streamlines SOC team tasks
- Ex: Auto search VirusTotal for SIEM alert source IP. Reduces analyst workload

POPULAR SOAR TOOLS
Splunk Phantom, IBM Resilient, Logsign, Demisto

SOAR BENEFITS
1. Saves Time: Automates workflows
   Common workflows: IP reputation check, Hash query, Scan file in sandbox

2. Centralization: One platform for everything
   Sandbox, Log Management, 3rd party tools all integrated in SOAR

3. Playbooks: Pre-defined investigation steps for different SIEM alert scenarios
   - Even if you forget procedure, follow playbook steps
   - Keeps whole SOC team on same page/analysis process
   - Ex: Force everyone to check IP reputation by adding to playbook

LETSDEFEND + SOAR
"Case Management" = SOAR equivalent
SIEM/Monitoring page: Open tickets for cases created
Shows list of open and closed cases
Click open case -> automatically assigned playbook appears
Follow playbook to investigate associated SIEM alert

<img width="1366" height="768" alt="Screenshot (8)" src="https://github.com/user-attachments/assets/e8ac0a41-057e-423a-9644-d6aaf82de6f3" />




9. **THREAT INTELLIGENCE FEED**
- SOC team should be immediately aware of latest threats and take precautions
- Threat Intelligence Feeds created for this need
- As SOC analyst, use these feeds to guide investigations

WHAT IS THREAT INTELLIGENCE FEED
- Data provided by third party company
- Includes: malware hashes, C2 domain/IP addresses etc
- LetsDefend Threat Intel page: Shows many types of data like hash, IP etc
- Data consists of artifacts from previous malicious activity
- Could be hash of malware or IP address of C2 center
- As SOC analyst: Search threat intel feeds to determine if hash/file was used in malicious scenario in past

FREE POPULAR SOURCES
- VirusTotal
- Talos Intelligence

IMPORTANT POINT
If data you run through feeds does not show up:
- Ex: Ran hash of .exe in VirusTotal, found nothing suspicious
- Mistake: Don't just assume file is clean
- SOC analyst should not assume clean only because no results in feeds

10. **COMMON MISTAKES MADE BY SOC ANALYSTS**
Like everyone else, SOC analysts can make mistakes. Avoid these:

. Over-reliance on VirusTotal Results
- Don't rely only on VirusTotal green screen showing "harmless"
- New malware uses AV bypass techniques not detected by VT
- Use VirusTotal as supporting tool only
- Perform analysis with this in mind

. Hasty Analysis of Malware in a Sandbox
- 3-4 minute sandbox analysis may not give accurate results
- Reasons:
  a. Malware might detect sandbox environment and not activate
  b. Malware may become active after 10 to 15 minutes
- Solution: Keep analysis duration as long as possible
- Do analysis in real environment if possible

. Inadequate Log Analysis
. Overlooking VirusTotal Dates

<img width="1366" height="768" alt="Screenshot (9)" src="https://github.com/user-attachments/assets/5e4889d8-7305-40cf-9033-92d91e122997" />


