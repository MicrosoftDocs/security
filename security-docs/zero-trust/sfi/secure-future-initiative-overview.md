---
title: Microsoft Secure Future Initiative (SFI) overview
description: Get an overview of Microsoft's Secure Future Initiative (SFI) and best practices cybersecurity. 
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

The Secure Future Initiative (SFI) initiative launched in November 2023 as a multiyear effort to increasingly secure the way in which Microsoft designs, builds, tests, and operates its products and services.

For the first year or so after the launch, we shifted to security as a critical priority across Microsoft. We focused on internal security training, and dedicated extensive engineering resources to improve security and mitigate risk across the company.

Over time, SFI efforts continue to evolve as a cross-company initiative in structured waves, keeping pace with shifts in the threat landscape. The ongoing evolution informs security innovation, development, and best practices across Microsoft. It also provides us with ongoing opportunities to work with customers and the broader security industry to strengthen our collective defenses.


## SFI progress reports

We produce periodic SFI progress reports about initiative updates and progress. Reports cover new security capabilities, news from engineering pillars, mapping to the NIST Cybersecurity Framework, and implementation guidance aligned with Zero Trust principles.

- Get a summary of the latest updates and progress over time in [What's new in SFI?](secure-future-initiative-whats-new.md)
- [Read the latest SFI blog](https://www.microsoft.com/en-us/security/blog/2025/11/10/securing-our-future-november-2025-progress-report-on-microsofts-secure-future-initiative/), and [review the latest SFI report from November 2025](https://www.microsoft.com/trust-center/security/secure-future-initiative/sfi-progress-report-november-2025).
- View earlier reports:

    - [SFI report - April 2025](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/sfi-april-2025-progress-report.pdf).
    - [SFI report - September 2024](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/SFI_September_2024_progress_report.pdf).


## SFI architecture

SFI architecture design focuses on a set of security principles that are adopted and integrated into Microsoft culture and governance. These security principles are applied to a set of focus areas (engineering pillars) by means of processes, standards, and continuous improvements.

:::image type="content" source="../media/secure-future-initiative/secure-future-initiative-overview.png" alt-text="Diagram summarizing the secure future initiative (SFI)." border="true":::


## Security principles

SFI focuses on these principles.

:::image type="content" source="../media/secure-future-initiative/secure-future-initiative-security-principles.png" alt-text="Diagram summarizing the secure future initiative (SFI) principles." border="true":::

We use these principles to:

- **Innovate**: Build by-design security features into Microsoft platforms and services.
- **Implement**: Introduce security innovations in Microsoft products with new features, secure defaults, and enforced standards.
- **Guide**: Provide customers with guidance and best practices to deploy, operate, and continuously improve security.


## SFI pillars, Zero Trust, and NIST

The SFI initiative focuses on six prioritized engineering pillars. Multiple objectives align with each pillar. Each objective represents a significant effort to improve security and reduce risk for Microsoft and our customers in a specific pillar area.

The pillars and objectives clearly align to Microsoft's [Zero Trust principles](../zero-trust-overview.md) and the [National Institute of Standards and Technology (NIST) Cybersecurity Framework](https://www.nist.gov/cyberframework). 

## Pillar mapping

The following table shows the pillar mapping. Get more details on NIST function acronyms in [the next section](#nist-functions).

**Pillar** | **Zero Trust principle** | **NIST CSF Function**
--- | --- | --- 
**1. Protect identities and secrets**<br/><br/> Ensure that only verified and authorized identities can access resources.  | **Verify explicitly**: Enforce continuous, context-aware, passwordless authentication (Windows Hello, FIDO2 passkeys, certificate etc.).<br/><br/>**Use least privilege**: Reduce overprivileged identities and enforce privileged identity management/just-in-time access.<br/><br/>**Assume breach**: Rotate credentials rapidly and use short-lived tokens to reduce blast radius. | **PR**: Implement controls to secure credentials, secrets, and access.<br/><br/>**DE**: Continuously monitor identity activities for anomalies.
**2. Protect tenants and isolate systems**<br/><br/> Minimize compromise blast radius by ensuring that tenants, environments, and systems are independently isolated and secured, with no implicit trust between them.  | **Verify explicitly**: Apply inter-tenant authentication and authorization with explicit approval and logging.<br/><br/>**Use least privilege**: Limit access between environments to approved paths only.<br/><br/>**Assume breach**: Use tenant isolation as a containment boundary. | **ID**: Discover tenant and production assets.<br/><br/>**PR**: Apply isolation, seigmentation, and strong boundaries.<br/><br/>**DE**: Look for isolation boundary violations or lateral movement.
**3. Protect networks**<br/><br/> Limit lateral movement and unauthorized access by means of granular network segmentation and identity-aware connectivity.  | **Verify explicitly**: Shift from implicit network trust to policy-based, identity-verified connections.<br/><br/>**Use least privilege**: Enforce micro-segmentation and just-enough access for workloads and endpoints.<br/><br/>**Assume breach**: Treat every network zone as potentially hostile. Isolate high-value assets and enforce strict egress control. | **ID**: Inventory and understand networking assets.<br/><br/>**PR**: Apply network security controls (segementation, encryption etc).
**4. Protect engineering systems**<br/><br/> Secure the entire software development lifecycle (SDLC) and delivery lifecycle by ensuring that code, build systems, and pipelines are tamper-resistant, auditable, and trustworthy.  | **Verify explicitly**: Authenticate every action in the SDLC, from code commits to builds, with traceable, signed identities.<br/><br/>**Use least privilege**: Restrict developer, agent, and pipeline access based on role and build context.<br/><br/>**Assume breach**: Segregate build systems and enforce code signed and reproducible builds to prevent tampering. | **ID**: Understand build/test/deployment systems and dependencies.<br/><br/>**PR**: Secure software pipelines, development tooling and artifacts.<br/><br/>**GV**: Apply engineering policies, standards, secure design.
**5. Monitor and detect threats**<br/><br/> Quickly detect, correlate, and prioritize security threats across Microsoft systems by unifying telemetry and analytics.  | **Verify explicitly**: Use telemetry-driven, continuous validation of user, device, and workload behavior.<br/>**Use least privilege**: Enforce adaptive access control with detection and dynamic conditional access policies.<br/><br/>**Assume breach**: Detect anomalies and behavior deviations on the premise that attackers might already have access to resources. | **ID**: Maintain awareness of all monitored systems.<br/><br/>**PR**: Ensure protective controls generate telemetry.<br/><br/>**DE**: Analyze logs and alerts to identity threats.<br/><br/>**RS**: Detect trigger response workflows.
**6. Accelerate response and remediation**<br/><br/> Minimize the impact and duration of security incidents with automation, coordinated response, and continuous learning..  | **Verify explicitly**: Continuously reassess trust in identities, devices, and systems after detection events.<br/><br/>**Use least privilege**: Automate token revocation, key rotation, and access removal during response.<br/><br/>**Assume breach**: Continuously feed incident learnings into system improvments for rapid containment and ongoing hardening. | **ID**: Understand scope and assets for response. Track changes and re-baseline post-incident.<br/><br/>**RC**: Restore secure operations after incidents. Remediate vulnerabilities and ensure resilience.<br/><br/>**RS**: Detect trigger response workflows.<br/><br/>**GV**: Apply lessons in governance and standards.

### NIST functions

The following table summarizes core NIST functions and categories, taken from the [downloadable CSF 2.0 article](https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf).

**Function** | **Category**
--- | ---
**Govern (GV)**<br/>Establish policies, procedures, and culture for managing cybersecurity risk, and aligning it with overall business strategy and outcomes of the other NIST functions. | **GV.OC**-Organizational Context<br/>**GV.RM**-Risk Management Strategy<br/>**GV.RR**-Roles, Responsibilities, and Authorities.<br/>**GV.PO**-Policy<br/>**GV.OV**-Oversight<br/>**GV.SC**-Cybersecurity Supply Chain Risk Management
**Identify (ID)**<br/>Understand assets, systems, data, and potential threats to build a strong organizational understanding of cyber risk. | **ID.AM**-Asset Management<br/>**ID.RA**-Risk Assessment<br/>**ID.IM**-Improvement
**Protect (PR)**<br/>Implement safeguards like access controls, data security, and training to ensure critical services can be delivered. | **PR.AA**-Identity Management, Authentication, and Access Control.<br/>**PR.AT**-Awareness and Training<br/>**PR.DS**-Data Security.<br/>**PR.PS**-Platform Security<br/>**PR.IR**-Technology Infrastructure Resilience
**Detect (DE)**<br/> Develop and implement activities such as continuous monitoring to identify the occurrence of cybersecurity events. | **DE.CM**-Continuous Monitoring<br/>**DE.AE**-Adverse Event Analysis
**Respond (RS)**<br/> Take action regarding a detected incident, including analysis, containment, eradication, and communication. | **RS.MA**-Incident Management<br/>**RS.AN**-Incident Analysis<br/>**RS.CO**-Incident Response Reporting and Communcation.<br/>**RS.MI**-Mitigation
**Recover (RC)**<br/>Restore systems and operations post-incident, emphasizing planning, communication, and improvement to minimize disruption. |**RC.RP**-Incident Recovery Plan Execution<br/>**RC.CO**-Incident Recovery Communication

## Next steps

- Review the detailed objectives for each engineering pillar:

    - [Protect identities and secrets](secure-future-initiative-identity-overview.md).
    - [Protect tenants and isolate systems](secure-future-initiative-tenant-overview.md).
    - [Protect networks](secure-future-initiative-network-overview.md).
    - [Protect engineering systems](secure-future-initiative-engineering-overview.md).
    - [Monitor and detect threats](secure-future-initiative-threat-overview.md)
    - [Accelerate response and remediation(secure-future-initiative-response-overview.md).
- Learn about [adopting Microsoft SFI best practices](secure-future-initiative-adoption.md).