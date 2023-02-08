---
title: Security operations  | Microsoft Docs
description: Detect, respond, and recover the system when it's attacked.
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
ms.topic: article
ms.service: microsoft-365-security
---

# Security operations 

Security operations (SecOps) maintain and restore the security assurances of the system as live adversaries attack it. The tasks of SecOps are described well by the NIST Cybersecurity Framework functions of Detect, Respond, and Recover.

- **Detect** - SecOps must detect the presence of adversaries in the system, who are incentivized to stay hidden in most cases as this allows them to achieve their objectives unimpeded. This can take the form of reacting to an alert of suspicious activity or proactively hunting for anomalous events in the enterprise activity logs.

- **Respond** - Upon detection of potential adversary action or campaign, SecOps must rapidly investigate to identify whether it is an actual attack (true positive) or a false alarm (false positive) and then enumerate the scope and goal of the adversary operation.

- **Recover** - The ultimate goal of SecOps is to preserve or restore the security assurances (confidentiality, integrity, availability) of business services during and after an attack.

The most significant security risk most organizations face is from human attack operators (of varying skill levels). This is because risk from automated/repeated attacks have been mitigated significantly for most organizations by signature and machine learning based approaches built into anti-malware (though there are notable exceptions like Wannacrypt and NotPetya, which moved faster than these defenses).

While human attack operators are challenging to face because of their adaptability (vs. automated/repeated logic), they are operating at the same "human speed" as defenders, which help level the playing field.

SecOps (sometimes referred to as a Security Operations Center (SOC)) has a critical role to play in limiting the time and access an attacker can get to valuable systems and data. Each minute that an attacker has in the environment allows them to continue to conduct attack operations and access sensitive or valuable systems.

## Objective and metrics

The metrics you measure will have a significant effect on the behaviors and outcomes of SecOps. Focusing on the right measurements will help drive continuous improvement in the right areas that meaningfully reduce risk.

To ensure that SecOps are effectively containing attackers access, the objectives should focus on:

- Reducing **time to acknowledge** an alert to ensure that detected adversaries are not ignored while defenders are spending time investigating false positives.

- Reducing **time to remediate** a discovered adversary to reduce their opportunity time to conduct and attack and reach sensitive systems

- **Prioritizing** security investments into systems that have high intrinsic value (likely targets or high business impact) and access to many systems or sensitive systems (administrator accounts and sensitive users)

- Increasing focus on **proactively hunting** for adversaries as your program matures and reactive incidents get under control. This is focused on reducing the time that a higher skilled adversary can operate in the environment (for example, skilled enough to evade reactive alerts).

For more information on how Microsoft's SOC uses these metrics, see [https://aka.ms/ITSOC](https://aka.ms/ITSOC).

## Hybrid enterprise view

SecOps should ensure their tooling, processes, and analyst skill sets enable visibility across the full span of their hybrid estate.

Attackers don't restrict their actions to a particular environment when targeting an organization, they will attack resources on any platform using any method available. Enterprise organizations adopting cloud services like Azure and AWS are effectively operating a hybrid of cloud and on-premises assets.

SecOps tooling and processes should be designed for attacks on cloud and on-premises assets as well as attackers pivoting between cloud and on-premises resources using identity or other means. This enterprise-wide view will enable SecOps teams to rapidly detect, respond, and recover from attacks, reducing organizational risk.

## Leverage native detections and controls

You should favor the use of security detections and controls built into the cloud platform before creating custom detections using event logs from the cloud.

Cloud platforms evolve rapidly with new features, which can make maintaining detections challenging. Native controls are maintained by the cloud provider and are typically high quality (low false positive rate).

Because many organizations may use multiple cloud platforms and need a unified view across the enterprise, you should ensure these native detections and controls feed a centralized SIEM or other tool. We don't recommend trying to substitute generalized log analysis tools and queries instead of native detections and controls. These tools can offer numerous values for proactive hunting activities but getting to a high-quality alert with these tools requires application of deep expertise and time that could be better spent on hunting and other activities.

To complement the broad visibility of a centralized SIEM (such as Microsoft Sentinel, Splunk, or QRadar), you should leverage native detections and controls such as:

- Organizations using Azure should leverage capabilities like Microsoft Defender for Cloud for alert generation on the Azure platform.

- Organizations should leverage native logging capabilities like Azure Monitor and AWS CloudTrail for pulling logs into a central view.

- Organizations using Azure should leverage Network Security Group (NSG) capabilities for visibility into network activities on the Azure platform.

- Investigation practices should leverage native tools with deep knowledge of the asset type such as an Endpoint Detection and Response (EDR) solution, identity tools, and Microsoft Sentinel.

## Prioritize alert and log integration

Ensure that you are integrating critical security alerts and logs into SIEMs without introducing a high volume of low value data.

Introducing too much low-value data can increase SIEM cost, increase noise and false positives, and lower performance.

The data you collect should be focused on supporting one or more of these operations activities:

- **Alerts** (detections from existing tools or data required for generating custom alerts)

- **Investigation** of an incident (for example, required for common queries)

- Proactive **hunting** activities

Integrating more data can allow you to enrich alerts with additional context that enable rapid response and remediation (filter false positives, and elevate true positives, etc.), but collection is not detection. If you don't have a reasonable expectation that the data will provide value (for example, high volume of firewall denies events), you may deprioritize integration of these events.

## SecOps resources for Microsoft security services

If you are new-to-role as a security analyst, see these resources to get you started.

| Topic | Resource |
|:-------|:-----|
| SecOps planning for incident response | [Incident response planning](incident-response-planning.md) for preparing your organization for an incident. |
| SecOps incident response process | [Incident response process](incident-response-process.md) for best practices on responding to an incident. |
| Incident response workflow  | [Example incident response workflow for Microsoft 365 Defender](/microsoft-365/security/defender/incidents-overview#example-incident-response-workflow-for-microsoft-365-defender) |
| Periodic security operations | [Example periodic security operations for Microsoft 365 Defender](/microsoft-365/security/defender/integrate-microsoft-365-defender-secops-tasks) |
| Investigation for Microsoft Sentinel | [Incidents in Microsoft Sentinel](/azure/sentinel/tutorial-investigate-cases) |
| Investigation for Microsoft 365 Defender | [Incidents in Microsoft 365 Defender](/microsoft-365/security/defender/incidents-overview) |
|||

If you are an experienced security analyst, see these resources to quickly ramp up your SecOps team for Microsoft security services.

| Topic | Resource |
|:-------|:-----|
| Azure Active Directory (Azure AD) | [Security operations guide](/azure/active-directory/fundamentals/security-operations-introduction) |
| Microsoft 365 Defender | [Security operations guide](/microsoft-365/security/defender/integrate-microsoft-365-defender-secops) |
| Microsoft Sentinel | [How to investigate incidents](/azure/sentinel/tutorial-investigate-cases) |
| Microsoft 365 Defender | [How to investigate incidents](/microsoft-365/security/defender/incidents-overview) |
| Security operations establishment or modernization | Azure Cloud Adoption Framework articles for [SecOps](/azure/cloud-adoption-framework/secure/security-operations) and [SecOps functions](/azure/cloud-adoption-framework/organize/cloud-security-operations-center)|
| Incident response playbooks |  Overview at [https://aka.ms/IRplaybooks](https://aka.ms/IRplaybooks) <br> - [Phishing](incident-response-playbook-phishing.md) <br> - [Password spray](incident-response-playbook-password-spray.md) <br> - [App consent grant](incident-response-playbook-app-consent.md) |
| SOC Process Framework | [Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-azure-sentinel-soc-process-framework-workbook/ba-p/2339315) |
| MSTICPy and Jupyter Notebooks | [Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/msticpy-and-jupyter-notebooks-in-azure-sentinel-an-update/ba-p/2279661) |
|||

### Blog series about SecOps within Microsoft

See this blog series about how the SecOps team at Microsoft works.

- [Part 1 - Organization: Mission and Culture](https://www.microsoft.com/security/blog/2019/02/21/lessons-learned-from-the-microsoft-soc-part-1-organization/)
- [Part 2a - People: Teams, Tiers, and Roles](https://www.microsoft.com/security/blog/2019/04/23/lessons-learned-microsoft-soc-part-2-organizing-people/)
- [Part 2b - People: Careers and Readiness](https://www.microsoft.com/security/blog/2019/06/06/lessons-learned-from-the-microsoft-soc-part-2b-career-paths-and-readiness/)
- [Part 3a - Technology: SOC Tooling](https://www.microsoft.com/security/blog/2019/10/07/ciso-series-lessons-learned-from-the-microsoft-soc-part-3a-choosing-soc-tools/)
- [Part 3b - Technology: Day in life of an analyst](https://www.microsoft.com/security/blog/2019/12/23/ciso-series-lessons-learned-from-the-microsoft-soc-part-3b-a-day-in-the-life/)
- [Part 3c - A day in the life part 2 - Microsoft Security](https://www.microsoft.com/security/blog/2020/05/04/lessons-learned-microsoft-soc-part-3c/)
- [Part 3d - Zen and the art of threat hunting](https://www.microsoft.com/security/blog/2020/06/25/zen-and-the-art-of-threat-hunting/)

### Simuland

[Simuland](https://www.microsoft.com/security/blog/2021/05/20/simuland-understand-adversary-tradecraft-and-improve-detection-strategies/) is an open-source initiative to deploy lab environments and end-to-end simulations that:

- Reproduce well-known techniques used in real attack scenarios.
- Actively test and verify the effectiveness of related Microsoft 365 Defender, Microsoft Defender for Cloud, and Microsoft Sentinel detections.
- Extend threat research using telemetry and forensic artifacts generated after each simulation exercise.

Simuland lab environments provide use cases from a variety of data sources including telemetry from  Microsoft 365 Defender security products, Microsoft Defender for Cloud, and other integrated data sources through Microsoft Sentinel data connectors.

In the safety of a trial or paid sandbox subscription, you can:

- Understand the underlying behavior and functionality of adversary tradecraft.
- Identify mitigations and attacker paths by documenting preconditions for each attacker action.
- Expedite the design and deployment of threat research lab environments.
- Stay up to date with the latest techniques and tools used by real threat actors.
- Identify, document, and share relevant data sources to model and detect adversary actions.
- Validate and tune detection capabilities.

The learnings from Simuland lab environment scenarios can then be implemented in production.

After reading an overview of [Simuland](https://www.microsoft.com/security/blog/2021/05/20/simuland-understand-adversary-tradecraft-and-improve-detection-strategies/), see the [Simuland GitHub repository](https://github.com/Azure/SimuLand).

## Key Microsoft security resources 

| Resource | Description |
|:-------|:-----|
| [2021 Microsoft Digital Defense Report](https://www.microsoft.com/security/business/microsoft-digital-defense-report) | A report that encompasses learnings from security experts, practitioners, and defenders at Microsoft to empower people everywhere to defend against cyberthreats. |
| [Microsoft Cybersecurity Reference Architectures](/security/cybersecurity-reference-architecture/mcra) | A set of visual architecture diagrams that show Microsoft's cybersecurity capabilities and their integration with Microsoft cloud platforms such as Microsoft 365 and Microsoft Azure and third-party cloud platforms and apps. |
| [Minutes matter infographic](https://github.com/MarkSimos/MicrosoftSecurity/raw/master/Microsoft_CDOC_and_DCU_Poster.pdf) download | An overview of how Microsoft's SecOps team does incident response to mitigate ongoing attacks.  |
| [Azure Cloud Adoption Framework security operations](/azure/cloud-adoption-framework/secure/security-operations) | Strategic guidance for leaders establishing or modernizing a security operation function. |
| [Microsoft cloud security for IT architects model](https://aka.ms/cloudarchsecurity) | Security across Microsoft cloud services and platforms for identity and device access, threat protection, and information protection. |
| [Microsoft security documentation](/security/) | Additional security guidance from Microsoft. |
|||