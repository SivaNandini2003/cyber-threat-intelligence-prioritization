Threat Prioritization System 

>>Overview

In modern cybersecurity operations, analysts are overwhelmed with thousands of potential attack techniques. Manually reviewing every technique is 
inefficient and time-consuming. This project builds a simple Python-based threat prioritization system using the MITRE ATT&CK enterprise dataset to 
automatically identify and rank high-risk attack techniques.

>>How the System Works

The system first loads the MITRE ATT&CK dataset and extracts only objects where `type == "attack-pattern"`, as these represent real adversarial techniques. 
Each technique is then evaluated using a scoring model designed to reflect potential risk and impact.

1-Base Score

Every technique begins with a base score of 5, ensuring all threats are considered significant by default.

2️-Name-Based Intelligence

The system increases the score if certain high-risk keywords appear in the technique name:

* credential (+3) → Indicates potential compromise of authentication data
* privilege (+3) → Suggests privilege escalation risk
* execution (+2) → Indicates active code execution
* persistence (+2) → Shows attacker staying power
* lateral (+2) → Suggests network-wide spread

These keywords reflect common high-impact attack behaviors.

3-Description-Based Intelligence

The description field is also analyzed to capture contextual risk indicators:

* administrator (+2) → High-level access exposure
* remote (+2) → External attack surface involvement
* bypass (+2) → Evasion of security controls
* stealth (+1) → Harder detection and monitoring

Using safe dictionary access ensures robustness even if fields are missing.

>>Prioritization Logic

After scoring all techniques, they are sorted in descending order. The Top 10 highest-scoring techniques are displayed to highlight the most critical risks. 
Additionally, techniques with a score ≥ 8.9 are flagged as "Critical Threats", allowing analysts to immediately focus on high-impact cases.

>>Why This Helps Analysts
This scoring system transforms raw threat intelligence data into prioritized, actionable insights. Instead of manually reviewing thousands of techniques, analysts 
can quickly identify those most likely to:
* Compromise credentials
* Escalate privileges
* Spread laterally
* Evade detection
* Operate remotely
By combining structured keyword analysis with logical scoring, the system improves efficiency, reduces response time, and supports better threat-informed 
decision-making.


