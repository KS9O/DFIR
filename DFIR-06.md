# Windows Dead Analysis
## Table of Contents
1. Power Forensics
2. Windows File Systems
3. Alternate Data Stream
4. ADS Forensics
5. File Carving
# PowerForensics
- A powershell forensics framework
- Works w/ FAT and NTFS
- Can be launched from live systems
- Depends mostly on master file table (MFT)
## Installation
- Powerfreonsics requires installation
- Powerforensics is available in the Powershell glalery
- Install the framework using: Install-Module -Name PowerForensics
## Operation Modes
- Live System = Powerforensics was initially developed as forensic toolkit for live systems
- Mounted Drive = PowerForensics can be used on mounted drives and non-mounted physical drives
    - Errors may occur in PowerForensics when parsing drives larger than 2 TB.
## Detecting Partitions
- Analysis typically begins by identifying the partitions
- Get=ForensicsPartitionTable can detect partitions on a drive
- Most images contain at least two partitions: system and boot
## Files & Records
- You can use powerForensics to view files and file information
- It can also detect special files, such as $MFT and $Volume
![Alt text](<assets/files and records of powerforenics.png>)
## Master File Table ( MFT) 
- A special file in NTFS systems that contains metadata for each stored file
- Changes dynamically when files are added or removed
## MFT Attributes
- Standard Information - Information such as time stamps and link counts
- Attribute List = Location of additional attributes outside the MFT
- File Name = Up to 255 characters
- Security Descriptor = Who owns the file
- Data = Contains the data section of the file
- Object ID = Volume-unqiue ID used by link-tracking services
- Index Root = Used to implement folders and other indexes
## PowerForensics Scripting
- Unlike regular browsing, PowerForensics lists files by parsing the MFT.
- It enables script-like functionality and smart searching
## Analysis Capabilities
- Boot and Partitions
- NTFS and EXT4
- Windows Artifacts
- Windows Registry
- Application Cache
# Windows File System
## Boot Record Types
- MBR  
Supports up to four partitions per storage device
- Works only w/ storage devices up to 2 TB
- GPT
- Supports up to 16 exabytes
- Supports up to 128 partitions
## What is a file system?
- the method computers use to manage the storage and retrieval of data
- File systems isolate data on storage devices for easier and faster identification and access
## FAT32 vs NTFS
- introduced in 1977 - Introduced in 1993
- Supports storage up 2TB - Supports storage up 256TB
- Supports files up to 4 GB - Supports up to 256TB
- Non-recoverable - Recoverable
- Can't Compress files - can compress files w/o user interaction
## NTFS Specialties
- Journaling = Recording storage device activity
- Indexing = Enables quick access to files stored on devices
- Alternate Data Stream = More than one resource included in a single file
## Attributes
- NTFS uses attributes to save information regarding files
- Attrobutes define data structures for raw bytes
- Saved in files called $AttrDef
## Attribute Forensics
- Youcan use parse attributes in a file system using PowerForensics
- The attributes list includes the mapping of data on the drive
# Alternate Data Stream
## $DATA Attribute
- $DATA contains the data content of a file
- By default, a files $DATA attribute is not assigned a name
- The attribute has no minimum or maximum size limit
- In NTFS, any file can have up to 1,024 different $DATA streams
## What is ADS?
- Alternate Data Stream
- Method of loading more than one data sector into a single file
- Works only w/ NTFS
- Typically used to hide files
## Creating ADS ( Alternate Data Stream)
- By default, Explorer.exe can load only the default data of the file
- Creating and loading data streams are done via CMD
- To create an alternate stream, simply add :[stream] to a files name
## ADS Execution
- Use the type command to read alternate data
- You can execute data in an alternate stream
- Execution does not depend on the main data's type
![Alt text](<assets/ADS Execution.png>)
## ADS Identification ( Alternation Data Stream )
- Explorer does not display ADS, but CMD does
- Use dir to display the contents of a folder
- Dir /R displays the contents of a folder w/ an ADS (if it exists)
# ADS Forensics
## Manual MFT Extraction
- Analyzing the MFT is necessary to obtain ADS
- MFT analysis will show dorted entries on the partition
- A DD raw image is required, but .E01 will also work
## MMLS
- MMLS is part of The sleuth kit
- It displays the volume contents w/ start and end sectors
- E01 images must be mounted first by running **ewf_mount[image] [path]
## ICAT
- The second step is to extract the raw MFT from the partition
- The ICAT tool will extract a raw and unparsed MFT
- ICAT uses the sectors offset and length to obtain data
## analyzeMFT
- The final step is to parse the raw MFT to a readable file
- Use analyzeMFT.py to parse the raw table to CSV file
- analyzeMFT is preinstalled in the SIFT workstation
## ADS in PowerForensics
- PowerForensics can detect alternate streams
- If provided w/ a volume it will list all files w/ an ADS
- If provided w/ a path, it will list all the streams of the file
## Autopsy
- Autopsy is based on the sleuth kit
- Autopsy automatically parses the MFT and shows ADS
- Extract files by right-clicking and selecting extract files
# File Carving
## Deleted Files
- When a user deletes a file, it is not actually deleted
- The file is marked as unallocated
- The file will remain the system until its sector is overwritten
## File Carving
- Reassembles files from fragments when no metadata is available
- File carving can be used to recover partially overwritten files
    - Carving can sometimes detect poorly hidden files
## Magic Numbers
- FF D8 FF E0 00 10 4A 46 49 46 00 01 = jpg, jpeg
- 50 4B 03 04 = zip apk / jar docx/ xlsx / pptx
- 89 50 4E 47 0D 0A 1A 0A = png
- FF FB = mp3
- 43 44 30 30 31 = ISO
- 4B 44 4D = VMDK
## Hex Editors
- File headers can be viewed in any hex editor
- use the command xxd to instantly view the header
- HxD is recommended for editing
## Hiding Files
- Most operating systems only pay attention to the first header
- Multiple files may be hidden by concatenating hex data
- Saving each hex section will result in a complete file
