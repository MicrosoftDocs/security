---
title: Meet regulatory and compliance requirements with Zero Trust
description: Learn how to Meet regulatory and compliance requirements with Zero Trust.
ms.date: 06/20/2023
ms.service: security
author: BrendaCarter
ms.author: bcarter
ms.topic: conceptual
ms.collection: 
  - zerotrust-solution
---

# Meet regulatory and compliance requirements

intro text

[]](zero-trust-adoption-overview.md)

:::image type="content" source="../media/adoption-guide/objective-adoption-process.svg" alt-text="Diagram of the adoption process for an objectives." lightbox="../media/adoption-guide/objective-adoption-process.svg":::

The following table is an accessible version of the illustration.

| Define strategy| Plan| Ready| Adopt| Govern and manage |
| --- | --- | --- | --- | --- |
| Organizational alignment <br><br> Strategic goals <br><br> Outcomes| Stakeholder team <br><br> Technical plans <br><br> Skills readiness| Evaluate <br><br> Test <br><br> Pilot| Incrementally implement across your digital estate | Track and measure <br><br> Monitor and detect <br><br> Iterate for maturity |


## Define strategy phase

:::image type="content" source="../media/adoption-guide/define-strategy-phase.svg" alt-text="The define strategy phase." lightbox="../media/adoption-guide/define-strategy-phase.svg":::


### Understand the motivations of your business leaders

Gaining alignment begins with understanding what motivates your leaders and why they should care about your security posture. The following table provides example perspectives, but it’s important for you to meet with each of these leaders and teams and come to a shared understanding of each other’s motivations.

| Role| Why rapidly modernizing your security posture is important |
| --- | --- |
| Chief Executive Officer (CEO)| Fundamentally, the CEO is expected to maximize returns to the shareholders within the law. To do this, the business must be empowered to achieve its strategic goals and objectives, inclusive of the security strategy, in a quantifiable way that enables evaluation of risks and costs. Business agility and business execution should be empowered by the security posture. |
| Chief Marketing Officer (CMO)| How the business is perceived both internally and externally relates to employee and customer confidence. Breach readiness and security incident communication strategy are vital to managing perception and opinions. |
| Chief Information Officer (CIO)| The applications used by a mobile and hybrid workforce must be accessible while securing the company's data. Security should be a measurable outcome and aligned with IT strategy. |
| Chief Information Security Officer (CISO)| Most best practice security standards and protocols require organizations to continually improve the suitability, adequacy, and effectiveness of the information security management system. Modernizing the security posture allows for the evolution of business security policies and procedures which in turn advance the overall security strategy within the business. |
| Chief Technology Officer (CTO)| The technology used to secure the business cannot be constricted to what is achievable using previous datacenter thinking only. Complimentary technologies that protect and enable business outcomes in a secure manner must be adopted. |
| Chief Operations Officer (COO)| The business must be able to operate profitably before, during, and after an attack. Security posture must enable fault tolerance and recoverability to prevent business outage. |
| Chief Financial Officer (CFO)| The security posture must be a predictable cost with a measurable outcome, like other business priorities. |

Additionally, different parts of your organization will have different motivations and incentives for doing this work. The following table summarizes some of these motivations. Be sure to connect with your stakeholders to understand their motivations.

| Area| Motivations |
| --- | --- |
| Business needs| To operate a business with a security posture that is integrated into business needs and imperatives. This security posture aligns with business outcomes and empowers the business attempting to implement security without creating onerous operating friction. |
| IT needs| A standardized security posture that caters for IT and Operational Technology (OT) security requirements, defines and instruments security posture tools and methodology, and provides predictable spend aligned to outcomes. |
| Operational needs| Implement existing security solutions in a standardized manner. Lower the management effort required to implement and maintain a security posture. Security posture governance leads towards a Security Operations (SecOps) model with defined roles and responsibilities. |
| Strategic needs| To incrementally increase the friction created by security solutions to attack scenarios and ruin an attacker’s return on investment. **Assume breach** requires planning to minimize blast radius and attack surfaces and reduce recovery time from a breach. |

### Defining your strategy

## Plan phase

:::image type="content" source="../media/adoption-guide/plan-phase.svg" alt-text="The plan phase." lightbox="../media/adoption-guide/plan-phase.svg":::


Many organizations can take a four-staged approach to these technical activities, summarized in the following chart.

| Stage 1| Stage 2 | Stage 3 | Stage 4 |
| --- | --- | --- | --- |
| Identify risks to your organization <br><br> Identify gaps in your security posture <br><br> Capture your initial Secure Score status <br><br> Identify regulatory requirements <br><br> Set leadership expectations | Develop a response readiness plan <br><br> Inventory your digital estate <br><br> Implement basic hygiene practices <br><br> Update your status for Secure Score <br><br> Capture your status in Compliance Manager| Visualize your security posture using audience-appropriate dashboards <br><br> Document and manage shadow IT using Microsoft Defender for Cloud Apps <br><br> Develop a methodology for patching and updating systems| Continuously educate your users <br><br> Evolve your organization’s SecOps capabilities <br><br> Continue to manage risk |

If this staged approach works for your organization, you can use this [downloadable PowerPoint slide deck](https://download.microsoft.com/download/a/b/5/ab51ac2a-e9de-4c8f-8323-6bc7c2f78c1f/ZeroTrust-Adoption-Resources.pptx) to track your progress through these stages and objectives. Here's an example.

:::image type="content" source="../media/adoption-guide/zero-trust-rapidly-modernize-security-posture-progress-tracking.png" alt-text="Example of the four stages to track progress." lightbox="../media/adoption-guide/zero-trust-rapidly-modernize-security-posture-progress-tracking.png":::

### Stakeholder team

Your stakeholder team for this business scenario includes leaders across your organization who are invested in your security posture and likely include the following roles and responsibilities:

| Stakeholder | Roles and responsibilities |
| --- | --- |
| Sponsor | Strategy, steering, escalation, approach, business alignment, and manage coordination.  |
| Project lead | Overall engagement, resources, timeline and schedule, communications, and other elements. |
| CISO | Security and governance of identities, devices, and apps. Owns risk and policy determination, tracking, and reporting. |
| Architecture lead | Technical requirements, architecture, reviews, decisions, and prioritization. |
| End user security and usability (EUC) lead | Your users’ needs and feedback. |
| Device management architect | The strategy for protecting organization data on devices, including managing devices. |
| App management lead | Prioritization and tech requirements for app investments, including bringing apps up to standards with modern authentication and Azure AD Conditional Access policies. |
| Service admins |  Tenant environment (preparation, testing, configuration). |
| Business unit representatives | Need and feedback from your business units. |

The [PowerPoint slide deck of resources](https://download.microsoft.com/download/a/b/5/ab51ac2a-e9de-4c8f-8323-6bc7c2f78c1f/ZeroTrust-Adoption-Resources.pptx) for this adoption content includes the following slide with a stakeholder view that you can customize for your own organization.

:::image type="content" source="../media/adoption-guide/zero-trust-rapidly-modernize-security-posture-stakeholders.png" alt-text="Example of stakeholders for modernizing your security posture." lightbox="../media/adoption-guide/zero-trust-rapidly-modernize-security-posture-stakeholders.png":::

### Technical plans and skills readiness

Microsoft provides resources to help you rapidly modernize your security posture. The following sections highlight resources for specific tasks in the four stages previously defined.

### Stage 1

In Stage 1, you begin to understand your current security posture. You start the conversations across your leadership team and organization to learn what Zero Trust is and how it aligns with business strategy and objectives.

| Objectives for Stage 1| Resources |
| --- | --- |
| Identify risks to your organization| [Implement security across the enterprise environment](/azure/cloud-adoption-framework/get-started/security) <br><br> This getting started guide outlines the key steps that can mitigate or avoid the business risk from cybersecurity attacks. It can help you rapidly establish essential security practices in the cloud and integrate security into your cloud adoption process. <br><br> Also see the resources earlier in this article: <br> <ul><li> Tabletop exercises </li><li> ISO standards </li></ul> |
| Identify gaps in your security posture| [Zero Trust concepts and deployment objectives](/security/zero-trust/deploy/overview)  <br><br> This series of articles provides recommendations by area (such as identity and endpoints). You can use these articles to assess how many of the recommendations are already complete and which ones remain. <br><br> Also, the planning resources in the [other business scenarios](zero-trust-adoption-overview.md#business-scenarios) include recommended resources for doing this work. |
| Capture your initial Secure Score status| [Assess your security posture with Microsoft Secure Score](/microsoft-365/security/defender/microsoft-secure-score-improvement-actions) <br><br> Understanding your initial Secure Score enables you to set quantifiable security goals and measure progress over time. It also enables you to recognize downward trends in your posture, facilitating justification for more modern feature deployments. |
| Identify regulatory requirements| Check in with your compliance team to learn about the regulations your organization is subject to. List the regulatory and governance frameworks and any audit findings or specific controls that must be met towards achieving secure compliance status. <br><br> Take a look at [Microsoft Purview Compliance Manager](/microsoft-365/compliance/compliance-manager) to see if your organization has started tracking progress against specific requirements. Some of the most commonly required standards and how to configure Azure AD for compliance can be found in our [standards documentation library](/azure/active-directory/standards/azure-ad-pci-dss-mfa). |
| Set leadership expectations | Use the [overview article](zero-trust-adoption-overview.md) as a resource to facilitate conversations with your leadership team on Zero Trust. It frames security as a business imperative and defines zero trust specific to leadership roles. Use the progress slides in the [Business Scenarios section](zero-trust-adoption-overview.md#business-scenarios) to present the work and track your progress at a high level for business leaders and other stakeholders. |

### Stage 2

In Stage 2, you continue to detail your current security posture, including:

- Developing a response readiness plan
- Starting an inventory of your digital estate
- Implementing basic hygiene



| Objectives for Stage 2| Resources |
| --- | --- |
| Develop a response readiness plan| [Cyberattacks Are Inevitable. Is Your Company Prepared?](https://hbr.org/2021/03/cyberattacks-are-inevitable-is-your-company-prepared) (Harvard Business Review) |
| Inventory your digital estate| [How do you manage IT asset inventory and documentation?](https://www.linkedin.com/advice/1/how-do-you-manage-asset-inventory-documentation) (LinkedIn article). <br><br> [IT Asset Valuation, Risk Assessment and Control Implementation Model](https://www.isaca.org/resources/isaca-journal/issues/2017/volume-3/it-asset-valuation-risk-assessment-and-control-implementation-model) by the Information Systems Audit and Control Association (ISACA) includes examples of how to measure and categorize assets. |
| Implement basic hygiene practices| Document the basic hygiene practices for your organization, including how to measure success. Hygiene practices are cybersecurity practices that you practice as a routine to mitigate online breaches. Many of these practices are included in Stage 1 of other business scenarios. Some are included in later stages. <br><br> [How to Have Better Cyber Hygiene](https://www.microsoft.com/en-us/microsoft-365-life-hacks/privacy-and-safety/cyber-hygiene) |
| Update your status for Secure Score| As you work through the recommendations across business scenarios, update your status for Secure Score. The score is a measure of progress and success that you can communicate across your organization. <br><br> [Assess your security posture with Microsoft Secure Score](/microsoft-365/security/defender/microsoft-secure-score-improvement-actions) |
| Capture your status in Compliance Manager| If you’ve started using [Microsoft Purview Compliance Manager](/microsoft-365/compliance/compliance-manager) to track your regulatory compliance work, check back periodically to update your status. Like Secure Score, this is a measure of progress and success that can be included as part of your security posture. |

### Stage 3


| Objectives for Stage 3| Resources |
| --- | --- |
| Visualize your security posture using audience-appropriate dashboards| [The tracking progress section in the overview article](zero-trust-adoption-overview.md#tracking-progress) provides several examples. <br><br> As you deploy and configure additional security capabilities, look for additional audience-scoped views that are valuable for your organization. For example, see [Monitor Zero Trust (TIC 3.0) security architectures with Microsoft Sentinel](/azure/sentinel/sentinel-solution). |
| Document and manage shadow IT using Defender for Cloud Apps| This is a hygiene area you can mature in this stage if you’ve deployed Defender for Cloud Apps. See [Integrate SaaS apps for Zero Trust with Microsoft 365](/security/zero-trust/integrate-saas-apps). |
| Develop a methodology for patching and updating systems regularly and with time sensitivity| This task within this business scenario isn't about how to patch and update systems. Rather, it is about developing a methodology to ensure patching and updating the various components of your digital estate happens regularly with accountability, visibility, and good communication to all affected individuals. Look for opportunities to automate this, where possible. <br><br> [What are the best practices for patching and updating your IT systems?](https://www.linkedin.com/advice/1/what-best-practices-patching-updating) (LinkedIn article) <br><br> [Does Patching Make Perfect?](https://www.infosecurity-magazine.com/opinions/patching-perfect/) (Infosecurity Magazine) |

### Stage 4

The objectives of Stage 4 are about maturing your organization’s ability to prevent and respond to attacks.

| Objectives for Stage 4 | Resources |
| --- | --- |
| Continuously educate users| To help Microsoft customers deploy user training quickly, easily, and effectively, use the [Microsoft Cybersecurity Awareness Kit](https://www.microsoft.com/en-us/security/blog/2020/05/13/empowering-remote-workforce-security-training/), developed in partnership with Terranova Security. <br><br> You can use attack simulation training in the Microsoft 365 Defender portal to run realistic attack scenarios in your organization. These simulated attacks can help you identify and find vulnerable users. See [Get started using Attack simulation training](/microsoft-365/security/office-365-security/attack-simulation-training-get-started). <br><br> Also see [Microsoft 365 security tips infographic](/microsoft-365/solutions/infographics-for-users) and [Microsoft Entra end-user rollout templates and materials](https://www.microsoft.com/en-us/download/details.aspx?id=57600). |
| Evolve your organization’s security operations capability| [Integrating Microsoft 365 Defender into your security operations](/microsoft-365/security/defender/integrate-microsoft-365-defender-secops) provides guidance for building and training your Security Operations Center (SOC) team, including how to develop and formalize a process for responding to incidents. <br><br> See the [Microsoft Security Operations library](/security/operations/overview) for guidance on how to respond to incidents and playbooks for responding to specific attack types. |
| Continue to manage risk| Develop a systematic way for your organization to evaluate and manage risk on an ongoing basis. Revisit the tabletop exercises or ISO standards to recalibrate where you are and what you have accomplished. |

## Ready phase

:::image type="content" source="../media/adoption-guide/ready-phase.svg" alt-text="The ready phase." lightbox="../media/adoption-guide/ready-phase.svg":::



## Adopt phase

:::image type="content" source="../media/adoption-guide/adopt-phase.svg" alt-text="The adopt phase." lightbox="../media/adoption-guide/adopt-phase.svg":::



:::image type="content" source="../media/adoption-guide/rapid-modernize-sec-posture.svg" alt-text="Diagram of rapidly modernizing your security posture." lightbox="../media/adoption-guide/rapid-modernize-sec-posture.svg":::

## Govern and manage

:::image type="content" source="../media/adoption-guide/govern-manage-phase.svg" alt-text="The govern and manage phase." lightbox="../media/adoption-guide/govern-manage-phase.svg":::



## Next Steps

- [Zero Trust adoption framework overview](zero-trust-adoption-overview.md)
- [Rapidly modernize your security posture](rapidly-modernize-security-posture.md)
- [Secure remote and hybrid work](secure-remote-hybrid-work.md)
- [Identify and protect sensitive business data](identify-protect-sensitive-business-data.md)
