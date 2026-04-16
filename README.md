# 🚀 Tier-0 Identity Security Lab

### Simulating Real-World Identity Attacks in a Hybrid Environment

---

## 🔍 Overview

This project demonstrates how identity compromise impacts a modern hybrid environment using Active Directory and cloud identity.

Instead of focusing on theory, this lab simulates real-world identity attack scenarios and analyzes how different identity types affect control, access, and detection.

> Identity is not just part of the security stack — it is the control plane.

---

## 🏗️ Architecture

![Resource Group Overview](screenshots/rg-overview.png)

*All lab resources are deployed within a single isolated Azure resource group to ensure clean segmentation and repeatability.*

---

![Virtual Network Configuration](screenshots/vnet-config.png)

*The virtual network defines the internal communication layer between the domain controller, sync server, and endpoints.*

---

![Virtual Machines](screenshots/vm-list.png)

*Core lab infrastructure including domain controller, hybrid sync server, and client endpoints.*

---

### Architecture Summary

* On-premises domain: `corp.local`
* Cloud identity: Microsoft Entra ID
* Hybrid sync via Entra Connect
* Monitoring via Microsoft Sentinel
* All resources deployed in Azure within a single VNet

---

## 🖥️ Active Directory (On-Prem)

![AD OU Structure](screenshots/ad-ou-structure.png)

*Organizational Units structured using a tiered model (Tier-0, Tier-1, Tier-2) to simulate enterprise identity segmentation.*

---

![AD Users](screenshots/ad-users.png)

*Standard users, service accounts, and administrative identities used for attack simulation.*

---

## ☁️ Microsoft Entra ID

![Entra Users](screenshots/entra-users.png)

*Hybrid identity synchronization showing on-prem users available in the cloud.*

---

![Roles and Administrators](screenshots/entra-roles.png)

*Privileged roles centrally managed in Entra ID, forming the control plane of the environment.*

---

![App Registrations](screenshots/app-registrations.png)

*Workload identities (service principals) created to simulate machine identity risk.*

---

## 🔐 Security Controls Implemented

![Conditional Access Policy](screenshots/conditional-access-policy.png)

*Conditional Access enforcing MFA for privileged roles.*

---

![PIM Activation](screenshots/pim-activation.png)

*Privileged Identity Management enforcing just-in-time administrative access.*

---

### Controls Configured

* Conditional Access (MFA for admin roles)
* Privileged Identity Management (PIM)
* Break-glass account exclusion
* Centralized logging with Sentinel

---

## 🔄 Hybrid Identity

![Entra Connect Sync](screenshots/entra-connect-sync.png)

*On-prem identities synchronized to cloud via Entra Connect, enabling hybrid authentication.*

---

## 📊 Monitoring & Detection

![Sentinel Overview](screenshots/sentinel-overview.png)

*Microsoft Sentinel used for centralized monitoring and investigation.*

---

![Sign-in Logs](screenshots/signin-logs.png)

*User authentication activity captured for visibility and analysis.*

---

![Audit Logs](screenshots/audit-logs.png)

*Administrative actions such as role assignments and policy changes.*

---

## ⚔️ Attack Scenarios Simulated

---

### 🔹 Scenario 1: Standard User Compromise

![Standard User Access](screenshots/std-user-limited.png)

*Standard users are restricted from administrative actions, demonstrating low blast radius.*

**Findings:**

* No privilege escalation
* Limited system visibility
* Minimal impact

---

### 🔹 Scenario 2: Tier-0 Identity Compromise

![Role Assignment](screenshots/tier0-role-assignment.png)

*Privileged account assigning Global Administrator role to another user.*

---

![Conditional Access Modification](screenshots/ca-modification.png)

*Security policies can be modified when Tier-0 access is compromised.*

---

![Persistent Admin Creation](screenshots/backdoor-admin.png)

*New privileged accounts can be created to maintain persistence.*

---

**Findings:**

* Full environment control achieved rapidly
* Security posture can be altered
* High blast radius across tenant

---

### 🔹 Scenario 3: Session Persistence

![Session Persistence](screenshots/session-persistence.png)

*Administrative actions continue without repeated authentication after initial login.*

**Findings:**

* MFA required only at login
* Session reuse reduces friction
* Increased risk post-authentication

---

### 🔹 Scenario 4: Workload Identity Risk

![Service Principal Permissions](screenshots/sp-permissions.png)

*Over-permissioned service principals demonstrate hidden attack surface risk.*

**Findings:**

* Low-privilege identities have minimal impact
* High-privilege identities can access broad directory data
* Machine identities are often under-monitored

---

## 📊 Key Takeaways

* Identity is the control plane of modern environments
* Tier-0 accounts can rapidly lead to full system control
* MFA alone is not sufficient without session-level protection
* Workload identities must be governed like user identities
* Detection relies heavily on identity-based telemetry

---

## 🛠️ Tools & Technologies

* Microsoft Entra ID
* Microsoft Sentinel
* Active Directory Domain Services
* Azure Virtual Machines
* Azure Networking

---

## 🔁 Identity Attack Flow

User Compromise → Privilege Escalation → Policy Modification → Persistence → Full Control

* Standard users are blocked early
* Tier-0 identities bypass most controls
* Sessions reduce authentication friction
* Workload identities introduce hidden risk

---

## 📌 Future Improvements

* Add automated attack simulation scripts
* Expand Sentinel detection queries (KQL)
* Include video walkthrough of lab
* Extend workload identity scenarios

---

## 💡 Final Thoughts

This project demonstrates how identity compromise behaves in a real hybrid environment.

Understanding identity behavior under attack conditions is critical for designing effective security controls.

---
