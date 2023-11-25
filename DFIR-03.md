# Incident Response Implemetation
## Table of Contents
1. SOC Operation & Lifecycle
2. Identification & Scoping
3. Containment
4. Intelligence Gathering
5. Eradication
6. Chain-of-Custody
# SOC Operation & Lifecycle
## SOC Relationship w/ IR
- SOC team isnt responsible for incident handling
- During an incident, SOC detects the event and notifies the IR team.
## Coordination: Who do we talk to?
- Management = Establishes response policy, budget, and staffing
- Information Assurance = Ensures security controls and policy enforcement
- IT Support = IT technical experts
- Legal Support = Ensures legal & policy compliance
- Public Affairs = Diplomatic communication w/ the public
- Human Resources = Insider threat situations, employees who violate policies
- BCP/DR = Works closely and in parallel with IRT
- Physical Security = Organization-wide drills regarding facilities
## SOC Model Criteria
1. 24x7x365
2. Employee morale
3. Cost
4. Expertise
5. Turnover & burnout
6. Decision points
7. Private information & NDA
8. Investment planning
9. Tooling & Correlation
10. Training, practice, and exercise
# Identification & Scoping
## Importance of Methodology
- Methodology = a predefined method of performing an action
- Procedures = Guidelines and instructions
- Incident Uniqueness = Every incident is unique, and procedures may not cover every possibility
## Preparation for Attack Scenarios
- Estimate and prepare to address attack scenarios
- Enumerate different attack scenarios
- Test methodology
- Devlop procedures
    - Unknown Scenarios = We can't know everything, so experience is always very important!
## Attack Scenarios
![Alt text](<../assets/Attack Scenarios.png>)
## Incident Detection
- Automation & Orchestration = Obtaining a timeline from host and network-based tools.
- Precursor = Information that indicates an attack may be imminent
- Indicators = Pointers to an incident that may be underway.
## Undetected Incidents
- Undetected Incidents = Not all incidents are obvious or detected
- Vigilance = Notice anything out of the ordinary? Do we have the right tools to discover an icident?
- Log & Artifact Retention = Long log retention and 3rd party experts.
## Incident Analysis & Priority
- Incident Analysis = Gather information, determine the incident's scope of impact, produce an inital report
- Prioritize Incidents = Prioritize by function, information sensitivity, and difficulty of recovery
    - Prioritizing Practice: Determine which incident should be handled first.
# Containment
- Containment = The process of endeavoring to stop the spread of a cyber intrusion
- Scope & Strategy = The scope of the intrusion must be evaluated to apply an effective strategy
## Containment Strategies
![Alt text](<../assets/Containment Strategies.png>)
## Should We sit and wait?
- Delaying containment is not recommended
- Be proactive and apply a containment strategy
- Deception systems help containment and intelligence gathering
- Apply containment as quickly as possible
# Intelligence Gathering
- Threat Information = Information that helps understand how an attacker operates to improve protection
- Threat Intelligence = Threat information that is processed and analyzed to devise more effective security measures.
    - Threat intelligence is based on threat information and translates it into effective action.
## Threat Information
![Alt text](<../assets/Threat Informationm.png>)
## Threat Intelligence
- Cyberseccurity is a team effort
- Information and threat intelligence must be shared
- Knowledge must be shared
- Information sharing and analysis organizations (ISAO) should be consulted
## Threat Intelligence Process
![Alt text](<../assets/Threat Intelligence Process.png>)
## Threat Hunting
- Know your system
- Know your enemy
- Proactively search for system loCs
- Review logs and other data for evidence and loCs
- Share information
## Threat Hunting Process
![Alt text](<../assets/Threat Hunting Process.png>)
## Deception Systems
- Moving Target Defense = Diverts attacker resources to decoy systems
- Intelligence Gathering = Enables gathering of TTPs
    - Although significant investment and training is required, the defensive yield will be worth it
# Eradication
- Eradication involves total removal of an intruder
- First comes evidence gathering and containment
- Examples: malware destruction, image recovery
# Chain-of-Custody
- Chain-of-Custody (CoC) = Critical process, document actions pertaining to forensic evidence
- CoC Process = the process is employed in any field in which forensic evidence must be presented in a court of law
    - Any action that involves forensic evidence must be documented, or the bad guys will not be punished
## CoC Process
![Alt text](<../assets/CoC Process.png>)
## CoC - The 'Ws' and 'H' of 5W1H
![Alt text](<../assets/Coc the 5w1h.png>)
## CoC Form Completion Example
![Alt text](<../assets/CoC Form completion example.png>)
## The Procedure in CoC is Crucial
- Forensics experts are careful about details
- It is important to acquire evidence prior to eradicating a malicious agent
- Other professionals must be informed of what was done to the evidence via the CoC form
