# 🔐 IAM Policies: Secure Onboarding & De-Provisioning

Identity and Access Management (IAM) ensures the right people have the right access—at the right time. Secure onboarding and de-provisioning are essential for reducing insider threats and maintaining regulatory compliance.

---

## 👶 Secure Onboarding

| Action | Description |
|--------|-------------|
| **🔧 Provision Accounts** | Automatically create accounts in AD, Azure, Salesforce, etc., via HR triggers. |
| **📋 Role-Based Access (RBAC)** | Assign least privilege permissions based on role or department. |
| **🛡️ MFA/2FA** | Enforce multi-factor authentication for all new users. |
| **📜 Policy Acknowledgement** | Require new users to sign security policy & acceptable use agreements. |
| **🎓 Security Training** | Conduct phishing awareness and data protection onboarding sessions. |

---

## 👋 Secure Offboarding / De-Provisioning

| Action | Description |
|--------|-------------|
| **⛔ Disable Accounts Immediately** | Upon resignation/termination, disable access to all systems. |
| **🔐 Revoke Access Tokens** | Kill active sessions and revoke API tokens, VPN, email, etc. |
| **🧹 Remove Group Memberships** | Detach from AD groups, shared drives, Slack channels. |
| **📦 Recover Devices & Assets** | Collect laptops, phones, security tokens. |
| **📁 Archive Data** | Securely back up and transfer ownership of critical files. |
| **📝 Document Everything** | Log the offboarding steps for auditing and compliance. |

---

> Automate IAM with tools like Azure AD, Okta, JumpCloud, or AWS IAM to reduce risk and manual errors.
