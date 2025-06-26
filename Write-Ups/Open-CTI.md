# 📊 OpenCTI Overview

## 🚀 What is OpenCTI?

**OpenCTI** (Open Cyber Threat Intelligence) is an open-source platform designed to **store, analyze, and visualize** cyber threat intelligence. Developed in collaboration with **ANSSI** (French National Cybersecurity Agency), it helps organizations manage technical and non-technical threat data — from IOCs to full-fledged campaigns — in one unified place.

> 🔗 Supports MITRE ATT&CK, integrates with MISP, TheHive, and more!

---

## 🎯 Objective

OpenCTI aims to provide:
- Centralized storage and enrichment of threat intelligence
- Visual relationships between entities (e.g., actors, malware, TTPs)
- Contextual data for better decision-making
- Flexibility through STIX2-based schema and connectors

---

## 🧠 Data Model & Architecture

OpenCTI leverages the **STIX2** format — a structured threat intelligence standard — enabling entities and their relationships to be traced clearly.

### 📐 Key Architectural Components:
- **GraphQL API**: Manages all data communication
- **Write Workers**: Handle asynchronous writing using RabbitMQ
- **Connectors**: Ingest, enrich, or export threat intel

| 🔌 **Connector Type** | 💡 Description | 🛠️ Examples |
|------------------------|----------------|-------------|
| External Input         | Pulls external data | CVE, MISP, TheHive |
| Stream                 | Subscribes to data streams | Tanium |
| Internal Enrichment    | Adds info to existing data | Enrichment services |
| Internal Import File   | Parses uploaded files | PDFs, STIX2 |
| Internal Export File   | Exports platform data | CSV, PDF, STIX2 |

---

## 📊 Dashboard

The dashboard provides a real-time snapshot of:
- Entity counts (reports, indicators, observables)
- Recent activity (24-hour stats)
- Visual summaries for quick navigation

---

## 🔍 Core Features by Tabs

### 🛡️ Activities & Knowledge
- **Activities**: Investigated incidents & reports
- **Knowledge**: Data on tools, actors, campaigns & victims

### 📚 Analysis
- View & annotate threat intel reports
- Example: MITRE’s Triton report integration

![image](https://github.com/user-attachments/assets/4caf3200-5efb-4787-9055-fd898e672166)

### 📆 Events
- Record incidents, link to indicators, threats, and observables

### 👁️ Observations
- Detection rules, artefacts, and technical indicators observed during threat hunts

![image](https://github.com/user-attachments/assets/f2ca0a7b-6a98-4c01-af21-99106403f959)


### ☠️ Threats
Classifies threat entities into:
- **Threat Actors**: Malicious individuals/groups
- **Intrusion Sets**: Tools + TTPs by known actors
- **Campaigns**: Coordinated attack efforts over time

### 🧰 Arsenal
Lists resources used in or related to attacks:
- **Malware**: e.g., 4H RAT
- **Attack Patterns**: Techniques like CLI execution
- **Courses of Action**: MITRE-mapped defenses
- **Tools**: Dual-use software like CMD
- **Vulnerabilities**: CVEs linked to threats

![image](https://github.com/user-attachments/assets/f0635f7b-9837-43fc-bbb6-1a6ee0aba04e)
![image](https://github.com/user-attachments/assets/06789647-e8d6-4ca3-80e0-1f082d11e94c)
![image](https://github.com/user-attachments/assets/f01dc6a0-59d5-4e90-9fe5-13bad6605177)


### 🌍 Entities
Groups info by:
- Sectors, Countries, Orgs, Individuals

---

## 🧭 Navigation Breakdown

When you explore a threat entity (e.g., **Cobalt Strike**), you'll interact with:

- **Overview**: General info, confidence score, external refs
- **Knowledge**: Attack vectors, reports, relations
- **Analysis**: Reports where it was detected
- **Indicators**: All related IOCs
- **Data**: Uploaded/generated threat files
- **History**: Change logs to entities & relationships

![image](https://github.com/user-attachments/assets/689d2425-4275-435c-ac7b-43ca93b9ea88)
![image](https://github.com/user-attachments/assets/7ba9fd79-f715-48d2-8174-2347ca6b3686)
![image](https://github.com/user-attachments/assets/18d94d61-6f8f-4585-ae30-31170de91836)
![image](https://github.com/user-attachments/assets/408852ca-6a62-4949-9d52-0ef3b9069db4)

---

## 📚 Want to Learn More?

Check out OpenCTI's [public documentation](https://docs.opencti.io/latest/), [GitHub](https://github.com/OpenCTI-Platform/opencti) repo, and available [connectors](https://docs.opencti.io/latest/deployment/connectors/).

---
References :
- [THM](https://tryhackme.com/room/opencti)
- [Answer's Explanation Guide](https://medium.com/@haircutfish/tryhackme-opencti-task-1-thru-task-5-7b9605694249)
