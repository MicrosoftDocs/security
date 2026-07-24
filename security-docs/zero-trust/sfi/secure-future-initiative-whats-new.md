---
title: What new in Microsoft Secure Future Initiative (SFI) 
description: Review what's new in Microsoft's Secure Future Initiative (SFI).
ms.date: 07/23/2026
ms.service: security
author: rayne-wiselman
ms.author: raynew
ms.subservice: zero-trust
ms.topic: whats-new
ms.collection:
  - highpri
  - zerotrust
  - sfi-zerotrust
---

# What's new in the Secure Future Initiative

The Secure Future Initiative (SFI) initiative is a multiyear, cross-Microsoft initiative to increasingly secure the way in which Microsoft designs, builds, tests, and operates its products and services. 

SFI is build upon:

- A set of security principles that drive innovation on security design, implementation on features, secure defaults, and standards within Microsoft products, and internal and external security guidance. [Learn more](secure-future-initiative-overview.md#security-principles).
- A set of prioritized security pillars and objectives. [Learn more](secure-future-initiative-overview.md#sfi-pillars-zero-trust-and-nist).

This article summarizes our latest progress on innovation, implementation, and guidance, as well as on the pillar objectives.

## Track ongoing progress

For detailed SFI progress read the latest SFI [July 2026 report](https://www.microsoft.com/trust-center/security/secure-future-initiative/sfi-progress-report-july-2026).

You can also review earlier reports at:

- [SFI report - November 2025](https://www.microsoft.com/trust-center/security/secure-future-initiative/sfi-progress-report-november-2025).
- [SFI report - April 2025](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/sfi-april-2025-progress-report.pdf).
- [SFI report - September 2024](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/SFI_September_2024_progress_report.pdf).

## Security innovations and updates

The table summarizes the latest updates.

**Platform** | **Updates** 
--- | --- 
New pattern |  **Monitor and detect**: [Manage memory safety in agentic systems](manage-agentic-memory-safety.md)
New pattern | **Accelerate response and remediation**: [Respond to incidents in AI systems](incident-response-ai-systems.md).
New pattern | **Monitor and detect**: [Complete AI threat modeling](threat-modeling-ai.md).
New pattern | **Monitor and detect**: [Implement AI observability](observability-ai-systems.md).
New pattern | **Monitor and detect**: [Secure autonomous agentic AI systems](secure-agentic-systems.md).
New pattern | **Monitor and detect**: [Identity risk for agentic AI systems](manage-agentic-risk.md).
New pattern | **Monitor and detect**: [Protect against indirect prompt injection attacks](defend-indirect-prompt-injection.md).
**[Azure](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/security/July-2026-SFI-Progress-Report.pdf#page=15)** advanced hardware-backed trust and confidential computing. | **Innovate**: Azure Integrated HSM reached general availability, providing hardware-backed [cryptographic key protection](/azure/security/fundamentals/key-management) with increased firmware and driver transparency for cloud and AI workloads.<br/>[Azure confidential VMs with Intel TDX](/azure/confidential-computing/tdx-confidential-vm-overview) strengthen protection for data in use with hardware-isolated execution environments, encrypted memory, and remote attestation.<br/>[Azure Local](/azure/azure-local/concepts/security-features) extended Azure Arc-enabled security baselines, hardened configurations, and signed components to edge and disconnected environments, with Small Form Factor deployments (preview) for resource-constrained edges.<br/><br/>**Guidance**: Use hardware-backed protections to keep cryptographic keys within secure hardware boundaries, and apply the same secure-by-default practices across local and disconnected environments.
**[Microsoft 365](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/security/July-2026-SFI-Progress-Report.pdf#page=16)** enabled secure-by-default configuration and identity-first controls for AI agents. | **Innovate**: Microsoft 365 baseline security mode enforces secure-by-default configurations, reducing exposure from legacy settings and strengthening protections against emerging AI-enabled threats.<br/>[Microsoft Entra managed identities](/entra/identity/managed-identities-azure-resources/overview) provide scoped authentication, policy enforcement, and lifecycle governance for enterprise AI agents.<br/>Role-based access controls enforce least-privilege for AI agents, keeping operations within authorized permissions.<br/><br/>**Guidance**: Enable baseline security mode, review enterprise agent activity regularly to confirm ownership and risk signals, and assign both an owner and a sponsor to each agent.
[Windows and Surface](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/security/July-2026-SFI-Progress-Report.pdf#page=16) modernized cryptographic and identity systems and strengthened hardware-rooted integrity. | **Innovate**: Windows combines post-quantum cryptographic capabilities for certificates, digital signatures, and TLS with a transition from NTLM to Kerberos-based identity flows, reducing legacy authentication dependencies.<br/>A default kernel trust policy in Windows 11 (April 2026) ensures only drivers signed through the Windows Hardware Compatibility Program can load by default.<br/>Windows Baseline Security Mode adds runtime integrity protections and consent-based access controls for applications and AI agents.<br/>Surface for Business devices incorporate memory-safe Rust-based firmware and a hardware-rooted chain of trust developed through the Open Device Partnership.<br/><br/>**Guidance**: Modernize cryptographic and authentication foundations to reduce reliance on legacy protocols such as NTLM, and enforce kernel-level integrity by restricting execution to signed drivers.
[Microsoft security](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/security/July-2026-SFI-Progress-Report.pdf#page=17) enabled AI-led vulnerability discovery and AI-powered defense at scale. | **Innovate**: A new multi-model AI-driven scanning system (codename MDASH) discovers, validates, and prioritizes vulnerabilities at scale, enabling earlier identification in the development lifecycle with proof-based verification.<br/>[Microsoft Security Exposure Management](/security-exposure-management/microsoft-security-exposure-management) with SecureNow combines guidance and actionable capabilities to help organizations assess exposure and prioritize remediation, available to all customers with a Microsoft Entra ID.<br/>Nation State Notifications in [Microsoft Defender](/defender-xdr/microsoft-threat-actor-naming) surface actionable nation-state, ransomware, and fraud intelligence with attributed actor context.<br/>Microsoft Entra Tenant Governance unifies multitenant environments under centralized governance to detect unmanaged or shadow tenants and enforce consistent least-privilege baselines.<br/><br/>**Guidance**: Use codename MDASH to identify and prioritize exploitable vulnerabilities earlier, and apply Exposure Management and SecureNow to continuously validate posture across identity, endpoint, source code, and cloud.


## Progress on pillar objectives

We disclose progress on pillar objectives as periodic SFI reports are published. Each objective represents a significant effort to improve security and reduce risk for Microsoft and our customers in a specific pillar area. Pillars, goals, and objectives might shift over time in response to dynamic security priorities and emerging threat landscapes.

### Protect identities and secrets

This table presents a progress summary. Get [the latest full progress details](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/security/July-2026-SFI-Progress-Report.pdf#page=20) in the July 2026 report.


**Objective** | **Progress**
--- | ---  
 **1. Protect cryptographic signing keys**<br/><br/>Protect identity infrastructure signing and platform keys with rapid and automatic rotation of identity infrastructure keys, using hardware storage and protection. | Target state reached:<br/><br/>- Completed migration to Azure Confidential Computing for 100% of Microsoft Entra ID token signing keys in Azure public and US Gov clouds, ensuring cryptographic operations occur within secure execution environments.
**2. Adopt standard SDKs for identity**<br/><br/>Strengthen identity standards and drive standards adoption with the use of standard SDKs across applications, so that apps and services use a uniform, hardened library for validating tokens. |- Microsoft Authentication Library (MSAL) updated to disrupt authorization-code social-engineering campaigns and released to customers.<br/>- 93% of Microsoft Entra traffic now flows through the standard SDK, replacing ad-hoc token handling with a single validated library.<br/>- Legacy authentication protocols continue to be retired across Office and Microsoft Entra workloads.
**3. Enforce phishing-resistant MFA**<br/><br/>Ensure user accounts are protected with securely enforced, phishing-resistant MFA. | - Phishing-resistant MFA enforcement reached broad maturity with 99.97% user and device coverage, including full enforcement on macOS and expanded Linux support.<br/>- Closing objective: transitioning to steady-state operations with ongoing monitoring, as defense shifts to counter OAuth consent phishing, open redirect abuse, and redirect URI hijacking.
**4. Standardize safe secrets**<br/><br/> Shift away from long-lived secrets such as service account credentials to ensure that applications are protected with system-managed credentials such as managed identities. | - New services increasingly use modern identity-based authentication by default, reducing reliance on long-lived, reusable credentials.<br/>- Expanding use of short-lived, workload-bound credentials that prevent stolen credentials from being reused outside their intended environment.
**5. Provide stateful validation for identity tokens**<br/><br/>Ensure identity tokens are protected with stateful and duration validation.| - Microsoft Entra now includes linkable identifiers in access tokens to correlate activity across Microsoft Entra and major Microsoft service audit logs (Exchange Online, Microsoft Graph, SharePoint Online, and Teams), improving investigation speed and containment for compromised sessions.
**6. Use fine-grained key partitioning**<br/><br/>Adopt more fine-grained partitioning of identity signing keys and platform keys. | - Datacenter key partitioning is fully deployed across all cloud environments for baseline identity operations.<br/>- New Azure cloud environments onboard secure-by-default with split keys, strengthening isolation boundaries.
**7. Introduce quantum-safe PKI systems**<br/><br/>Ensure identity and certificate PKI systems are ready for a post-quantum cryptography world. | - Planning advanced from initial assessment to a defined transition approach, with validated scope across certificate services, identity platforms, and critical service trust chains, and a phased implementation plan in development.


### Protect tenants and isolate systems

This table presents a progress summary. Get [the latest full progress details](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/security/July-2026-SFI-Progress-Report.pdf#page=21) in the July 2026 report.

**Objective** | **Progress**
--- | ---  
**1. Remove legacy systems that risk security**<br/><br/> Maintain the security posture and commercial relationship of tenants by removing all unused, aged, or legacy systems. | - Retirement of Azure Service Manager (ASM) is complete across all remaining workload classes, and migration to Azure Resource Manager reached 100% (up from 98% in November 2025), eliminating classic administrator-role and management-certificate risks.<br/>- Satellite-tenant cleanup matured, with 15,500 aged or unused tenants retired this cycle as the effort shifts from broad cleanup to governance, supported by automated lifecycle checks.
**2. Secure all tenants and their resources**<br/><br/> Protect Microsoft, acquired, and employee-created tenants, commerce accounts, and tenant resources in accordance with security best practice baselines. | - Inventory and lifecycle coverage spans all tenant classes (production, productivity, auxiliary, and ephemeral), so every tenant is governed from creation through retirement.<br/>- The ephemeral tenant fleet is lifecycle-managed with a default 90-day expiration, systematically purging test artifacts, credentials, and transient configurations.
**3. Provide higher security for Entra ID apps**<br/><br/>Manage Microsoft Entra ID applications with a high and consistent security bar to reduce the vector for lateral movement. | - Decommissioned 1.4 million unused Microsoft Entra applications (an increase of 176,198 since November 2025) and continued stripping unnecessary critical-privilege Graph permissions from production apps.<br/>- 86.45% of multitenant applications declare an allowed-tenants list under enforced policy.<br/>- Network restrictions on managed identities tripled from 5.9 million (November 2025) to 18.1 million, and 99.99% are blocked from service-to-service authentication into production from non-production or non-Microsoft IP ranges.
**4. Eliminate identity lateral movement**<br/><br/>Eliminate identity lateral movement pivots between tenants, environments, and clouds. | - Cross-boundary credential isolation advanced from 98% (November 2025) to 98.7%, closing credential paths that allowed token re-creation across tenants.<br/>- Guest invitation pathways are being tightened, and unmanaged guest access was reduced by 228,000 with further cleanup in progress.
**5. Continuous least-privilege enforcement**<br/><br/>Ensure continuous least-privilege access enforcement for apps and users. | - Emergency access is moving from persistent privileged identities to on-demand, dual-authorization workflows through Dual-Key Break Glass (DKBG) controls; rollout is targeted for completion by end of July 2026, eliminating 29,000 existing break-glass accounts.<br/>- The high-privilege application reduction program is 81% complete, shrinking persistent, elevated access.
**6. Secure devices used for access**<br/><br/> Ensure that only secure, managed, healthy devices are granted access to tenants.  | - All production access across Microsoft tenants now requires a locked-down endpoint, with 125,979 production-ready locked-down devices deployed (up from 112,000 in November 2025).<br/>- 56,581 of our highest-risk users now operate exclusively on locked-down endpoints, up from 44,516 since November 2025.


### Protect networks

This table presents a progress summary. Get [the latest full progress details](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/security/July-2026-SFI-Progress-Report.pdf#page=22) in the July 2026 report.

**Objective** | **Progress**
--- | ---  
**1. Inventory and security standards**<br/><br/>Secure Microsoft production networks and connected systems with accurate inventory, complete device lifecycle management, and consistently enforced baseline controls. | - Centralized telemetry and control systems provide effectively complete visibility of production network assets through a complete device lifecycle management process.<br/>- Core controls (centralized authentication, authorization, and accounting; IPv4/IPv6 access control lists; and per-device keys) are consistently enforced across production network devices.<br/>- Closing objective: this objective has reached its intended end state and transitions to steady-state operations focused on durability and regression prevention.
**2. Network isolation**<br/><br/>Apply identity-aware network isolation and microsegmentation to Microsoft production environments, creating additional layers of defense against attackers. | - Policy-driven isolation is operating at scale, with adoption reaching 4.36 million resources in learning mode and approximately 1 million in enforced mode.<br/>- Public access has been removed from 732,000 resources, and permissive network rules are being replaced with tightly scoped, least-privilege controls.<br/>- Segmentation coverage is extending from critical and high-value services to all Microsoft services, strengthening containment boundaries.
**3. Secure customer cloud networks**<br/><br/>Strengthen network defenses with modern firewalling, segmentation policies, and platform-level enforcement, ensuring that only authorized traffic can flow and that potential breaches are contained. | - Azure provides integrated mechanisms for defining logical isolation boundaries around PaaS resources, supporting secure-by-default deployment patterns with traffic pattern learning windows.<br/>- Ongoing efforts focus on expanding adoption of these capabilities and aligning them to secure deployment baselines.

### Protect engineering systems

This table presents a progress summary. Get [the latest full progress details](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/security/July-2026-SFI-Progress-Report.pdf#page=23) in the July 2026 report.

**Objective** | **Progress**
--- | --- 
**1. Complete software asset inventory**<br/><br/>Build and maintain an inventory of software assets used to deploy Microsoft products and services. | - Engineering asset visibility and access governance have stabilized into a mature, consistently operating capability across development environments.
**2. Zero trust for source code access** <br/><br/>Ensure secure access to source code and engineering systems infrastructure with Zero Trust principles and least-privilege access policies. | - Zero Trust for source-code access is now broadly enforced, with code changes governed through policy-based checks and approvals.<br/>- A new permissions service that manages least-privileged access is adopted across 71% of high-value production repositories; remaining gaps are concentrated in automated and non-human identity workflows.
**3. Secure code deployment**<br/><br/>Protect source code that deploys Microsoft production environments with security best practices. | - Secure code deployment controls remain strong, with hardware-backed protection for signing keys and expanded adoption of confidential computing in Azure DevOps continuing to strengthen software integrity and supply-chain security.
**4. Standardize secure development pipelines**<br/><br/>Secure development, build, test, and release environments with standardized, governed pipelines, and infrastructure isolation.| - 93% of critical and high-value build pipelines and 90% of release pipelines use centrally governed templates across approximately 80,000 monitored pipelines, enforcing consistent security controls including blocking known malicious endpoints.<br/>- Broad network endpoint isolation continues; remaining work focuses on broader template adoption and stricter enforcement.
**5. Protect the software supply chain**<br/><br/>Secure the software supply chain to protect Microsoft production environments.| - Supply-chain security has shifted from reactive remediation to governed prevention: more than 550,000 critical and high-risk open-source vulnerabilities remediated, with automated container patching addressing about 3 million vulnerability instances each month.<br/>- PR-time blocking of foreign checked-in binaries increased fix rates from 13% to 47%, and blocked malicious packages during the Shai-Hulud v2 supply-chain attack before they reached internal systems.


### Monitor and detect threats

This table presents a progress summary. Get [the latest full progress details](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/security/July-2026-SFI-Progress-Report.pdf#page=24) in the July 2026 report.

**Objective** | **Progress**
--- | ---  
**1. Complete production infrastructure inventory**<br/><br/>Maintain a current resource inventory across Microsoft production infrastructure and services.| - Most assets, including network devices, physical servers, and virtual machines, are actively tracked through a unified inventory system, with security telemetry centrally collected and retained for two years.<br/>- Efforts are shifting to ensure freshness and accuracy of inventory systems and regression detection.
**2. Standardize security log retention**<br/><br/>Retain security logs for at least two years, and make six months of appropriate logs available.|  - More than 81% of services now emit critical security logs in a standard format and retain them for two years.<br/>- Automated collection reduces operational burden on service teams, and LLM-based analysis enhances log quality by scanning code repositories and identifying telemetry gaps.
**3. Centralize access to security logs**<br/><br/> Ensure security logs are accessible from a central data lake for efficient and effective investigation and threat hunting. | - Standardized retention policies and scalable access controls enable security teams to efficiently retrieve and analyze logs for investigations and threat hunting.<br/>- Major log categories now meet minimum retention standards, and a centralized tracking framework ensures remaining telemetry gaps are prioritized and resolved within defined SLAs.
**4. Detect and respond quickly**<br/><br/> Detect and respond automatically to anomalous access, behavior, and configurations across Microsoft production infrastructure and services. | - Detection is moving beyond signature-based approaches toward behavior and baseline-driven detection, with more than 100 new detections introduced alongside enhancements to the existing 250+ detections.<br/>- AI-assisted authoring is increasing throughput and accelerating deployment, and collaboration with threat research and Red Team operations is improving detection quality.


### Accelerate response and remediation

This table presents a progress summary. Get [the latest full progress details](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/security/July-2026-SFI-Progress-Report.pdf#page=25) in the July 2026 report.

**Objective** | **Progress**
--- | ---  
**1. Accelerate vulnerability mitigation**<br/><br/> Reduce "Time to Mitigation" for high-severity cloud security vulnerabilities with accelerated response. | - Microsoft is partnering with leading AI and security experts, including through initiatives such as Project Glasswing and an expanded April 2026 collaboration with OpenAI (Trusted Access for Cyber), to rapidly identify and mitigate vulnerabilities. This is reflected in a significant increase in security updates in the June 2026 Patch Tuesday release, including many vulnerabilities discovered by codename MDASH.<br/>- Automation and tactical mitigation capabilities enable rapid response; in one case a mitigation for an actively exploited client-side vulnerability was deployed without a customer update in under a day.
**2. Advance transparency of cloud vulnerabilities**<br/><br/>Increase transparency of mitigated cloud vulnerabilities with the adoption and release of Common Weakness Enumeration (CWE) and Common Platform Enumeration (CPE) industry standards. Release high severity Common Vulnerabilities and Exposures (CVEs) affecting the cloud. | - Publishing CVEs enriched with CWE and CPE annotations is now an established practice, and support for machine-readable CSAF and VEX formats helps customers automate consumption of vulnerability and release information.<br/>- Transparency emphasizes completeness as well as volume, including publishing CVEs that require no customer action. Investments in researcher recognition and coordinated initiatives like Zero Day Quest (which awarded $2.3 million in 2026) strengthen early discovery.
**3. Enhance public messaging and engagement**<br/><br/>Improve the accuracy, effectiveness, transparency, and velocity of public messaging and customer engagement. | - Customer communication during security incidents is now mature and repeatable, with the Customer Security Management Office (CSMO) coordinating customer-facing communications across major incidents using defined playbooks and cross-team alignment.<br/>- Nation State Notifications deliver actionable intelligence on breaches linked to nation-state actors, ransomware campaigns, and fraud operations directly in Microsoft Defender, alongside related alerts and incidents.


## Next steps

Learn about [adopting Microsoft SFI best practices](secure-future-initiative-adoption.md).