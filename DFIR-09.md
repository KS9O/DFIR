# Log Analysis & Timeline
## Table of Contents
1. Log overview
2. Windows Logs
3. Log Analysis
4. Linux Logs
5. Statistical Analysis
6. Log Attacks
# Log Overview
- Logs can be created automatically by systems, but some require manual setup, almost all apps and operating systems are generating logs or can be configured to generate logs
- Some applications and devices differentiate between various types of logs
- Logs can be found according to their file names or using GUI-based options
## Why Use Logs?
- Store information that is not found elsewhere
- Record useful information about certain eventsin the system
- Logs can assist in the troubleshooting process when errors occur
- Regarded as evidence in a court of law
- REquired for many governance, risk, management, and compliance (GRC) strategies
- Included in an aincidient response investigation
## Log Classification
- Informational
- Debug
- Warning
- Error
- Alert
## Common Log Generators
- Syslog = used by linux os w/ tcp/udp protcol on prt 514
- SNMP = Network device management
- LEA = Proprietary checkpoint protocol
- Event Viewer = Used by Microsoft Windows
- Database = Many applications work w/ database event logs
- SDEE = Backward compatible w/ RDEP
## Network Time Protocol ( NTP)
- Syncs clocks across the network
- Ensures a more accurat eevent timeline
- Can operate locally or over the internet
## Timeline
- Constructs a picture of all key logged events
- Reveals the sequence of events
- Mandatory in many forensic reports
# Windows Logs
- Types : Apllication, service, security, and system
- Applicatiiopn and service logs include many useful logs, such as PowerShell and Terminal Services
- Can be used to troubleshoot blue screen of death (BSOD) errors
- Can be use to investigate successful and failed logons
## Windows Event Viewer
- Presents details of events (at the bottom of the window)
- Each event category has a unique ID
- The detail section displays event in XML format
## Event Viewer Log Filtering
- Enables faster viewing of essntial event information
- Filters include data and time, event level and event id and more
- It is also possible to filter by XML
## Event IDs
- 4720 = User account created
- 4726 = User account Deleted
- 4727 - Security-enabled global group was created
- 4626 = sucessful logon
- 1102 = an audit log was cleared
- 4732 = a member was added to a security-enabled local grouo
- 4725 = user account was disabled
- 4625 = account failed to log on
## Logon Type IDs
- 2 = Interactive login
- 3 = Network
- 4 = Batch
- 5 = Service
- 7 = Unlock
- 8 = Network clear text
- 10 = Remote interactive
- 11 = Logon w/ cached credentials
## PowerShell Logs
- Store historical PowerShell commands
- Two ways to view historyical PowerShell records:
- - Open PowerShell and click the UP key
- - Open the file at the following location: %AppData%\Microsoft\Windows\PowerShell\PSReadLine

    - PowerShell History helps detect fileless attacks
# Log Analysis
## Pre-Analysis Notes
- Define log analysis goals, Analyze logs to characterize the element that may be involved in an event
- Use logs to choose appropriate tools for the investigation
- note that it is not recommended to search through a log line by line
## Query Builder
- Microsoft Log Parser 2.2
- CLI interface used to parse and investigate logs via SQL
- Can extract data from text-based files, such as LOG, CSV, XML, and EVTX
- Log Parser Lizard
- A built-in Microsfot Log PArser 2.2
- USer-friendly GUI w/ options to extract data from various types of logs
## Microsoft Log Parser 2.2
- Can investigate Windows event logs from files or from the Event Viewer
- Supports many log types, including IIS, SCV, EXML, and EVT
## Log Parser Lizard
- The top pane is used for queries, and the bottom pane displays the results
- Charts can be used to discover trends in the logs
## Manual Log Review Limitations
- Aggregate vs. distinct logs
- Search through millions of logs
- Hard to see the big picture
# Linux Logs
## Basics
- Logs are different in CentOS/RedHat and Ubuntu/Debian
- Almost all log files are in the /var/log directory
    - To view or access the log files, you must have root permission
## Linux Log File Contents
- /var/log/messages = global system message
- /var/log/kern.log = Data logged by the kernel
- /var/log/secure and /var/log/auth.log = Authentication and authorization privileges
- /var/log/cron = active cron job data
- /var/log/dkpg.log and /var/log/yum.log = Logs data when a package is installed or removed
- /var/log/boot.log = Boot message data
## Linux Log Commands
- head = Reads the first 10 lines of a file
- more = basic terminal paging program that displays contents page by page
- grep = searches for specific strings in files
- tail = reads the last 10 lines of a file
- less = like the more command but w/ search options
- awk = text processing program for better log viewing
# Statistical Analysis
## Intro to Statistical Analysis
- Some events will not be noticed if they occur only once
- When a malicious event occurs only once, it may appear to be a legitimate action
- When malicious events occur in large volumes, it is much easier to detect them
- Example: A user who sent 1.000 emails in one week sends 10,000 more email messages
## Frequency & Baseline
- Frequency = a spike in data over time may be considered abnormal behavior
- Data can be monitored by hour, week, month, and year
- Baseline = Sets a standard for normal behavior for the purpose of comparison
- Baseline example: the number of su commands used per hour each day
## Anomaly Detection
- Detecting events that did not previously occur in the system
- Determining normal operations of users every hour to establish a baseline
- Using propiretary systems that offer user behavior analytics (UBA) to monitor unusla events
    - Anomaly detection can trigger false positive alerts
# Log Attacks
## Why Attack Logs?
- Attackers do not want to get caught
- Removing evidence from the target is crucial to remainin anonymous
    - Information in logs about passwords, hosts, and users can be used during an attack
## What to Attack?
- The host in which logs are generated
- Transmitted logs
- Agents that collect logs
- The database in which logs are stored
    - Log attacks are aimed at disrupting a service or changing, deleting, and viewing log data
## Windows Log Attacks
- Deleting logs using the event viewer = Not useful, since logs are generated when logs are deleted
- SIEM monitors this type of event
- Deleting files from %system32%/winevt/logs = Requires high-level privileges
- to executhe this, the event log service must be disabled
- Doesnt delete all recent logs
## Linux Log Attacks
- Unlike Windows, manipulating log files is easy in Linux
- You must have sudo permission to midify logs
- The following command modifies a log in a UNIX-like system: sudo nano /var/log/messages
## Important for Upcoming Lab
- ![Alt text](<assets/upcoming for lab.png>)
