# Threat Hunting
## Table Of Contents
1. Threat Hunting & Intelligence
2. Threat Exchange
3. Malware Forensics
# Threat Hunting & Intelligence
- Threat hunting is a proactive apporach to handling cyberattacks
- Its aim is to protect an organization from covert cyberthreats
- It typically is performed by Tier 3 SOC personnel
    - The average breach can go undetected for more than 6 months
## Threat Intelligence
- Threat intellgience is based on learning from other's mistakes
- Forensic researchers can learn about new exploitation techniques from public sources
    - Threat intelligence involves much more than simply reading an article about a breach
## Threat Hunting vs. Threat Intelligence
- **Threat Intelligence** involves obtaining threat-related information from various sources.
- The technique is used to imrpove the level of security in an organization.
- **Threat Hunting** involves the discovery of seemingly undetectable breaches
- The process investigates anomalies and suspicious activity
    - Threat hunting includes forensics, log parsing, and research.
## Hunting for Threats via CVEs
- As part of threat unting, a researcher may look for well-known CVEs
- A potential attack vector for a computer may be a documented CVE
- Searhc engines for CVEs include cve.mitre.org
## Tracking Breaches
- Tracking CVEs is often not enough
- More information must be gathered online
- By sharing information about breach IOC's, a researcher can easily find potential attack vectors
- The vector can be used to compromise a network.
## Indicators of Compromise (IOCs)
- An important part of dealing w/ a threat is obtaining IOCs
- IOCs help determine if an organization was harmed by a threat was implemented
- IOCs can also be used to distinguish false positives
# Threat Exchange
- IBM X-Force
- AlienVault OTX
- CrowdStrike
- Facebook
## AlientVault Open Threat Exchange
- different threat exchange platforms exists in the market
- Their aim is to share information about newly discovered threats
- AlienVault OTX is an example of a platform that shares information regarding threats : otx.alienvault.com
## AlienVault OTX IOCs
- AlienVault OTX provides a list of discovered IOCs
- It also offers a way to search for IOCs
## Threat Hunting Cycles
- Threat hunting is often divided into separate categories
- The hunt in each category will include different targets
- A hunt cycle can be created to change the focus of the threat hunting process periodically
![Alt text](<assets/threat hunting cycle.png>)
# Malware Forensics
- Many types of malware have been developed, literally millions, they can evolve, we as cyber defenders patch it, the hacker will have to use it, this means evolves
- Each type behaves differently
- Malware actibity can be discovered by analyzing the behavior of a computer
- Its constantly seeing our defensives , we catch it and they make it more powerful
## Suspicious Behavior
- Increased Traffic
- Accessed File Types
- Service Inspection
- Domain Identification
- Persistence = linux can run for years, while windows computer has to be reinstalled every year, apparently 
## Identifying Suspicious Behavior
- To identify malware activity, you must monitor suspicious system behavior continuously
- You can use several tools to monitor such behavior, including Wireshark and PowerShell
## Zeekbro
- Zeek is a framework used to parse, normalize, and correlate logs
- It focuses on extracting security-related information from logs to detect anomalies
- Zeek was previously known as Bro
    - Zeek can read PCAP files and extract useful security-related fields from them.
## Zeek Logs
- Zeek can monitor traffic on its own or investigate PCAP files
- Zeek outputs log files in a structured format w/ predefined names
- Zeek can also be used online to parse small PCAP files
![Alt text](<assets/Zeekbro Logs.png>)
## Persistence
- Malware may use persistence techniques to preserve a foothold in a compromised computer
- Persistence techniques may also constitute IOCs
- Although many persistence techniques exist, malware developers typically stick to just a few
    - Since persistence is performed using high-level privileges, many types of malware launch privilege escalation attacks
## Common Hiding Mechanisms
- Hiding Mechansim = Explanation
- Registry Keys = Regedit can be used to hide and launch programs automatically *
- Sheduled Tasks = A task can be scheduled to run a malicious payload
- Services = a malware service can be added to the system
- Startup Folder = Malware can be hidden in a startup folder *
- AppCert DLLs = Dlls that run in every process can be infected
- Bootkit = MBR can be manipulated to load malware upon restart
## Analysis Process
- Find = Find persistent malware
- Analyze = Analyze the file's hash and extract IOCs
- Other? = Check if other machines are infected
- Anomaly = Find anomalies, such as suspicious IPs
- Conclusion = Should you continue to investigate the incident or not
## Hiding from Analysis
- Many malware developers use well-known techniques for persistence
- Some persistence methods are very difficult to monitor
- For example, advanced manlware can use prorcess hollowing as a hiding technique
## Process Hollowing
- It hides in a memory process of a legitimate process and run my malware from there
- Main = Open the main process in suspend mode
- Copy = open a malware and copy its content,
- Paste = Paste the copied contents to the process's memory
- Run = Run the hollowed process w/ the content
