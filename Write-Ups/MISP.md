# 🧠 MISP – Malware Information Sharing Platform

## 🔍 What is MISP?

**[MISP](https://www.misp-project.org/)** is an **open-source threat intelligence platform** designed to facilitate the **collection, storage, sharing, and correlation** of indicators of compromise (IOCs) related to:

- 🦠 Malware
- 🎣 Phishing
- 💳 Financial fraud
- 🛡️ Cyber attacks

It supports closed, semi-private, and public sharing models and integrates with NIDS, SIEMs, and log analysis tools.

---

## 🚀 Key Use Cases

- 🔬 **Malware Reverse Engineering**  
- 🕵️ **Security Investigations**  
- 🧠 **Adversary & Threat Intelligence Analysis**  
- 👮 **Law Enforcement & Forensics**  
- 📊 **Risk & Threat Research**  
- 💰 **Fraud Detection & Prevention**  

---

## ⚙️ MISP Core Features

| Feature | Description |
|--------|-------------|
| 🧠 **IOC Database** | Stores technical and contextual data like IPs, hashes, domains |
| 🔗 **Automatic Correlation** | Identifies links between malware, incidents, or campaigns |
| 🔁 **Data Sharing** | Uses a decentralized sharing model |
| ⬇️ **Import/Export** | Integrates with tools like OpenIOC, NIDS, ThreatConnect |
| 🧬 **Event Graph** | Visualizes relationships between events, objects, attributes |
| 📡 **API Support** | Enables automation and integration with internal tools |

---

## 🧩 Key Terminologies

- **🗂️ Events**: Group of related indicators and metadata.
- **📍 Attributes**: Data points (e.g., IPs, hashes).
- **🔘 Objects**: Structured groupings of attributes.
- **🔁 Object References**: Relationships between objects.
- **🕓 Sightings**: Time-stamped observations of an attribute.
- **🏷️ Tags**: Labels applied for classification and filtering.
- **📚 Taxonomies**: Standardized tag libraries.
- **🌌 Galaxies**: Threat actor profiles or attack patterns.
- **🚨 Indicators**: Observable items that signal malicious activity.

---

## 🧪 Event Management Workflow

### 1️⃣ Event Creation
- Add description, date/time, and threat level.
- Choose a **distribution level**:
  - 🔒 Organisation only
  - 👥 Community only
  - 🌐 Connected Communities
  - 🕸️ All Communities
- Optionally assign **sharing groups**.
![image](https://github.com/user-attachments/assets/14d60b35-61af-4bcc-964d-32132eb0b00a)
![image](https://github.com/user-attachments/assets/1268010e-2a90-4430-927a-c9a3af818393)


### 2️⃣ Attributes & Attachments
- Add IOCs (e.g., Emotet IPs, hashes, URLs).
- Attach binaries (e.g., Cobalt Strike EXEs).
- Enable **IDS export** for detection systems.
- Use **batch import** for multiple indicators.

### 3️⃣ Event Publishing
- Events are published by the Org Admin.
- Shared across selected MISP community levels.

---

## 🌐 Feeds

MISP feeds provide **up-to-date threat data** that analysts can preview, import, and correlate with existing events. Admins control feed availability.

📦 Feeds help with:
- 🚚 Data ingestion
- 🔍 Threat correlation
- 📈 Event enrichment

---

## 🏷️ Taxonomies & Tagging

### 🧮 Taxonomies
Used to:
- Set classification tags (e.g., **TLP**, **confidence**)
- Standardize data labeling for tools like VirusTotal
- Enable structured exports

🔤 **Machine Tags Format**:
