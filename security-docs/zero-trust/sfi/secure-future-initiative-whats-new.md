---
title: What new in Microsoft Secure Future Initiative (SFI) 
description: Review what's new in Microsoft's Secure Future Initiative (SFI).
ms.date: 12/28/2025
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

# What's new in the Secure Future Initiative

The Secure Future Initiative (SFI) initiative is a multiyear, cross-Microsoft initiative to increasingly secure the way in which Microsoft designs, builds, tests, and operates its products and services. 

SFI is build upon:

- A set of security principles that drive innovation on security design, implementation on features, secure defaults, and standards within Microsoft products, and internal and external security guidance. [Learn more](secure-future-initiative-overview.md#security-principles).
- A set of prioritized security pillars and objectives. [Learn more](secure-future-initiative-overview.md#sfi-pillars-zero-trust-and-nist).

This article summarizes our latest progress on innovation, implementation, and guidance, as well as on the pillar objectives.

## Track ongoing progress

For detailed SFI progress read the latest SFI [November 2025 report](https://www.microsoft.com/trust-center/security/secure-future-initiative/sfi-progress-report-november-2025).

You can also review earlier reports at:

- [SFI report - April 2025](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/sfi-april-2025-progress-report.pdf).
- [SFI report - September 2024](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/microsoft-brand/documents/SFI_September_2024_progress_report.pdf).

## Security innovations and updates

The table summarizes the latest updates.

**Platform** | **Updates** 
--- | --- 
**[Azure](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/security/sfi-nov-2025-progress-report.pdf#page=18)**  enforced additional secure defaults. | **Innovate**: [Azure Bastion Developer](/azure/bastion/quickstart-developer) expanded secure-by-default VM connectivity to 35 Azure regions, reducing attack surfaces.<br/>In Azure Local we [increased security settings enabled by default](/azure/azure-local/concepts/security-features).<br/>For [increased hardware trust](https://azure.microsoft.com/blog/protecting-azure-infrastructure-from-silicon-to-systems/), Microsoft-designed hardware-security module (HSM) tamper-resistant chips are integrated into the Azure infrastructure to keep encryption keys within secure hardware boundaries, eliminating latency and exposure risk.<br/><br/>**Implement**: Increased mandatory enforcement of strong multifactor authentication, emphasizing phishing-resistant authentication methods for all Azure service users, helping to neutralize stolen credentials at scale.<br/><br/>**Guidance**: [Microsoft Cloud Security Benchmark v2](/security/benchmark/azure/overview) released, with clear and comprehensive security best practices that can be enforced using Azure Policy.
**[Microsoft 365](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/security/sfi-nov-2025-progress-report.pdf#page=19)** provided increased AI control and data security. | **Innovate**:  Microsoft 365 introduced a [dedicated AI Admin role](/microsoft-365-copilot/extensibility/connector-admin-delegation) to secure Copilot management, move away from the Global Administrator role, and enforce least-privilege principles.<br/>[Centralized Copilot agent control and governance](/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps) in the Microsoft 365 Admin Center allows IT admins to easily manage, configure, and monitor agents.<br/><br/> **Implement**: Microsoft Purview's [secure-by-default adaptive labelling](/purview/deploymentmodels/depmod-securebydefault-intro) now classifies and secures more thatn 50 million items monthly.<br/><br/>**Guidance**: Helping customers to use the AI admin roles for Copilot tasks, enforcing least-privilege.<br/>Guidance on use of [Microsoft Purview DSPM for AI](/purview/data-security-posture-management-learn-about) to monitor Copilot data usage, and detect misuse.
[Windows and Surface](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/security/sfi-nov-2025-progress-report.pdf#page=20) enhanced Zero Trust principles with expanded passkeys, automatic recovery capabilities, and memory-safe improvements. | **Innovate**: In Windows 11, Windows Hello and [passkeys integration](/windows/security/identity-protection/passkeys) offers a more secure, phishing-resistant passwordless sign-in experience.<br/>Surface is [advancing Windows security through the Open Device Partnership](https://blogs.windows.com/windowsexperience/2025/11/10/advancing-security-with-windows-and-surface-microsoft-sfi-report-nov-2025/), an open-source firmware initiative that replaces legacy firmware with a transparent, secure, and reusable platform.<br/><br/>**Implement**: Improvements in Hotpatch to [support ARM64 devices](https://techcommunity.microsoft.com/blog/windows-itpro-blog/hotpatching-now-available-for-64-bit-arm-architecture/4430949). Hotpatch is now enabled by default when creating a new Quality Update Policy in Autopatch, making it easier to maintain security and compliance with less disruption.<br/><br/>**Guidance**: Helping customers to [enable Quick Machine Recovery on Windows 11](/windows/configuration/quick-machine-recovery) to automatically remediate boot failures and protect against boot-time attacks.<br/>Helping customers to [adopt passwordless sign-ins](/windows/security/book/identity-protection-passwordless-sign-in), integrating with password managers such as 1Password or Bitwarden.
[Microsoft security](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/security/sfi-nov-2025-progress-report.pdf#page=21) introduced data security posture management for AI, and shifted Microsoft Sentinel into a AI-first security platform. | **Innovate**: [Microsoft Sentinel data lake](/azure/sentinel/datalake/sentinel-lake-overview) enables a tenant-wide repository for collecting, storing, and managing large volumes of security-related data.<br/>More than 35 Microsoft and partner agents now work to automate repetitive tasks and reduce manual workloads. Partner-developed agents are available via the new [Microsoft Security Store](https://securitystore.microsoft.com/agents).<br/><br/>**Implement**: [Microsoft Entra entitlement management](/entra/id-governance/entitlement-management-overview) is being used to govern access across Microsoft engineering teams.<br/>In Microsoft Purview, [adaptive protection with data loss prevention policies](/purview/dlp-adaptive-protection-learn) blocks risky sharing activities based on user behavior across USB drives, web, email, and Team for proactive and consistent protection.<br/><br/>**Guidance**: Help customers to consolidate security data with [onboarding to Microsoft Sentinel data lake and Microsoft Sentinel graph](/azure/sentinel/datalake/sentinel-lake-onboarding).<br/>Help customers to [enable Security Copilot agents](https://www.microsoft.com/security/blog/2025/11/18/agents-built-into-your-workflow-get-security-copilot-with-microsoft-365-e5/) for analysts to benefits fron AI capabilities during incident triage, reporting, and more.


## Progress on pillar objectives

We disclose progress on pillar objectives as periodic SFI reports are published. Each objective represents a significant effort to improve security and reduce risk for Microsoft and our customers in a specific pillar area. Pillars, goals, and objectives might shift over time in response to dynamic security priorities and emerging threat landscapes.

## Protect identities and secrets

This table presents a progress summary. Get [the latest full progress details](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/security/sfi-nov-2025-progress-report.pdf#page=23) in the November 2025 report.


**Objective** | **Progress**
--- | ---  
 **1. Protect cryptographic signing keys**<br/><br/>Protect identity infrastructure signing and platform keys with rapid and automatic rotation of identity infrastructure keys, using hardware storage and protection. | Significant progress:<br/><br/>- Migrated ~95% of Entra ID signing VMs to Azure Confidential Compute, improving key protection. 
**2. Adopt standard SDKs for identity**<br/><br/>Strengthen identity standards and drive standards adoption with the use of standard SDKs across applications, so that apps and services use a uniform, hardened library for validating tokens. |- Expanded measurement of standard SDK adoption to include Microsoft Account and internal platform identity systems.<br/>- Now validating more than 94% of Microsoft Entra ID security tokens in Microsoft with our standard SDKs, reducing risk from custom code.<br/>- Microsoft Authentication Library (MSL) released as a common implementation and Microsoft Entra SDK for Cloud Services.
**3. Enforce phishing-resistant MFA**<br/><br/>Ensure user accounts are protected with securely enforced, phishing-resistant MFA. | - 99.6% MFA adoption achieved across users/devices, ensuring strong authentication.>br/>- 100% compliance on iOS and 99.97% on Android.
**4. Standardize safe secrets**<br/><br/> Shift away from long-lived secrets such as service account credentials to ensure that applications are protected with system-managed credentials such as managed identities. | Continuous remediation of secrets. High coverage (~99.5%) of detected sensitive data in code or config. 
|**5. Provide stateful validation for identity tokens**<br/><br/>Ensure identity tokens are protected with stateful and duration validation.| Standardized validation implemented, with high coverage for critical tokens. | 
**6. Use fine-grained key partitioning**<br/><br/>Adopt more fine-grained partioning of identity signing keys and platform keys. | Partitioning implemented for many key types. Scope limited for sensitive keys.
**7. Introduce quantum-safe PKI systems**<br/><br/>Ensure identity and certificate PKI systems are ready for a post-quantum cryptography world. | Early planning, with some post-quantum PKI pilots in progress. 


## Protect tenants and isolate systems

This table presents a progress summary. Get [the latest full progress details](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/security/sfi-nov-2025-progress-report.pdf#page=25) in the November 2025 report.

**Objective** | **Progress**
--- | ---  
**1. Remove legacy systems that risk security**<br/><br/> Maintain the security posture and commercial relationship of tenants by removing all unused, aged, or legacy systems. | - Reducing legacy footprint across identity provisioning, resource management, and unused tenants.<br/>- Shifting the Source of Authority (SOA) from on-premises Active Directorion to cloud native platforms such as Microsoft Entra ID.<br/>- Retired the use of ADFS in productivity environment, advanced the migration of ASM to ARM to more than 98%.<br/>- We retired an additional 560,000 unused and aged tenants and 83,000 apps, reducing attack surfaces and eliminating unmanaged identity lifecycles.
**2. Secure all tenants and their resources**<br/><br/> Protect Microsoft, acquired, and employee-created tenants, commerce accounts, and tenant resources in accordance with security best practice baselines. | - Tenant segmentation strengthened by removing test/unused tenants.<br/>- Auxiliary tenant fleet created to support controlled productivity environments.
**3. Provide higher security for Entra ID apps**<br/><br/>Manage Microsoft Entra ID applications with a high and consistent security bar to reduce the vector for lateral movement. | Tenant segmentation strengthened by removing test/unused tenants.<br/>- We created a purpose-built, non-production auxiliary tenant fleet with strict access controls, used for testing, development, demos, and partner collaboration.
**4. Eliminate identity lateral movement**<br/><br/>Eliminate identity lateral movement pivots between tenants, environments, and clouds. | - Improved cross‑boundary secret isolation from ~94% (April) to ~98%, closing credential paths that allowed token re‑creation across tenants. Each secret removed reduces the risk of adversaries pivoting across tenants.<br/>- We're stamping certificates with tenant and cloud metadata for increased traceability, helping us to identify cross-boundary traversal risk.
**5. Continuous least-privilege enforcement**<br/><br/>Ensure continuous least-privilege access enforcement for apps and users. | - We're advanceing least-privilege enforcement across Microsoft services for a secure-by-default posture that minimises risk.<br/>- Our high-privilege reducation program is 78% coplete, lowering attack surfaces by migrating thousands of appliations to least-privileged models.<br/> - We're rolling out additional enhancements to our authorization model to strengthen posture, and a new authentication flow to drive further reductions in high-privilege apps. 
**6. Secure devices used for access**<br/><br/> Adopt fine-grained partitioning of identity signing keys and platform keys. Ensure that only secure, managed, healthy devices are granted access to tenants.  | - All production access across Microsoft tenants required locked-down endpoints.<br/>- We're deploying increased production-ready locked down devices.<br/>- Our security posture ensures that privileged operations can only be performed from compliant endpoints.


## Protect networks

This table presents a progress summary. Get [the latest full progress details](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/security/sfi-nov-2025-progress-report.pdf#page=27) in the November 2025 report.

**Objective** | **Progress**
--- | ---  
**1. Complete network device inventory and asset lifecycle management**<br/><br/>Secure Microsoft production networks and systems connected to networks with improved network isolation, monitoring, accurate inventory, and secure operations. | - Improved telemetry provides increased asset visibility for a complete inventory of all production network devices tracked in a central inventory with lifecycle metadata.<br/>- All network devices in production networks are configured with centralized authentication, audit trail, and ACLs for IPv4/IPv6 to restrict lateral movement. 
 **2. Strengthen security through enhanced network isolation and controls**<br/><br/>Apply identity-aware network isolation and microsegmentation to Microsoft production environments, creating additional layers of defense against attackers. | Network segmentation and protective controls have been improved to reduce implicit trust and restrict network paths.
**3. Accelerate adoption of Network Security Perimeter (NSP)**<br/><br/>Place entries resources under modern perimeter enforcement and segmentation to ensure network traffic is validated and only allowed where necessary to reduce the risk of lateral movement and unauthorized access. | - We're continuing to expand network isolation across production environments. <br/>- NSP adoption has grown to over 1.1 million resources in learning mode and around 500,000 in enfnrced mode. Public access has been disable for thousands of resources.<br/>- Tagged first party IPs increased to 21%, supporting fine-grained segmentation.<br/> - Network Manager now enforces centralized ACLs across more than 6000 devices, reducing lateral risk and strengthening defense layers. 
**4. Secure customer cloud networks**<br/><br/>Strengthen network defenses with modern firewalling, segmentation policies, and platform-level enforcement, ensuring that only authorized traffic can flow and that potential breaches are contained. | - The NSP feature has reached general avaiability, allowing customers to define logical isolation boundaries around PaaS resources.<br/>- Azure Bastion Developer now supports private connectivity to AKS clusters for more secure access to AKS API severs without public exposure or VPN setup.

## Protect engineering systems

This table presents a progress summary. Get [the latest full progress details](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/security/sfi-nov-2025-progress-report.pdf#page=28) in the November 2025 report.

**Objective** | **Progress**
--- | --- 
**1. Complete software asset inventory**<br/><br/>Build and maintain an inventory of software assets used to deploy Microsoft products and services. | - Inventory spans all Azure DevOps repositories and pipelines with full metadata.<br/>- “StartRight” tooling ensures ~80% of assets are inventoried at creation and “StayRight” captures the rest within 24 hours, enabling rapid incident response and policy enforcement. 
**2. Zero trust for source code access** <br/><br/>Ensure secure access to source code and engineering systems infrastructure with Zero Trust principles and least-privilege access policies. | - Standing admin access reduced, and just‑in‑time elevation required.<br/>- Azure DevOps OAuth apps use Microsoft Entra authentication with conditional access.<br/>- Nearly all production code changes include proof‑of‑presence checks.
**3. Secure code deployment**<br/><br/>Protect source code that deploys Micorsoft production environments with security best practices. | - Code signing access is almost entirely locked to production identities.<br/>- Repositories enforce branch policies with minimum approver counts and expanded secrets detection analytics strengthen compliance and durability. 
**4.Standardize secure development pipelines**<br/><br/>Apply network isolation and microsegmentation to Microsoft production environments. Secure development, build, test, and release environments with standardized, governed pipelines, and infrastructure isolation.| - Nearly all production build pipelines and 94% of release pipelines use centrally governed templates.<br/>- Increased network isolation (~89% complete) blocks direct access to public registries and flags unvetted dependencies.
**5. Protect the software supply chain**<br/><br/>Secure the software supply chain to protect Microsoft production environments.| - Supply chain protections are maturing. internal artifact feeds are broadly adopted and component governance runs by default.<br/>-  AI agents now remediate open‑source vulnerabilities asynchronously, reducing detection‑to‑resolution latency.


## Monitor and detect threats

This table presents a progress summary. Get [the latest full progress details](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/security/sfi-nov-2025-progress-report.pdf#page=31) in the November 2025 report.

**Objective** | **Progress**
--- | ---  
**1. Complete production infrastructure inventory**<br/><br/>Maintain a current resource inventory across Microsoft production infrastructure and services.| - More than 98% of production infrastructure is centrally tracked, improving visibility into system and security states and enabling long‑term trend analysis and investigation.<br/>- Security logsfrom modes are centrally collection with a two-year retention policy. This visibility helps operational resilience, threat detection, and compliance readiness.
**2. Standardize security log retention.**<br/><br/>Retain security logs for at least two years, and make six months of appropriate logs available.|  - More than 72% of services are now fully compliant with our standardized  logging format, ensuring critical security events are captured in a uniform  and actionable way.<br/>- To accelerate adoption across the remaining services,  we are investing in AI-driven analysis of service code repositories and  function calls.<br/>- We're also continually refining our standard logging baselines dynamically in response to security incident learning.
**3. Centralize access to security logs**<br/><br/> Ensure security logs are accessible from a central data lake for efficient and effective investigation and threat hunting. | - To strengthen our threat detection and response capabilities, we have  implemented a robust and scalable access model that enables security  teams to efficiently retrieve and analyze logs for investigations and threat  hunting.<br/> -A AT the time of writing, the centralized access model for security logs has matured, with 6 out of 7 major log categories now following the  minimum retention standards.
**4. Detect and respond quickly**<br/><br/> Detect and respond automatically to anomalous access, behavior, and configurations across Microsoft production infrastructure and services. | - For our strategy to continuously evaluate detection  coverage, identify gaps, and stay ahead of emerging threats, security and engineering teams collaborated to expand and refine our detection capabilities. This resulted in the deployment of more than 50 new detections targeting  high-priority TTPs (including data exfiltration, credential access, and  remote code execution).This brings our total to more than 250 active  detections across production infrastructure – applicable detections will be  added to Microsoft Defender.<br/> - AI-driven imporivement are leveraged at every stage of the detection lifecycle, from identifying new detection capabilities to development/test acceleration and improved signals. This helps us to scale detection coverage which maintaining precision and resilience. 


## Accelerate response and remediation

This table presents a progress summary. Get [the latest full progress details](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/security/sfi-nov-2025-progress-report.pdf#page=33) in the November 2025 report.

**Objective** | **Progress**
--- | ---  
**1. Accelerate vulnerability mitigation**<br/><br/> Reduce "Time to Mitigation" for high-severity cloud security vulnerabilities with accelerated response. | - AI-based vulnerability triage and expedited software processes, supported by signal intelligence that processes over 100 trillion signals every day, has strengthened our ability to accurately identify and assign vulnerabilities to the correct internal teams. The result is faster remediation and more efficient resolution of critical vulnerabilities, resulting in a 72% success rate, as we expanded the program’s scope and mitigated more vulnerabilities.<br/><br/> - Early in 2025 we organized a live hacking event (Zero Day Quest), working with expert security researchers to uncover critical bugs, driving improvement across key platforms.
**2. Advance transparency of cloud vulnerabilities**<br/><br/>Increase transparency of mitigated cloud vulnerabilities with the adoption and release of Common Weakness Enumeration (CWE) and Common Platform Enumeration (CPE) industry standards. Release high severity Common Vulnerabilities and Exposures (CVEs) affecting the cloud. | - We continue to advance transparency by publishing CVEs enriched with Common Weakness Enumeration and Common Platform Enumeration. Since January 2025, we've published 1096 CVEs, with 53 no-action cloud CVEs.<br/>- Internal Microsoft researchers discovered more than 48% of these vulnerabilities. The adoption of industry standards enables customers and the broader ecosystem to better understand root causes and impacted products. Investments in bounty programs and live hacking events, such as the Zero Day Quest, further demonstrate our commitment to openness and proactive security improvements across key cloud environments.
**3. Enhance public messaging and engagement**<br/><br/>Improve the accuracy, effectiveness, transparency, and velocity of public messaging and customer engagement. | - The CSMO has improved customer engagement and incident communication by partnering with internal Microsoft Support and Security Resilience teams.<br/>- By standardizing incident communications, the CSMO has increased speed and transparency in response efforts. These advances, combined with expanded executive engagement and collaboration with global security advisors, help ensure rapid, effective public messaging and proactive customer engagement during security incidents. Additionally, the CSMO proactively notifies customers of critical risks, ensuring CISOs receive timely updates. 


## Next steps

Learn about [adopting Microsoft SFI best practices](secure-future-initiative-adoption.md).