# 🔐 Administrator Access Audit Worksheet

A practical worksheet to track and audit administrative access across systems for accountability, least privilege, and compliance.

---

## Section 1: Admin Account Inventory

| # | Username | Full Name | Department | System(s) Accessed | Admin Level (Local/Domain/App) | Last Login | MFA Enabled | Unique ID | Notes |
|---|----------|-----------|------------|--------------------|-------------------------------|------------|-------------|------------|-------|
| 1 | admin    | Shared account | IT Sec   | VPN Appliance         | Local                        | 2024-12-11 | No          | No         | Needs review |
| 2 | j.smith  | John Smith    | IT Ops   | Windows Server 2019   | Domain Admin                 | 2025-07-25 | Yes         | Yes        | OK |
| 3 | root     | Shared UNIX   | DevOps   | Linux Web Server       | Local                        | 2025-07-23 | No          | No         | Must be disabled |
| 4 | a.khan   | Aisha Khan    | CloudSec | Azure, AWS             | Cloud Admin                  | 2025-07-24 | Yes         | Yes        | Review quarterly |

---

## Section 2: Access Controls Review

| Item | Control in Place | Notes |
|------|------------------|-------|
| Default admin accounts disabled | Yes / No | Should be disabled or renamed |
| Shared admin accounts eliminated | Yes / No | All accounts should be personal |
| MFA required for admin accounts | Yes / No | Highly recommended |
| Admin activity logged and monitored | Yes / No | SIEM integration advised |
| Admin privileges reviewed regularly | Yes / No | Quarterly review best |
| Passwords rotated regularly | Yes / No | 60–90 day policy ideal |
| Admin group membership reviewed | Yes / No | Validate membership in “Administrators”, “Domain Admins”, etc. |

---

## Section 3: Action Plan

| Issue Found | Risk Level | Action Required | Owner | Target Completion |
|-------------|------------|------------------|--------|-------------------|
| Shared account "admin" on VPN | High | Create individual user IDs and disable shared login | IT Sec Team | Aug 5, 2025 |
| No MFA on root access | High | Enable TOTP-based MFA via PAM solution | DevOps Lead | Aug 10, 2025 |
| Unknown account with admin access | Medium | Investigate ownership, revoke if unauthorized | IAM Admin | Aug 1, 2025 |

---

## 🧠 Pro Tips

- Prefer **Role-Based Access Control (RBAC)** with defined roles.
- Audit **privileged groups** regularly (e.g., Domain Admins, root, sudoers).
- Use **SIEM/SOAR tools** for real-time monitoring and alerting.
- Set up alerts for use of **shared or default admin accounts**.
