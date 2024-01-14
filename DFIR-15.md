# Malware Defense & Persistence
## Table Of Contents
1. Advanced Persistent Threats
2. Hiding Mechanisms
3. Advanced Malware Analysis
# APT ( Advanced Persistent Threats)
## Persistent Hackers
- Advanced Persistent threats (APT) refer to hackers who remain in a network for an extensive time period
- Persistent hackers typically use advanced techniques and tools
- Many such hackers are supported by states or agencies
    - The average time for APTs to remain hidden is 6 months
- These can be nation states, North Korea, Russia, China
## Open-Source Intelligence
- Open-source intelligence (OSINT) describes information collected from the internet about a certain target
- A lot of seemingly unimportant information is often revealed in social media forums and other publicly available sources
    - Some online companies will collect information about a target for a fee.
## APT Flow
- OSINT = Data acquistion from public sources
- ET = External takeover
- PE = Privilege escalation
- LM & IT = Lateral movement and internal takeover
- HM & IT = Hiding mechanisms and information theft
## Case Studdy: Regin
- The US government is suspected of creating malware called Regin
- The mwalware targeted companies throughout the world to perform mass surveillance
- Nearly half of the attacks targeted the private sector
    - Currently, no country has officially taken responsibility for the attack
## Locating Persistent Malware
- To locate persistent malware, we should strive to know the attackers options
- Tools like Autorun can help locate persistent malware
- Autorun.inf is another tool that can be used.
## Auto - Executables
- Windows OS includes options to run executables automatically
- For example, executables can be run by adding them to the startup directory
- Using autorun.inf is another way to execute programs automatically
# Hiding Mechanisms
- APT groups use a variety of techniques to hide their activity
- Packing, obfuscation, and other anti-forensics techniques can be difficult to investigate
- Due to the many defensive possibilites for hackers, protection against APTs is challenging
    - APTs may be hard to detect, but network traffic for CNC servers can be an wasier investigation choice.
## Anti-Forensics Technqiues
    - The anti-forensics techniques listed below can make it harder for an investigator to detect an incident
- Technique = Description
- Encryption = Hackers can encrypt static data to avoid detection
- Steganography = Hackers can hide crucial information in existing files
- Tunneling = Hackers can hide information in protocol packets
- Spoofing = Hackers can posion networks and cause them to send fake packets to make network analysis more difficult
## Steganography
- Steganography is a method of hiding a file in another file
- Several tools can be used to locate steganography, such as zsteg, binwalk, and others
- an attacker can hide an executable in an image using CMD-based commands
## Spoofing
- Spoofing is a method of changing the source to represent someone else
- Nmap includes several techniques to spoof the identity of a scanner
- -sl represents an idle scan
- -D represents a decoy
## Packing 
- Packing is a means of distributing an executable in a packed state. The packed program will be unpacked at runtimes
- When malware is packed, security applciations that perform automated static analysis may not flag a binary as malicious
    - Malware packing is considered an obfuscation technique.
## Executable Packer
- UPX(ulitimate packer of executables) is a free, portable, high-performance executable packer
- it arches a provided exectuable w. an excellent compression ratio
- It typically is uised to evade malware detection
    - UPX assigns its own unique signature to executables that it packs.
## UPX Usage 
- UPX is automatic, you only need to choose which action to perform on the specififed executable
- To use the default packing method, running upx.exe [executable name]
- UPX also includes a decompression option
# Advanced Malware Analysis
## Assembly Language
- Assembly is a programming language in which machine code insutrctions are written for the computer's CPU to execute.
- In assembly, each command targets a particular hardware componenet.
    - Each line of an assembly programs contains one operation for the computer.
## CPU Architecture
- The CPU architecture refers to the processors design
- The design determines which software can run on the computer and which hardware components are supported
- Each processor architecture includes its own unqiue assembly instructions
    - Intels x86 processor is the most architecture used by PCs
## CPU Architecture Types
- CPU architecture types include
- NASM
- TASM
- ARM
- MIPS
- AMD
## Intels NASM x86
- Netwide assembler (NASM) is an assembler and disassembler for the intel x86 architecture
- It can be used to write 16-bit, 32-bit (IA-32), and 64-bit x86-64) programs.
    - NASM is a popular linux assembler
## Disassembly
- Disassembly converts machine code into human-readable format for viewing
- It typically is performed by the IDA (interactive disassmbler)
    - IDA is the most widely used free disassembler.
## Debugging
- Debugging is a method of investigating the instructions a process sends to the CPU
- This method is rewuired due to the inability of static analysis to guess the instructions sent to the CPU by a process
    - Debugging can be dangerous, since it rewuires the execution of the suspicious program.
## Intel Debugging Terminology
- Breakpoint = Manual pause of a program for investigation purpose
- INT3/0xCC = Operational codes for breakpoints in the CPU
- Patching = Modifying operations in a program to control its functionality
## OllyDbg
- OllyDbg is a debugger that can analyze malware while it is running
- Malware analysts and reverse engineers commonly utilize this debugger, which is free, easy to use, and includes plug-ins that extend its capabilities.
    - OllyDbg comes in two versions that support the x64 and x86 architectures
## OllyDbg Example
- An executable is loaded into OllyDbg by selecting it or attaching a running process from the File tab.
## Anti-Debugging
- Anti-debugging refers to techniques used to prevent reverse engineering and debugging
- Each of the anti-debugging techniques can be bypassed
## IsDebuggerPresent()
- ISDebuggerPresent() is a common anti-debugging function
- By resetting the value of EAX to 0, you can bypass this method.
- The example on the right shows C language code that includes the functions
# Exam Review
- Non-repudiation, means its settled it can not be changed
- Accountability is what we use for audits, who is incharge of viewing logs for web servers, accountability is when we place the finger and say it stops here. at a certain GPO. group 
- Static binaries are a minimal footprint and we use them because they are the clean ones we download
