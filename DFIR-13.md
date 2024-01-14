# Dynamic Malware Analysis
## Table Of Contents
1. Dynamic Analysis Introduction
2. Environment Setup
3. System Monitoring
4. ProcMon
5. Network Monitoring
6. Malware Samples
# Dynamic Malware Analysis
- a methodology based on executing malware
- Used to analyze malwares behavior and impact on the system
- Behavior analysis is another term
    - Performing static and dynamic analysis helps identify the true intent of malware
## Static vs. Dynamic Analysis
- **Static Analysis**
- Cide us bit executed and is safe to analyze
- Reviewing the programs code or PE format
- Uses a signature-based approach for analysis
- Involves file fingerprint, virus scanning, RE file's binary, packer detection, etc.
- Ineffective against sophisticated malware
- **Behavioral Analysis**
- Code is executed and can affect the OS directly
- Observing and controlling running code
- Uses a behavior-based approach for analysis
- Involves API traces, registry changes, network and system calls, etc.
- Effective against all types of malware.
## Dynamic Analysis Benefits
- Tracking changes
- The malware's code can depend on file system changes that cannot be viewed just in code
- Obfuscated data
- It is common for malware to obfuscate data and only reveal it on execuation
    - In an optimal scenario, dynamic and static analysis are used side by side
# Environment Setup
## Setting up
- It is necessary to prepare a suitable workspace for investigation
- This environment should be disconnected from the network
- More VMs can be added to simulate a real-life environment
## Main Guidelines
- Virtual Environment
- Different OSs
- Snapshots - 
- Network Connection
## Flare VM
- A Windows-based security distribution designed for reverse engineering (RE), malware analysis (MA), DFIR, and penetration testing (PT)
- The VM contains multiple tools for investigating malware samples
    - The project is based on a script that installs additional tools on a regular windows 7 VM.
## Cuckoo
- An open-source, automated malware analysis system
- Automatically runs and analyzes files while running inside an isolated OS
    - Cuckoo Sandbox can be downloaded from the following link:cuckoosandbox.org
## Online Sandboxing
- Free tools are available online to provide dynamic malware analysis and a sandbox environment
- These sites include hybrid-analysis.com
- joesandbox.com
# System Monitoring
## Monitored Data
- File System Changesd = malware usually makes changes inside the OS file system
- Network Activity = Analyzing the system's network activity
- Registry Changes = Analyzing the files access to registry entries
## Autoruns
- Autoruns is part of the sysinternals suite
- This tool allows you to analyze executables that run on the system at boot
- Autorun has several functionalities, such as Check VirusTotal
## Process Explorer
- Allows you to analyze all processes running at any given moment
- Process Explorer can display DLL files imported by a process.
- Displays general information about the system, processes, etc.
## Process Info
- Process Explorer allows you to view more information about a process.
- The threads tab shows all actions that run through this process.
- The TCP/IP tab shows all the network connections for the process.
## Regshot
- A registry utility that allows you to take snapshots of the registry
- It compares before and after snapshots of the registry
- Regshot displays changes and new keys added in an output text file.
# ProcMon
## Process Monitor
- Monitors information about individual events per process
- The information includes the event sequence number, time stamp, etc.
- Process Monitor has a visual and user-friendly interface
## Event Properties
- Allows you to view the full details of an event by double-clicking its row
- The properties can contain additional data bout the process
- This tool also has advanced filtering options
## ProcMon Filters
- Users can set a filter for an executable running on the system
- This feature is especially useful for malware analysis
- A researcher can set filters for the specific malware examined
