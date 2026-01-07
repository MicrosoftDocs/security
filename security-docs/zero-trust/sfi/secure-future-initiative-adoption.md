---
title: Adopting Microsoft Secure Future Initiative (SFI) best practices
description: Learn about adopting Microsoft's Secure Future Initiative (SFI) best practice patterns. 
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

# Adopt Secure Future Initiative (SFI) best practices

Microsoft's SFI initiative launched as a multiyear effort to further secure the way that  Microsoft designs, builds, tests, and operates its infrastructure, products, and services.

This article shows how your organization might consider and adopt some of these SFI best practices.

> [!NOTE]
> - We're continuously working on content that details each best practice pattern within pillars. Links to these best practices are included where available and we're planning to publish more over time.
> - Before you start, [get an overview of SFI](secure-future-initiative-overview.md).

## Protect identities and secrets

Initiatives under this pillar aim to reduce the risk of unauthorized access by implementing and enforcing standards to control user/app authentication and authorization, and to harden the identity and secrets infrastructure. The Microsoft SFI initiative work focuses on:

- Passwordless, phishing-resistant multifactor authentication (MFA) (FIDO2 passkeys, certificate-based auth) for all users.
- Deprecation of passwords, SMS OTP etc.
- Replacement of static credentials with managed identities and Microsoft Entra Workload ID.
- Storage of secrets in Azure Key Vault, key protection with Managed Hardware Security Module (HSM) with role-based access control (RBAC), network isolation, and access logs.
- Automated key rotation and HSM-backed token signing.
- Adoption of standard SDKs with supported identity libraries (MSAL, Microsoft.Identity.Web), and avoiding custom Json Web Token (JWT) validation.
- Periodic scanning of code pipelines, and repos for leaked secrets.

### Adopt best practices

Key adoption best practices for identity and secrets protection are summarized in the following table.

**Best practice** | **Zero Trust** | **Adoption considerations** | **Detailed guidance**
--- | --- | --- | ---
Implement and enforce phishing-resistant MFA across privileged accounts and admins.<br/><br/>Deprecate legacy MFA methods that aren't phishing-resistant or sufficiently secure.<br/><br/>Eliminate static credentials  and enable dynamic short-lived tokens for workloads.<br/><br/>Centralize credentials in in centralized, monitored vaults.<br/><br/>Automate secret rotation and signing key lifecycle.<br/><br/> Use standardized, Microsoft-supported SDKs, avoid custom JwT identification.<br/><br/>Continuously scan, detect, and remediate credential vulnerabilities. | <br/><br/><br/><br/>**Verify explicitly**: Continuous, adaptive authentication based on risk and context.<br/><br/> **Use least privilege**: Use Just-In-Time/Just-Enough Access controls.<br/><br/>**Assume breach**: Credential misuse triggers automatic revocation and access reviews. | <br/><br/><br/><br/>Might require modernization of older applications to support managed identities.<br/><br/> User enablement and hardware are required for some MFA methods.<br/><br/> Operational overhead for auditing and rotation policies. | <br/><br/><br/><br/>[Adopt phishing-resistant MFA](/security/zero-trust/sfi/phishing-resistant-mfa).<br/><br/>[Adopt standard SDKs for identity](/security/zero-trust/sfi/adopt-standard-sdk-identity).


## Protect tenants and isolate systems

Initiatives under this pillar aim to independently secure and isolate tenants and environments to eliminate implicit trust and reduce blast radius. The Microsoft SFI initiative focuses on:

- Strong tenant isolation and configuration governance across production tenants.
- Restriction of cross-tenant access and privileged delegation.
- Implementation of privileged access workstations (PAWs) and isolated admin tools.
- Application of tenant baselines and resource isolation.
- Segmentation of management and customer data paths, with no implicit trust between engineering, customer, and operational tenants.


### Adopt best practices

Key adoption best practices for identity and secrets protection are summarized in the following table.

**Best practice** | **Zero Trust** | **Adoption considerations** | **Detailed guidance**
--- | --- | --- | ---
Create isolated environments for production, test, and partner tenants.<br/><br/> Limit or eliminate cross-tenant roles, and enforce conditional access.<br/><br/> Require hardening devices for administration.<br/><br/>Define and enforce tenant baselines and resource isolation using consistent policies and controls.<br/><br/>Enforce strict data path separation across environments. | <br/><br/><br/><br/>**Verify explicitly**: Cross-tenant and inter-environment trust always reauthenticated and logged.<br/><br/> **Use least privilege**: Access boundaries defined per tenant, workload, and admin role.<br/><br/>**Assume breach**: Tenant isolation used as a hard boundary to prevent lateral movement. | <br/><br/><br/><br/>Requires good tenant inventory and centralized governance.<br/><br/>Multi-tenant orgs may need federated identity strategies or cross-tenant access policies.<br/><br/>Initial increase in admin complexity to configure PIM and conditional access rules. |<br/><br/> [Eliminate identity lateral movement](/security/zero-trust/sfi/eliminate-identity-lateral-movement)<br/><br/>[Remove legacy systems](/security/zero-trust/sfi/remove-legacy-systems-that-risk-security)<br/><br/>[Increase security for Microsoft Entra ID apps](/security/zero-trust/sfi/higher-security-microsoft-entra-id-apps)<br/><br/>[Secure all tenants and resources](/security/zero-trust/sfi/secure-all-tenants-resources).


## Protect networks

Initiatives under this pillar aim to limit lateral movements and enforce explicit validation for all connectivity through network segmentation. The Microsoft SFI initiative focuses on:

- Network segmentation and isolation between production, engineering, and corporate environments.
- Identity-based access layered on top of network segmentation.
- Private access for management interfaces.
- Continuous access evaluation (CAE) for network sessions.
- No implicit trust across network resources.
- Use of network-level threat-intelligence-enabled firewalls, strict egress control, and telemetry logging.

### Adopt best practices

Key adoption best practices for identity and secrets protection are summarized in the following table.

**Best practice* | **Zero Trust** | **Adoption considerations** | **Detailed guidance**
--- | --- | --- | ---
Implement of macro and microsegmentation across networks and subnets, separating production, admin, and PaaS service boundaries.<br/><br/>  Restrict admin access via Private Link, Azure Bastion, and just-in-time admin access.<br/><br/>Implement session validation tied to identity state.<br/><br/>Use Secure Access Service Edge (SASE) and Zero Trust network access (ZTNA) instead of VPNs.<br/><br/> Enable and tune Microsoft Defender for network telemetry. | <br/><br/>**Verify explicitly**: Every connection is authenticated, authorized, and encrypted.<br/><br/> **Use least privilege**: Access granted only to required services or segments.<br/><br/>**Assume breach**: Network segmentation and monitoring detect and contain lateral movement. | <br/><br/>Deep understanding of existing traffic flows; segmentation can disrupt legacy integrations.<br/><br/>Retraining users used to VPN-based access on ZTNA rollout.<br/><br/>Additional cost and storage overhead of network telemetry in SIEM. | <br/><br/><br/><br/> [Isolate networks](/security/zero-trust/sfi/network-isolation).


## Protect engineering systems

Initiatives under this pillar aim to secure the entire software engineering and delivery process. The Microsoft SFI initiative focuses on:

- Isolation of build environments from internet and production.
- Code signing using trusted pipelines.
- Adoption of two-person integrity for sensitive operations.
- Software Bill of Materials (SBOM) tracking
- Pipeline scanning for leaked credentials or malicious code.
- Standardization of SDKs, developer security tooling, and dependency verification.

### Adopt best practices

Key adoption best practices for identity and secrets protection are summarized in the following table.

**Best practice** | **Zero Trust** | **Adoption considerations** | **Detailed guidance**
--- | --- | --- | ---
Run builds in secure isolated environments.<br/><br/>Require verified build provenance and signed artifacts.<br/><br/>Require code or release approval from multiple trusted approvers.<br/><br/> Maintain software component inventories/SBOM tracking for all builds.<br/><br/>Integrate secrets scanning and SAST/DAST tools into CI/CD pipelines for code scanning.<br/><br/>Enforce trusted package sources and signed dependencies. | <br/><br/>**Verify explicitly**: Authenticate all code commits, build actions, and releases.<br/><br/> **Use least privilege**: Developers, pipelines, and service principals only access what they need.<br/><br/>**Assume breach**: Treat build and repo systems as potential targets. Isolate and monitor them.| <br/><br/>High load of upfront work to modernize pipelines and dependency tracking.<br/><br/>Handling legacy build tools that might not support signing or SBOM formats.<br/><br/>Added build-time complexity for artifact signing that significantly improves traceability. | <br/><br/>[Standardize secure development pipelines](/security/zero-trust/sfi/standardize-secure-development-pipelines)<br/><br/>[Apply Zero Trust principles for source code access](/security/zero-trust/sfi/zero-trust-source-code-access)<br/><br/>[Protect the software supply chain](/security/zero-trust/sfi/protect-software-supply-chain).


## Monitor and detect cyberthreats

Initiatives under this pillar aim to unify telemetry across identity, endpoint, network, and engineering systems for proactive, contextualized threat detection, and fast, effective investigation and response. The Microsoft SFI initiative focuses on:

- Unified telemetry ingestion from identity, endpoint, network, and engineering systems.
- Development of threat correlation models and AI-driven detection.
- Shared detection rules across tenants.
- Centralized dashboards for rapid triage.
- Threat intelligence integration from MSTIC and global sources.

### Adopt best practices

Key adoption best practices for identity and secrets protection are summarized in the following table.

**Best practice** | **Zero Trust** | **Adoption considerations** | **Detailed guidance**
--- | --- | --- | ---
Centralize logs (identity, Key Vault, network, endpoint etc) into Microsoft Sentinel or another security information and event management (SIEM) solution.<br/><br/>  Use analytics and ML-based threat detection for abnormal behavior<br/><br/>Standardize detection templates and automation<br/><br/>Consolidate visibility across assets and incidents<br/><br/>Use threat feeds to enrich detection and alerting | <br/><br/>**Verify explicitly**: Continuous validation of behavior and state against normal baselines.<br/><br/> **Use least privilege**: Detections inform adaptive policies that restrict access automatically.<br/><br/>**Assume breach**: Assume that attackers might already have access, and detect attack movement quickly.| <br/><br/>Ongoing tuning to avoid alert fatigue.<br/><br/> Costs for licensing and ingestion volume for Sentinel/SIEM.<br/><br/> Continuous refinement and analyst training for detection logic. | [Inventory production infrastructure](/security/zero-trust/sfi/complete-production-infrastructure-inventory)<br/><br/>[Set security log retention standards](/security/zero-trust/sfi/security-log-retention-standards)<br/><br/>[Detect and respond to anomalies](/security/zero-trust/sfi/rapid-anomaly-detection-response)<br/><br/>[Centralize access to security logs](/security/zero-trust/sfi/centralize-access-to-security-logs).



## Accelerate response and remediation

Initiatives under this pillar aim to minimize the duration and impact of security incidents through automation, orchestration, and systemic learning. The Microsoft SFI initiative focuses on:

- Rapid coordinated incident response and patching, with automation of common mitigations.
- Systematic post-incident learning, and "secure-by-default” changes integrated into products and services.
- Continuous improvement loops and cross-team incident-response playbooks.

### Adopt best practices

Key adoption best practices for identity and secrets protection are summarized in the following table.

**Key practices** | **Zero Trust** | **Adoption considerations** | **Detailed guidance**
--- | --- | --- | ---
Develop and test incident response playbooks for common attack types.<br/><br/>  Automate token revocation, key rotation, and account disablement workflows.<br/> Tie vulnerability management processes to business risk and exposure.<br/><br/>  Adopt post-incident learning loops, and integrate lessons into policy and code baselines.<br/><br/>  Design communication plans (legal, PR, technical etc.) for significant breaches.<br/><br/> Run regular tabletop exercises with leadership and technical teams. | <br/><br/>**Verify explicitly**: Continuously reassess and revoke trust as needed after a security event.<br/><br/> **Use least privilege**: Automate containment by restricting or removing access rapidly.<br/><br/>**Assume breach**: Treat every incident as a catalyst for architectural and procedural hardening. | Disciplined coordination is needed between the security operations center (SOC), engineering, and leadership.<br/><br/> Automation of remediation actions must balance speed and risk of disruption.<br/><br/> Time and learning can result from tabletop exercises that might expose procedural gaps, but deliver large maturity gains. | <br/><br/><br/><br/>[Accelerate vulnerability mitigation](/security/zero-trust/sfi/accelerate-vulnerability-mitigation).



## Next steps

[Integrate NIST CSF 2.0 governance](integrate-nist-2-governance.md)
 155 changes: 155 additions & 0 deletions155  
security-docs/zero-trust/sfi/secure-future-initiative-overview.md
Viewed
Original file line number	Original file line	Diff line number	Diff line change
@@ -0,0 +1,155 @@
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

# Secure Future Initiative (SFI) overview

The SFI initiative launched as a multiyear effort to increasingly secure the way in which Microsoft designs, builds, tests, and operates its products and services. Over a year or so, the initiative dedicated extensive internal engineering resources to mitigate risk and improve security across Microsoft.

Initiative efforts continue to evolve in structured waves, and keep pace with shifts in the threat landscape. This evolution provides Microsoft with ongoing opportunities to work with customers and the broader security industry to strengthen our collective defenses.

Ongoing SFI work focuses on themes that include:

- Applying Zero Trust principles.
- Discovering dynamic asset inventory.
- Implementing fine-grained identity and access control, and network segmentation.
- Testing security controls and threat detection with continuous Red Team operations.
- Streamlining operations to respond more rapidly while staying secure.

SFI efforts inform Microsoft's ongoing security best practices, and development and innovation across the Microsoft security portfolio.

## Initiative architecture

SFI is designed and developed around a set of security principles that are adopted, delivered, and governed across Microsoft. These security principles are applied to a set of focus areas by means of processes, standards, and continuous improvements.

:::image type="content" source="../media/zero-trust/secure-future-initiative-overview.png" alt-text="Diagram summarizing the secure future initiative (SFI)." border="true":::


## Security principles

Microsoft's security standards, processes, culture, and governance focuses on these principles:

- **Secure by design: Security is the first priority during product and service design**. Outcomes include:
    - Creation of new teams within Microsoft, including the Artificial Generative Intelligence Safety & Security (AeGIS) organization that provides product teams with expertize on AI Red Teaming, incident response and more. [Learn more about the Microsoft AI Red Team (AIRT)](https://aka.ms/MSFT_AIRT_Lessons).
    - Focus on improved user experience and product security integration with an internal and [public Secure by Design UX Toolkit](https://microsoft.design/articles/secure-by-design-a-ux-toolkit/).
    - Adoption of security principles and the toolkit to develop secure-by-design roadmaps, and to prioritize and launch proactive security features across Microsoft.
- **Secure by default: Security protection is enabled and enforced by default**. Outcomes include:
    - Teams across Microsoft deliver new security innovations with a focus on better default protection.
    - In Microsoft 365, examples include the [Copilot Control System](https://adoption.microsoft.com/en-us/copilot/control-system/), and multifactor authentication for all Microsoft 365 Admin Center users.
    - In Windows, Microsoft rolled out the [Windows Resiliency Initiative](https://www.microsoft.com/windows/business/windows-resiliency-initiative?msockid=3867c9cd6a036861120cdcb96b93697a), [Windows Autopatch](/windows/deployment/windows-autopatch/overview/windows-autopatch-overview), and [Windows Smart App Control](https://support.microsoft.com/windows/app-browser-control-in-the-windows-security-app-8f68fb65-ebb4-3cfb-4bd7-ef0f376f3dc3#bkmk_smart-app-control).
    - In Azure, [Azure AI Foundry](/azure/ai-foundry/what-is-azure-ai-foundry) provides a platform and tooling for designing, customizing, and managing AI apps and agents. MFA in the Azure portal improves effective account security. 
    - In Microsoft Security, MFA enforces [strong authentication and other security measures for sovereign clouds](https://azure.microsoft.com/blog/microsoft-strengthens-sovereign-cloud-capabilities-with-new-services/?msockid=3867c9cd6a036861120cdcb96b93697a). New Microsoft Defender for Cloud App capabilities improve [protection and attack detection for OAuth apps.
- **Secure operations: Continuously improving security controls and monitor to meet shifting threats**. Outcomes include:
    - Microsoft's annual [Responsible AI Transparency Report](https://www.microsoft.com/corporate-responsibility/responsible-ai-transparency-report/?msockid=3867c9cd6a036861120cdcb96b93697a) outlines how we apply secure operational principles to our AI systems.
    - The [Central Fraud and Abuse Risk (CFAR) team](https://www.microsoft.com/security/security-insider/risk-management/three-lessons-from-microsoft-fight-against-fraud) was created and scaled for holistic protection our digital ecosystem by improving security policy, detection, investigation, and response.


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