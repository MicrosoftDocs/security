---
title: Meet regulatory and compliance requirements with Zero Trust
description: Learn how to Meet regulatory and compliance requirements with Zero Trust.
ms.date: 06/27/2023
ms.service: security
author: BrendaCarter
ms.author: bcarter
ms.topic: conceptual
ms.collection: 
  - zerotrust-adopt
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

This article uses the same lifecycle phases as the [Cloud Adoption Framework for Azure](/azure/cloud-adoption-framework/overview)—Define strategy, Plan, Ready, Adopt, and Govern and manage—but adapted for Zero Trust.

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
| Chief Risk Officer (CRO)| Owns the Risk component of the [Governance Risk and Compliance (GRC)](/compliance/assurance/assurance-governance) framework within the organization. Mitigates threats to non-conformance and compliance. |

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

:::image type="content" source="../media/adoption-guide/regulatory-compliance-governance-pyramid.svg" alt-text="The governance pyramid strategy model." lightbox="../media/adoption-guide/regulatory-compliance-governance-pyramid.svg":::

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

Many organizations can take a four-staged approach to these technical activities, summarized in the following table.

| **Stage 1**| **Stage 2**| **Stage 3**| **Stage 4** |
| --- | --- | --- | --- |
| Identify regulatory requirements that apply to your organization. <br><br> Use Compliance Manager to identify regulations that might affect your business, assess compliance with the high-level requirements imposed by those regulations, and plan remediation for identified gaps. <br><br> Review current guidance for regulations that apply to your organization.| Use content explorer in Microsoft Purview to  identify data that is subject to regulation requirements and assess its risk and exposure. Define custom classifiers to adapt this capability to your business needs. <br><br> Assess requirements for information protection, such as data retention and records management policies, and then implement basic information protection and data governance policies using retention and sensitivity labels. <br><br> Implement basic DLP policies to control the flow of regulated information. <br><br> Implement [communication compliance policies](/microsoft-365/compliance/communication-compliance) if required by regulations.| Extend data lifecycle management policies with automation. <br><br> Set up partitioning and isolation controls using sensitivity labels, DLP or [information barriers](/microsoft-365/compliance/information-barriers) if required by regulations. <br><br> Expand information protection policies by implementing container labeling, automatic and mandatory labeling, and stricter DLP policies. Then expand these policies to on-premises data, devices (endpoints), and third-party cloud services using additional capabilities in Microsoft Purview. <br><br> Reassess compliance using Compliance Manager and identify and remediate remaining gaps.| Use Azure Sentinel to build reports based on the unified audit log to continuously assess and inventory the compliance status of your information. <br><br> Continue using Compliance Manager on an ongoing basis to identify and remediate remaining gaps and meet the requirements of new or updated regulations. |

If this staged approach works for your organization, you can use [this PowerPoint slide deck](https://download.microsoft.com/download/a/b/5/ab51ac2a-e9de-4c8f-8323-6bc7c2f78c1f/ZeroTrust-Adoption-Resources.pptx) to track your progress through these stages and objectives. Here's the initial slide for this business scenario.

:::image type="content" source="../media/adoption-guide/zero-trust-meet-regulatory-compliance-requirements-progress-tracking.png" alt-text="PowerPoint slide for the stages of your meet regulatory and compliance requirements deployment." lightbox="../media/adoption-guide/zero-trust-meet-regulatory-compliance-requirements-progress-tracking.png":::

### Stakeholder team

Your stakeholder team for this business scenario includes leaders across your organization who are invested in your security posture and are likely to include the following roles:

| Program leaders and technical owners | Accountability |
| --- | --- |
| Sponsor | Strategy, steering, escalation, approach, business alignment, and coordination management. |
| Project lead | Overall management of engagement, resources, timeline and schedule, communications, and others. |
| CISO | Protection and governance of data assets and systems, such as risk and policy determination and tracking and reporting. |
| IT Compliance manager | Determination of required controls to address compliance and protection requirements. |
| End user security and usability (EUC) lead | Representation of your employees. |
| Investigation and audit roles | Investigation and reporting in cooperation with compliance and protection leads. |
| Information protection manager | Data classification and sensitive data identification, controls, and remediation. |
| Architecture lead | Technical requirements, architecture, reviews, decisions, and prioritization. |
| Microsoft 365 admins | Tenant and environment, preparation, configuration, testing. |

The [PowerPoint slide deck of resources](https://download.microsoft.com/download/a/b/5/ab51ac2a-e9de-4c8f-8323-6bc7c2f78c1f/ZeroTrust-Adoption-Resources.pptx) for this adoption content includes the following slide with a stakeholder view that you can customize for your own organization.

:::image type="content" source="../media/adoption-guide/zero-trust-meet-regulatory-compliance-requirements-stakeholders.png" alt-text="PowerPoint slide to identify key stakeholders for your meet regulatory and compliance requirements deployment." lightbox="../media/adoption-guide/zero-trust-meet-regulatory-compliance-requirements-stakeholders.png":::

### Technical plans and skills readiness

Microsoft provides resources to help you meet regulatory and compliance requirements. The following sections highlight resources for specific objectives in the four stages previously defined.

#### Stage 1

In Stage 1, you identify the regulations that apply to your organization and begin using Compliance Manager. You also review [regulations that apply to your organization](/microsoft-365/compliance/compliance-manager-templates-list).

| Objectives for Stage 1 | Resources |
| --- | --- |
| Identify compliance requirements using governance pyramid. | [Compliance manager assessments](/microsoft-365/compliance/compliance-manager-assessments) |
| Use Compliance Manager to assess compliance and plan remediation for identified gaps. | Visit the Microsoft Purview compliance portal and review all customer-managed improvement actions relevant to your organization. |
| Review current guidance for regulations that apply to your organization. | See the following table. |

This table lists common regulations or standards.

| Regulation or standard| Resources |
| --- | --- |
| National Institute of Standards and Technology (NIST)| [Configure Azure AD to meet NIST authenticator assurance levels](/azure/active-directory/standards/nist-overview) |
| Federal Risk and Authorization Management Program (FedRAMP)| [Configure Azure AD to meet FedRAMP High Impact level](/azure/active-directory/standards/configure-for-fedramp-high-impact) |
| Cybersecurity Maturity Model Certification (CMMC)| [Configure Azure AD for CMMC compliance](/azure/active-directory/standards/configure-for-cmmc-compliance) |
| Executive Order on Improving the Nation’s Cybersecurity (EO 14028)| [Meet identity requirements of memorandum 22-09 with Azure AD](/azure/active-directory/standards/memo-22-09-meet-identity-requirements) |
| Health Insurance Portability and Accountability Act of 1996 (HIPAA)| [Configuring Azure AD for HIPAA compliance](/azure/active-directory/standards/hipaa-configure-for-compliance) |
| Payment Card Industry Security Standards Council (PCI SSC)| [Azure AD PCI-DSS guidance](/azure/active-directory/standards/pci-dss-guidance) |
| Financial services regulations| [Key compliance and security considerations for US banking and capital markets](/microsoft-365/solutions/financial-services-secure-collaboration) <ul><li> U.S. Securities and Exchange Commission (SEC) </li><li> Financial Industry Regulatory Authority (FINRA) </li><li> Federal Financial Institutions Examination Council (FFIEC) </li><li> Commodity Futures Trading Commission (CFTC) </li></ul> |
| North America Electric Reliability Corporation (NERC)| [Key Compliance and Security Considerations for the Energy Industry](/microsoft-365/solutions/energy-secure-collaboration) |

#### Stage 2

In Stage 2, you begin implementing controls for data that are not already in place. Additional guidance for planning and deploying information protection controls are in the [Identify and protect sensitive business data](identify-protect-sensitive-business-data.md) Zero Trust adoption guide.

| Objectives for Stage 2| Resources |
| --- | --- |
| Use content explorer to identify regulated data. | [Get started with content explorer](/microsoft-365/compliance/data-classification-content-explorer) <br><br> Content explorer can assist you in reviewing the current exposure of regulated data and assess its compliance with regulations dictating where it must be stored and how it must be protected. <br><br> [Create custom sensitive information types](/microsoft-365/compliance/create-a-custom-sensitive-information-type) |
| Implement basic data governance and information protection policies using retention and sensitivity labels. | [Learn about retention policies & labels to retain or delete](/microsoft-365/compliance/retention) <br><br> [Learn about sensitivity labels](/microsoft-365/compliance/sensitivity-labels) |
| Verify your DLP and encryption policies. | [Purview data loss prevention](/microsoft-365/compliance/dlp-learn-about-dlp) <br><br> Encryption with [Sensitivity labelling](/microsoft-365/compliance/encryption-sensitivity-labels) <br><br> [Encryption for Office 365](/microsoft-365/compliance/encryption) |
| Implement communication policies (if applicable). | [Create and manage communication compliance policies](/microsoft-365/compliance/communication-compliance-policies) |

#### Stage 3

In Stage 3, you begin to automate your data governance policies for retention and deletion, including use of adaptive scopes.

This stage includes implementing controls for segregation and isolation. NIST, for example, prescribes hosting projects in an isolated environment if these projects relate to specific types of classified work for and with the United States government. In some scenarios, financial services regulations require partitioning environments to prevent employees of different parts of the business from communicating with each other.

| Objectives for Stage 3| Resources |
| --- | --- |
| Extend data lifecycle management policies with automation. | [Data lifecycle management](/microsoft-365/compliance/data-lifecycle-management) |
| Set up partitioning and isolation controls (if applicable). | [Information barriers](/microsoft-365/compliance/information-barriers) <br><br> [Data loss prevention](/microsoft-365/compliance/dlp-learn-about-dlp) <br><br> [Cross-tenant access](/azure/active-directory/external-identities/cross-tenant-access-overview) |
| Expand information protection policies to additional workloads. | [Learn about the information protection scanner](/microsoft-365/compliance/deploy-scanner) <br><br> [Use data loss prevention policies for non-Microsoft cloud apps](/microsoft-365/compliance/dlp-use-policies-non-microsoft-cloud-apps) <br><br> [Data loss prevention and Microsoft Teams](/microsoft-365/compliance/dlp-microsoft-teams) <br><br> [Using Endpoint data loss prevention](/microsoft-365/compliance/endpoint-dlp-using) <br><br> [Use sensitivity labels to protect content in Microsoft Teams, Microsoft 365 groups, and SharePoint sites](/microsoft-365/compliance/sensitivity-labels-teams-groups-sites) |
| Re-assess compliance using Compliance Manager, identify and remediate remaining gaps.| [Compliance Manager](/microsoft-365/compliance/compliance-manager) |

#### Stage 4

The objectives in Stage 4 are about operationalizing this scenario by moving to a continuous motion of evaluating the compliance of your assets to your applicable regulations and standards. 

| Objectives for Stage 4| Resources |
| --- | --- |
| Continuously assess and inventory the compliance status of resources. | This article has identified every required tool and for this objective, you form a repeatable, iterative process that allows for continuous monitoring of resources and assets within the digital estate. <br><br> [Search the audit log in the compliance portal](/microsoft-365/compliance/audit-log-search) |
| Use Azure Sentinel to build reports to measure compliance. | Use [Azure Sentinel](/azure/sentinel/overview) to build reports based on the Unified Audit Log to assess and measure compliance and demonstrate the effectiveness of controls. <br><br> [Log analytics in Azure](/azure/azure-monitor/logs/log-analytics-overview) |
| Utilize Compliance Manager to identify and remediate new gaps. | [Compliance Manager](/microsoft-365/compliance/compliance-manager) |

## Ready phase

:::image type="content" source="../media/adoption-guide/ready-phase.svg" alt-text="The ready phase." lightbox="../media/adoption-guide/ready-phase.svg":::

The majority of compliance work happens through policy enforcement. You determine what conditions must be met to achieve compliance and then create a policy or set of policies to automate a set of controls. Policy enforcement with Zero Trust creates repeatable verification for specific compliance controls being implemented. By building controls into the operational technology that the organization interacts with every day, it becomes a much simpler task to achieve audit readiness. 

During the **Ready** phase, you evaluate, test, and pilot the policies you are targeting to be sure these achieve the intended results. Be sure these do not introduce new risks. For this Zero Trust business scenario, it’s important to work with your stakeholders who are implementing access controls, data protection, and other infrastructure protections. For example, the recommendations for evaluating, testing, and piloting policies to enable remote and hybrid work are different than the recommendations for identifying and protecting sensitive data across your digital estate. 

### Example controls

Each pillar of Zero Trust can be mapped against specific controls within a regulatory or standards framework.

#### Example 1

Zero Trust for Identity is mapped to Access Control Management within the Center for Internet Security (CIS)) Benchmark, as well as to Annexure A.9.2.2 User Access Provisioning in ISO 27001:2022.

:::image type="content" source="../media/adoption-guide/regulatory-compliance-example-identities.svg" alt-text="Zero Trust for identity mapped to Access Control Management." lightbox="../media/adoption-guide/regulatory-compliance-example-identities.svg":::

In this diagram, Access Control Management is defined in Annexure 9.2.2 of the ISO 27001 requirements standard, User Access Provisioning. The requirements for this section are satisfied by requiring multifactor authentication. 

The execution of each control, like the enforcement of Conditional Access policies, is unique to each organization. Your organization’s risk profile along with an inventory of assets should create an accurate surface area and scope of implementation.

#### Example 2

One of the more obvious correlations between Zero Trust architecture and industry standards includes information classification. Annexure 8.2.1 from ISO 27001, dictates that: 

- Information must be classified in terms of legal requirements, value, criticality and sensitivity to any unauthorized disclosure or modification, ideally classified to reflect business activity rather than inhibit or complicate it.

:::image type="content" source="../media/adoption-guide/regulatory-compliance-example-data.svg" alt-text="Zero Trust for data mapped to Access Control Management." lightbox="../media/adoption-guide/regulatory-compliance-example-data.svg":::

In this diagram, the Microsoft Purview data classification service is used to define and apply sensitivity labels to emails, documents, and structured data. 

#### Example 3

Annexure 8.1.1 In ISO 27001:2022 (Inventory of assets) requires that “any assets associated with information and information processing facilities need to be identified and managed over the lifecycle, and are always up to date.”

The fulfillment of this control requirement can be achieved through the implementation of Intune device management. This requirement provides a clear account of inventory and reports the status of compliance for each device against defined company or industry policies.

:::image type="content" source="../media/adoption-guide/regulatory-compliance-example-devices.svg" alt-text="Zero Trust for devices mapped to Access Control Management." lightbox="../media/adoption-guide/regulatory-compliance-example-devices.svg":::

In this, you use Microsoft Intune to manage devices, including setting up compliance policies to report on the compliance of devices against the policies you set. You can additionally use Conditional Access policies to require device compliance during the authentication and authorization process.

#### Example 4

The most comprehensive example of a pillar of Zero Trust that has been mapped to industry standards would be Threat intelligence and Incident response. The entire Microsoft Defender and Azure Sentinel breadth of products become applicable in this scenario to provide in-depth analysis and execution of threat intelligence and real-time incident response.

:::image type="content" source="../media/adoption-guide/regulatory-compliance-example-threat-intelligence.svg" alt-text="Zero Trust for threat intelligence mapped to Access Control Management." lightbox="../media/adoption-guide/regulatory-compliance-example-threat-intelligence.svg":::

In this diagram, Microsoft Sentinel together with Microsoft Defender tools provide threat intelligence.

## Adopt phase

:::image type="content" source="../media/adoption-guide/adopt-phase.svg" alt-text="The adopt phase." lightbox="../media/adoption-guide/adopt-phase.svg":::

In the adoption phase, you incrementally implement your technical plans across your digital estate. You’ll need to categorize the technical plans by area and work with the corresponding teams to accomplish this.

For identity and device access, take a staged approach where you start with a small number of users and devices and then gradually increase the deployment to include your full environment. This is described in the [Secure remote and hybrid work](secure-remote-hybrid-work.md) adoption scenario. Here is an example.

:::image type="content" source="../media/adoption-guide/adoption-phases.svg" alt-text="Pilot, evaluate, and full deployment adoption phases." lightbox="../media/adoption-guide/adoption-phases.svg":::

Adoption for protecting data involves cascading the work and iterating as you go to be sure the policies you create are appropriately honed for your environment. This is described in the [Identify and protect sensitive data](identify-protect-sensitive-business-data.md) adoption scenario. Here is an example.

:::image type="content" source="../media/adoption-guide/adoption-information-protection.svg" alt-text="Process for technical adoption of information protection." lightbox="../media/adoption-guide/adoption-information-protection.svg":::

## Govern and manage

Meeting regulatory and compliance requirements is an ongoing process. As you transition to this phase, shift to tracking and monitoring. Microsoft provides a handful of tools to help.

You can use content explorer to monitor the status of organizational compliance. For data classification, content explorer provides a view of the landscape and spread of sensitive information within your organization. From trainable classifiers to different types of sensitive data—either through adaptive scopes or manually created sensitivity labels—your administrators can see whether the prescribed sensitivity schema is being applied correctly throughout the organization. This is also an opportunity to identify specific areas of risk where sensitive information is consistently shared in Exchange, SharePoint, and OneDrive. Here is an example.

:::image type="content" source="../media/adoption-guide/article-5-meet-regulatory-and-compliance-requirements-06.png" alt-text="Example of a content explorer dashboard." lightbox="../media/adoption-guide/article-5-meet-regulatory-and-compliance-requirements-06.png":::

By using the greater reporting functionality within the Microsoft Purview Compliance portal, you can create and quantify a macro-view of compliance. Here is an example.

:::image type="content" source="../media/adoption-guide/article-5-meet-regulatory-and-compliance-requirements-07.png" alt-text="Example of a macro-view dashboard for Microsoft Purview Compliance." lightbox="../media/adoption-guide/article-5-meet-regulatory-and-compliance-requirements-07.png":::

The same thinking and process can be applied to Azure. Use Defender for Cloud-Regulatory Compliance to determine a compliance score similar to the same score provided in the Purview Compliance Manager. The score is aligned to multiple regulatory standards and frameworks across various industry verticals. It is up to your organization to understand which of these regulatory standards and frameworks apply to the score. The status provided by this dashboard displays a constant real-time assessment of passing versus failing assessments with each standard. Here is an example.

:::image type="content" source="../media/adoption-guide/article-5-meet-regulatory-and-compliance-requirements-08.png" alt-text="Example of the compliance score in the Microsoft Defender for Cloud portal." lightbox="../media/adoption-guide/article-5-meet-regulatory-and-compliance-requirements-08.png":::

The Purview dashboards provide a broad assessment that can help inform your business leaders and be used in departmental reporting, such as a quarterly review. On a more operational note, you can leverage Microsoft Sentinel by creating a Log Analytics workspace for unified audit log data. This workspace can be connected to your Microsoft 365 data and provide insights on user activity. Here is an example.

:::image type="content" source="../media/adoption-guide/article-5-meet-regulatory-and-compliance-requirements-09.png" alt-text="Example of data gathered in Microsoft Sentinel for Office 365." lightbox="../media/adoption-guide/article-5-meet-regulatory-and-compliance-requirements-09.png":::

This data is customizable and can be used in conjunction with the other dashboards to contextualize the regulatory requirement specifically aligned to your organization’s strategy, risk profile, goals, and objectives.

## Next Steps

- [Zero Trust adoption framework overview](zero-trust-adoption-overview.md)
- [Rapidly modernize your security posture](rapidly-modernize-security-posture.md)
- [Secure remote and hybrid work](secure-remote-hybrid-work.md)
- [Identify and protect sensitive business data](identify-protect-sensitive-business-data.md)
