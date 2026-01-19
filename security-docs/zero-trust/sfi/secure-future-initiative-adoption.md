---
title: Adopting Microsoft Secure Future Initiative (SFI) best practices
description: Learn about adopting Microsoft's Secure Future Initiative (SFI) best practice patterns. 
ms.date: 01/19/2026
ms.service: security
author: rayne-wiselman
ms.author: raynew
ms.subservice: zero-trust
ms.topic: conceptual
---

# Adopt Secure Future Initiative best practices

Microsoft's Secure Future Initiative (SFI) launched as a multiyear effort to further secure the way that Microsoft designs, builds, tests, and operates its infrastructure, products, and services.

This article shows how your organization might consider and adopt some of these SFI best practices.

> [!NOTE]
> - We're continuously working on content that details each best practice pattern within pillars. Links to these best practices are included where available and we're planning to publish more over time.
> - Before you start, [get an overview of SFI](secure-future-initiative-overview.md).

## Protect identities and secrets

Initiatives under this pillar aim to reduce the risk of unauthorized access by implementing and enforcing standards to control user/app authentication and authorization, and to harden the identity and secrets infrastructure. The Microsoft SFI initiative work focuses on:

- Passwordless, phishing-resistant multifactor authentication (MFA) (FIDO2 passkeys, certificate-based auth) for all users.
- Deprecation of passwords, SMS OTP, etc.
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
Centralize logs (identity, Key Vault, network, endpoint, etc) into Microsoft Sentinel or another security information and event management (SIEM) solution.<br/><br/>  Use analytics and ML-based threat detection for abnormal behavior<br/><br/>Standardize detection templates and automation<br/><br/>Consolidate visibility across assets and incidents<br/><br/>Use threat feeds to enrich detection and alerting | <br/><br/>**Verify explicitly**: Continuous validation of behavior and state against normal baselines.<br/><br/> **Use least privilege**: Detections inform adaptive policies that restrict access automatically.<br/><br/>**Assume breach**: Assume that attackers might already have access, and detect attack movement quickly.| <br/><br/>Ongoing tuning to avoid alert fatigue.<br/><br/> Costs for licensing and ingestion volume for Sentinel/SIEM.<br/><br/> Continuous refinement and analyst training for detection logic. | [Inventory production infrastructure](/security/zero-trust/sfi/complete-production-infrastructure-inventory)<br/><br/>[Set security log retention standards](/security/zero-trust/sfi/security-log-retention-standards)<br/><br/>[Detect and respond to anomalies](/security/zero-trust/sfi/rapid-anomaly-detection-response)<br/><br/>[Centralize access to security logs](/security/zero-trust/sfi/centralize-access-to-security-logs).



## Accelerate response and remediation

Initiatives under this pillar aim to minimize the duration and impact of security incidents through automation, orchestration, and systemic learning. The Microsoft SFI initiative focuses on:

- Rapid coordinated incident response and patching, with automation of common mitigations.
- Systematic post-incident learning, and "secure-by-default” changes integrated into products and services.
- Continuous improvement loops and cross-team incident-response playbooks.

### Adopt best practices

Key adoption best practices for identity and secrets protection are summarized in the following table.

**Key practices** | **Zero Trust** | **Adoption considerations** | **Detailed guidance**
--- | --- | --- | ---
Develop and test incident response playbooks for common attack types.<br/><br/>  Automate token revocation, key rotation, and account disablement workflows.<br/> Tie vulnerability management processes to business risk and exposure.<br/><br/>  Adopt post-incident learning loops, and integrate lessons into policy and code baselines.<br/><br/>  Design communication plans (legal, PR, technical, etc.) for significant breaches.<br/><br/> Run regular tabletop exercises with leadership and technical teams. | <br/><br/>**Verify explicitly**: Continuously reassess and revoke trust as needed after a security event.<br/><br/> **Use least privilege**: Automate containment by restricting or removing access rapidly.<br/><br/>**Assume breach**: Treat every incident as a catalyst for architectural and procedural hardening. | Disciplined coordination is needed between the security operations center (SOC), engineering, and leadership.<br/><br/> Automation of remediation actions must balance speed and risk of disruption.<br/><br/> Time and learning can result from tabletop exercises that might expose procedural gaps, but deliver large maturity gains. | <br/><br/><br/><br/>[Accelerate vulnerability mitigation](/security/zero-trust/sfi/accelerate-vulnerability-mitigation).



## Next steps

Review [what's new in SFI](secure-future-initiative-whats-new.md).