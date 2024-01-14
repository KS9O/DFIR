# Data Acquisition
## Table of Contents
1. Data Acquisition
2. Drive Capture
3. Advanced Capture Tools
4. Evidence Inspection
5. Virtual Drives
6. Memory Dumping
7. Virtual Memory Dumping
8. Memory in Other Locations
# Data Acquisition
## State Capture
- To Conduct a proper investigation, you must preserve the affected state
- A capture enables understanding a threat and investigating it at the same time
- A state capture prevents the loss of evidence
## Captureable Evidence
- Hard Disk Drive(HDD) or Solid-State Drive (SSD) - the hard drive may contain file and log evidence
- Memory - the memory is full of evidence of running processes
    - Capturing network traffic does not constitute preservation of evidence
## Image Capture Pros & Cons
Advantages                            Disadvantages
![Alt text](<assets/Image Capture prosandcons.png>)
- there are possibilities of partial capture, like encryption, pc shutting off
- **good hackers will always use encryption, which is very difficult to reverse.**
## Acquisition Recommendations
1. Memory captures are better if the user is logged on
2. Use sterilized media for acquisiton
3. Complete memory acquisition before drive acquisition
4. System interaction should be minimal
5. Choose the right capture format
6. Some capture tools are more efficient than others
7. Always capture to an external source
8. Document the capture properly
# Drive Capture
## Drive Sectors & Partitions
- Each drive is divided into sectors
- Although some sectors may not be allocated, they can still include data
- A partition is a logical, not physical, entity containing multiple sectors
![Alt text](<assets/drive sectors and partitions.png>)
## Partial & Full Clone
- Full Clone - A full clone is the cloest option to having the actual drive, but only some of the data on a drive is useful for forensics
- Logical Image - A logical image narrows the search field, some evidence may be spread across multiple partitions
    - Capturing the state of an HDD or SSD is known as cloning. A data dump of the drive
## Capture Tools
- dd, the lowest we should use, its not used for capturing
- Clonezilla
- FTK Imager
- Acronis
- Falcon
## Capture Formats
- RAW
- ISO
- EWF 
- dd
    - the capture format is based on the media from which it is captured
## The dd Tool
- a linux CLI tool used to fully clone drives and partitions
- Typically used via a live media drive
## The dd Command
![Alt text](<assets/dd command.png>)
- dd: data duplicator
- if: the source disk
- of: the target disk where the piped data is written
    - bs and conv determine how data is copied
## Capture from Live Media
- Drives always start in 2048
- Cloning is typically done through external media
- This prevents accidental changes to the drive
- It is also important to save the clone to an external drive
# Advanced Capture Tools
## Clonezilla
- Clonezilla is a live linux distrubiton dedicated to cloning drives
- Clonezilla uses its own format to save images
- It can clone more than 40 computers at the same time
## Clonezilla capture modes
- Device-image - this option creates an image capture from an actual drive
- Device-device - this option clones an entire drive or partition to another drive or partition
- Remote-source - one of clonezillas most important features is that it can clone over the network
## FTK Imager
- FTK Imager is part of the Forensic toolkit suite of tools
- The tool can be installed on the OS or executed from live media
- Although FTK is commercial, the imaging software is free
## Forensic Image Formarts
- E01 - Provides compression per file cehcksum and password protection
- AFF - Stores the imaged disk as compressed segments for better saving and metadata of the image
    - unlike non-forensic images, forensic images provide additional features that do not alter content on the drive
# Evidence Inspection
- The traditional way to investigate an image is to open it in a dedicated software tool
- An alternative method is to create a VM based on the image
    - If a drive is encrypted, the preferred method of investigation is to create a VM based on the image
## Autopsy
- Autopsy uses forensic tools from The Sleuth Kit
- Each case to be examined in autopsy is created separately
- A case can include multiple captures
## Autopsy features
- Autopsy includes many tools to enhance the analysis of captured images
- These tools include hash lookup, file carving, metadata extraction, and others
- The tools can extract important data and index data for faster queries
## OSFMount
- Used to allow us to mount dd images in windows
## Preservation
- a critical part of any cyber investigation is the isolation and preservation of digital evidence in its original state
- Preservation of evidence helps both the investigation and the legal process that may follow
## Hashing
- Hashing can verify file integrity
- Hashing both the capture source and the captured image can prove a file's authenticity
    - in a criminal investigation, hashes can be used in a court of law to provide evidence of integrity.
