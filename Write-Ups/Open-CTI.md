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

### 📆 Events
- Record incidents, link to indicators, threats, and observables

### 👁️ Observations
- Detection rules, artefacts, and technical indicators observed during threat hunts

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

---

## 📚 Want to Learn More?

Check out OpenCTI's [public documentation](https://docs.opencti.io/latest/), [GitHub](https://github.com/OpenCTI-Platform/opencti) repo, and available [connectors](https://docs.opencti.io/latest/deployment/connectors/).

---
References :
- [THM](https://tryhackme.com/room/opencti)
- [Answer's Explanation Guide](https://medium.com/@haircutfish/tryhackme-opencti-task-1-thru-task-5-7b9605694249)
