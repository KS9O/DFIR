# Linux Forensics
## Table of Contents
1. Linux Live Forensics
2. Linux Live Acquisiton
3. Linux File Systems
4. File System Analysis
5. Linux Memory Forensics
6. Process Investigation
# Linux Live Forensics
## Methods
- In linux, everything has file representation: memory, running processes, etc.
- Dead and live analysis are similar in many aspects
- Most linux-based data is not binary
## Linux Forensics Acquisiton
- Static binaries are used for a minimal footprint on the system
- Binaries should be loaded from a live CD
- In most cases, such Rescue CDs are custom made
## Static Binaries
- Live CDs should be mounted as RO ( read only)
- Although the binaries are static, some may rely on other binaries to work
- Busybox is also commonly used in such cases
## Extraction Over NC
- To prevent writing to disk, data acquisiton should be done over the network
- Netcat is typically used to send and receive the data
- On the compromised host, a static binary of nc(netcat) is used
# Linux Live Acquisiton
## Network Data Extraction
- Netstat can be used to obtain network information
- Netstat can show open and established sockets
- This is useful when attmepting to identify backdoors
![Alt text](<assets/network data extration.png>)
# Process Acquisiton
- ps is used in Linux to acquire process information
- However, from a forensics perspective lsof is better
- lsof lists are based on the files used by processes
## Kernel Modules
- Inspecting the kernel modules may reveal malicious activity
- Kernel modules can be hidden and require a more thorough investigation
## File Acqusition
- dd = a bit for bit copy
- file extraction is possible over the network using dd
- dd can copy files and parititons byte by byte
- Using piping and input redirection, the data can be sent over the network.
# Linux File Systems
## Different Distrubtion File Systems
- Ubuntu
- Debian
- Linux Mint
- Red Hat
## extended File System
- A family of file systems that includes Ext2, Ext3, and Ext4
- Ext4 is the most common file system in linux distributions
    - Ext4 includes many features, such as journaling, space allocation, and others
## Other File Systems
- XFS = Designed to span multiple storage devices
- Divides the file system into mapped lbocks of data
- BTRFS = Space-efficient file system
- Supports compression and snapshots
## File System Comparison
![Alt text](<assets/File System Comparison.png>)
## Multiple File Systems
- At any given time, Linux hosts multiple file systems
- Among them are tmpfs, squashfs, and others
- The systems can be viewed using df -T
# File System Analysis
## Image Mounting
- Captured images can be mounted directly in Linux
- the losetup command is used to creapte a loop device
- loop devices can be moutned the ssame way as other devices
## Journaling
- Keeps track of changes not yet commited to the file system
- Journaling can be done on an etnire file or just itsm etadata
- Was introduced in Ext3 and improved Ext4
## Jlas and JCAT
- This sleuth kit provides tools to insepct hte journal
- JLS lists all teh blocks, while JCAT prints information of a given block.
- The block data is usually unreadable but may include file names
## Inode Structure
- Inodes are the Linux equivalent of MFT
- They map files to the system w/o file names and inclucde time stamps
## inodes 
- inodes can be view3ed using the ils and ffstat commands
- By defualt, ils only displays deleted nodes
- inodes can be viewed more elaborately on live systems
- its epoch to datetime
## File System Debugging
- Linux has a special utility to debvug file systems called debugfs
- debugf can also be used to recover files
# Linux Memory Forensics
## Linux Memory
- RAM = Linux uses RAM in a similar way to windows, RAM can be investigated using volatility
- SWAP = The linux equivalent to page file, can be a file or an entire partition
    - The swapon -s command can be used to check the location of the swap
## fmem Kernel Module
- One way to create a memory dump is to use the fmem kernel module
- the kernel module creates /dev/fmem, which can be captured
- Because the memory isd dynamic, issues may arise when using dd.
## LiME
- A more stable tool for memory dumping is LiME
- LiME also supports mobile devices
- a python utility called LiMEaide enables remote memory dumping
## Swap Digger
- Swap Digger is a bash script that automates swap analysis
- The Script looks up passwords and URLs
- Swap Digger can operate on live systems and mounted captures
# Process Investigation
- Processes in Linux have file representations
- Process files include metadata associated w/ the process
- Processes are mapped in the /proc/ directory
    - The /proc/ directory uses tmpfs, meaing the files are saved in volatile memory
## Proc Directory
- Each process listed by ps or lsof is mapped in /proc/.
- Process directories are based on their PIDs
- Each folder contains additional files required for the processes to run
## /proc/[PID] Content
![Alt text](<assets/2023-12-10 11_46_47-Linux Forensics_ UCF-CS-40-DFIR.png>)
## Maps and Descriptors
- Two other useful commands are maps and fd.
- The maps command lists all laoded lbiraries
- the fd command lists all file descriptors
## Extracting the Executable
- The executable for each process can be extracted using a cp
- Extraction will work even if the executable was deleted
