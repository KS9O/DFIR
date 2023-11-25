# Introduction to DFIR
## Table of Contents
1. Intro to DFIR
2. Incident Response Planning
3. DFIR Process
4. DFIR Toolset
5. DFIR Use Case
6. DFIR Environment
7. DFIR Scenarios
# Intro to DFIR
## Digital Forensics & Incident Response
- Digital Forensics (DF) = Examining and analyzing artifacts after a cyberattack
- Incident Response (IR) = Performing actions when a security breach occurs
    - DFIR, investigating and responding to a cyberattack after an incident
## What is Digital Forensics?
- Revealing and collecting all electronic data w/o modifying or contaminating it
- Preserving evidence and reconstructing past events
## What is Incident Response?
- Confronting and managing a security breach or attack
- Reducing damage and the cost of the recovery effort
## What is Threat Hunting?
- Active defense
- Proactively searching for threats
## DF vs. IR vs. TH
![Alt text](<../assets/df vs ir vs th.png>)
## DFIR Timeline
- IR planning should be done prioer to an attack
- The avverage time for an attack to be detected is 6 months
- digital forensics relies on data collected during IR.
![Alt text](<../assets/DFIR timeline.png>)
# Incident Response Planning
## Incident Responder Responsibilties 
- Establish an effective incident response plan (IRP) and maintain its effectiveness based on potential threats
- Investigate current and past incidents and analyze them
- Provide recommendations according to analyzed incident findings.
## IR Execution
- Successful IR = a good plan will provide a reponse for any relevant issue
- Following the Steps = The plan should include various steps, such as containment and eradication
## Six Stages
1. Preparation
2. Identification
3. Containment
4. Eradication
5. Recovery
6. Lessons Learned
## DFIR Process
## What is Evidence?
- In a court of law = Anything you saw,heard, or said that proves that something occured
- in digital forensics = log records, files, processess, etc
## Example of Evidence
- Autoruns identifies possible startup locations
- Startup programs can be evidence of persistent malware
- the programs reside in known folders and registry keys
## DFIR Process
1. Collect Evidence
2. Examine Colleccted Data
3. Analyze important artifacts
4. Report the findings
## DF Analysis Types
- Dead Analysis = Analyzing powered-off computers
- May include analysis of cloned drives
- Live Analysis = Analyzing powered-on computers
## Targeted Artifacts
- Files on a Drive
- Memory Artifacts
- Processes
- Log Files
- Cached Data
## DF Domains
- Network Forensics = Focuses on gathering data about traffic passing through network equipment
- Host Forensics = Focuses on gathering data regarding hosts, such as files or memory
# DFIR Toolset
## Acquisition Tools
- dd(Data Dump): Drive Acquisition
= A Linux utility for managing and converting storage drives
- FTK Imager: Drive and Memory Acquisition = Advanced forensics GUI-based program that enables multiple operations on images
- Dumpit: Memory Acquisition = A memory acquisition tool often used in Windows-based systems.
## Drive Inspection Tools
- Autopsy: Open-Source = Autopsy is part of the sleuth kit collection of Python tools used for forensic investigations
- FTK: Proprietary = Includes tools for cloned drive inspection
- EnCase: Proprietary = Includes many advanced features for image inspection.
## Memory Inspection 
- Volatility Framework = Open-source collection of Python tools supported by both Linux and Windows
- Rekall = Open-source framework for advanced forensic and incident response
    - Not many tools exist that can perform computer memory forensics
## Data Carving
- Bulk Extractor = Attempts to recover files without using a file system structure
- HxD = Although not carving software, it is commonly used to view raw data
- PhotoRec = a powerful carving tool mainly focused on media files
## Process Investigation
- A key step in DFIR is investigating processes of infected systems
- In Windows, this can be done using sysinternals tools
- The tools include a process explorer and process monitor
## Network Forensics
- Wireshark: Static Analysis = Operates on data that was already captured
- NetworkMiner = Focuses more on artifact recovery than protocol analysis
    - if network monitoring was no configured prior to an attack, it will only be relevant for memory artifacts (MA)
## Customized Tools
- Some tools can only be used for specific devices, such as DVRs
- Some forensic tools are custom-made for dedicated parsing
- Hashing is a common identification method
- Can prove the identity of specific files
# DFIR Use Case
## DF Scenario: Data Leak
- DF can be used to prove data leaks
- File carving can be used to identify if files existed on media devices even after deletion
- Hashing can be used to verify file identification
![Alt text](<../assets/DF Scenario Data Leak.png>)
## PhotoRec
- Files deleted from a drive are not necessarily destroyed
- They can often be recovered using special software
- Tools like PhotoRec can be parse drive images w/o accessing the file.
## Metadata and EXIF
- File contain metadata hidden from the user
- Metadata can include information regarding camera moel and location
- Tools like ExifTool canread this data and help the investigation
## What is EXIF?
- Includes GPS coordinates, camera models, and the exact time a photo was taken
- Can be used as evidence when an investigator recovers photo
# DFIR Environment
## DF Distributions
- Computer Aided INvestigate Environment (CAINE) = Used mainly for acquisition and live forensics
- REMnux = Used mainly as a persistent forensics system for memory artifacts
- FLARE VM = Used mainly for malware analysis
## FlareVM
- Windows can be turned into a DF environment using the FlareVM script
- The script installs and configures many MA and RE tools
## SIFT Workstation
- SIFT is a virtual Debian appliance dedicated to DF
- Developed by SANS, a leading cybersecurity training institution
- Comes as a pre-packed OVA
## CAINE Live
- CAINE is a distribution that runs from a live USB
- Its main feature is the ability to run entirely from RAM
- It enables real-time forensic acquistion
## Benefits of LIVE USB
- An essential part of any forensics toolkit
- Used for data acquistion and live forensics
## NirSoft Launcher
- As with a live USB, most forensic distros include additional tools
- The tools canbe executed w/o booting the distro
- NirSoft Launcher is an example of a unified interface for such tools.
# DFIR Scenarios
## DFIR for social engineering
- in phishing, SE refers to investigating the message and attached links
- in real-world social engineering, the IR team can set up decoys.
- Traces are usually emails, messages, and suspicious links
- the evidence is typically collected from employees
    - DF for social engineering is followed by threat hunting to determine wheter other employees were also affected.
## DFIR for Web Server Defacing
- Identify if and how the defacing occurred.
- Restore the content of the original site from backup
- Intrusion Detection = Identify the intrusion point
- Identifying Persistence = Identify if any backdoors remain
## DFIR for Trojan Delivery
- Response depends on whether the trojan was already executed
- If eecuted, it focuses on containment and eradication
- involves malware analysis
- Reveals actions the trojan performed in the system
