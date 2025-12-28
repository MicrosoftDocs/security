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

## Latest updates

The table summarizes some of the latest examples of innovation, implementation, and guidance. A full list is available in the [November report](https://www.microsoft.com/trust-center/security/secure-future-initiative/sfi-progress-report-november-2025).

**Platform** | **Updates** 
--- | --- 
**[Azure](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/security/sfi-nov-2025-progress-report.pdf#page=18)**  enforced additional secure defaults. | **Innovate**: [Azure Bastion Developer](/azure/bastion/quickstart-developer) expanded secure-by-default VM connectivity to 35 Azure regions, reducing attack surfaces. In Azure Local we [increased security settings enabled by default](/azure/azure-local/concepts/security-features). For [increased hardware trust](https://azure.microsoft.com/blog/protecting-azure-infrastructure-from-silicon-to-systems/), Microsoft-designed hardware-security module (HSM) tamper-resistant chips are integrated into the Azure infrastructure to keep encryption keys within secure hardware boundaries, eliminating latency and exposure risk.<br/><br/>**Implement**: Increased mandatory enforcement of strong multifactor authentication, emphasizing phishing-resistant authentication methods for all Azure service users, helping to neutralize stolen credentials at scale.<br/><br/>**Guidance**: [Microsoft Cloud Security Benchmark v2](/security/benchmark/azure/overview) released, with clear and comprehensive security best practices that can be enforced using Azure Policy.
**[Microsoft 365](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/security/sfi-nov-2025-progress-report.pdf#page=19)** provided increased AI control and data security. | **Innovate**:  Microsoft 365 introduced a [dedicated AI Admin role](/microsoft-365-copilot/extensibility/connector-admin-delegation) to secure Copilot management, move away from the Global Administrator role, and enforce least-privilege principles. [Centralized Copilot agent control and governance](/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps) in the Microsoft 365 Admin Center allows IT admins to easily manage, configure, and monitor agents.<br/><br/> **Implement**: Microsoft Purview's[secure-by-default adaptive labelling](/purview/deploymentmodels/depmod-securebydefault-intro) now classifies and secures more thatn 50 million items monthly.<br/><br/>**Guidance**: Guiding customers to use the AI admin roles for Copilot tasks, enforcing least-privilege. Use of [Microsoft Purview DSPM for AI](/purview/data-security-posture-management-learn-about) to monitor Copilot data usage, and detect misuse.
[Windows and Surface](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/security/) enhanced Zero Trust principles with expanded passkeys, automatic recovery capabilities, and memory-safe improvements. | **Innovate**: In Windows 11, Windows Hello and [passkeys integration](/windows/security/identity-protection/passkeys) offers a more secure, phishing-resistant passwordless sign-in experience. Surface is [advancing Windows security through the Open Device Partnership](https://blogs.windows.com/windowsexperience/2025/11/10/advancing-security-with-windows-and-surface-microsoft-sfi-report-nov-2025/), an open-source firmware initiative that replaces legacy firmware with a transparent, secure, and reusable platform.<br/><br/>**Implement**: Improvements in Hotpatch to [support ARM64 devices](https://techcommunity.microsoft.com/blog/windows-itpro-blog/hotpatching-now-available-for-64-bit-arm-architecture/4430949). Hotpatch is now enabled by default when creating a new Quality Update Policy in Autopatch, making it easier to maintain security and compliance with less disruption.<br/><br/>**Guidance**: Guiding customers to [enable Quick Machine Recovery on Windows 11](/windows/configuration/quick-machine-recovery) to automatically remediate boot failures and protect against boot-time attacks. Helping customers to [adopt passwordless sign-ins](/windows/security/book/identity-protection-passwordless-sign-in), integrating with password managers such as 1Password or Bitwarden.
[Microsoft security](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/security/sfi-nov-2025-progress-report.pdf#page=21) introduced data security posture management for AI, and shifted Microsoft Sentinel into a AI-first security platform. | **Innovate**: [Microsoft Sentinel data lake](/azure/sentinel/datalake/sentinel-lake-overview) enables a tenant-wide repository for collecting, storing, and managing large volumes of security-related data. More than 35 Microsoft and partner agents work to automate repetitive tasks and reduce manual workloads. Partner-developed agents are availble via the new [Microsoft Security Store](https://securitystore.microsoft.com/agents).<br/><br/>**Implement**: [Microsoft Entra entitlement management](/entra/id-governance/entitlement-management-overview) is being used to govern access across Microsoft engineering teams. In Microsoft Purview, [adaptive protection with data loss prevention policies](/purview/dlp-adaptive-protection-learn) blocks risky sharing activities based on user behavior across USB drives, web, email, and Team for proactive and consistent protection.<br/><br/>**Guidance**: Help customers to consolidate security data with [onboarding to Microsoft Sentinel data lake and Microsoft Sentinel graph](/azure/sentinel/datalake/sentinel-lake-onboarding).<br/><br/>Help customers to [enable Security Copilot agents](https://www.microsoft.com/security/blog/2025/11/18/agents-built-into-your-workflow-get-security-copilot-with-microsoft-365-e5/) for analysts to benefits fron AI capabilities during incident triage, reporting, and more.

## SFI pillars, Zero Trust, NIST

The SFI initiative focuses on six prioritized engineering pillars. Multiple objectives are aligned with each pillar. Each objective represents a significant effort to improve security and reduce risk for Microsoft and our customers in a specific pillar area.

 Microsoft discloses the progress of these objectives against principles and pillars in our periodic SFI reports. Goals and objectives might shift over time in response to dynamic security priorities and emerging threat landscapes.

The pillars and objectives clearly align with Microsoft's Zero Trust principles and the [National Institute of Standards and Technology (NIST) Cybersecurity Framework](https://www.nist.gov/cyberframework). NIST functions referenced in the table are as follows:

- Govern (GV): Establish policies, procedures, and culture for managing cybersecurity risk, aligning it with overall business strategy and outcomes of the other NIST functions.
- Identify (ID): Understand assets, systems, data, and potential threats to build a strong organizational understanding of cyber risk.
- Protect (PR): Implement safeguards like access controls, data security, and training to ensure critical services can be delivered.
- Detect (DE): Develop and implement activities to identify the occurrence of cybersecurity events, such as continuous monitoring.
- Respond (RS): Take action regarding a detected incident, including analysis, containment, eradication, and communication.
- Recover (RC): Restore systems and operations post-incident, emphasizing planning, communication, and improvement to minimize disruption.


**Pillar** | **Zero Trust principle** | **NIST CSF Function**
--- | --- | --- 
**1. Protect identities and secrets**<br/> Ensure that only verified and authorized identities can access resources.  | **Verify explicitly**: Enforce continuous, context-aware, passwordless authentication (Windows Hello, FIDO2 passkeys, certificate etc.).<br/><br/>**Use least privilege**: Reduce overprivileged identities and enforce privileged identity management/just-in-time access.<br/><br/>**Assume breach**: Rotate credentials rapidly and use short-lived tokens to reduce blast radius. | **Protect (PR)**: Implement controls to secure credentials, secrets, and access.<br/><br/>**Detect (DE)**: Continuously monitor identity activities for anomalies.
**2. Protect tenants and isolate systems**<br/> Minimize compromise blast radius by ensuring that tenants, environments, and systems are independently isolated and secured, with no implicit trust between them.  | **Verify explicitly**: Apply inter-tenant authentication and authorization with explicit approval and logging.<br/><br/>**Use least privilege**: Limit access between environments to approved paths only.<br/><br/>**Assume breach**: Use tenant isolation as a containment boundary. | **Identify (ID)**: Discover tenant and production assets.<br/><br/>**Protect (PR)**: Apply isolation, seigmentation, and strong boundaries.<br/><br/>**Detect (DE)**: Look for isolation boundary violations or lateral movement.
**3. Protect networks**<br/> Limit lateral movement and unauthorized access by means of granular network segmentation and identity-aware connectivity.  | **Verify explicitly**: Shift from implicit network trust to policy-based, identity-verified connections.<br/><br/>**Use least privilege**: Enforce micro-segmentation and just-enough access for workloads and endpoints.<br/><br/>**Assume breach**: Treat every network zone as potentially hostile. Isolate high-value assets and enforce strict egress control. | **Identify (ID)**: Inventory and understand networking assets.<br/><br/>**Protect (PR)**: Apply network security controls (segementation, encryption etc).
**4. Protect engineering systems**<br/> Secure the entire software development lifecycle (SDLC) and delivery lifecycle by ensuring that code, build systems, and pipelines are tamper-resistant, auditable, and trustworthy.  | **Verify explicitly**: Authenticate every action in the SDLC, from code commits to builds, with traceable, signed identities.<br/>**Use least privilege**: Restrict developer, agent, and pipeline access based on role and build context.<br/><br/>**Assume breach**: Segregate build systems and enforce code signed and reproducible builds to prevent tampering. | **Identify (ID)**: Understand build/test/deployment systems and dependencies.<br/><br/>**Protect (PR)**: Secure software pipelines, development tooling and artifacts.<br/><br/>**Govern (GV)**: Apply engineering policies, standards, secure design.
**5. Monitor and detect threats**<br/> Quickly detect, correlate, and prioritize security threats across Microsoft systems by unifying telemetry and analytics.  | **Verify explicitly**: Use telemetry-driven, continuous validation of user, device, and workload behavior.<br/><br/>**Use least privilege**: Enforce adaptive access control with detection and dynamic conditional access policies.<br/><br/>**Assume breach**: Detect anomalies and behavior deviations on the premise that attackers might already have access to resources. | **Identify (ID)**: Maintain awareness of all monitored systems.<br/><br/>**Protect (PR)**: Ensure protective controls generate telemetry.<br/><br/>**Detect (DE)**: Analyze logs and alerts to identity threats.<br/><br/>**Respond (RS)**: Detect trigger response workflows.
**6. Accelerate response and remediation**<br/> Minimize the impact and duration of security incidents with automation, coordinated response, and continuous learning..  | **Verify explicitly**: Continuously reassess trust in identities, devices, and systems after detection events.<br/><br/>**Use least privilege**: Automate token revocation, key rotation, and access removal during response.<br/><br/>**Assume breach**: Continuously feed incident learnings into system improvments for rapid containment and ongoing hardening. | **Identify (ID)**: Understand scope and assets for response. Track changes and re-baseline post-incident.<br/><br/>**Recover (RC)**: Restore secure operations after incidents. Remediate vulnerabilities and ensure resilience.<br/><br/>**Detect (DE)**: Analyze logs and alerts to identity threats.<br/><br/>**Respond (RS)**: Detect trigger response workflows.br/><br/>**Govern (GV)**: Apply lessons in governance and standards.


## Pillar 1: Protect identities and secrets

This pillar aims to strengthen trust in every identity and credential used across Microsoft systems by eliminating weaknesses in how accounts, tokens, and secrets are issued, stored, and used. It reduces the risk of unauthorized access by enforcing standards to harden the identity and secrets infrastructure, and to control user and application authentication and authorization. 

Microsoft objectives for this pillar are summarized in the following table. Progress is shown for each objective, as well as the mapping between the objective, Zero Trust principles, and [NIST CSF functions and categories](https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf).

**Objective** | **Progress** | **Zero Trust** | **NIST mapping**
--- | --- | --- | ---
**1. Protect cryptographic signing keys**<br/><br/>Protect identity infrastructure signing and platform keys with rapid and automatic rotation of identity infrastructure keys, using hardware storage and protection. | Migrated ~95% of Entra ID signing VMs to Azure Confidential Compute, improving key protection. | **Verify explicitly**: Protect identity signing assets. Strong attestation of keys built into workflow.<br/><br/>**Assume breach**: Protect keys as if compromise can occur, using hardware‑assisted isolation. | **Protect-Identity Management, Authentication, and Access Control (PR.AA-04)**: Keys are only accessible to verified identities.<br/><br/>**Protect:Platform Security (PR.PS-01)**: Protect cryptographic assets on hardware/software platforms.
**2. Adopt standard SDKs for identity**<br/><br/>Strengthen identity standards and drive standards adoption with the use of standard SDKs across applications, so that apps and services use a uniform, hardened library for validating tokens. | ~94.3% of Entra ID token validation migrated to standard SDKs, reducing risk from custom code. |  **Verify explicitly**: Standard validated libraries reduce variability and risk. Use consistent validation.<br/><br/>**Assume breach**: Reduces attack surface from custom implementations. | **PR.AA-01**: Define rules for SDK access.<br/><br/>**PR.AA-02**: Manage accounts used in SDK validation.<br/><br/>**PR.AA-03**: Enforce token validation through standardized SDK.
**3. Enforce phishing-resistant MFA**<br/><br/>Ensure user accounts are protected with securely manEnforcaged, phishing-resistant MFA. | 99.6% MFA adoption achieved across users/devices, ensuring strong authentication. | **Verify explicitly**: Strong authentication techniques verify user identity every access attempt.<br/><br/>**Use least privilege**: MFA strengthens least‑privilege enforcement by reducing unauthorized access. | **PR.AA-01**: Policies require MFA.<br/><br/>**PR.AA-03**: MFA enforced on all accounts.
**4. Safe secrets standard**<br/><br/> Shift away from long-lived secrets such as service account credentials to ensure that applications are protected with system-managed credentials such as managed identities. | Continuous remediation of secrets; high coverage (~99.5%) of detected sensitive data in code or config. | **Use least privilege**: Restrict secret access. Avoid hard‑coded or persistent credentials.<br/><br/>**Assume breach**: Treat every secret as potentially compromised unless strongly guarded. | **PR.AA-04**: Only verified identities can access secrets.<br/><br/>**Protect:Data Security (PR.DS-01)**: Secrets are encrypted and protected.<br/><br/>**PR.PS-01**: Secret management systems implemented are secure platforms to protect sensitive data.
**5. Stateful validation for identity tokens**<br/><br/>Ensure identity tokens are protected with stateful and duration validation.| Standardized validation implemented; high coverage for critical tokens. | **Verify explicitly**: Fully validate identity tokens at every enforcement point.<br/><br/>**Assume breach**: Ensure invalid or malformed tokens are rejected. | **PR.AA-03**: Token validation enforced in access decisions.<br/><br/>**Detect:Adverse Event Analysis (DE.AE-02)**: Anomalous activity detection. Detect unusual token usage.<br/><br/> **DE-AE-03**: Uauthorized activity detection. Monitor for misuse or compromised tokens.
**6. Fine-grained key partitioning**<br/><br/>Adopt more fine-grained partioning of identity signing keys and platform keys. | Partitioning implemented for many key types; scope limited for sensitive keys. | **Use least privilege**: Partitioning limits privilege scopes for key usage.<br/><br/>**Assume breach**: ELimits impact if key segment is compromised. | **PR.AA-04**: Identity proofing. Verify identities accessing each key partition.<br/><br/>**PR.AA-05**: Separation of duties. Isolate key operations to enforce limited privileges.
**7. Quantum-safe PKI systems**<br/><br/>Ensure identity and certificate PKI systems are ready for a post-quantum cryptography world. | Early planning; some post-quantum PKI pilots in progress. | **Verify explicitly**: Use post‑quantum cryptography for identity assertions.<br/><br/>**Assume breach**: Anticipate future threats; prepare for stronger resistance. | **PR.AA-04**: Identity proofing. Only authorized identities management PKI operations.


## Pillar 2: Protect tenants and isolate systems

The goal of this pillar is to contain potential threat blast radius by preventing lateral movement or privilege escalation. It ensures that tenant-level security boundaries are correctly configured, hardened, and isolated. Microsoft objectives for this pillar are summarized in the following table.

**Objective** | **Progress** | **Zero Trust** | **NIST mapping**
--- | --- | --- | ---
**1. Remove legacy systems that risk security**<br/><br/> Maintain the security posture and commercial relationship of tenants by removing all unused, aged, or legacy systems. | Microsoft retired ADFS in productivity and migrated ~98% ASM‑managed assets to ARM; retired 560,000 unused tenants & 83,000 apps, reducing attack surface and eliminating unmanaged identity lifecycles. | **Verify explicitly**: All identity and resource systems are authenticated and validated through modern control planes.<br/><br/>**Use least privilege**: Eliminates old systems without modern, fine‑grained controls. <br/><br/>**Assume breach**: Removes legacy trust paths and minimizes blast radius. | **Identify:Asset Management (ID.AM-02)**: Inventory of organizational resources. Track tenant and resource onboarding and disused assets.<br/><br/>**ID.AM-08**: Resource lifecycle management. Track, manage, and decommission tenants/apps safely. <br/><br/>**PR.PS-01**: Platform Security. Secure platforms and services on a modern foundation.
**2. Secure all tenants and their resources**<br/><br/> Protect Microsoft, acquired, and employee-created tenants, commerce accounts, and tenant resources in accordance with security best practice baselines. | Tenant segmentation strengthened by removing test/unused tenants; auxiliary tenant fleet created to support controlled productivity environments. | **Verify explicitly**: Authenticate all tenant‑to‑tenant interactions.<br/><br/>**Use least privilege**: Policies and segmentation limit permissions across environments. <br/><br/>**Assume breach**: Tenant boundaries assume potential compromise and are designed to contain lateral movement. | **ID.AM-08**: Resource lifecycle management. Maintain defined tenant resource lifecycles. <br/><br/>**PR.AA-01**: Access control policy. Define tenant access policies.<br/><br/>**PR.AA-05**: Separation of duties. Limit administrative privilege across tenants.<br/><br/>**Privacy-Infrastructure resilience (PR.IR-01)**: Improve platform resilience against misuse or misconfiguration. 
**3. Higher security for Entra ID apps**<br/><br/>Manage Microsoft Entra ID applications with a high and consistent security bar. | Tenant segmentation strengthened by removing test/unused tenants; auxiliary tenant fleet created to support controlled productivity environments. | **Verify explicitly**: Enforce strong authentication and app vetting.<br/><br/>**Use least privilege**: App permissions restricted to minimal necessary rights. <br/><br/>**Assume breach**: App access designed with containment and monitoring. | **PR.AA-01**: Access control policy. Govern app access consistently.<br/><br/>**PR.AA-03**: Access enforcement. Enforce app authentication controls.
**4. Eliminate identity lateral movement**<br/><br/>Eliminate identity lateral movement pivots between tenants, environments, and clouds. | Improved cross‑boundary secret isolation from ~94% (April) to ~98%, closing credential paths that allowed token re‑creation across tenants. | **Verify explicitly**: Validate every token and trust boundary crossing.<br/><br/>**Use least privilege**: imit identity reuse and privilege escalation across tenants. <br/><br/>**Assume breach**: Design boundaries to contain identity misuse. | **PR.AA-03**: Access enforcement. Block unauthorized lateral authentication.
**5. Continuous least-privilege enforcement**<br/><br/>Ensure continuous least-privilege access enforcement for apps and users. | Automated least‑privilege enforcement and policy guardrails applied across tenant and identity lifecycles. | **Verify explicitly**: Policies ensure least privilege decisions are verified at every access.<br/><br/>**Use least privilege**: Core outcome of this objective — enforce only necessary permissions. | **PR.AA-03**: Access enforcement. Enforce minimal privileges.
**6. Secure devices used for access**<br/><br/> Adopt fine-grained partitioning of identity signing keys and platform keys. Ensure that only secure, managed, healthy devices are granted access to Microsoft tenants.  | Devices accessing tenants are hardened with policy‑enforced secure configurations (e.g., secure endpoints and conditional access). | **Verify explicitly**: ach device identity is validated and continuously assessed.<br/><br/>**Use least privilege**: Device posture gating ensures minimal risk access. | **PR.PS-01**: Platform Security. Devices and endpoints hardened per secure baseline to reduce risk.<br/><br/>**PR.IR‑01**: Infrastructure Resilience. Endpoints resilient to compromise and aligned to service baselines


## Pillar 3: Protect networks

This pillar aims to limit adversary movement and unauthorized access across corporate networks. Networks are segmented and isolated with fine-grained network controls. Every connection is verified, controlled, and continuously monitored. Microsoft objectives for this pillar are summarized in the following table.

**Objective** | **Progress** | **Zero Trust** | **NIST mapping**
--- | --- | --- | ---
**1. Complete network device inventory and asset lifecycle management**<br/><br/>Secure Microsoft production networks and systems connected to networks with improved network isolation, monitoring, accurate inventory, and secure operations. | Enabled comprehensive tracking of network devices and their lifecycle, improving visibility into network attack surface. | **Verify explicitly**: Know what devices are present and who/what they connect to.<br/><br/>**Assume breach**: Full inventory supports detection and containment of breaches. | **ID.AM-02**: Inventory of organizational resources. All network devices are inventoried and tracked. 
**2. Strengthen security through enhanced network isolation and controls**<br/><br/>Apply identity-aware network isolation and microsegmentation to Microsoft production environments, creating additional layers of defense against attackers. | Network segmentation and protective controls have been improved to reduce implicit trust and restrict network paths. | **Verify explicitly**: Authenticate and authorize network flows before allowing communication. <br/><br/>**Use least privileged access**: Restrict lateral movement and limit network access rights.<br/><br/>**Assume breach**: Assume attackers may be in the network; isolate segments for containment. | **PR-PS-02**: Platform Security. Secure network platform configurations help enforce isolation and protect network boundaries. (Platform security covers network protection technologies such as segmentation firewalls, ACLs, and infrastructure controls.)
**3. Accelerate adoption of Network Security Perimeter (NSP)**<br/><br/>Place entries resources under modern perimeter enforcement and segmentation to ensure network traffic is validated and only allowed where necessary to reduce the risk of lateral movement and unauthorized access. | Over 1.1M resources placed in NSP learning mode with ~500k resources enforced, accelerating modern protective controls adoption.  | **Verify explicitly**: NSP enforces strong validation of traffic entering protected segments. <br/><br/>**Use least privileged access**: Only necessary traffic is allowed to traverse network boundaries.<br/><br/>**Assume breach**: Perimeter enforcement assumes threat presence and restricts spread. | **PR-PS-01**: Platform Security. NSP technologies and perimetral controls are part of secure platform defenses. (These technologies enforce network segmentation and traffic policies to protect infrastructure.)
**4. Improve network acccess controls and protective technologies**<br/><br/>Strengthen network defenses with modern firewalling, segmentation policies, and platform-level enforcement, ensuring that only authorized traffic can flow and that potential breaches are contained. | Protective technologies such as next‑gen firewalling and segmentation policies have been expanded to cover broad network estates. | **Verify explicitly**: Access control policies verify traffic flows and endpoints. <br/><br/>**Use least privileged access**: Policy enforcement limits access to minimal required paths.<br/><br/>**Assume breach**: Contain attacks via strong network controls and visibility. | **PR.AA-03**: Access enforcement. Enforce network access decisions.br/><br/> **PR.PS-01**: Platform Security. Infrastructure (firewalls, NSGs, segmentation) enforced at platform level.


## Pillar 4 - Protect engineering systems

This pillar ensures software lifecycle security across code, build systems, and pipelines. Every software artifact is verifiably authentic and securely produced in an isolated, monitored environment to ensure the integrity of the supply chain. Microsoft objectives for this pillar are summarized in the following table.

**Objective** | **Progress** | **Zero Trust** | **NIST mapping**
--- | --- | --- | ---
**1. Complete software asset inventor**<br/><br/>Build and maintain an inventory of software assets used to deploy Microsoft products and services. | Enventory spans all Azure DevOps repositories and pipelines with full metadata. “StartRight” tooling ensures ~80% of assets are inventoried at creation and “StayRight” captures the rest within 24 hours, enabling rapid incident response and policy enforcement. | **Verify explicitly**:Know every engineering asset and associate it with identity/context.<br/><br/>**Assume breach**: Full visibility supports rapid detection and containment. | **ID.AM-02**: Inventory of organizational resources. All engineering systems are inventoried. (Supports accurate asset visibility and risk management.) 
**2. Zero trust for source code access** <br/><br/>Ensure secure access to source code and engineering systems infrastructure with Zero Trust principles and least-privilege access policies. | Standing admin access reduced; just‑in‑time elevation required. Azure DevOps OAuth apps use Microsoft Entra authentication with conditional access and nearly all prod code changes include proof‑of‑presence checks. | **Verify explicitly**: Enforce strong authentication and conditional access for source code access.<br/><br/>**Use least privilege access**: Minimize standing privileges and use just‑in‑time elevation.<br/><br/>**Assume breach**: Assume credential risk and enforce strict access guards. | **PR.AA-01**: Access control policy. Policies govern source code access.<br/><br/>**PR.AA-02**: Account management. Manage engineering accounts securely. <br/><br/>**PR.AA-03**: Access enforcement. Enforce source code access rules. <br/><br/>**PR.AA-04**: Identity proofing. Verify identities accessing code. <br/><br/>**PR.AA-05**: Separation of duties. Reduce conflicting privileges.<br/><br/>**PR.AA-06**: Credential protection. Protect credentials used in engineering access. <br/><br/>**PR.DS-01**: Data‑at‑rest protection. Source code and related data secured. <br/><br/>**PR.DS-02**: Data‑in‑transit protection. Secure transmission of code and artifacts.<br/><br/>**PR.DS-10**: Data security assurance. Controls ensure data integrity and protection throughout engineering systems.
**3. Secure code deployment**<br/><br/>Protect source code that deploys Micorsoft production environments with security best practices. | Code signing access is almost entirely locked to production identities. Repositories enforce branch policies with minimum approver counts and expanded secrets detection analytics strengthen compliance and durability. | **Verify explicitly**: Authenticate all signing and deployment actions.<br/><br/>**Assume breach**: Design deployment controls assuming system compromise.| **PR.AA-04**: Identity proofing. Ensure that deployment and signing actions are by verified identities.<br/><br/> **PR.PR-06**: Platform Security. Secure platforms (build & deploy systems) enforce protective controls.
**4.Standardize secure development pipelines**<br/><br/>Apply network isolation and microsegmentation to Microsoft production environments. Secure development, build, test, and release environments with standardized, governed pipelines, and infrastructure isolation.| Nearly all production build pipelines and 94% of release pipelines use centrally governed templates. Increased network isolation (~89% complete) blocks direct access to public registries and flags unvetted dependencies.| **Verify explicitly**: Validate build and release pipelines and ensure compliance with security guardrails.<br/><br/> **Use least privilege**: Limit access within pipelines and enforce standardized workflows that reduce unnecessary rights.<br/><br/> **Assume breach**: Pipeline isolation and governance contain potential compromise.| **PR.DS-01**: Data‑at‑rest protection: Protect pipeline artifacts and metadata.<br/><br/>**PR.DS-02**: Data‑in‑transit protection: Secure communication between pipeline stages.<br/><br/>**PR.DS-10**: Data security assurance: Pipeline controls ensure consistent data protection.<br/><br/> **PR.IR-01**: Infrastructure resilience: Pipeline systems resilient to attacks and misconfigurations.<br/><br/>**PR.PS-06**: Platform Security: Secure build/run platforms enforce isolation and protection.
**5. Protect the software supply chain**<br/><br/>Secure the software supply chain to protect Microsoft production environments.| Supply chain protections are maturing: internal artifact feeds broadly adopted and component governance runs by default. AI agents now remediate open‑source vulnerabilities asynchronously, reducing detection‑to‑resolution latency. | **Use least privilege**: Limit access and usage of third‑party components.<br/><br/> **Assume breach**: Protect supply chain and assume component compromise risk.| **Govern-Cybersecurity Supply Chain Risk Management (GV.SC-01)**: Supply chain governance: Source component selection and oversight.<br/><br/>**GV.SC-02**: Supplier risk assessment: Evaluate risks across software supply partners.<br/><br/>**GV.SC-03**: Contractual security requirements: Enforce vendor security terms.<br/><br/> **GV.SC-04**: Shared responsibility models: Define roles for secure engineering.<br/><br/>**GV.SC-07**: Transparency and reporting: Share security findings and metrics with stakeholders.<br/><br/>**GVS.C-09**: Continuous supply chain monitoring: Monitor third‑party components and flows.<br/><br/>**Identity-Risk Assessment (ID.RA-10)**: Risk assessment: Ongoing risk analysis across the supply chain.<br/><br/>**.PR.PS-06**: Platform Security: Secure build/run platforms enforce isolation and protection.

## Pillar 5: Monitor and detect threats

This pillar aims to continuously monitor and rapidly detect security threats. Focus is on on proactive, intelligence-driven detection to surface attacker behavior early,  and enable rapid coordinated investigation across all business areas. Microsoft objectives for this pillar are summarized in the following table.

**Objective** | **Progress** | **Zero Trust** | **NIST mapping**
--- | --- | --- | ---
**1. Centralize telemetry and infrastructure tracking**<br/><br/>Maintain a current resource inventory across Microsoft production infrastructure and services.| ~98% of production infrastructure is centrally tracked, improving visibility into system and security states and enabling long‑term trend analysis and investigation. | **Verify explicitly**:Ensure logging and telemetry originate from authenticated, trusted sources.<br/><br/>**Assume breach**: Centralized logs support detection even when attackers evade initial controls.| **ID.AM-02**: Inventory of organizational resources: Maintain a complete view of monitored assets.<br/><br/>** **Detect:Continuous Monitoring (DE-AM-02)**: Monitoring processes. Centralized telemetry supports continuous observation.

**2. Retain logs for forensic analysis and trending**<br/><br/>Retain security logs for at least two years, and make six months of appropriate logs available.| Logs are retained for 2 years, supporting deeper investigation and detection accuracy across incident timelines. | **Verify explicitly**: Retained logs allow verification of past events and patterns.<br/><br/>**Assume breach**: Long retention ensures detection windows cover advanced stealth techniques.| **DE.CM-02**: Inventory of organizational resources: Maintain a complete view of monitored assets.<br/><br/>** **DE/DP-01






























)**: Monitoring processes. Centralized telemetry supports continuous observation.

**1. Complete production infrastructure inventory** | 
**2. Security log retention standards** | 
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