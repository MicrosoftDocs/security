---
title: Microsoft Secure Future Initiative (SFI) overview
description: Get an overview of Microsoft's Secure Future Initiative (SFI), provides a series of best practices for key focus areas in cybersecurity. 
ms.date: 11/03/2025
ms.service: security
author: rayne-wiselman
ms.author: raynew
ms.subservice: zero-trust
ms.topic: conceptual
ms.collection:
  - highpri
  - zerotrust
  - sfi-zerotrust
---

# Secure Future Initiative overview

The Secure Future Initiative (SFI) initiative launched in November 2023 as a multiyear effort to increasingly secure the way in which Microsoft designs, builds, tests, and operates its products and services. For the first year or so after the launch, we shifted to security as a number one priority across Microsoft, provided security training, and dedicated extensive internal engineering resources to improve security and mitigate risk across Microsoft.

Over time, SFI efforts continue to evolve as a cross-company initiative in structured waves, keeping pace with shifts in the threat landscape. The ongoing evolution informs innovation, development, and best practices across the Microsoft security portfolio. It also provides Microsoft with ongoing opportunities to work with customers and with the broader security industry to strengthen our collective defenses.


## SFI progress reports

Microsoft produces periodic SFI progress reports with detailed information about initiative updates and progress. Reports cover areas such as new security capabilities, news from engineering pillars, mapping to the NIST Cybersecurity Framework, and implementation guidance aligned with Zero Trust principles.

- [Read the latest SFI blog](https://www.microsoft.com/security/blog/2025/11/10/securing-our-future-november-2025-progress-report-on-microsofts-secure-future-initiative/), and [review the SFI November 2025 report](https://www.microsoft.com/trust-center/security/secure-future-initiative/sfi-progress-report-november-2025).
- [SFI report - April 2025](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/sfi-april-2025-progress-report.pdf).
- [SFI report - September 2024](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/SFI_September_2024_progress_report.pdf).


## SFI architecture

SFI is designed and developed around a set of security principles that are adopted across Microsoft security culture and governance. These principles are applied to a set of focus areas (engineering pillars) by means of processes, standards, and continuous improvements.

:::image type="content" source="media/secure-future-initiative/secure-future-initiative-overview.png" alt-text="Diagram summarizing the secure future initiative (SFI)." border="true":::


## Security principles

SFI focuses on these principles.

:::image type="content" source="media/secure-future-initiative/secure-future-initiative-security-principles.png" alt-text="Diagram summarizing the security principles in secure future initiative (SFI)." border="true":::

We use these principles to:

- **Innovate**: Design and build security into platforms and services.
- **Implement**: Implement security innovations in Microsoft products and features with secure defaults and enforced standards.
- **Guide**: Provide customers with guidance and best practices to deploy, operate, and continuously improve security. 

The table summarizes some of the latest examples of innovation, implementation, and guidance. A full list is available in the [November report](https://www.microsoft.com/trust-center/security/secure-future-initiative/sfi-progress-report-november-2025).

**Platform** | **Updates** 
--- | --- 
**[Azure](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/security/sfi-nov-2025-progress-report.pdf#page=18)**  enforced additional secure defaults. | **Innovate**: [Azure Bastion Developer](/azure/bastion/quickstart-developer) expanded secure-by-default VM connectivity to 35 Azure regions, reducing attack surfaces. In Azure Local we [increased security settings enabled by default](/azure/azure-local/concepts/security-features). For [increased hardware trust](https://azure.microsoft.com/blog/protecting-azure-infrastructure-from-silicon-to-systems/), Microsoft-designed hardware-security module (HSM) tamper-resistant chips are integrated into the Azure infrastructure to keep encryption keys within secure hardware boundaries, eliminating latency and exposure risk.<br/><br/>**Implement**: Increased mandatory enforcement of strong multifactor authentication, emphasizing phishing-resistant authentication methods for all Azure service users, helping to neutralize stolen credentials at scale.<br/><br/>**Guidance**: [Microsoft Cloud Security Benchmark v2](/security/benchmark/azure/overview) released, with clear and comprehensive security best practices that can be enforced using Azure Policy.
**[Microsoft 365](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/security/sfi-nov-2025-progress-report.pdf#page=19)** provided increased AI control and data security. | **Innovate**:  Microsoft 365 introduced a [dedicated AI Admin role](/microsoft-365-copilot/extensibility/connector-admin-delegation) to secure Copilot management, move away from the Global Administrator role, and enforce least-privilege principles. [Centralized Copilot agent control and governance](/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps) in the Microsoft 365 Admin Center allows IT admins to easily manage, configure, and monitor agents.<br/><br/> **Implement**: Microsoft Purview's[secure-by-default adaptive labelling](/purview/deploymentmodels/depmod-securebydefault-intro) now classifies and secures more thatn 50 million items monthly.<br/><br/>**Guidance**: Guiding customers to use the AI admin roles for Copilot tasks, enforcing least-privilege. Use of [Microsoft Purview DSPM for AI](/purview/data-security-posture-management-learn-about) to monitor Copilot data usage, and detect misuse.
[Windows and Surface](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/security/) enhanced Zero Trust principles with expanded passkeys, automatic recovery capabilities, and memory-safe improvements. | **Innovate**: In Windows 11, Windows Hello and [passkeys integration](/windows/security/identity-protection/passkeys) offers a more secure, phishing-resistant passwordless sign-in experience. Surface is [advancing Windows security through the Open Device Partnership](https://blogs.windows.com/windowsexperience/2025/11/10/advancing-security-with-windows-and-surface-microsoft-sfi-report-nov-2025/), an open-source firmware initiative that replaces legacy firmware with a transparent, secure, and reusable platform.<br/><br/>**Implement**: Improvements in Hotpatch to [support ARM64 devices](https://techcommunity.microsoft.com/blog/windows-itpro-blog/hotpatching-now-available-for-64-bit-arm-architecture/4430949). Hotpatch is now enabled by default when creating a new Quality Update Policy in Autopatch, making it easier to maintain security and compliance with less disruption.<br/><br/>**Guidance**: Guiding customers to [enable Quick Machine Recovery on Windows 11](/windows/configuration/quick-machine-recovery) to automatically remediate boot failures and protect against boot-time attacks. Helping customers to [adopt passwordless sign-ins](/windows/security/book/identity-protection-passwordless-sign-in), integrating with password managers such as 1Password or Bitwarden.
[Microsoft security](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/security/sfi-nov-2025-progress-report.pdf#page=21) introduced data security posture management for AI, and shifted Microsoft Sentinel into a AI-first security platform. | **Innovate**: [Microsoft Sentinel data lake](/azure/sentinel/datalake/sentinel-lake-overview) enables a tenant-wide repository for collecting, storing, and managing large volumes of security-related data. More than 35 Microsoft and partner agents work to automate repetitive tasks and reduce manual workloads. Partner-developed agents are availble via the new [Microsoft Security Store](https://securitystore.microsoft.com/agents).<br/><br/>**Implement**: [Microsoft Entra entitlement management](/entra/id-governance/entitlement-management-overview) is being used to govern access across Microsoft engineering teams. In Microsoft Purview, [adaptive protection with data loss prevention policies](/purview/dlp-adaptive-protection-learn) blocks risky sharing activities based on user behavior across USB drives, web, email, and Team for proactive and consistent protection.<br/><br/>**Guidance**: Help customers to consolidate security data with [onboarding to Microsoft Sentinel data lake and Microsoft Sentinel graph](/azure/sentinel/datalake/sentinel-lake-onboarding).<br/><br/>Help customers to [enable Security Copilot agents](https://www.microsoft.com/security/blog/2025/11/18/agents-built-into-your-workflow-get-security-copilot-with-microsoft-365-e5/) for analysts to benefits fron AI capabilities during incident triage, reporting, and more.

## SFI pillars and Zero Trust

The SFI initiative focuses on six prioritized pillars. Multiple objectives aligned with each pillar. Each objective represents a significant effort to improve security and reduce risk for Microsoft and our customers in a specific pillar area.

 Microsoft discloses the progress of these objectives against principles and pillars in periodic SFI reports. Our goals and objectives might shift over time in response to dynamic security priorities and emerging threat landscapes.

The pillars clearly align with Microsoft's Zero Trust principles.

**Pillar** | **Zero Trust alignment**
--- | --- 
**1. Protect identities and secrets**<br/> Ensure that only verified and authorized identities can access resources.  | **Verify explicitly**: Enforce continuous, context-aware, passwordless authentication (Windows Hello, FIDO2 passkeys, certificate etc.).<br/><br/>**Use least privilege**: Reduce overprivileged identities and enforce privileged identity management/just-in-time access.<br/><br/>**Assume breach**: Rotate credentials rapidly and use short-lived tokens to reduce blast radius.
**2. Protect tenants and isolate systems**<br/> Minimize compromise blast radius by ensuring that tenants, environments, and systems are independently isolated and secured, with no implicit trust between them.  | **Verify explicitly**: Apply inter-tenant authentication and authorization with explicit approval and logging.<br/><br/>**Use least privilege**: Limit access between environments to approved paths only.<br/><br/>**Assume breach**: Use tenant isolation as a containment boundary.
**3. Protect networks**<br/> Limit lateral movement and unauthorized access by means of granular network segmentation and identity-aware connectivity.  | **Verify explicitly**: Shift from implicit network trust to policy-based, identity-verified connections.<br/><br/>**Use least privilege**: Enforce micro-segmentation and just-enough access for workloads and endpoints.<br/><br/>**Assume breach**: Treat every network zone as potentially hostile. Isolate high-value assets and enforce strict egress control.
**4. Protect engineering systems**<br/> Secure the entire software development lifecycle (SDLC) and delivery lifecycle by ensuring that code, build systems, and pipelines are tamper-resistant, auditable, and trustworthy.  | **Verify explicitly**: Authenticate every action in the SDLC, from code commits to builds, with traceable, signed identities.<br/>**Use least privilege**: Restrict developer, agent, and pipeline access based on role and build context.<br/><br/>**Assume breach**: Segregate build systems and enforce code signed and reproducible builds to prevent tampering.
**5. Monitor and detect cyberthreats**<br/> Quickly detect, correlate, and prioritize security threats across Microsoft systems by unifying telemetry and analytics.  | **Verify explicitly**: Use telemetry-driven, continuous validation of user, device, and workload behavior.<br/><br/>**Use least privilege**: Enforce adaptive access control with detection and dynamic conditional access policies.<br/><br/>**Assume breach**: Detect anomalies and behavior deviations on the premise that attackers might already have access to resources.
**6. Accelerate response and remediation**<br/> Minimize the impact and duration of security incidents with automation, coordinated response, and continuous learning..  | **Verify explicitly**: Continuously reassess trust in identities, devices, and systems after detection events.<br/><br/>**Use least privilege**: Automate token revocation, key rotation, and access removal during response.<br/><br/>**Assume breach**: Continuously feed incident learnings into system improvments for rapid containment and ongoing hardening.


## Protect identities and secrets

This pillar aims to strengthen trust in every identity and credential used across Microsoft systems by eliminating weaknesses in how accounts, tokens, and secrets are issued, stored, and used. It reduces the risk of unauthorized access by enforcing standards to harden the identity and secrets infrastructure, and to control user and application authentication and authorization. Microsoft objectives for this pillar are summarized in the following table.


**Objective** | **Details**
--- | ---
**1. Protect cryptographic signing keys** | Protect identity infrastructure signing and platform keys with rapid and automatic rotation of identity infrastructure keys, using hardware storage and protection.
**2. Adopt standard SDKs for identity** | Strengthen identity standards and drive standards adoption with the use of standard SDKs across applications, so that apps and services use a uniform, hardened library for validating tokens.
**3. Phishing-resistant MFA** | Ensure user accounts are protected with securely managed, phishing-resistant MFA.
**4. Safe secrets standard** | Shift away from long-lived secrets such as service account credentials to ensure that applications are protected with system-managed credentials such as managed identities.
**5. Stateful validation for identity tokens** | Ensure identity tokens are protected with stateful and duration validation.
**6. Fine-grained key partitioning** | Adopt more fine-grained partioning of identity signing keys and platform keys.
**7. Quantum-safe PKI systems** | Ensure identity and certificate PKI systems are ready for a post-quantum cryptography world.


## Protect tenants and isolate systems

The goal of this pillar is to contain potential threat blast radius by preventing lateral movement or privilege escalation. It ensures that tenant-level security boundaries are correctly configured, hardened, and isolated. Microsoft objectives for this pillar are summarized in the following table.

**Objective** | **Details**
--- | ---
**1. Remove legacy systems that risk security** |Maintain the security posture and commercial relationship of tenants by removing all unused, aged, or legacy systems.
**2. Secure all tenants and their resources** | Protect Microsoft, acquired, and employee-created tenants, commerce accounts, and tenant resources in accordance with security best practice baselines.
**3. Higher security for Entra ID apps** | Manage Microsoft Entra ID applications with a high and consistent security bar.
**4. Eliminate identity lateral movement** | Eliminate identity lateral movement pivots between tenants, environments, and clouds.
**5. Continuous least-privilege enforcement** | Ensure ontinuous least-privilege access enforcement for apps and users.
**6. Secure devices used for access** | Adopt fine-grained partitioning of identity signing keys and platform keys. Ensure that only secure, managed, healthy devices are granted access to Microsoft tenants.


## Protect networks

This pillar aims to limit adversary movement and unauthorized access across corporate networks. Networks are segmented and isolated with fine-grained network controls. Every connection is verified, controlled, and continuously monitored. Microsoft objectives for this pillar are summarized in the following table.

**Objective** | **Details**
--- | ---
**1. Inventory and security standards** | Secure Microsoft production networks and systems connected to networks with improved network isolation, monitoring, accurate inventory, and secure operations.
**2. Network isolation** | Apply identity-aware network isolation and microsegmentation to Microsoft production environments, creating additional layers of defense against attackers.
**3. Secure customer cloud networks** | Enable customers to easily secure their networks and configure network isolation of resources in the cloud.


## Protect engineering systems

This pillar ensures software lifecycle security across code, build systems, and pipelines. Every software artifact is verifiably authentic and securely produced in an isolated, monitored environment to ensure the integrity of the supply chain. Microsoft objectives for this pillar are summarized in the following table.

**Objective** | **Details**
--- | ---
**1. Complete software asset inventory** | Build and maintain an inventory of software assets used to deploy Microsoft products and services.
**2. Zero trust for source code access** | Ensure secure access to source code and engineering systems infrastructure with Zero Trust principles and least-privilege access policies.
**3. Secure code deployment** | Protect source code that deploys Micorsoft production environments with security best practices.
**4. Standardize secure development pipelines** | Apply network isolation and microsegmentation to Microsoft production environments. Secure development, build, test, and release environments with standardized, governed pipelines, and infrastructure isolation.
**5. Protect the software supply chain** | Secure the software supply chain to protect Microsoft production environments.

## Monitor and detect cyberthreats

This pillar aims to continuously monitor and rapidly detect security threats. Focus is on on proactive, intelligence-driven detection to surface attacker behavior early,  and enable rapid coordinated investigation across all business areas. Microsoft objectives for this pillar are summarized in the following table.


**Objective** | **Details**
--- | ---
**1. Complete production infrastructure inventory** | Maintain a current resource inventory across Microsoft production infrastructure and services.
**2. Security log retention standards** | Retain security logs for at least two years, and make six months of appropriate logs available.
**3. Centralize access to security logs** | Ensure security logs are accessible from a central data lake for efficient and effective investigation and threat hunting.
**4. Rapid anomaly detection and response** | Detect and respond quickly and automatically to anomalous access, behavior, and configurations across Microsoft production infrastructure and services.


## Accelerate response and remediation

The goal of this pillar is to quickly contain threats, restore trust, and improve resilience. It aims to minimize the impact and duration of security events and attacker dwell time in internal networks. Microsoft objectives for this pillar are summarized in the following table.

**Objective** | **Details**
--- | ---
**1. Accelerate vulnerability mitigation** | Reduce "Time to Mitigation" for high-severity cloud security vulnerabilities with accelerated response.
**2. Transparency of cloud vulnerabilities** | Increase transparency of mitigated cloud vulnerabilities with the adoption and release of Common Weakness Enumeration (CWE) and Common Platform Enumeration (CPE) industry standards. Release high severity Common Vulnerabilities and Exposures (CVEs) affecting the cloud.
**3. Enhance public messaging and engagement** | Improve the accuracy, effectiveness, transparency, and velocity of public messaging and customer engagement.


## Next steps

[Learn about](secure-future-initiative-guidance.md) adopting Microsoft SFI best practices.