# Active Directory Basics

**Platform:** TryHackMe  
**Path:** Cyber101  
**Module:** Windows and AD Fundamentals  
**Difficulty:** Easy  

---

## 🎯 Learning Objectives
- Centralized Identity & Access Management (IAM): Comprehend the core architecture of Active Directory (AD) and the foundational role of Domain Controllers (DCs) in managing domain resources.
- Least Privilege & Administrative Delegation: Analyze the configuration of delegating specific administrative tasks over Organizational Units (OUs) without exposing full Domain Admin rights.
- Directory Structure Optimization: Establish systematic object organization by separating servers and workstations into distinct OUs to apply targeted security baselines.
- Group Policy Deployment & Propagation: Evaluate the mechanism of Group Policy Objects (GPOs) and their delivery via the network `SYSVOL` share to enforce consistent enterprise baselines.
- Enterprise Authentication & Trust Models: Differentiate between secure Kerberos ticketing (TGT/TGS) and legacy NetNTLM protocols, while understanding multi-domain interaction through trust relationships.

---

## 📖 Key Concepts (in my own words)
- Domain Controller (DC): The central server running Active Directory Domain Services (AD DS) that handles all authentication, authorization, and directory management within a Windows domain.
- Organizational Unit (OU): Container objects within Active Directory used to partition users, groups, and computers logically, serving as the primary boundaries for applying GPOs and delegating administrative rights.
- Administrative Delegation: The process of granting granular, limited permissions to standard users or groups over a specific OU or object, eliminating the need for broad administrative privileges.
- SYSVOL Share: A mandatory, domain-wide network share residing on all Domain Controllers used to replicate GPO templates, scripts, and policy files to all domain-joined endpoints.
- Kerberos (TGT & TGS): The primary, ticket-based authentication protocol in modern Windows domains. Clients use a Ticket Granting Ticket (TGT) to verify identity and securely request a Ticket Granting Service (TGS) token to access enterprise resources.
- Trust Relationship: A secure, logical bridge configured between separate Windows domains that allows users from one domain namespace to be authenticated and authorized to access assets in another.

---

## 🛠️ Practical Application

### Step 1 - [Centralized Administration & Resource Governance]
Active Directory functions as the central source of truth for an enterprise network. Identities are classified clearly into standard user objects, security groups, and machine accounts (automatically designated with a `$` suffix, e.g., `TomPC$`). Complete dominion over these objects is held by the `Domain Admins` group.

**Practical Note:** From a SOC perspective, anomalous creation of machine accounts or modification of core domain groups are immediate high-fidelity indicators of potential privilege escalation or persistence mechanisms.

### Step 2 - [Enforcing Least Privilege through OU Delegation]
To limit the enterprise attack surface, full administrative accounts must be restricted. Through the Delegation of Control wizard, a standard user can be safely granted granular rights—such as permitting an account to perform password resets strictly within a specific departmental OU (e.g., Sales). This permits tasks to be carried out via administrative PowerShell commands without elevating the user's permanent directory-wide privileges.

Key Insight: Analysts monitoring directory logs should correlate Event ID 4724 (An attempt was made to reset an account's password) with the initiating security identifier to verify if a password reset fell within a user's authorized delegated scope or signaled malicious lateral movement.

### Step 3 - [Directory Hardening & GPO Baselines]
An unorganized Active Directory structure leads to a weak security posture. Restructuring a domain involves isolating endpoints by function into dedicated OUs (e.g., separating Workstations from Servers). This logical segmentation ensures that Group Policy Objects (GPOs), distributed via `SYSVOL`, apply strict, distinct security baselines according to the asset's specific risk profile.

Critical Knowledge: Applying identical security policies across endpoints and critical servers violates hardening principles. Separating assets into distinct OUs allows defensive teams to isolate critical tier-0 infrastructure and strictly restrict inbound/outbound communication.

### Step 4 - [Securing the Authentication Perimeter]
Modern Windows environments prioritize Kerberos authentication by default due to its robust ticket-based framework. Legacy NetNTLM challenge-response protocols are maintained exclusively for backwards compatibility. While NetNTLM prevents the plain-text transmission of credentials over the wire, it remains structurally vulnerable to credential relay attacks and offline cryptographic cracking.

Practical Note: Hardening the authentication perimeter requires threat hunters to locate and disable legacy NetNTLM configurations, forcing the entire domain to operate on Kerberos to effectively neutralize NTLM relay techniques.

---

## Why it matters
Mastering Active Directory core primitives is indispensable for developing a highly resilient corporate defense. Proper implementation of administrative delegation prevents credential exposure by avoiding the overuse of Domain Admin privileges. Furthermore, systematic directory structuring via functional OUs allows for the precise deployment of GPOs, establishing consistent security baselines that restrict lateral movement and unauthorized access across endpoints. Transitioning from legacy NetNTLM protocols to secure, ticket-based Kerberos architectures closes structural cryptographic gaps frequently exploited during corporate intrusions. For a SOC Analyst, clear visibility into AD architecture—from `SYSVOL` policy delivery to cross-domain trust relationships—is foundational to mapping attack paths, detecting credential abuse, and neutralizing enterprise-wide threats.
