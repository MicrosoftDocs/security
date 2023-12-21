---
title: Implement threat protection and XDR
description: Implement threat protection and XDR.  
ms.date: 12/18/2023
ms.service: security
author: BrendaCarter
ms.author: bcarter
ms.topic: conceptual
ms.collection: 
  - zerotrust-adopt
---

# Implement threat protection and XDR

As part of Zero Trust adoption guidance, this article describes how to protect your organization from cyberattacks and their possible resulting cost and reputation loss. This article is part of the [Prevent or reduce business damage from a breach](prevent-reduce-business-damage-breach.md) business scenario and focuses on how to create a threat protection and eXtended detection and response (XDR) infrastructure to detect and thwart cyberattacks in progress and minimize the business damage from a breach.

For the elements of the “assume breach” Zero Trust guiding principle:

- **Use analytics to get visibility, drive threat detection, and improve defenses**

  Described in this article.

- Minimize blast radius and segment access

  Described in the [implement security breach prevention and recovery infrastructure](prevent-reduce-business-damage-breach-infrastructure.md) article.

 - Verify end-to-end encryption

   Described in the [implement security breach prevention and recovery infrastructure](prevent-reduce-business-damage-breach-infrastructure.md) article.

This article assumes that you have already [modernized your security posture](rapidly-modernize-security-posture.md).

## The adoption cycle for implementing threat protection and XDR

This article walks through implementing threat protection and XDR elements of the [Prevent or reduce business damage from a breach](prevent-reduce-business-damage-breach.md) business scenario using the same lifecycle phases as the [Cloud Adoption Framework for Azure](/azure/cloud-adoption-framework/overview)—Define strategy, Plan, Ready, Adopt, and Govern and manage—but adapted for Zero Trust.

:::image type="content" source="../media/adoption-guide/objective-adoption-process.svg" alt-text="Diagram of the adoption process for an objective." lightbox="../media/adoption-guide/objective-adoption-process.svg":::

The following table is an accessible version of the illustration.

| Define strategy| Plan| Ready| Adopt| Govern and manage |
| --- | --- | --- | --- | --- |
| Outcomes <br><br> Organizational alignment <br><br> Strategic goals| Stakeholder team <br><br> Technical plans <br><br> Skills readiness| Evaluate <br><br> Test <br><br> Pilot| Incrementally implement across your digital estate | Track and measure <br><br> Monitor and detect <br><br> Iterate for maturity |

Read more about the Zero Trust adoption cycle in the [Zero Trust adoption framework overview](zero-trust-adoption-overview.md).

For more information about the "Prevent or reduce business damage from a breach" business scenario, see:

- The [overview](prevent-reduce-business-damage-breach.md)
- The additional elements of [implementing security breach prevention and recovery infrastructure](prevent-reduce-business-damage-breach-infrastructure.md)

## Define strategy phase

:::image type="content" source="../media/adoption-guide/define-strategy-phase.svg" alt-text="The define strategy phase." lightbox="../media/adoption-guide/define-strategy-phase.svg":::

The **Define strategy** phase is critical to define and formalize our efforts – it formalizes the “Why?” of this scenario. In this phase, you understand the scenario through business, IT, operational and strategic perspectives. You define the outcomes against which to measure success in the scenario, understanding that security is an incremental and iterative journey.

This article suggests motivations and outcomes that are relevant to many organizations. Use these suggestions to hone the strategy for your organization based on your unique needs.

### Motivations for implementing threat protection and XDR

The motivations for implementing threat protection and XDR are straightforward, but different parts of your organization have different incentives for doing this work. The following table summarizes some of these motivations.

| Area | Motivations |
| --- | --- |
| Business needs | To prevent an impact on or disruption of your organization’s ability to perform normal business activities or being held for ransom, lower the cost of cyber insurance, and prevent regulatory fines. |
| IT needs | To assist the Security Operations (SecOps) team in creating and maintaining an integrated defense toolset to secure the assets important to the business. Integration and reporting should occur across asset classes and technologies and lower the effort required to provide predictable security outcomes. |
| Operational needs | To keep your business processes operating through proactive detection and response to attacks in real time. |
| Strategic needs | Minimize attack damage and costs and maintain your organization’s reputation with customers and partners. |


### Outcomes for implementing threat protection and XDR

Applying the overall goal of Zero Trust to “never trust, always verify” adds a significant layer of protection to your environment. It’s important to be clear on the outcomes you expect to achieve so that you can strike the right balance of protection for all teams involved. The following table provides suggested objectives and outcomes for implementing threat protection and XDR.

| Objective | Outcome |
| --- | --- |
| Business outcomes | Threat protection results in minimal costs associated with business disruption, ransom payments, or regulatory fines. |
| Governance | Threat protection and XDR tools are deployed and SecOps processes are updated for the changing cybersecurity landscape, threats that are encountered, and automation of incident response. |
| Organizational resilience | Between [security breach prevention and recovery](prevent-reduce-business-damage-breach-infrastructure.md) and proactive threat protection, your organization can recover from an attack quickly and prevent future attacks of its type. |
| Security | Threat protection is integrated into your overall security requirements and policies. |

## Plan phase

:::image type="content" source="../media/adoption-guide/plan-phase.svg" alt-text="The plan phase." lightbox="../media/adoption-guide/plan-phase.svg":::

Adoption plans convert the principles of Zero Trust strategy into an actionable plan. Your collective teams can use the adoption plan to guide their technical efforts and align them with your organization's business strategy.

The motivations and outcomes you define, together with your business leaders and teams, support the “Why?” for your organization and become the North Star for your strategy. Next comes the technical planning to achieve the objectives.

Technical adoption for implementing threat protection and XDR involves:

- Setting up the suite of XDR tools provided by Microsoft to:

  - Perform incident response to detect and thwart attacks.

  - Proactively hunt for threats.

  - Automatically detect and respond to known attacks.

- Integrating Microsoft Defender XDR and Microsoft Sentinel.

- Defining SecOps processes and procedures for incident response and recovery.

Implementing threat protection and XDR also involves a few related activities, including:

- Using the XDR tools to monitor both your business critical and honeypot resources, which you implemented in the [security breach prevention and recovery](prevent-reduce-business-damage-breach-infrastructure.md) article to lure attackers into showing their presence before they can attack your real resources.
- Evolving your SecOps team to be aware of the latest attacks and their methods.

Many organizations can take a four-staged approach to these deployment objectives, summarized in the following table.


| Stage 1 | Stage 2 | Stage 3 | Stage 4 |
| --- | --- | --- | --- |
| Turn on XDR tools: <br>- Defender for Endpoint <br> - Defender for Office 365 <br> - Microsoft Entra ID Protection <br> - Defender for Identity  <br> - Defender for Cloud Apps <br><br> Investigate and respond to threats using Microsoft Defender XDR | Turn on Defender for Cloud <br><br> Define internal process for SecOps <br><br> Monitor business critical and honeypot resources with XDR tools | Turn on Defender for IoT <br><br> Design a Microsoft Sentinel workspace and ingest XDR signals <br><br> Proactively hunt for threats | Evolve SecOps as a discipline in your organization <br><br> Leverage automation to reduce load on your SecOps analysts |

If this staged approach works for your organization, you can share your progress with your teams and business leaders by downloading [this PowerPoint slide deck](https://download.microsoft.com/download/a/b/5/ab51ac2a-e9de-4c8f-8323-6bc7c2f78c1f/ZeroTrust-Adoption-Resources.pptx) to track your progress through these stages and objectives. Here's the initial slide for this business scenario.

:::image type="content" source="../media/adoption-guide/zero-trust-threat-protection-xdr-progress-tracking.png" alt-text="PowerPoint slide for the deployment stages of implementing threat detection and XDR." lightbox="../media/adoption-guide/zero-trust-threat-protection-xdr-progress-tracking.png":::

### Understand your organization

This recommended staged approach for technical implementation can help give context to the exercise of understanding your organization. 

A foundational step in the Zero Trust adoption lifecycle for every business scenario includes taking inventory and determining the current state of your SecOps team. For this business scenario, you need to:

- Inventory your current XDR tools, their integration, and the use of automation for incident response.
- Review your incident response and recovery procedures and processes.
- Review the deployment of your honeypot resources.
- Determine the readiness state of your security analysts and whether they need additional skills training or development.

### Organizational planning and alignment

The technical work of implementing threat protection and XDR falls your organization’s security team responsible for threat detection and response, which is mostly staffed by frontline security analysts who understand the current threat landscape and can use XDR tools to detect and respond quickly to an attack.

This table summarizes roles that are recommended when building a sponsorship program and project management hierarchy to determine and drive results.

| Program leaders and technical owners | Accountability |
| --- | --- |
| CISO, CIO, or Director of Data Security | Executive sponsorship |
| Program lead from Data Security | Drive results and cross-team collaboration |
| Security Architect | Advise on incident response strategies and practices, XDR tools and infrastructure, and SecOps team evolution |
| SecOps lead | Implement incident response procedures, XDR infrastructure configuration, incident response automation, and the SecOps discipline in your organization |
| Security for IT lead | Advise on, implement, and manage business critical and honeypot resources |

The [PowerPoint deck of resources](https://download.microsoft.com/download/a/b/5/ab51ac2a-e9de-4c8f-8323-6bc7c2f78c1f/ZeroTrust-Adoption-Resources.pptx) for this adoption content includes the following slide with a stakeholder view that you can customize for your own organization.

:::image type="content" source="../media/adoption-guide/zero-trust-threat-protection-xdr-stakeholders.png" alt-text="PowerPoint slide for the stakeholders of implementing threat detection and XDR." lightbox="../media/adoption-guide/zero-trust-threat-protection-xdr-stakeholders.png":::

### Technical planning and skills readiness

Before you embark on the technical work, Microsoft recommends getting to know the capabilities, how they work together, and best practices for approaching this work. 

Because Zero Trust assumes breach, you must prepare for a breach. Adopt a breach response framework based on [NIST](https://csrc.nist.gov/pubs/sp/800/61/r2/final), [ISO 27001](https://iso-docs.com/blogs/iso-27001-standard/iso-27001-annex-a-16-information-security-incident-management#:~:text=The%20ISO%2027001%20standard%20provides,comprehensive%20and%20up%20to%20date.), [CIS](https://www.cisecurity.org/controls/incident-response-management), or [MITRE](https://attack.mitre.org/) to lower the impact of a breach or cyberattack on your organization.

The following table includes several Microsoft training resources to help your security teams gain skills.

| Resource | Description |
|:-----|:-----|
| Module: [Mitigate incidents with Microsoft Defender XDR](/training/modules/mitigate-incidents-microsoft-365-defender/) | Learn how the Microsoft Defender XDR portal provides a unified view of incidents and alerts from the Microsoft Defender XDR family of products. |
| Learning Path: [Mitigate threats using Microsoft Defender XDR](/training/paths/sc-200-mitigate-threats-using-microsoft-365-defender/) | Analyze threat data across domains and rapidly remediate threats with built-in orchestration and automation in Microsoft Defender XDR. |
| Module: [Improve your reliability with modern operations practices: Incident response](/training/modules/improve-reliability-incidents/) | Learn the fundamentals of efficient incident response and the Azure tools that make them possible. |
| Module: [Training: Security incident management in Microsoft Sentinel](/training/modules/incident-management-sentinel/) | Learn about Microsoft Sentinel events and entities and discover ways to resolve incidents. |

#### Stage 1

The Stage 1 deployment objectives include enabling your primary Microsoft XDR tools and the use of Microsoft Defender XDR, which integrates the signals from the tools into a single portal, for incident response.

<a name='turn-on-xdr-tools'></a>
##### Turn on XDR tools

Start with the core suite of XDR tools to protect your organization from attacks on devices, identities, and cloud-based applications.

| Resource | Description |
|:-----|:-----|
| [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint) | An enterprise endpoint security platform to help your enterprise network prevent, detect, investigate, and respond to advanced threats against devices, which may include laptops, phones, tablets, PCs, access points, routers, and firewalls. |
| [Defender for Office 365](/microsoft-365/security/office-365-security/mdo-about) | A seamless integration into your Microsoft 365 or Office 365 subscription that protects against threats in email, links (URLS), attachments, and collaboration tools. |
| [Microsoft Entra ID Protection](/entra/id-protection/overview-identity-protection) | Helps organizations detect, investigate, and remediate identity-based risks. These identity-based risks can be further fed into tools like Entra Conditional Access to make access decisions or fed back to a security information and event management (SIEM) tool for further investigation and correlation. |
| [Defender for Identity](/defender-for-identity/what-is) | Leverages signals from both on-premises Active Directory and cloud identities to help you better identify, detect, and investigate advanced threats directed at your organization. |
| [Defender for Cloud Apps](/defender-cloud-apps/what-is-defender-for-cloud-apps) | Delivers full protection for SaaS applications, helping you monitor and protect your cloud app data. |

##### Investigate and respond to threats using Microsoft Defender XDR

Now that you have enabled the primary XDR tools, you can begin using Microsoft Defender XDR and its portal to analyze alerts and incidents and perform incident response on suspected cyberattacks.

| Resource | Description |
|:-----|:-----|
| [Integrating Microsoft 365 XDR into your security operations](/microsoft-365/security/defender/integrate-microsoft-365-defender-secops)	| Carefully plan your integration with your SecOps team to optimize the day-to-day operations and lifecycle management of the tools in the Microsoft Defender XDR. |
| [Incident response with Microsoft Defender XDR](/microsoft-365/security/defender/incidents-overview) | How to use Microsoft Defender XDR to analyze alerts and incidents and incorporate best practices into your SecOps procedures and processes. |
| [Investigate incidents with Microsoft Defender XDR](/microsoft-365/security/defender/investigate-incidents) | How to analyze the alerts that affect your network, understand what they mean, and collate the evidence so that you can devise an effective remediation plan. |
| Module: [Mitigate incidents with Microsoft Defender XDR](/training/modules/mitigate-incidents-microsoft-365-defender/) | Learn how the Microsoft Defender XDR portal provides a unified view of incidents and alerts from the Microsoft Defender XDR family of products. |
| Learning Path: [Mitigate threats using Microsoft Defender XDR](/training/paths/sc-200-mitigate-threats-using-microsoft-365-defender/) | Analyze threat data across domains and rapidly remediate threats with built-in orchestration and automation in Microsoft Defender XDR. |

#### Stage 2

In this stage, you enable additional XDR tools for Azure and on-premises resources, create or update your SecOps processes and procedures for Microsoft threat protection and XDR services, and monitor your business critical and honeypot resources to detect cyber attackers early in the breach.

##### Turn on Microsoft Defender for Cloud

Microsoft Defender for Cloud is a cloud-native application protection platform (CNAPP) designed to protect cloud-based applications from various cyber threats and vulnerabilities. Use Microsoft Defender for Cloud for Azure, hybrid cloud, and on-premises workload protection and security.

| Resource | Description |
|:-----|:-----|
| [Microsoft Defender for Cloud](/azure/defender-for-cloud/defender-for-cloud-introduction) | Get started with the documentation set. |
| [Security alerts and incidents for Microsoft Defender for Cloud](/azure/defender-for-cloud/alerts-overview) | Use Microsoft Defender for Cloud Security to perform incident response for your Azure, hybrid cloud, and on-premises workloads. |
| Module: [Remediate security alerts using Microsoft Defender for Cloud](/training/modules/remediate-azure-defender-security-alerts/) | Learn how to hunt for threats and remediate risks for your Azure, hybrid cloud, and on-premises workloads.  |
| Learning Path: [Mitigate threats using Microsoft Defender for Cloud](/training/paths/sc-200-mitigate-threats-using-azure-defender/) | Learn how to detect, investigate, and respond to advanced threats on your Azure, hybrid cloud, and on-premises workloads.  |

##### Define internal process for SecOps

With the Microsoft XDR tools in place, ensure that their use is integrated into your SecOps processes and procedures.

| Resource | Description |
|:-----|:-----|
| [Incident response overview](/security/operations/incident-response-overview) | Proactively investigate and remediate active attack campaigns on your organization. |
| [Incident response planning](/security/operations/incident-response-planning) | Use this article as a checklist to prepare your SecOps team to respond to cybersecurity incidents. |
| [Common attack incident response playbooks](/security/operations/incident-response-playbooks) | Use these articles for detailed guidance on common attack methods that malicious users employ every day. |
| [Integrating Microsoft 365 XDR into your security operations](/microsoft-365/security/defender/integrate-microsoft-365-defender-secops) | Carefully plan your integration with your SecOps team to optimize the day-to-day operations and lifecycle management tools in the Microsoft Defender XDR. |
| [Six Tabletop Exercises to Help Prepare Your Cybersecurity Team](https://www.cisecurity.org/insights/white-papers/six-tabletop-exercises-prepare-cybersecurity-team) | Use these exercises provided by the Center for Internet Security (CIS) to prepare your SecOps team. |

##### Monitor business critical and honeypot resources with XDR tools

Your deployed honeypot resources act as a target for cyber attackers and can be used to detect their activities early before they move on to real targets and cause business damage. Focus part of your threat detection and hunting on monitoring both your business critical and honeypot resources.

| Resource | Description |
|:-----|:-----|
| [Incident response with Microsoft Defender XDR](/microsoft-365/security/defender/incidents-overview) | Use Microsoft Defender XDR to spot incidents with alerts that affect your business critical and honeypot resources. |
| [Security alerts and incidents for Microsoft Defender for Cloud](/azure/defender-for-cloud/alerts-overview) | Use Microsoft Defender for Cloud to search for alerts triggered by advanced detections for your business critical and honeypot resources, such as Azure, hybrid cloud, and on-premises workloads. |

#### Stage 3

In this stage, you enable Defender for IoT, integrate Microsoft Defender XDR with Microsoft Sentinel, and then use the combined threat protection and XDR infrastructure to proactively hunt for threats.

##### Turn on Defender for IoT

The Internet of Things (IoT) supports billions of connected devices that use both operational technology (OT) and IoT networks. IoT/OT devices and networks are often built using specialized protocols and might prioritize operational challenges over security. Microsoft Defender for IoT is a unified security solution built specifically to identify IoT and OT devices, vulnerabilities, and threats. 

| Resource | Description |
|:-----|:-----|
| [Microsoft Defender for IoT](/azure/defender-for-iot/organizations/overview) | Get started with the documentation set. |
| [Module: Introduction to Microsoft Defender for IoT](/training/modules/introduction-to-microsoft-defender-iot/) | Learn about Defender for IoT components and features and how they support OT and IoT device security monitoring. |
| [Learning Path: Enhance IoT solution security by using Microsoft Defender for IoT](/training/paths/enhance-iot-solution-security-by-using-azure-defender/) | Learn about security considerations that apply at each level of the IoT solution and the Azure services and tools that can be configured to address security concerns from the ground up. |

##### Design a Microsoft Sentinel workspace and ingest XDR signals

Microsoft Sentinel is a cloud-native solution that provides security information and event management (SIEM) and security orchestration, automation, and response (SOAR) capabilities. Together, Microsoft Sentinel and Microsoft Defender XDR provide a comprehensive solution to help your organization defend against modern cyberattacks. 

| Resource | Description |
|:-----|:-----|
| [Implement Microsoft Sentinel and Microsoft Defender XDR for Zero Trust](/security/operations/siem-xdr-overview) | Get started with this solution documentation that also incorporates Zero Trust principles. |
| Module: [Connect Microsoft Defender XDR to Microsoft Sentinel](/training/modules/connect-microsoft-defender-365-to-azure-sentinel/) | Learn about the configuration options and data provided by Microsoft Sentinel connectors for Microsoft Defender XDR. |
| [Architect your Microsoft Sentinel workspace](/security/operations/siem-workspace) | Learn how to design and implement Microsoft Sentinel workspaces. |
| [Ingest data sources and configure incident detection in Microsoft Sentinel](/security/operations/ingest-data-sources) | Learn how to configure data connectors for data ingestion into your Microsoft Sentinel workspace.  |
| Module: [Connect data to Microsoft Sentinel using data connectors](/training/modules/connect-data-to-azure-sentinel-with-data-connectors/) | Get an overview of the available data connectors for Microsoft Sentinel. |

##### Proactively hunt for threats

Now that your XDR and SIEM infrastructure is in place, your SecOps team can take the initiative and proactively hunt for threats in progress in your environment instead of acting reactively to attacks that have already caused damage.

| Resource | Description |
|:-----|:-----|
| [Proactively hunt for threats with advanced hunting in Microsoft Defender XDR](/microsoft-365/security/defender/advanced-hunting-overview) | Get started with the documentation set for threat hunting with Microsoft Defender XDR. |
| [Hunt for threats with Microsoft Sentinel](/azure/sentinel/hunting) | Get started with the documentation set for threat hunting with Microsoft Sentinel. |
| Module: [Threat hunting with Microsoft Sentinel](/training/modules/hunt-threats-sentinel/) | Learn to proactively identify threat behaviors by using Microsoft Sentinel queries. |

#### Stage 4

In this stage, you evolve SecOps as a discipline in your organization and use the capabilities of Microsoft Defender XDR and Microsoft Sentinel to automate incident responses for known or previous attacks.

##### Evolve SecOps as a discipline in your organization

Multiple complex malicious events, attributes, and contextual information comprise advanced cybersecurity attacks. Identifying and deciding which of these activities qualify as suspicious can be a challenging task. Your knowledge of known attributes and abnormal activities specific to your industry is fundamental in knowing when to determine that an observed behavior is suspicious.

To evolve your SecOps team and discipline beyond the day-to-day tasks of incident response and recovery, specialists or senior members should understand the larger threat landscape and disseminate that knowledge throughout the team.

| Resource | Description |
|:-----|:-----|
| [Threat analytics in Microsoft Defender XDR](/microsoft-365/security/defender/threat-analytics) | Use the threat analytics dashboard in the [Microsoft Defender XDR portal](https://security.microsoft.com/threatanalytics3) (requires sign-in) for reports that are most relevant to your organization. |
| [Microsoft Defender Threat Intelligence (Defender TI)](/defender/threat-intelligence/what-is-microsoft-defender-threat-intelligence-defender-ti) | Use this built-in platform to streamline triage, incident response, threat hunting, vulnerability management, and cyber threat intelligence analyst workflows when conducting threat infrastructure analysis and gathering threat intelligence. |
| [Microsoft Security Blog](https://www.microsoft.com/security/blog/) | Get the latest about security threats and new features and updates for Microsoft Defender XDR and Microsoft Sentinel. |

##### Leverage automation to reduce load on your SecOps analysts

Use the capabilities of Microsoft Defender XDR and Microsoft Sentinel to automate incident response to detect and recover from known and anticipated incidents and to better focus your SecOps team on unanticipated attacks and new attack methods.

| Resource | Description |
|:-----|:-----|
| [Automated investigation and response in Microsoft Defender XDR](/microsoft-365/security/defender/m365d-autoir) | Get started with the Microsoft Defender XDR documentation set. |
| [Configure automated investigation and remediation capabilities](/microsoft-365/security/defender-endpoint/configure-automated-investigations-remediation) | For attacks on devices, get started with the Microsoft Defender for Endpoint documentation set. |
| [Automate threat response with playbooks in Microsoft Sentinel](/azure/sentinel/automate-responses-with-playbooks) | Get started with the documentation set for using playbooks in Microsoft Sentinel. |

### Cloud adoption plan

An adoption plan is an essential requirement for a successful cloud adoption. Key attributes of a successful adoption plan for implementing threat protection and XDR include:

- **Strategy and planning are aligned:** As you draw up your plans for testing, piloting, and rolling out threat protection and attack recovery capabilities across your on-premises and cloud infrastructure, be sure to revisit your strategy and objectives to ensure your plans are aligned. This includes priority and target milestones of goals for attack detection and response and use of automation.
- **The plan is iterative:** As you start to roll out your plan, you'll learn many things about your XDR environment and the tools you're using. At each stage of your roll-out, revisit your results compared to the objectives and fine tune the plans. For example, this can include revisiting earlier work to fine tune procedures and policies.
- **Training your SecOps staff is well-planned:** From your security architects to your frontline security analysts, everybody is trained to be successful with their threat protection, detection, mitigation, and recovery responsibilities.

For more information from the Cloud Adoption Framework for Azure, see [Plan for cloud adoption](/azure/cloud-adoption-framework/plan/plan-intro).


## Ready phase

:::image type="content" source="../media/adoption-guide/ready-phase.svg" alt-text="The ready phase." lightbox="../media/adoption-guide/ready-phase.svg":::

Use the resources listed in this article to prioritize your plan. The work of implementing threat protection and XDR represents one of the layers in your multi-layer Zero Trust deployment strategy.

The staged approach recommended in this article includes cascading the threat protection work in a methodical way across your digital estate. At this phase, revisit these elements of the plan to be sure everything is ready to go:

- Your SecOps team is informed that changes to their incident response processes for Microsoft Defender XDR and Microsoft Sentinel are imminent
- Your SecOps team is informed of documentation and training resources 
- Threat hunting procedures and guidelines and automation techniques are ready for use by analysts
- Your honeypot resources are in place

The planning phase demonstrated the gap between what you have and where you want to be. Use this phase to implement and test XDR tools and their use. For example, SecOps team leads can:

- Enable and use XDR tools for Microsoft Defender XDR to perform incident response on current attacks
- Configure the integration of Microsoft Defender XDR and Microsoft Sentinel using data connectors and workspaces
- Define or refine the SecOps team procedures and processes
- Explore and test threat hunting for proactive identification of threats and automation to detect and recover from known attacks

## Adopt phase

:::image type="content" source="../media/adoption-guide/adopt-phase.svg" alt-text="The adopt phase." lightbox="../media/adoption-guide/adopt-phase.svg":::

Microsoft recommends a cascading, iterative approach to implementing threat protection and XDR. This allows you to refine your strategy and policies as you go to increase the accuracy of the results.
There’s no need to wait until one phase is complete before beginning the next. Your results are more effective if you implement elements of each stage if you iterate along the way.

The main elements of your **Adopt** phase should include:

- Making Microsoft Defender XDR part of your ongoing, day-to-day incident response workflow in your SecOps team.
- Using the features of Microsoft Sentinel with Microsoft Defender XDR integration.
- Implementing automation to address known attacks, freeing up your SecOps team to perform threat hunting, and evolving your team’s discipline to be forward-thinking and prepared for new trends in cyberattacks

## Govern and manage phases

:::image type="content" source="../media/adoption-guide/govern-manage-phase.svg" alt-text="The govern and manage phase." lightbox="../media/adoption-guide/govern-manage-phase.svg":::

Governance of your organization’s ability to detect attacks with a threat protection and XDR infrastructure is an iterative process. By thoughtfully creating your implementation plan and rolling it out across your SecOps team you have created a foundation. Use the following tasks to help you start building your initial governance plan for this foundation.

| Objective | Tasks |
|:-----|:-----|
| Track and measure | Assign owners for critical actions and responsibilities such as incident response procedures, threat intelligence gathering and dissemination, and automation maintenance. <br><br> Create actionable plans with dates and schedules for each action. |
| Monitor and detect | Manage security threats using Microsoft Defender XDR and Microsoft Sentinel, using automation for common or previous attacks. |
| Iterate for maturity | Continually reassess risks and the cyberthreat landscape and make changes to SecOps procedures, responsibilities, policies, and priorities. |

## Next Steps

For this business scenario:

- [Prevent or reduce business damage from a breach](prevent-reduce-business-damage-breach.md)
- [Implement security breach prevention and recovery infrastructure](prevent-reduce-business-damage-breach-infrastructure.md)

Additional articles in the Zero Trust adoption framework:

- [Zero Trust adoption framework overview](zero-trust-adoption-overview.md)
- [Rapidly modernize your security posture](rapidly-modernize-security-posture.md)
- [Secure remote and hybrid work](secure-remote-hybrid-work.md)
- [Identify and protect sensitive business data](identify-protect-sensitive-business-data.md)
- [Meet regulatory and compliance requirements](meet-regulatory-compliance-requirements.md)
