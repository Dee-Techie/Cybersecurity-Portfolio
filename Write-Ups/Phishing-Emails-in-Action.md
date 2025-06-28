# 🧪 Phishing Emails in Action

This section explores real phishing email samples and the various techniques used to make them look legitimate. The more convincing the email, the higher the chance the victim will fall for the scam. ⚠️

---

## 📧 1. "Cancel your PayPal Order"

### Techniques Used:
- 📬 Spoofed email address
- 🔗 URL shortening
- 🎨 HTML impersonation (PayPal)

### Examples:
- Unusual recipient address (mismatch)
- Sender appears to be PayPal but originates from `sultanbogor.com`
- Urgent subject line prompts quick reaction
- Only interactive element: **Cancel the Order** button
- Uses shortened URLs to mask the true destination

![image](https://github.com/user-attachments/assets/85b3548f-a6b6-4507-885f-ac39c6857e2a)

➡️ **Tip:** Use online tools to preview shortened URLs before clicking.

---

## 📦 2. "Track Your Package"

### Techniques Used:
- 📬 Spoofed email address
- 👁️ [Pixel tracking](https://www.theverge.com/22288190/email-pixel-trackers-how-to-stop-images-automatic-download)
- 🔗 Link manipulation

### Examples:
- Pretends to be from a mail distribution center
- Subject includes a fake tracking number
- Embedded tracking pixel image (`Tracking.png`)
- Yahoo blocked image loading to prevent tracking
- Link points to a shady, suspicious domain
<img src="https://github.com/user-attachments/assets/570d90ce-4edc-427c-9b4c-aa1df3db023e" alt="Fake Email Sample 1" />
<img src="https://github.com/user-attachments/assets/1ae5f9f9-990d-48a7-bc9c-41d9207ec1e3" alt="Fake email 1 HTML" />

🔍 **Insight:** Tracking pixels can inform attackers that a user opened the email.

---

## 📄 3. "Select Your Email Provider to View Document"

### Techniques Used:
- ⏰ Urgency
- 🎨 HTML impersonation (Microsoft/Adobe)
- 🔗 Link manipulation
- 🛑 Credential harvesting
- ❌ Poor grammar/typos

### Examples:
- Urgent request to download a fax document before expiration
- Fake OneDrive and Adobe login pages
- URLs do not relate to Microsoft or Adobe
- Page titles and layout mimic real services, but contain spelling errors
- Fake login page captures credentials for criminal use
<img src="https://github.com/user-attachments/assets/8c4fcbfa-58eb-4c76-a025-4d8391fd6aa9" alt="Urgent Request Emails" width="600" />
<img src="https://github.com/user-attachments/assets/2beb4dcd-9305-477d-bcde-2ef6d7a37b40" alt="Fake Outlook page" width="600" />
<img src="https://github.com/user-attachments/assets/84e4aa03-fbf4-4aa5-ba4f-0da1b8098bd5" alt="Fake Adobe Page" width="400" />
<img src="https://github.com/user-attachments/assets/f18e101b-87fa-4e51-ba2f-b37967f83aea" alt="Credential Farming" width="390" />

⚠️ **Reminder:** Victims are **not** logging into a real service — credentials are sent to attacker-controlled servers.

🔎 **Further Analysis:**  
This email sample can be explored on Any.Run:  
👉 [View Full Analysis](https://app.any.run/tasks/12dcbc54-be0f-4250-b6c1-94d548816e5c/#)

---

> 🧠 Always examine headers, links, and urgency in suspicious emails. If it feels off, verify before interacting!
