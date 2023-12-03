# Windows Live Analysis
## Table Of Contents
1. Live Forensics
2. USE History
3. DNS Cache
4. Browser Forensics
5. Additional Browser Artifacts
6. Process Forensics
7. Recently Used
# Live Forensics
- Analysis of system artifacts while a computer is powered on
- Memory dump
- Virtual storage drive imaging 
    - The main purpose is to acquire volatile data that would otherwise be lost if the computer was turned off.
    - Volatile data is any data that is stored in memory, or exists in transit, that will be lost when the computer loses power or is turned off. Volatile data resides in registries, cache, and random access memory (RAM).
## Significance of Live Forensics
- Some data may be lost when a computer is turned off
- Over time, OS data may be overwritten
    - some data may be encrypted when a system is shut down
- Instructor called it a blackhole shut VM, a bit bucket, where we can throw the system in it so it cant shutdown to collect all the data on it and connect a honeypot to see the malware
## Recoverable Artifacts
- Registry Entries
- File Logs
- Master File Table
- Browser History
- USB Devices
## Irrecoverable Artifacts
- PowerShell History
- Prefetch
- DNS Cache
- USB Devices
    - during reboot, some artifacts may be partially deleted
- Powershell history actually stays cached the entire duration its on, until it reboots
# USB History
- USB is an industry standard for device connection, data transfer, and power supply
- USB devices belong to one of several classes, including HID, storage and others

## USB Device Classes
- 01h = Audio Devices ( speakers, sound cards)
- 02h/0Ah = Communication devices (network card, modem)
- 03h = HID(keyboard, mouse)
- 06h = Image transfer device (PTP, MTP)
- 08h = Mass storage (USB flash drive, memory card)
- 09h = USB hub
## USB Logs
- USB Connection do not creapte specific logs or files
- They trigger special events in Event Viewer
- USB connection events can be viewed using USBDeview by NirSoft
# DNS Cache
- Temporary database maintained by the computer's OS
- Contains records of recent visits to websites and other internet domains
## Listening DNS Cache
- Even in private mode, Windows maintains a cache database
- ipconfig /displaydns displays the DNS cache in Windows
- The records can help identify sites that were accessed in a non-monitored network
# Browser Forensics
## Browser Investigation
- The purpose of a browser is to connect to the internet and facilitate a simple and friendly user experience
- Browsers typically collect data about a user's searches and other activities
    - Most of the collected data can be retrieved by analyzing the browser's cache files.
## Browser Artifacts
- History = Includes entered URLs and webpages marked as favorites
- Cache = Files, image, scripts, and other media-related data
    - In digital forensics, items related to browsing history and cache are known as web artifacts
## Cache vs. History
- Cache 
.stores images, cookies, etc
- harder to clear
- the format is different among browsers
- may not disclose visited sites
- Not saved in private mode
- History
- stores only URLs
- Easily cleared
- The format is the same among browsders
- Explicit indication of visited sites
- Not saved in private mode
## Artifact Locations
    - Each OS stores browser data in different folders
- Artifacts               Location
- Chrome URLs = \Users\[user]\AppData\Local\Google\Chrome\UserData\Default\history
- Chrome Favorites = \Users\[user]\AppData\Local\Google\Chrome\UserData\Default\Bookmarks
- Chrome Cookies = \Users\[user]\AppData\Local\Google\Chrome\UserData\Default\Cookies.db
- Firefox Cookies = \Users\[user]\AppData\Roaming\Mozilla\Firefox\Profiles\xxxxxxx.default\cookies.sqlite
## Browser Cache
- Firefox = stores cache that can be viewed by entering about:cache in the URL field
- Chrome = Stores cache in C;\Users\[user]\AppData\Local\Google\Chrome\User Data\profile 1\Cache
    - Cache can be stored by both the browser and the OS
# Additional Browser Artifacts
## Google Analytics Cookies
- A method of tacking site visits, user activity, and other elements
- Inlcude time stamps and visit count
## Browser Search Terms
- Most modern browsers successfully save search terms
- Some search terms can be derived from URLs
    - Example: https://google.com/search?q=digital+forensics$cad=h
## Browser Search History
- Browsers save a users search history
- You can view the search history by clicking the search input line
- You can disable auto-complete searches in the browser settings
## Browser Investigation Tools
- BrowsingHistoryView - A free tool that can read history data from internet explorer, firefox, chrome and safari
- Axiom = a tool that can carve deleted artifacts from image captures
    - Other browser investigation tools are available, many of which are commerical
## BrowsingHistoryView
- This lighweight tool hleps cross-search browsing history
- The tool is available from NirSoft
- It does not display information such as cached credentials
# Process Forensics
- Instances of computer programs that are being executed
- Contain program code and activity
## Process Information
- PID
- Remote Connections
- File System Modifications
- Registry Changes
- DLL Usage
## Prefetch Files
- Applications executed in Windows create prefetch files
- The files are used as cache for loading time optimizations
    - Even if a process is no longer active, the prefetch file may indicate previous executions
## Prefetch Location
- Prefetch files contain process activity cache
- If not disabled, Windows stores prefetch files in C;\Windows\Prefetch
- The files contain metadata regarding the application
## WinPrefetchView
- WinprefetchView is a tool used to analyze prefetch files
- The tool is freely available from NirSoft
- It can determine the files last execution and location
# Recently Used
## Most Recently Used
- Lists programs or documents that were recently accessed
- Allows users to quickly access the last files and documents that were worked on
- MRU lists are saved in dedicated registers
## Registry
- Stores information in key-value format
- The registry can help identify persistent threats that execute during boot
- One of the keys is: HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
## RunMRU
- The run prompt uses the most recent used (MRU) Utility
- The registry key is: HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\RunMRU
- Features such as find and printers also use MRU
## AppCompactCache
- The registry key used to track compatibility issues
- Contains data about the file path, size and modification
- The registry key is: HKLM\SYSTEM\CurrentControlSet\Control\SessionManager\AppCompactCache\AppCompactCache
## Jump Lists
- Artifacts that can indicate a user's interactions w/ the OS
- Jump Lists track files accessed by a user and list them in the recent menu group
- Can also be viewed in Explorer's Recent Items
