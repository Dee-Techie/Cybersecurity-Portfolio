#  🫷 IDS & IPS - A brief overview (THM)

---

## 🔍 What is an IDS?

**Intrusion Detection System (IDS)** is a **passive** security solution that monitors network or system activities for malicious patterns and policy violations, raising alerts but **not taking direct action**.

### 🧭 Types of IDS:
- 🛰️ **NIDS (Network IDS)**: Monitors traffic across the whole network.
- 💻 **HIDS (Host IDS)**: Monitors traffic on a single device/host.

---

## 🛑 What is an IPS?

**Intrusion Prevention System (IPS)** is an **active** solution that **detects and blocks** malicious activities as they happen.

### 🔐 Types of IPS:
- 🌐 **NIPS (Network IPS)**: Monitors & stops threats across the network.
- 🧠 **NBA (Network Behavior Analysis)**: Learns normal patterns (baseline) to detect new threats.
- 📡 **WIPS (Wireless IPS)**: Secures wireless networks.
- 🖥️ **HIPS (Host IPS)**: Protects a specific device by terminating threats.

---

## 🧪 Detection & Prevention Techniques

| Technique        | Description |
|------------------|-------------|
| 🧬 **Signature-Based** | Matches known attack patterns. Great for detecting **known threats**. |
| 🧠 **Behaviour-Based** | Uses anomaly detection by comparing to baseline behaviour. Useful for **zero-day or unknown attacks**. |
| 📜 **Policy-Based** | Checks violations against defined security policies. |

---

## 🧾 Summary: IDS vs IPS

| Feature  | IDS 🕵️ | IPS 🚫 |
|----------|--------|--------|
| Passive/Active | Passive | Active |
| Action | Detects only | Detects & blocks |
| Intervention | Needs human input | Blocks autonomously |
| Use Case | Alerting & monitoring | Prevention & blocking |

---

## 🧠 Quick Answers Recap

| Question | Correct Answer |
|---------|----------------|
| Stop threats on a local machine | 🖥️ **HIPS** |
| Detect threats on a local network | 🌐 **NIDS** |
| Detect threats on a local machine | 💻 **HIDS** |
| Stop threats on a local network | 🔐 **NIPS** |
| Detects anomalies using baselining | 🧠 **NBA** |
| Snort is a... | 🚀 **Full-blown** NIPS |
| NBA training period is called... | 🧪 **Baselining** |

---

🎯 This foundation is critical before diving into Snort labs and packet analysis!
