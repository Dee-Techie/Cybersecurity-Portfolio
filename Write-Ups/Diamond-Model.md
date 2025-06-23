# 💎 The Diamond Model of Intrusion Analysis

The **Diamond Model** is a cybersecurity framework designed to analyze and understand cyber intrusions. It focuses on the relationship between four core components involved in every cyber event:

- 🧑‍💻 **Adversary**
- 🎯 **Victim**
- 🧰 **Capability**
- 🧱 **Infrastructure**

Each cyber event connects these elements, enabling threat analysts to trace attacker behavior, identify patterns, and guide threat hunting and defense strategies.

---

## 👤 Adversary

An **adversary** (aka hacker, threat actor, or attacker) is the entity behind a cyberattack.

- 🔍 **Adversary Operator**: The person(s) conducting the intrusion.
- 🧑‍💼 **Adversary Customer**: The one who benefits—could be the same or different from the operator.
- 🎭 Attribution is difficult initially; use logs, signatures, and behavior to profile them.

---

## 🎯 Victim

The **victim** is the target of the adversary. Could be a person, system, or organization.

- 👥 **Victim Personae**: People or organizations being targeted.
- 🖥️ **Victim Assets**: IPs, domains, networks, systems, etc., being exploited.
- 📩 Example: Spear-phishing email clicked by a company employee.

---

## 🧰 Capability

**Capabilities** are tools, techniques, and procedures (TTPs) used in the attack.

- 🧠 Skills: Password guessing, malware development, phishing.
- 🛠️ **Capability Capacity**: Vulnerabilities each tool can exploit.
- 💣 **Adversary Arsenal**: Complete set of capabilities an adversary possesses or has access to.

---

## 🧱 Infrastructure

**Infrastructure** refers to the systems used to launch or support the attack.

- 🌐 IPs, domains, email accounts, USBs, etc.
- 🏢 **Type 1 Infrastructure**: Controlled by the adversary.
- 🔀 **Type 2 Infrastructure**: Controlled by intermediaries (compromised or unknowing).
- 🛰️ **Service Providers**: ISPs, domain registrars, etc., enabling adversary infrastructure.

---

## 🧩 Event Meta-Features (Optional but Valuable)

Additional context to enrich the analysis:

- 🕒 **Timestamp**: When the event occurred. Helps identify attack patterns.
- 🔄 **Phase** (per Cyber Kill Chain): 
  1. Reconnaissance
  2. Weaponization
  3. Delivery
  4. Exploitation
  5. Installation
  6. Command & Control
  7. Actions on Objective
- 📊 **Result**: Success, failure, unknown. Often mapped to CIA triad (Confidentiality, Integrity, Availability).
- 🔁 **Direction**: Flow of the event (e.g., Victim-to-Infrastructure, Infrastructure-to-Victim, etc.).
- 🧪 **Methodology**: Type of attack – phishing, DDoS, scan, etc.
- 🧾 **Resources**: Requirements like software, knowledge, access, funds, etc., needed to carry out the intrusion.

---

## 🌍 Social-Political Component

This component explains **why** the adversary is attacking:

- 💸 **Financial gain**
- 🕵️ **Espionage**
- 🎭 **Hacktivism**
- 🤝 **Community status** (acceptance in hacker circles)

🪙 **Example**: Victim systems are hijacked into a **botnet** used for **crypto mining**, benefiting the adversary financially while consuming the victim’s computing resources and bandwidth.

---

## 💻 Technology Component

This highlights the relationship between **Capability** and **Infrastructure**—explaining **how** the adversary executes their operations.

- 🔗 Describes how tools (capabilities) and platforms (infrastructure) interconnect.
- 🎯 **Example**: A **watering-hole attack**, where legitimate websites are compromised to lure victims.

---

🧠 **Summary**:  
The Diamond Model provides a structured approach to mapping the *who*, *what*, *how*, *where*, and *why* of cyberattacks. By analyzing adversary behavior through its core components and optional meta-features—including socio-political motives and technology usage—security teams can develop deeper insights and more effective defense strategies. 🔐
