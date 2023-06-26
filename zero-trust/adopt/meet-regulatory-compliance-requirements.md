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

As part of [Zero Trust](zero-trust-adoption-overview.md) adoption guidance, this article describes the business scenario of meeting regulatory and compliance requirements that might be applicable to your organization. 

Regardless of the complexity of your organization’s IT environment or the size of your organization, new regulatory requirements that might affect your business are continually adding up. These regulations include the European Union’s General Data Protection Regulation (GDPR), the California Consumer Privacy Act (CCPA), a myriad of healthcare and financial information regulations as well as data residency requirements. 

The process of meeting regulatory and compliance requirements can be long, complex, and tedious when not managed properly. This challenge has considerably increased the workload of security, compliance, and regulations teams to achieve and prove compliance, prepare for an audit, and put ongoing best practices into place.

A Zero Trust approach often exceeds some types of requirements imposed by compliance regulations, for example, those controlling access to personal data. Organizations that have implemented a Zero Trust approach may find that they already meet some new conditions or can easily build upon their Zero Trust architecture to be compliant. 

| Traditional approaches to meeting regulatory and compliance requirements | Modern approach to meeting regulatory and compliance requirements with Zero Trust |
| --- | --- |
| Many organizations use various legacy solutions stitched together. These solutions often don’t work together seamlessly, exposing infrastructure gaps and increasing operational costs. <br><br> Some independent “best of breed solutions” might even prevent compliance with certain regulations while they are used to meet another. <br><br> One widespread example of this is the use of encryption to ensure data is securely handled by authorized individuals. But most encryption solutions make data opaque to services such as Data Loss Prevention (DLP), eDiscovery, or archiving. Encryption prevents the organization from performing due diligence on actions performed by users that utilize encrypted data. This result forces organizations to make hard and risky decisions, such as either banning all use of file-level encryption for transfers of sensitive data or letting encrypted data go outside the organization uninspected. | Unifying your security strategy and policy with a Zero Trust approach breaks down silos between IT teams and systems, enabling better visibility and protection across the IT stack. <br><br> Natively integrated compliance solutions, such as those in Microsoft Purview, not only work together to support your compliance requirements **and** those of a Zero Trust approach, but they do it with full transparency, allowing each solution to leverage the benefits of others, such as communication compliance leveraging sensitivity labels in content. Integrated compliance solutions can provide the required coverage with minimal tradeoffs, such as encrypted content being transparently processed by eDiscovery or DLP solutions. <br><br> Real-time visibility allows automatic discovery of assets, including critical assets and workloads, while compliance mandates can be applied to these assets through classification and sensitivity labeling. <br><br> Implementing a Zero Trust architecture helps you meet regulatory and compliance requirements with a comprehensive strategy. The use of Microsoft Purview solutions in a Zero Trust architecture helps you discover, govern, protect, and manage your organization’s entire data estate according to the regulations that impact your organization. <br><br> Zero Trust strategies often involve implementing controls that meet or exceed certain regulatory requirements, which reduces the burden of performing system-wide changes to adhere to new regulatory requirements. |

The guidance in this article walks you through how to get started with Zero Trust as a framework for meeting your regulatory and compliance requirements with an emphasis on how to communicate and work with business leaders and teams across your organization.

This article uses the same lifecycle phases as the Cloud Adoption Framework for Azure—Define strategy, Plan, Ready, Adopt, and Govern and manage—but adapted for Zero Trust.

:::image type="content" source="../media/adoption-guide/objective-adoption-process.svg" alt-text="Diagram of the adoption process for an objectives." lightbox="../media/adoption-guide/objective-adoption-process.svg":::

The following table is an accessible version of the illustration.

| Define strategy| Plan| Ready| Adopt| Govern and manage |
| --- | --- | --- | --- | --- |
| Organizational alignment <br><br> Strategic goals <br><br> Outcomes| Stakeholder team <br><br> Technical plans <br><br> Skills readiness| Evaluate <br><br> Test <br><br> Pilot| Incrementally implement across your digital estate | Track and measure <br><br> Monitor and detect <br><br> Iterate for maturity |


## Define strategy phase

:::image type="content" source="../media/adoption-guide/define-strategy-phase.svg" alt-text="The define strategy phase." lightbox="../media/adoption-guide/define-strategy-phase.svg":::

The **Define strategy** phase is critical to defining and formalizing efforts to address the “Why?” of this scenario. In this phase, you understand the scenario through regulatory, business, IT, operational, and strategic perspectives.

You then define the outcomes against which to measure success in this scenario, understanding that compliance is an incremental and iterative journey.

This article suggests motivations and outcomes that are relevant to many organizations. Use these suggestions to hone the strategy for your organization based on your unique needs.

### Understanding the motivations of your business leaders

While Zero Trust can help streamline the process of meeting regulatory requirements, perhaps the biggest challenge is gaining support and contribution from leaders across your organization. This adoption guidance is designed to help you communicate with them so you can gain organizational alignment, define your strategic goals, and identify outcomes.

Gaining alignment begins with understanding what motivates your leaders and why they should care about meeting regulatory requirements. The following table provides example perspectives, but it’s important for you to meet with each of these leaders and teams and come to a shared understanding of each other’s motivations.

| Role| Why meeting regulatory requirements is important |
| --- | --- |
| Chief Executive Officer (CEO) | Responsible for securing organizational strategy that is validated by external auditing bodies. The CEO will mostly report to a board of directors who may also evaluate the level of compliance with legislative requirements across the organization as well as annual audit findings. |
| Chief Marketing Officer (CMO) | Responsible for ensuring that confidential company information is not externally shared solely for marketing purposes. |
| Chief Information Officer (CIO)| Is typically the information officer in the organization and will be held liable to information regulators. |
| Chief Technology Officer (CTO) | Responsible for maintaining regulatory compliance within the digital estate. |
| Chief Information Security Officer (CISO) | Responsible for the adoption and conformance to industry standards that provide controls directly related to information security compliance. |
| Chief Operations Officer (COO) | Ensures that company policies and procedures relating to information security, data privacy, and other regulatory practices are upheld on an operational level. |
| Chief Financial Officer (CFO) | Assesses financial drawbacks and advantages to compliance, such as cyber insurance and tax compliance. |
| Chief Risk Officer (CRO)| Owns the Risk component of the [Governance Risk and Compliance (GRC)](https://learn.microsoft.com/en-us/compliance/assurance/assurance-governance) framework within the organization. Mitigates threats to non-conformance and compliance. |

Additionally, different parts of your organization will have different motivations and incentives for doing the work of regulatory and compliance requirements. The following table summarizes some of these motivations. Be sure to connect with your stakeholders to understand their motivations.

| Area| Motivations |
| --- | --- |
| Business needs | To comply with regulatory and legislative requirements that apply. |
| IT needs | To implement technologies that automate conformance to regulatory and compliance requirements, as set out by your organization within the scope of identities, data, devices (endpoints), applications, and infrastructure. |
| Operational needs | Implement policies, procedures, and work instructions that are referenced and aligned to relevant industry standards and relevant compliance requirements. |
| Strategic needs | Reduce the risk of infringing on national, regional, and local laws and the potential financial and public reputational damages that can result from infringements. |

### Using the governance pyramid to inform strategy

The most important thing to remember with this business scenario is that the Zero Trust framework serves as part of a much larger governance model that establishes the hierarchy of various legislative, statutory, regulatory, policy, and procedural requirements within an organization. In the compliance and regulatory space, there can be many ways to achieve the same requirement or control. It is important to state that **this article pursues regulatory compliance using a Zero Trust approach.**

A strategy model that is often used within regulatory compliance is the governance pyramid shown here.

>> Pyramid figure

This pyramid illustrates the different levels on which most organizations manage information technology (IT) governance. From the top of the pyramid to the bottom, these levels are legislation, standards, policies and procedures, and work instructions. 

The top of the pyramid represents the most important level — legislation. At this level, the variation between organizations is less because laws apply broadly to many organizations, although national and business-specific regulations can apply only to some companies and not others. The base of the pyramid, work instructions, represents the area with the greatest variation and surface area of implementation across organizations. This is the level that allows an organization to leverage technology to fulfil the more important requirements for the higher levels.

The right side of the pyramid provides examples of scenarios where organizational compliance can lead to positive business outcomes and benefits. Business relevance creates more incentives for organizations to have a governance strategy.

The following table describes how the different governance levels on the left side of the pyramid can provide the strategic business advantages on the right side.

| Governance level| Strategic business relevance and outcomes |
| --- | --- |
| Legislation and laws, considered collectively | Passing legal audits can avoid fines and penalties and builds consumer trust and brand loyalty. |
| Standards provide a reliable basis for people to share the same expectations about a product or service | Standards provide quality assurance through various industry quality controls. Some certifications have cyber insurance benefits as well. |
| Policies and procedures document an organization’s day-to-day functions and operations | Many manual processes related to governance can be streamlined and automated. |
| Work instructions describe how to perform a process based on the defined policies and procedures in detailed steps | The intricate details of manuals and instruction documents can be streamlined by technology. This can greatly reduce human error and save time. <br><br> An example is using Azure Active Directory (Azure AD) Conditional Access policies as part of the employee onboarding process. |

The governance pyramid model helps focus priorities:

1. Legislative and legal requirements 

   Organizations can face serious repercussions if these are not followed.

2. Industry-specific and security standards 

   Organizations may have an industry requirement to be compliant or certified with one or more of these standards. The Zero Trust framework can be mapped against various security, information security, and infrastructure management standards. 

3. Policies and procedures 

   Organization-specific and govern the more intrinsic processes within the business.

4. Work instructions 

   Detailed controls that are very technical and customized for organizations to fulfil the policies and procedures.

There are several standards that add the most value to areas of the Zero Trust architecture. Focusing attention on the following standards that apply to you will yield more impact: 

- The [Center for Internet Security (CIS) Benchmarks](https://www.cisecurity.org/cis-benchmarks) provide valuable guidance for device management and endpoint management policies. CIS Benchmarks include implementation guides for Microsoft 365 and Microsoft Azure. Organizations across all industries and verticals use CIS benchmarks to assist them in achieving security and compliance goals. especially those that operate in heavily regulated environments.

- National Institute of Standards and Technology (NIST) provides the [NIST Special Publication (NIST SP 800-63-4 ipd) Digital Identity Guidelines](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-63A-4.ipd.pdf). These guidelines provide technical requirements for federal agencies implementing digital identity services and are not intended to constrain the development or use of standards outside of this purpose. It is important to note that these requirements are made to enhance the existing protocols that form part of Zero Trust strategy. Both government and public sector organizations particularly in the United States subscribe to NIST, however publicly listed companies can also make use of the guiding principles within the framework. NIST also provides help for implementing a Zero Trust architecture in the publications included with [NIST SP 1800-35](https://www.nccoe.nist.gov/projects/implementing-zero-trust-architecture).

- The newly revised [ISO 27002:2022](https://www.iso.org/standard/75652.html) standard is recommended for overall data governance and information security. However, the Annexure A controls provide a good foundation for creating a checklist of security controls, which can later be converted into workable objectives.

   ISO 27001:2022 also provides comprehensive guidelines on how risk management can be implemented in the context of information security. This may be particularly beneficial with the number of metrics available to users in most portals and dashboards.

Standards like these can be prioritized to provide your organization with a baseline of policies and controls to meet common requirements.

Microsoft provides the Microsoft Purview Compliance Manager to help you plan and track progress toward meetings standards that apply to your organization. Compliance Manager can help you throughout your compliance journey, from taking inventory of your data protection risks to managing the complexities of implementing controls, staying current with regulations and certifications, and reporting to auditors.

### Defining your strategy

From a compliance perspective, your organization should define its strategy according to its intrinsic Governance Risk & Compliance (GRC) methodology. If the organization does not subscribe to a specific standard, policy, or framework, then an assessment template should be obtained from Compliance Manager. Every active Microsoft 365 subscription is assigned a data protection baseline that may be mapped against Zero Trust deployment guidelines. This baseline gives your implementers a great starting point to what the practical implementation of Zero Trust from a compliance perspective should look like. These documented controls can later be converted to measurable objectives. These objectives should be Specific, Measurable, Achievable, Realistic, and Time-bound (SMART). 

The Data Protection Baseline template in Compliance Manager integrates 36 actions for Zero Trust, aligned across the following control families:

- Zero Trust Application
- Zero Trust App development guidance
- Zero Trust Endpoint
- Zero Trust Data
- Zero Trust Identity
- Zero Trust Infrastructure
- Zero Trust Network
- Zero Trust Visibility, automation, and orchestration

These align strongly with the Zero Trust reference architecture, shown here.

:::image type="content" source="../media/zero-trust-ramp-overview/zero-trust-architecture.svg" alt-text="The overall architecture for Zero Trust" lightbox="../media/zero-trust-ramp-overview/zero-trust-architecture.svg":::



## Plan phase

:::image type="content" source="../media/adoption-guide/plan-phase.svg" alt-text="The plan phase." lightbox="../media/adoption-guide/plan-phase.svg":::


Many organizations can take a four-staged approach to these technical activities, summarized in the following chart.

| Stage 1| Stage 2 | Stage 3 | Stage 4 |
| --- | --- | --- | --- |
| Identify risks to your organization <br><br> Identify gaps in your security posture <br><br> Capture your initial Secure Score status <br><br> Identify regulatory requirements <br><br> Set leadership expectations | Develop a response readiness plan <br><br> Inventory your digital estate <br><br> Implement basic hygiene practices <br><br> Update your status for Secure Score <br><br> Capture your status in Compliance Manager| Visualize your security posture using audience-appropriate dashboards <br><br> Document and manage shadow IT using Microsoft Defender for Cloud Apps <br><br> Develop a methodology for patching and updating systems| Continuously educate your users <br><br> Evolve your organization’s SecOps capabilities <br><br> Continue to manage risk |

If this staged approach works for your organization, you can use this [downloadable PowerPoint slide deck](https://download.microsoft.com/download/a/b/5/ab51ac2a-e9de-4c8f-8323-6bc7c2f78c1f/ZeroTrust-Adoption-Resources.pptx) to track your progress through these stages and objectives. Here's the initial slide for this business scenario.

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
