# Incident Response Preparation
## Table of Contents
1. Defining Assets
2. CIA Triad
3. Security Operation Center
4. Incident Response Plan
5. Technical Preparation
6. Disaster Recovery Plan
7. GRC Compliance
# Defining Assets
## Asset Definition
- Item of value is related to organizational objectives
- can be a computer or data
- Assets have interrelated characteristics such as value, criticality, and their involvement in business objectives
## Asset Types
- Tanigble assets = physical items such as company vehicles, buildings, hardware, software, etc.
- Intangible assets = Intellectual propertyu, patents, trademarks, etc.
## Most Valuable Assets
- Employees are the most valuable assets
- Employee skills represent 85% of a companys asset values
## Aset Protection
- What does secure mean in the cyber realmn?
- Does cybersecurity probide 100% protection?
- is there a single solution for all incidents?
- Is there a protection checklist for all assets?
# CIA Triad
- Cornerstone of an organoizations security infrastructure
- Helps security practitioners w/ risk assessment and asset management
- Serves as a tool or guide for securing information systems
## CIA Definition
- Confidentiality = Ensures sensitive data is accessed only by authorized individual
- Integrity = The certainty that data is trustworthy and accurate (unaltered)
- Availability = Guarantee of non-stop access to data
## Confidentiality Violation Scenario
- A popular website is breached, an attacker downloads the entire dataanse, including usernames and passwords and sells it in the darknet
- Note: the data must not be changedm and the websiute is sitll up and running
    - this is a violation of confidentiality because senstivie customer data was exposed to unaothroized individuals
## Integrity Violation Scenario
- An attacker launches a successful SQL injection attack on a finical webstie that changes stock vaules in a database for personal gain
    - This is an integrity violation based on data tampering and manipulation
## Availability Violation Scenario
- Moraro Botnet performs DDOS attacks against large DNS providers, resulting in the inaccessibility of several high-profile websites
    - This is an availability violation becuase several websites were not accessible to legitimate customers
## Additional Concepts
- Non-Repudiation = Provides proof of the oprigin and integrity of data
- Accountability = Tracks users activites during an incident
- Enforced through audits
# Security Operation Center
## Management Strategies
- Top-Down Approach = Evalulate, manage, and execute business decisions made by high-level executives
- Bottom-Up Approach = Employees share their ideas and market observations
## SOC Responsibilities
- Responsible fo tthe most critical IT Systems in a company
- Detect, analyze and respond to cybersecurity incidents
- Employ people w/ high-level skill in IT and cybersecurity
## Soc Roles
- Tier 1
- Tier 2
- Tier 3
- SOC Manager
- CISO
## Additional Roles in a Case of a Breach
1. CEO
2. Public Relations
3. Board of Directors
4. System Team
5. Network Team
6. NOC
7. Help Desk
8. Outsource Advisors
## RACI Table
- **R**esponsible, **A**countable, **C**onsulted, **I**nformed
- The tables main purpose is project management
- Used to assign roles adn responsibilities for each incidnet alert
![Alt text](<assets/RACI Example.png>)
# Incident Response Plan
## SANS & NIST
- **SANS**
- Private organization established in 1989
- Offers research and education in the field of information of security
- **NIST**
- National Institute of Standards and Technology
- Non-regulatory government agency that develops technology, metrics, and standards
- Part of the U.S department of Commerce
## SANS Steps of Incident Response
- Preparation = Define critical security incidents, performs risk assessment, identify sensitive assets
- Identification = Monitor IT systems and detect deviations from normal operations
- Containment = Implement short-term containment and network segment isolation, shut down hacked servers.
- Eradication = Remove malware from infected systems, identify and fix the root cause
- Recovery = Bring infected production systems back online
- Lessons Learned = Prepare complete documentation of the incident
## Ransomware Incident
![Alt text](<assets/randsomware incident.png>)
# Technical Preparation
## Preparing for an Incident
- Create a ***jump kit*** w/ tools to handle an event
- Use CD-ROMs or flash drives w/ RO switches
- Build an investigation VM for malware analysis
- Work w/ snapshots after initilazing the system
    - The steps are mandatory for ongoing incident management
## Jump Kit Items
1. A powerful laptop
2. Packet sniffer
3. Screwdrivers, flashlights, tweezers, etc.
4. USB drive w/ essential applications (read-only)
5. Blank media disk drive
6. Network cables
7. Network hub or tap
8. Write-blocking device(s) and hard drives
# Disaster Recovery Plan
## DRP Definition
- Outlines response strategies for unplanned events
- Helps minimize the effects of a disaster
- Earhtquakes, fires, floods, cyberattacks, and others
- Determines which application must always remain operational
## EC-Council Disaster Recovery Plan
![Alt text](<assets/EC-Council Disaster Recovery Plan.png>)
## Backup Sites
- a **hotsite** is a backup site thats up and running continuously and ready for immediate switchover
- a **warmsite** has servers and other resources for backup purposes but is not as ready for swithcover as a hotsite
- a **coldsite** whicch is the cheapest option, does not always have the necessary equipment to enable the resumption of normal operation
# GRC Compliance
## Governance Perspective
- Policies = official statements that reflect the stance and direction of top-level management
- Standards = acceptable level of quality
- Procedures = Describe each step required for specific tasks
- Guidelines = Recommendations or suggestions that are not necessarily mandatory
## Standards & Regulations
![Alt text](<../assets/standards and regulations.png>)

# DO LAB 2 and 4
