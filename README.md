# MITRE-ATT&CK

# Objective

The objective of this lab was to understand and apply the MITRE ATT&CK framework within a threat intelligence context using the TryHackMe MITRE ATT&CK room. The lab focused on learning how adversary behaviors are categorized into tactics and techniques, how observed activity can be mapped to ATT&CK, profilling Advanced Persistent Threat(APT's), and how this framework supports threat intelligence analysis, detection development, and incident response.

# Lab Focus Areas (MITRE ATT&CK)

- Understanding the structure of the MITRE ATT&CK framework

- TTP Mapping(adversary goals)

- Techniques and sub-techniques (how goals are achieved)

- Defensive Countermeasures(D3FEND)
  
- Using ATT&CK as a common language for threat intelligence and SOC operations

# Skills Learned

- MITRE ATT&CK Framework Navigation & Interpretation

- Adversary Behavior Analysis

- Threat Intelligence Structuring & Classification

- Mapping Observed Activity to ATT&CK Tactics & Techniques

- Understanding Detection Gaps & Defensive Coverage

- Analytical Thinking in Cyber Threat Intelligence
  
# STEPS

# Step 1
# Adversary Profiling (Mustang Panda):
My first objective was to utilize the MITRE ATT&CK knowledge base to profile "Mustang Panda," a known threat actor. I needed to understand their operational history, target demographics, and technical tradecraft to inform potential defensive postures.




<img width="624" height="499" alt="image" src="https://github.com/user-attachments/assets/440d806a-ebfa-407a-b88c-b827797164b2" />

<img width="624" height="315" alt="image" src="https://github.com/user-attachments/assets/0b007744-ce35-4846-bc51-dab9ffa6a9dc" />


● Intelligence Gathering: By navigating the Group page (G0129), I confirmed that Mustang Panda is a China-based cyber espionage group active since at least 2012.

● TTP Mapping: I analyzed their specific tradecraft. I identified that they utilize specific techniques for reconnaissance and execution. Notably, I mapped their "Reconnaissance" tactics to ATT&CK Technique ID T1598 (Phishing for Information).

● Tool Analysis: Further investigation into their software arsenal revealed their reliance on Cobalt Strike for Access Token Manipulation, a critical finding for tuning endpoint detection logic.

● Visualization: I utilized the ATT&CK Navigator to visually map these techniques (highlighted in yellow in my analysis) to see coverage gaps and prioritize defensive focus areas like "Command and Scripting Interpreter" and "Scheduled Task/Job."

# Step2
# Sector-Specific Threat Assessment (Aviation):
Scenario: I was tasked with acting as a security analyst for an organization in the aviation sector migrating to the cloud. I needed to identify relevant threat actors targeting this vertical to assess our defensive coverage.

<img width="624" height="928" alt="image" src="https://github.com/user-attachments/assets/62ab6c99-01c0-4ab1-97d9-17beea9182e9" />

<img width="578" height="1080" alt="image" src="https://github.com/user-attachments/assets/10d5920c-ab3d-4600-b4a3-7855c86862ad" />

<img width="624" height="690" alt="image" src="https://github.com/user-attachments/assets/b2659949-7b0b-446b-a066-07159175f503" />

● Threat Identification: Using the ATT&CK Groups search, I identified APT33 as the primary adversary targeting the aviation sector with activity dating back to 2013.

● Cloud Vector Analysis: Since the organization was migrating infrastructure, I focused on APT33’s cloud capabilities. I determined that "Cloud Accounts" was a key sub-technique of concern for our Office 365 environment.

● Tool & Mitigation Mapping:

* Offensive Tool: I linked the tool "Ruler" to this specific sub-technique, noting it as a high-priority indicator of compromise (IoC).
* Mitigation Strategy: I recommended "User Account Management" as the primary mitigation strategy to reduce exposure to dormant or unused accounts.
* Detection: I mapped the detection strategy to ID DET0546, ensuring our SIEM rules could alert on abused or compromised cloud accounts.

# Step 3
# Applied Cyber Analytics (MITRE CAR):
To enhance detection beyond standard signatures, I explored the Cyber Analytics Repository (CAR).

<img width="624" height="439" alt="image" src="https://github.com/user-attachments/assets/a317e22b-1cc2-4a26-ace4-4b6a09bda44b" />


● Analytic Implementation: I investigated specific analytics to detect adversarial behavior. I examined CAR-2019-07-001, linking it to the Defense Evasion tactic.

● Contextual Awareness: I analyzed the "Access Permission Modification" analytic and categorized its type as "Situational Awareness," understanding that while not always malicious, it provides critical context during an investigation.

● Query Logic: I reviewed pseudo-code and Splunk search queries (e.g., looking for svchost.exe creating files in System32\Tasks) to understand how to implement these analytics in a real-world SIEM environment.

# Step 4
Designing Countermeasures (MITRE D3FEND):
Moving from detection to active defense, I utilized the MITRE D3FEND framework to create a technical defense strategy.



<img width="624" height="122" alt="image" src="https://github.com/user-attachments/assets/989d14fe-c522-4ea2-95e2-5c6d1d3728af" />


<img width="519" height="1080" alt="image" src="https://github.com/user-attachments/assets/282db2df-a729-455e-9616-6ce2b65593a6" />


● Credential Hardening: I focused on the "Credential Rotation" (D3-CRO) technique. I analyzed the artifact relationships and determined that this technique helps mitigate risks by regularly regenerating passwords and certificates.

● Behavioral Analysis: I explored "User Behavior Analysis" as a sub-technique. Specifically, I identified "User Geolocation Logon Pattern Analysis" as the method to detect anomalous access attempts based on physical location.

● Data Source Requirement: To implement this, I confirmed that the primary digital artifact required for analysis is Network Traffic, specifically aiming to ingest and correlate IP geolocation data with logon events.

# Step 5
Assessing Emerging Threats (ATLAS & AADAPT):
Finally, I future-proofed my analysis by exploring frameworks dedicated to Artificial Intelligence and Digital Assets.

<img width="624" height="392" alt="image" src="https://github.com/user-attachments/assets/85f0a309-ab8f-4e7b-a72a-34598bd75dcf" />

<img width="624" height="1004" alt="image" src="https://github.com/user-attachments/assets/78f027ed-fb08-4ecc-bdb4-dfbff44ba503" />


● Blockchain Security (AADAPT): In the realm of digital asset protection, I identified that the technique "Scrape Blockchain Data" maps to ID ADT3025, highlighting the risk of reconnaissance against public ledgers.

● AI Threat Landscape (ATLAS): I investigated attacks against Machine Learning models. I determined that "LLM Prompt Obfuscation"; a method used to bypass safety guardrails in Large Language Models, falls under the Defense Evasion tactic within the ATLAS framework.

# Summary
This project reinforced my ability to use the MITRE ecosystem as a holistic toolset for SOC operations. I successfully demonstrated the workflow of:

● Profiling specific APTs (Mustang Panda, APT33) relevant to organizational context.

● Mapping technical indicators (Cobalt Strike, Ruler) to standardized IDs.

● Translating threat intel into actionable defenses (D3FEND) and specific analytics (CAR).

● Adapting to modern attack surfaces involving Cloud, AI, and Blockchain.

