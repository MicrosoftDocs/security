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

The Secure Future Initiative (SFI) initiative launched in November 2023 as a multiyear effort to increasingly secure the way in which Microsoft designs, builds, tests, and operates its products and services.

For the first year or so after the launch, we shifted to security as a number one priority across Microsoft, focused on intensive security training, and dedicated extensive internal engineering resources to improve security and mitigate risk across Microsoft.

Over time, SFI efforts continue to evolve as a cross-company initiative in structured waves, keeping pace with shifts in the threat landscape. The ongoing evolution informs security innovation, development, and best practices across Microsoft. It also provides Microsoft with ongoing opportunities to work with customers and with the broader security industry to strengthen our collective defenses.


## SFI progress reports

We produces periodic SFI progress reports with detailed information about initiative updates and progress. Reports cover new security capabilities, news from engineering pillars, mapping to the NIST Cybersecurity Framework, and implementation guidance aligned with Zero Trust principles.

- [Get a summary of the latest updates](ecure-future-initiative-whats-new.md) in What's new in SFI?
- [Read the latest SFI blog](https://www.microsoft.com/security/blog/2025/11/10/securing-our-future-november-2025-progress-report-on-microsofts-secure-future-initiative/), and [review the SFI November 2025 report](https://www.microsoft.com/trust-center/security/secure-future-initiative/sfi-progress-report-november-2025).
- [SFI report - April 2025](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/sfi-april-2025-progress-report.pdf).
- [SFI report - September 2024](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/SFI_September_2024_progress_report.pdf).


## SFI architecture

SFI architecture design focuses on a set of security principles that are adopted and integrated into Microsoft culture and governance. These security principles are applied to a set of focus areas (engineering pillars) by means of processes, standards, and continuous improvements.

:::image type="content" source="../media/secure-future-initiative/secure-future-initiative-overview.png" alt-text="Diagram summarizing the secure future initiative (SFI)." border="true":::


## Security principles

SFI focuses on these principles.

:::image type="content" source="../media/secure-future-initiative/secure-future-initiative-security-principles.png" alt-text="Diagram summarizing the secure future initiative (SFI) principles." border="true":::

We use these principles to:

- **Innovate**: Build security features by design into Microsoft platforms and services.
- **Implement**: Implement security innovations in Microsoft products and features with secure defaults and enforced standards.
- **Guide**: Provide customers with guidance and best practices to deploy, operate, and continuously improve security. 


## SFI pillars, Zero Trust, and NIST

The SFI initiative focuses on six prioritized engineering pillars. Multiple objectives are aligned with each pillar. Each objective represents a significant effort to improve security and reduce risk for Microsoft and our customers in a specific pillar area.

The pillars and objectives clearly align with Microsoft's [Zero Trust principles](/zero-trust/zero-trust-overview) and the [National Institute of Standards and Technology (NIST) Cybersecurity Framework](https://www.nist.gov/cyberframework).

### NIST functions

The following table summarizes core NIST functions and categories, taken from the [downloadable CSF 2.0 article](https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf).

**Function** | **Category**
--- | ---
**Govern (GV)**<br/><br/>Establish policies, procedures, and culture for managing cybersecurity risk, aligning it with overall business strategy and outcomes of the other NIST functions. | GV.OC-Organizational context.<br/><br/>GV.RM-Risk Management STrategy<br/><br/>GV.RR-Roles, Responsibilites, and Authorities.<br/><br/>GV.PO-Policy<br/><br/>GV.OV-Oversight<br/><br/>GV.SC-Cybersecurity Supply Chain Risk Management.
**Identify (ID)**<br/><br/>Understand assets, systems, data, and potential threats to build a strong organizational understanding of cyber risk. | ID.AM-Asset Management.<br/><br/>ID.RA-Risk Assessment<br/><br/>ID.IM-Improvement.
**Protect (PR)**<br/><br/> Implement safeguards like access controls, data security, and training to ensure critical services can be delivered. | PR.AA-Identity management, Authentication, and Access Control.<br/><br/>PR.AT-Awareness and Training<br/><br/>PR.DS-Data Security.<br/><br/>PR.PS-Platform Security<br/><br/>PR.IR-OTechnology Infrastructure Resilience.
**Detect (DE)**<br/><br/> Develop and implement activities to identify the occurrence of cybersecurity events, such as continuous monitoring. | DE.CM-Continuous Monitoring.<br/><br/>DE.AE-Adverse Event Analysis.
**Respond (RS)**<br/><br/> Take action regarding a detected incident, including analysis, containment, eradication, and communication. | RS.MA-Incident Management.<br/><br/>RS.AN-Incident Analysis<br/><br/>RS.CO-Incident Respoonse Reporting and Communcation.<br/><br/>RS.MI-Mitigation.
**Recover (RC)**<br/><br/>Restore systems and operations post-incident, emphasizing planning, communication, and improvement to minimize disruption. |RC.RP-Incident Recovery Plan Execution.<br/><br/>RC.CO-Incident Recovery Communication.

## Pillar mapping

**Pillar** | **Zero Trust principle** | **NIST CSF Function**
--- | --- | --- 
**1. Protect identities and secrets**<br/> Ensure that only verified and authorized identities can access resources.  | **Verify explicitly**: Enforce continuous, context-aware, passwordless authentication (Windows Hello, FIDO2 passkeys, certificate etc.).<br/><br/>**Use least privilege**: Reduce overprivileged identities and enforce privileged identity management/just-in-time access.<br/><br/>**Assume breach**: Rotate credentials rapidly and use short-lived tokens to reduce blast radius. | **Protect (PR)**: Implement controls to secure credentials, secrets, and access.<br/><br/>**Detect (DE)**: Continuously monitor identity activities for anomalies.
**2. Protect tenants and isolate systems**<br/> Minimize compromise blast radius by ensuring that tenants, environments, and systems are independently isolated and secured, with no implicit trust between them.  | **Verify explicitly**: Apply inter-tenant authentication and authorization with explicit approval and logging.<br/><br/>**Use least privilege**: Limit access between environments to approved paths only.<br/><br/>**Assume breach**: Use tenant isolation as a containment boundary. | **Identify (ID)**: Discover tenant and production assets.<br/><br/>**Protect (PR)**: Apply isolation, seigmentation, and strong boundaries.<br/><br/>**Detect (DE)**: Look for isolation boundary violations or lateral movement.
**3. Protect networks**<br/> Limit lateral movement and unauthorized access by means of granular network segmentation and identity-aware connectivity.  | **Verify explicitly**: Shift from implicit network trust to policy-based, identity-verified connections.<br/><br/>**Use least privilege**: Enforce micro-segmentation and just-enough access for workloads and endpoints.<br/><br/>**Assume breach**: Treat every network zone as potentially hostile. Isolate high-value assets and enforce strict egress control. | **Identify (ID)**: Inventory and understand networking assets.<br/><br/>**Protect (PR)**: Apply network security controls (segementation, encryption etc).
**4. Protect engineering systems**<br/> Secure the entire software development lifecycle (SDLC) and delivery lifecycle by ensuring that code, build systems, and pipelines are tamper-resistant, auditable, and trustworthy.  | **Verify explicitly**: Authenticate every action in the SDLC, from code commits to builds, with traceable, signed identities.<br/>**Use least privilege**: Restrict developer, agent, and pipeline access based on role and build context.<br/><br/>**Assume breach**: Segregate build systems and enforce code signed and reproducible builds to prevent tampering. | **Identify (ID)**: Understand build/test/deployment systems and dependencies.<br/><br/>**Protect (PR)**: Secure software pipelines, development tooling and artifacts.<br/><br/>**Govern (GV)**: Apply engineering policies, standards, secure design.
**5. Monitor and detect threats**<br/> Quickly detect, correlate, and prioritize security threats across Microsoft systems by unifying telemetry and analytics.  | **Verify explicitly**: Use telemetry-driven, continuous validation of user, device, and workload behavior.<br/><br/>**Use least privilege**: Enforce adaptive access control with detection and dynamic conditional access policies.<br/><br/>**Assume breach**: Detect anomalies and behavior deviations on the premise that attackers might already have access to resources. | **Identify (ID)**: Maintain awareness of all monitored systems.<br/><br/>**Protect (PR)**: Ensure protective controls generate telemetry.<br/><br/>**Detect (DE)**: Analyze logs and alerts to identity threats.<br/><br/>**Respond (RS)**: Detect trigger response workflows.
**6. Accelerate response and remediation**<br/> Minimize the impact and duration of security incidents with automation, coordinated response, and continuous learning..  | **Verify explicitly**: Continuously reassess trust in identities, devices, and systems after detection events.<br/><br/>**Use least privilege**: Automate token revocation, key rotation, and access removal during response.<br/><br/>**Assume breach**: Continuously feed incident learnings into system improvments for rapid containment and ongoing hardening. | **Identify (ID)**: Understand scope and assets for response. Track changes and re-baseline post-incident.<br/><br/>**Recover (RC)**: Restore secure operations after incidents. Remediate vulnerabilities and ensure resilience.<br/><br/>**Detect (DE)**: Analyze logs and alerts to identity threats.<br/><br/>**Respond (RS)**: Detect trigger response workflows.br/><br/>**Govern (GV)**: Apply lessons in governance and standards.


### Pillar 1: Protect identities and secrets

This pillar aims to strengthen trust in every identity and credential used across Microsoft systems by eliminating weaknesses in how accounts, tokens, and secrets are issued, stored, and used. It reduces the risk of unauthorized access by enforcing standards to harden the identity and secrets infrastructure, and to control user and application authentication and authorization. 

Microsoft objectives for this pillar are summarized in the following table. You can see how each objective maps toZero Trust principles, and to  [NIST CSF functions and categories](https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf).

**Objective** | **Zero Trust** | **NIST mapping**
--- | --- | --- 
**1. Protect cryptographic signing keys**<br/><br/>Protect identity infrastructure signing and platform keys with rapid and automatic rotation of identity infrastructure keys, using hardware storage and protection. | **Verify explicitly**: Protect identity signing assets. Strong attestation of keys built into workflow.<br/><br/>**Assume breach**: Protect keys as if compromise can occur, using hardware‑assisted isolation. | **Protect-Identity Management, Authentication, and Access Control (PR.AA-04)**: Keys are only accessible to verified identities.<br/><br/>**Protect:Platform Security (PR.PS-01)**: Protect cryptographic assets on hardware/software platforms.
**2. Adopt standard SDKs for identity**<br/><br/>Strengthen identity standards and drive standards adoption with the use of standard SDKs across applications, so that apps and services use a uniform, hardened library for validating tokens. |  **Verify explicitly**: Standard validated libraries reduce variability and risk. Use consistent validation.<br/><br/>**Assume breach**: Reduces attack surface from custom implementations. | **PR.AA-01**: Define rules for SDK access.<br/><br/>**PR.AA-02**: Manage accounts used in SDK validation.<br/><br/>**PR.AA-03**: Enforce token validation through standardized SDK.
**3. Enforce phishing-resistant MFA**<br/><br/>Ensure user accounts are protected with securely manEnforcaged, phishing-resistant MFA.  | **Verify explicitly**: Strong authentication techniques verify user identity every access attempt.<br/><br/>**Use least privilege**: MFA strengthens least‑privilege enforcement by reducing unauthorized access. | **PR.AA-01**: Policies require MFA.<br/><br/>**PR.AA-03**: MFA enforced on all accounts.
**4. Safe secrets standard**<br/><br/> Shift away from long-lived secrets such as service account credentials to ensure that applications are protected with system-managed credentials such as managed identities. | **Use least privilege**: Restrict secret access. Avoid hard‑coded or persistent credentials.<br/><br/>**Assume breach**: Treat every secret as potentially compromised unless strongly guarded. | **PR.AA-04**: Only verified identities can access secrets.<br/><br/>**Protect:Data Security (PR.DS-01)**: Secrets are encrypted and protected.<br/><br/>**PR.PS-01**: Secret management systems implemented are secure platforms to protect sensitive data.
**5. Stateful validation for identity tokens**<br/><br/>Ensure identity tokens are protected with stateful and duration validation. | **Verify explicitly**: Fully validate identity tokens at every enforcement point.<br/><br/>**Assume breach**: Ensure invalid or malformed tokens are rejected. | **PR.AA-03**: Token validation enforced in access decisions.<br/><br/>**Detect:Adverse Event Analysis (DE.AE-02)**: Anomalous activity detection. Detect unusual token usage.<br/><br/> **DE-AE-03**: Uauthorized activity detection. Monitor for misuse or compromised tokens.
**6. Fine-grained key partitioning**<br/><br/>Adopt more fine-grained partioning of identity signing keys and platform keys. | **Use least privilege**: Partitioning limits privilege scopes for key usage.<br/><br/>**Assume breach**: Limits impact if key segment is compromised. | **PR.AA-04**: Identity proofing. Verify identities accessing each key partition.<br/><br/>**PR.AA-05**: Separation of duties. Isolate key operations to enforce limited privileges.
**7. Quantum-safe PKI systems**<br/><br/>Ensure identity and certificate PKI systems are ready for a post-quantum cryptography world. | **Verify explicitly**: Use post‑quantum cryptography for identity assertions.<br/><br/>**Assume breach**: Anticipate future threats; prepare for stronger resistance. | **PR.AA-04**: Identity proofing. Only authorized identities management PKI operations.


### Pillar 2: Protect tenants and isolate systems

The goal of this pillar is to contain potential threat blast radius by preventing lateral movement or privilege escalation. It ensures that tenant-level security boundaries are correctly configured, hardened, and isolated. Microsoft objectives for this pillar are summarized in the following table.

**Objective** | **Zero Trust** | **NIST mapping**
--- | --- | --- 
**1. Remove legacy systems that risk security**<br/><br/> Maintain the security posture and commercial relationship of tenants by removing all unused, aged, or legacy systems. | **Verify explicitly**: All identity and resource systems are authenticated and validated through modern control planes.<br/><br/>**Use least privilege**: Eliminates old systems without modern, fine‑grained controls. <br/><br/>**Assume breach**: Removes legacy trust paths and minimizes blast radius. | **Identify:Asset Management (ID.AM-02)**: Inventory of organizational resources. Track tenant and resource onboarding and disused assets.<br/><br/>**ID.AM-08**: Resource lifecycle management. Track, manage, and decommission tenants/apps safely. <br/><br/>**PR.PS-01**: Platform Security. Secure platforms and services on a modern foundation.
**2. Secure all tenants and their resources**<br/><br/> Protect Microsoft, acquired, and employee-created tenants, commerce accounts, and tenant resources in accordance with security best practice baselines. |  **Verify explicitly**: Authenticate all tenant‑to‑tenant interactions.<br/><br/>**Use least privilege**: Policies and segmentation limit permissions across environments. <br/><br/>**Assume breach**: Tenant boundaries assume potential compromise and are designed to contain lateral movement. | **ID.AM-08**: Resource lifecycle management. Maintain defined tenant resource lifecycles. <br/><br/>**PR.AA-01**: Access control policy. Define tenant access policies.<br/><br/>**PR.AA-05**: Separation of duties. Limit administrative privilege across tenants.<br/><br/>**Privacy-Infrastructure resilience (PR.IR-01)**: Improve platform resilience against misuse or misconfiguration. 
**3. Higher security for Entra ID apps**<br/><br/>Manage Microsoft Entra ID applications with a high and consistent security bar. |  **Verify explicitly**: Enforce strong authentication and app vetting.<br/><br/>**Use least privilege**: App permissions restricted to minimal necessary rights. <br/><br/>**Assume breach**: App access designed with containment and monitoring. | **PR.AA-01**: Access control policy. Govern app access consistently.<br/><br/>**PR.AA-03**: Access enforcement. Enforce app authentication controls.
**4. Eliminate identity lateral movement**<br/><br/>Eliminate identity lateral movement pivots between tenants, environments, and clouds.  | **Verify explicitly**: Validate every token and trust boundary crossing.<br/><br/>**Use least privilege**: imit identity reuse and privilege escalation across tenants. <br/><br/>**Assume breach**: Design boundaries to contain identity misuse. | **PR.AA-03**: Access enforcement. Block unauthorized lateral authentication.
**5. Continuous least-privilege enforcement**<br/><br/>Ensure continuous least-privilege access enforcement for apps and users.  | **Verify explicitly**: Policies ensure least privilege decisions are verified at every access.<br/><br/>**Use least privilege**: Core outcome of this objective — enforce only necessary permissions. | **PR.AA-03**: Access enforcement. Enforce minimal privileges.
**6. Secure devices used for access**<br/><br/> Adopt fine-grained partitioning of identity signing keys and platform keys. Ensure that only secure, managed, healthy devices are granted access to Microsoft tenants.  | **Verify explicitly**: ach device identity is validated and continuously assessed.<br/><br/>**Use least privilege**: Device posture gating ensures minimal risk access. | **PR.PS-01**: Platform Security. Devices and endpoints hardened per secure baseline to reduce risk.<br/><br/>**PR.IR‑01**: Infrastructure Resilience. Endpoints resilient to compromise and aligned to service baselines


## Pillar 3: Protect networks

This pillar aims to limit adversary movement and unauthorized access across corporate networks. Networks are segmented and isolated with fine-grained network controls. Every connection is verified, controlled, and continuously monitored. Microsoft objectives for this pillar are summarized in the following table.

**Objective** | **Zero Trust** | **NIST mapping**
--- | --- | --- 
**1. Complete network device inventory and asset lifecycle management**<br/><br/>Secure Microsoft production networks and systems connected to networks with improved network isolation, monitoring, accurate inventory, and secure operations.  | **Verify explicitly**: Know what devices are present and who/what they connect to.<br/><br/>**Assume breach**: Full inventory supports detection and containment of breaches. | **ID.AM-02**: Inventory of organizational resources. All network devices are inventoried and tracked. 
**2. Strengthen security through enhanced network isolation and controls**<br/><br/>Apply identity-aware network isolation and microsegmentation to Microsoft production environments, creating additional layers of defense against attackers. |  **Verify explicitly**: Authenticate and authorize network flows before allowing communication. <br/><br/>**Use least privileged access**: Restrict lateral movement and limit network access rights.<br/><br/>**Assume breach**: Assume attackers may be in the network; isolate segments for containment. | **PR-PS-02**: Platform Security. Secure network platform configurations help enforce isolation and protect network boundaries. (Platform security covers network protection technologies such as segmentation firewalls, ACLs, and infrastructure controls.)
**3. Accelerate adoption of Network Security Perimeter (NSP)**<br/><br/>Place entries resources under modern perimeter enforcement and segmentation to ensure network traffic is validated and only allowed where necessary to reduce the risk of lateral movement and unauthorized access.   | **Verify explicitly**: NSP enforces strong validation of traffic entering protected segments. <br/><br/>**Use least privileged access**: Only necessary traffic is allowed to traverse network boundaries.<br/><br/>**Assume breach**: Perimeter enforcement assumes threat presence and restricts spread. | **PR-PS-01**: Platform Security. NSP technologies and perimetral controls are part of secure platform defenses. (These technologies enforce network segmentation and traffic policies to protect infrastructure.)
**4. Improve network acccess controls and protective technologies**<br/><br/>Strengthen network defenses with modern firewalling, segmentation policies, and platform-level enforcement, ensuring that only authorized traffic can flow and that potential breaches are contained. | **Verify explicitly**: Access control policies verify traffic flows and endpoints. <br/><br/>**Use least privileged access**: Policy enforcement limits access to minimal required paths.<br/><br/>**Assume breach**: Contain attacks via strong network controls and visibility. | **PR.AA-03**: Access enforcement. Enforce network access decisions.br/><br/> **PR.PS-01**: Platform Security. Infrastructure (firewalls, NSGs, segmentation) enforced at platform level.


## Pillar 4 - Protect engineering systems

This pillar ensures software lifecycle security across code, build systems, and pipelines. Every software artifact is verifiably authentic and securely produced in an isolated, monitored environment to ensure the integrity of the supply chain. Microsoft objectives for this pillar are summarized in the following table.

**Objective** | **Zero Trust** | **NIST mapping**
--- | --- | --- 
**1. Complete software asset inventor**<br/><br/>Build and maintain an inventory of software assets used to deploy Microsoft products and services.  | **Verify explicitly**:Know every engineering asset and associate it with identity/context.<br/><br/>**Assume breach**: Full visibility supports rapid detection and containment. | **ID.AM-02**: Inventory of organizational resources. All engineering systems are inventoried. (Supports accurate asset visibility and risk management.) 
**2. Zero trust for source code access** <br/><br/>Ensure secure access to source code and engineering systems infrastructure with Zero Trust principles and least-privilege access policies. | **Verify explicitly**: Enforce strong authentication and conditional access for source code access.<br/><br/>**Use least privilege access**: Minimize standing privileges and use just‑in‑time elevation.<br/><br/>**Assume breach**: Assume credential risk and enforce strict access guards. | **PR.AA-01**: Access control policy. Policies govern source code access.<br/><br/>**PR.AA-02**: Account management. Manage engineering accounts securely. <br/><br/>**PR.AA-03**: Access enforcement. Enforce source code access rules. <br/><br/>**PR.AA-04**: Identity proofing. Verify identities accessing code. <br/><br/>**PR.AA-05**: Separation of duties. Reduce conflicting privileges.<br/><br/>**PR.AA-06**: Credential protection. Protect credentials used in engineering access. <br/><br/>**PR.DS-01**: Data‑at‑rest protection. Source code and related data secured. <br/><br/>**PR.DS-02**: Data‑in‑transit protection. Secure transmission of code and artifacts.<br/><br/>**PR.DS-10**: Data security assurance. Controls ensure data integrity and protection throughout engineering systems.
**3. Secure code deployment**<br/><br/>Protect source code that deploys Micorsoft production environments with security best practices. |  **Verify explicitly**: Authenticate all signing and deployment actions.<br/><br/>**Assume breach**: Design deployment controls assuming system compromise.| **PR.AA-04**: Identity proofing. Ensure that deployment and signing actions are by verified identities.<br/><br/> **PR.PR-06**: Platform Security. Secure platforms (build & deploy systems) enforce protective controls.
**4.Standardize secure development pipelines**<br/><br/>Apply network isolation and microsegmentation to Microsoft production environments. Secure development, build, test, and release environments with standardized, governed pipelines, and infrastructure isolation.|  **Verify explicitly**: Validate build and release pipelines and ensure compliance with security guardrails.<br/><br/> **Use least privilege**: Limit access within pipelines and enforce standardized workflows that reduce unnecessary rights.<br/><br/> **Assume breach**: Pipeline isolation and governance contain potential compromise.| **PR.DS-01**: Data‑at‑rest protection: Protect pipeline artifacts and metadata.<br/><br/>**PR.DS-02**: Data‑in‑transit protection: Secure communication between pipeline stages.<br/><br/>**PR.DS-10**: Data security assurance: Pipeline controls ensure consistent data protection.<br/><br/> **PR.IR-01**: Infrastructure resilience: Pipeline systems resilient to attacks and misconfigurations.<br/><br/>**PR.PS-06**: Platform Security: Secure build/run platforms enforce isolation and protection.
**5. Protect the software supply chain**<br/><br/>Secure the software supply chain to protect Microsoft production environments. | **Use least privilege**: Limit access and usage of third‑party components.<br/><br/> **Assume breach**: Protect supply chain and assume component compromise risk.| **Govern-Cybersecurity Supply Chain Risk Management (GV.SC-01)**: Supply chain governance: Source component selection and oversight.<br/><br/>**GV.SC-02**: Supplier risk assessment: Evaluate risks across software supply partners.<br/><br/>**GV.SC-03**: Contractual security requirements: Enforce vendor security terms.<br/><br/> **GV.SC-04**: Shared responsibility models: Define roles for secure engineering.<br/><br/>**GV.SC-07**: Transparency and reporting: Share security findings and metrics with stakeholders.<br/><br/>**GVS.C-09**: Continuous supply chain monitoring: Monitor third‑party components and flows.<br/><br/>**Identity-Risk Assessment (ID.RA-10)**: Risk assessment: Ongoing risk analysis across the supply chain.<br/><br/>**.PR.PS-06**: Platform Security: Secure build/run platforms enforce isolation and protection.

## Pillar 5: Monitor and detect threats

This pillar aims to continuously monitor and rapidly detect security threats. Focus is on on proactive, intelligence-driven detection to surface attacker behavior early,  and enable rapid coordinated investigation across all business areas. Microsoft objectives for this pillar are summarized in the following table.

**Objective** |  **Zero Trust** | **NIST mapping**
--- | --- | --- 
**1. Centralize telemetry and infrastructure tracking**<br/><br/>Maintain a current resource inventory across Microsoft production infrastructure and services. | **Verify explicitly**:Ensure logging and telemetry originate from authenticated, trusted sources.<br/><br/>**Assume breach**: Centralized logs support detection even when attackers evade initial controls.| **ID.AM-02**: Inventory of organizational resources: Maintain a complete view of monitored assets.<br/><br/>** **Detect:Continuous Monitoring (DE-AM-02)**: Monitoring processes. Centralized telemetry supports continuous observation.
**2. Retain logs for forensic analysis and trending**<br/><br/>Retain security logs for at least two years, and make six months of appropriate logs available. | **Verify explicitly**: Retained logs allow verification of past events and patterns.<br/><br/>**Assume breach**: Long retention ensures detection windows cover advanced stealth techniques.| **DE.CM-02**: Inventory of organizational resources: Maintain a complete view of monitored assets.<br/><br/>** **DE/DP-01






























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