# 👋 Hi, I'm John Burns

### 🛡️ Security Engineer | Systems Automation | Cloud & Infrastructure Defense  
[Website](https://www.johnedwardburns.com) • [LinkedIn](https://www.linkedin.com/in/johnedwardburns/) • 📧 john.edward.burns.jr@gmail.com  

# Microsoft Entra ID Identity Security Baseline

This project documents a practical identity security baseline for Microsoft Entra ID (Azure AD) environments. It focuses on reducing account compromise risk, protecting privileged access, and establishing repeatable identity governance processes.

This baseline is designed for small-to-mid organizations using Microsoft 365 E3 with Security add-ons.

---

## Project Goals

The objective of this project is to:

- Reduce credential-based attacks (password spray, phishing)
- Eliminate legacy authentication exposure
- Protect privileged administrative accounts
- Improve visibility into identity-related activity
- Establish governance processes for access review and monitoring

---

# 1. Risk Assessment

## Common Identity Threats Addressed

### 1. Password Spray & Credential Stuffing
Attackers attempt to authenticate using commonly used passwords across many accounts.

**Mitigation:**
- Enforce MFA for all users
- Block legacy authentication protocols

---

### 2. Privileged Account Compromise
Global Admin and high-privilege accounts are high-value targets.

**Mitigation:**
- Require compliant device for admin access
- Restrict admin access by policy
- Implement break-glass accounts
- Monitor admin sign-ins

---

### 3. Legacy Authentication Exploitation
Legacy protocols (POP, IMAP, SMTP AUTH, etc.) bypass modern controls.

**Mitigation:**
- Block legacy authentication tenant-wide
- Audit service accounts for dependency

---

### 4. Privilege Creep
Users accumulate excessive access over time.

**Mitigation:**
- Quarterly access reviews
- Role assignment audit exports
- Documented exception tracking

---

# 2. Conditional Access Policy Design

## Policy 1 – Require MFA for All Users

**Scope**
- All users (excluding break-glass accounts)
- All cloud apps

**Control**
- Require MFA

**Objective**
Ensure stolen credentials alone cannot access resources.

---

## Policy 2 – Block Legacy Authentication

**Scope**
- All users
- All cloud apps

**Condition**
- Client apps → Legacy authentication clients

**Control**
- Block access

**Objective**
Eliminate common bypass paths for MFA.

---

## Policy 3 – Require Compliant Device for Admin Roles

**Scope**
- Directory roles (Global Admin, App Admin, etc.)

**Control**
- Require compliant device

**Objective**
Reduce risk of privileged access from unmanaged devices.

---

## Policy 4 – Break-Glass Account Strategy

Two emergency access accounts:
- Excluded from Conditional Access
- Strong password stored securely
- Monitored for any sign-in activity
- No daily usage permitted

---

# 3. Rollout Strategy

## Phase 1 – Pilot

- Create test group (5–10 users)
- Deploy MFA policy in report-only mode
- Monitor sign-in logs daily

## Phase 2 – Expand

- Expand to 25% of organization
- Validate helpdesk impact
- Communicate clearly to users

## Phase 3 – Enforce

- Enforce MFA for all users
- Block legacy authentication tenant-wide
- Deploy admin device restrictions

## Rollback Plan

- Switch policies to report-only
- Use break-glass accounts for emergency access
- Maintain documented exceptions

---

# 4. Monitoring & Operations

## Daily Review

- Entra ID sign-in logs
- Failed Conditional Access attempts
- Risky sign-ins
- Admin account activity

## Weekly Review

- Privileged role assignments
- MFA registration gaps
- Legacy auth attempt count

## Monthly Review

- Access review for admin roles
- Exception list review
- Audit log export

---

# 5. Identity Reporting Automation

PowerShell reporting scripts can be used to:

- Export privileged role assignments
- Identify inactive accounts
- Export MFA registration status
- Audit group membership

Automation reduces manual error and improves audit readiness.

---

# 6. Governance Process

Identity governance is not a one-time configuration.

This baseline includes:

- Documented role assignment policy
- Defined exception workflow
- Quarterly review cadence
- Admin account usage monitoring

---

# Architecture Overview

Users → Entra ID → Conditional Access → Microsoft 365 Apps  
                ↓  
        Logging & Monitoring  
                ↓  
        Governance & Review

---

# Lessons Learned

- Always deploy Conditional Access in report-only mode first.
- Identify service accounts before blocking legacy authentication.
- Break-glass accounts must be tested quarterly.
- Governance processes matter more than policy creation.

---

# Future Improvements

- Implement Privileged Identity Management (PIM)
- Integrate Microsoft Sentinel monitoring
- Add automated alerting for admin role changes
- Integrate Purview DLP with identity-based controls

---

# Author

John Burns Jr.  
Identity & Access Management Focus  
Microsoft Entra ID | Conditional Access | RBAC | Security Hardening



<!--## 📺 Popular YouTube Videos: -->


<!-- ## 🤳 Connect with me: -->
