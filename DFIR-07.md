# Memory Analysis
## Table of Contents
1. Memory Analysis
2. Memory Identification
3. Process Investigation
4. Network Investigation
5. Code Injecction Investigation
6. File & Process Dumping
7. System Investigation
# Memory Analysis
- one of the most important sources of information
- an entire area of expertise 
- extremely useful in malware analysis
## memory analysis use cases
- fileless malware = some malware can run in memory w/o creating files in the system
- Encrypted systems = when loaded into memory, most information will be unencrypted
## Decision Tree - Recap
- Memory extraction is directly affected by the systems state
- Memory dumping is different in bare-metal and virtual systems
- for bare-matal, the acquisiton depends on wheter the system is on or off
![Alt text](<assets/decisison tree.png>)
## Dump Formarts - Recap
- Raw
- Crash dump
- hibernation
- EWF
- AFF4
## Analysis Frameworks
- Volatility = a widely used framework for memory analysis and investagion, #1 used 
- Rekall = framework developed by google and an alternative to volatility, they no longer use because of python 3, they tell you to use volatility
## Six Investigation Steps
1. Procesxess = Investigate rogue proccesses
2. DLL and Handles = Check DLLs used by various executables, we can use the same "clean DLL" and compare hashes to see if its infected
3. Network = Check network activity and artifacts, is netcat running, a file opening a port and listening, or is something going out, volatility will run all these things
4. Code Injection = Check for malware traces in memory, we insert code into a legitmate running process and we can overwrite memory, buffer overflow is technically a type but not the way we would see it
5. Rootkits = Check for sings of rootkits, it changes bootlevels, and files unknown, hard to detect and get rid of
6. Dump = Dump suspicious processess for in-depth analysis, going to have to learn how to read assembly reading language
# Memory Identification
## KDBG( Kernal Debug) for System Profiling
- Prior to analsys, the memory structure needs to be identified
- Volatility uses the _KDDEBUGGER_DATA64 structure to detect the windows versions
    - Rekall uses global symbol information
## Profile Identification
- Detecting the correct profile is crucial for memory analysis
- The locations of artifacts are different among OS's
- Volatility uses the imageinfo command
## Memory Interactions
- Plugins = the most common method is to analyze memory using volatility
- Volshell = an advanced debug shell that interacts w/ memory
## VM Metadata
- Memory obtained from VMs will have additional metadata
![Alt text](<assets/vm metadata.png>)
- in virtual block, this data is saved in a structure called DBGFCOREDSCRIPTOR
- VMware metadata can be extracted using the vmwareinfo command
## Image Conversion
- Crash dumps and hibernation files cannot be read as is
- They require conversion via the imagecopy command
# Process Investigation
## Search Goals
- Parental Structures - Legitimate processess have identifiable parent tree structures, its all the services
- Hidden Processess - Some processes may attempt to hide their execution
- Suspicious Details = Malicious processes will often attempt to copy the names of PIDs of legitimate processes
## PSlist and Pstree (Processlist, ProcessTree)
- Pslist is a basic plugin used to view the process list
- Pstree is more advanced and shows the process hierarchy as well
- Alternativaly, processes can be corelated using the PID (Process ID)and PPID(Parent Process ID) its important to kno wthe relation between the PID and PPID
![Alt text](<assets/Pslist and PsTree.png>)    
    
    - PSxview can also be used to tell if a process is trying to hide by having a hidden flag
## Legitimate Tree
![Alt text](<assets/legitimate tree.png>)
- Windows maintains an organized process hierarchy
- Out-of-place processes are easily identifiable
- For example, svchost.exe must be executed under services.exe
## Suspicious Process Tree
- lsass process is how stuxnet tries to hide
![Alt text](<assets/suspicious process tree.png>)
    - in the case of stuxnet, the malware created processes w/ illegitmate ppids
- lsass is always started with windows login
- 668 is the legit way of lsass, so in the picture above we can see how the ppid and pid arent legitmate
# Network Investigation
## Network Connections
- Connscan - Scans for identifiable TCP connections in older versions of windows
- Scokets - Scans for all open sockets
    - netscan can be used in more recent versions of windows
## Connections Lookup
- if a suspicious connection is found, its IP can be looked up
- The IP can also be correlated to a PID
## Sockets
- Sockets displays only local open ports
- It shows both TCP and UDP ports
- not all ports detected by Conscan will be displayed by Socekts
    - Conscan and sockets should be used as complementary plugins
## URL Identification
- URLs represent network-related information not identified in memory
- There is no available utility that can be used to scan for URLs
- URLs can, however, be retrieved via strings or bulk extractor
![Alt text](<assets/URL Identification.png>)
