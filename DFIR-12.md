# Static Malware Analysis
## Table of Contents
1. Malware Types
2. Malware Investigation
3. Static Malware Analysis
4. Hash Identification
5. Portable Executable
6. PE Investigation
7. Dynamic Linked Library
# Malware Types
- Software intentionally designed to cause damage to a computer
- Divide into families, with different characteristics
    - Malware is derived from **mal**icious soft**ware**
## Common Malware Types
- Ransomware = a malware encrypting data/files for money
- Rootkit = malware that bypasses authentication but purpose is to hide its presence, theres no legit rootkits they are all malicious, it uses hidden software to bypass authentication
- Backdoor = A method of bypassing some type of authentication procedure, 
- Botnet = a machine thats taken over by a malware and a C2 takes over controling it to help attack, it lurks waiting
## Other Malware Types
- Scareware
- Downloader
- Worm
- Information Thief
# Malware Investigation
## Investigation Techniques
- Malware Analysis = Describes all actions, methods, and tools used to identify and study malicious behavior
- Reverse Engineering = The process of deconstructiong an executable to reveal its design, architecture, and activity
    - These techniques are associated w/ one another but can also be applied independently.
## Analysis Methods
- Basic static analysis
- Basic dynamic analysis
- advanced static analysis
- advanced dynamic analysis
# Static Malware Analysis
## Static Analysis
- Identify if its an actual malware rather than a false positive
- Used to identify IOCs for malware
    - Static analysis can provide a lot of information even w/o executing the code
## Viewing Raw Data
- Hex editors can be used to view the raw data of an executable
- They enable quick searches for byte patterns
- Can be used to identify packed malware
## Binwalk
- Enables identification of magic byte patterns in files
- Files can contain additional files, as a method of hiding them
- Binwalk can find magic signatures used in UNIX and Windows files
## Sysinternals Suite
- A collection of tools that help manage, diagnose, troubleshoot, and monitor the windows environment
    - There is a 'live' version of Sysinternals that can be used w/o installation
## Strings
- Strings is a CLI tool designed for Linux and Windows
- The tool prints all the hard-coded strings in an exectuable file
- A string is any combination of three or more ASCII( a standard data-encoding format for electronic communication between computers.) characters
## Sigcheck (signature check)
- Microsoft requires any binary to be signed
- Many variants of malware have invalid signatures
- Sigcheck is used to verify signatures, and also provides hash and version information
# Hash Identification
## Investigation Techniques
- Malware Hashes = Testing the hash of malware is the most basic method of identification
- Yara Rules = An advanced method if identification based on patterns
    - Note that hashes and yara rules are useless against zero-day threats and newer malware variations
## Certutil
- Certutil is provided in the windows OS
- It enables the generation of multiple hash signatures for a file
- Certutil supports multiple hash formats, including MD5, SHA1, SHA256, and others
    - syntax: certutil -hashfile [file path] [hash]
## AV Engines
- Can help determine if a program is malicious
- Antivirus applications can identify malware by comparing its signature with an internal database
- Advanced antivirus apps use behacior analysis
## VirusTotal
- During an investigation, it is important to compare multiple sources
- VirusTotal is a web engine that includes up to 70 AV engines
- It auotmaitcally shares the results w/ security-related com,munities
## NoDistribute (Legacy)
- NoDistribute is a website similar to VirusTotal
- The site decalres that it does not share results
- NoDstribute inspects files using up to 35 AV engines
# Portable Executable
- a format for executables, used in Windows OS
- The format is a data structure that encapsulates the necessary information for the Windows loader
    - .exe is the most common extension of portable executables
- you can run without an installer basically
## Portable Executable (PE) File Sections
- .text  
- .rdata
- .data
- .rsrc
## Portable Exectuable Format
- Understanding te sections can help find data within the executable
![Alt text](<assets/PE Format.png>)
- For example, the .text section contails DLLs used by the program
- Note that not every executable will have the same sections
## PeView
- PeView is a tool that provides a way to view the PE structure content
- The tool displays the header sectionm resources, and more within an exe file.
- Documentation for each section is available on the internet
- if we are depending on a DLL that means we are not portable, 
# PE Investigation
## PE-Bear
- Programs store information in their metadata
- Pre-analyzers can parse the information and display it in readable format
- PE-Bear can reveal the compilation time and PE architecture
## PEiD
- Detects most common packers, cryptors, and compilers for PE files
- Allows detection and analysis of the .text section and its contents
- Can unpack some common packers
    - PEiD can currently detect more than 470 different signatures in PE files
## Resource Hacker
- A resource editor for windows applications
- enables viewing and editing all resources in executable
    - Resource hacker analyzes the .rsrc section and extracts additional information from it
# Dynamic Linked Libraries
- A windows file containing code and data that can be used by another program
- The purpose is to create reusable and shared code
    - Advantages include the use of fewer resources, modular architecture, and ease of deployment
## Important DLLs
![Alt text](<assets/important DLLs.png>)
## Dependency Walker
- A lot can be learned from the DLLs loaded by an executable
- DW helps monitor imported DLLs and List functions called by specific DLLs
## Dependency Walker Profiling
- By default, the output contains all functions in the DLLs
- To view only live functions that were called the prrofiling feature is used
- Profiling is done by clicking profile tab -> start profiling
