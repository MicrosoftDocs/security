---
title: Zero Trust adoption framework overview
description: This article gives an overview of the Zero Trust adoption framework.
ms.date: 12/14/2023    
ms.service: security
author: BrendaCarter
ms.author: bcarter
ms.topic: conceptual
ms.collection: 
  - msftsolution-overview
  - zerotrust-adopt
---

# Zero Trust adoption framework overview

:::image type="content" source="../media/adoption-guide/zero-trust-working-group.jpg" alt-text="Zero Trust working group" lightbox="../media/adoption-guide/zero-trust-working-group.jpg":::

Digital transformation is shaping a new normal. Organizations are embracing digital transformation to manage continuous business environment changes by tracking:

- Shifting business models and partnerships.
- Technology trends.
- Regulatory, geopolitical, and cultural forces.

Additionally, COVID-19 remote work accelerated this transformation and is shifting security from a cost center to a strategic driver for growth.

Zero Trust is security for digital business. Digital transformation requires updating traditional security models because traditional security approaches don’t meet current requirements for business agility, user experiences, and continuously evolving threats. Organizations are implementing Zero Trust to address these challenges and enable the new normal of working anywhere, with anyone, at any time.

However, shifting from a traditional security model to Zero Trust represents a significant transformation that requires buy-in, adoption, and change management across an entire organization. Updating a traditional security model to Zero Trust is a transformation that takes time and requires buy-in, adoption, and change management across an entire organization. Business leaders, technology leaders, security leaders, and security practitioners all play critical parts in creating an agile Zero Trust security approach. 

Many security architects and IT teams ask for help communicating to business leaders, tracking progress, and driving adoption. This guidance helps security and technology teams collaborate with business leaders on Zero Trust by providing:

- Recommended Zero Trust objectives for business leaders across organizations.
- A methodical and phased approach to implementing a Zero Trust architecture.
- A systematic way to track progress, scoped to business leaders.
- Curation of the most relevant resources for adoption of Zero Trust from slides that are ready to present to business leaders to technical implementation guidance and user infographics.

“Our goal is to help every organization strengthen its security capabilities through a Zero Trust architecture built on our comprehensive solutions that span identity, security, compliance, and device management across all clouds and platforms.” –Satya Nadella, executive chairman and CEO of Microsoft

As a Microsoft partner, NBConsult contributed to and provided material feedback to this adoption guidance.

## Zero Trust requires buy-in at the highest level

Zero Trust protects business assets wherever they're and wherever they go. Zero Trust is a proactive, integrated approach to security that requires knowing what business assets and processes are most important to protect, and securing these while preserving business agility.

**Adopting a Zero Trust approach requires buy-in across the C-suite.** As the threat landscape expands, and critical attacks become more common, business leaders across functional areas are increasingly concerned with the cybersecurity approach their organization's take.

Zero Trust allows the entire C-suite and business to embrace a measurable business outcome that is aligned to reducing threats and increasing productivity.

Zero Trust adds value to two predominant scenarios that are seen in the marketplace:

1. **A formal security strategy aligned to business outcomes.** This Zero Trust approach provides a holistic view on security to the entire business, through values that are shared across the business and adopted at every level from the top down. This is often CISO-led and business outcomes are tracked as part of the reporting function of Zero Trust in an ongoing manner.
1. **Delegated security to IT functions** where security is treated as another technology vertical with minimal C-suite input and integration. This often focuses on short term cost optimization for security rather than managing it as a business risk, often further separating security into non-integrated “best of breed” independent solutions. 

Zero Trust provides a way of integrating the vertical solutions into a single vision. This vision supports consistent business capabilities and outcomes and provides ongoing measurable metrics on the state of security.

Traditionally the CISO or IT/Security manager sets strategy, or at least security technology choices. However, buy-in from the other C-level leaders is required to justify additional "security" spending. Under the Zero Trust security strategy, other C-suite members are required to take part in the Zero Trust journey, understanding that security is a shared business responsibility aligned to business outcomes.

The following is a generalized view of the possible functions taken by various C-level functions and how they align to an integrated vision of security using Zero Trust.

| Role | Responsibility | Zero Trust interest |
| --- | --- | --- |
| Chief Executive Officer (CEO) | Responsible for the business | Zero Trust provides an integrated approach to security across all digital layers. |
| Chief Marketing Officer (CMO) | Responsible for the marketing vision and execution | Zero Trust allows for the rapid recovery from breach and empowers the responsible reporting function for a public-facing organization, allowing breaches to be contained without reputational loss. |
| Chief Information Officer (CIO) | Responsible for IT as a whole | Zero Trust principles eliminate vertical security solutions that aren't aligned to business outcomes and enables Security as a Platform, which does align to business outcomes. |
| Chief Information Security Officer (CISO) | Responsible for security program implementation | Zero Trust principles provide a sufficient foundation for the organization to comply with various security standards and enables the organization to secure data, assets, and infrastructure. |
| Chief Technology Officer (CTO) | Chief Architect in the business | Zero Trust helps with defensible technology alignment aligned to business outcomes. Using Zero Trust, security is baked into every architecture. |
| Chief Operations Officer (COO) | Responsible for operational execution | Zero Trust helps with operational governance; the “how to” of the security vision and the surfacing of who did what and when. Both are aligned to business outcomes. |
| Chief Financial Officer (CFO) | Responsible for governance and spend | Zero Trust helps with the accountability of spend and the defensibility of spend; a measurable way of gaining a risk-based measure against security and Zero Trust spending aligned to business outcomes. |

## Zero Trust principles for the C-suite

Zero Trust is a strategy and architecture based on three principles.

| Principle | Technical description | Business description |
| --- | --- | --- |
| Verify explicitly | Always authenticate and authorize based on all available data points, including user identity, location, device health, service or workload, data classification, and anomalies. | This principle requires users to verify who they are, using more than one method, so that compromised accounts gained by hackers aren't allowed to access your data and apps. <br><br> This approach also requires devices to be recognized as being allowed to access the environment and, ideally, to be managed and healthy (not compromised by malware). |
| Use least privileged access | Limit user access with just-in-time and just-enough-access (JIT/JEA), risk-based adaptive policies, and data protection to help secure both data and productivity. | This principle limits the blast radius of a potential breach so that if an account is compromised, the potential damage is limited. <br><br> For accounts with greater privileges, such as administrator accounts, this involves using capabilities that limit how much access these accounts have and when they have access. It also involves using higher-levels of risk-based authentication policies for these accounts. <br><br> This principle also involves identifying and protecting sensitive data. For example, a document folder associated with a sensitive project should only include access permissions for the team members who need it. <br><br> These protections together limit how much damage can be caused by a compromised user account. |
| Assume breach | Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses. | This principle assumes the likelihood that an attacker will gain access to an account, identity, endpoint, application, API, or other asset. To respond, Microsoft protects all of the assets accordingly to limit the damage. <br><br> This principle also involves implementing tools for ongoing threat detection and rapid response. Ideally these tools have access to signals integrated across your environment and can take automated actions, such as disabling an account, to reduce the damage as soon as possible.|

## Zero Trust functional areas and technical architecture

The three principles of Zero Trust are applied across defense areas. These are sometimes referred to as functional areas or disciplines of IT management. Many organizations are structured around these areas with teams of specialized individuals.

Zero Trust requires taking an integrated approach across these areas and teams, which is why it's so important to have buy-in across the C-suite and a well-orchestrated strategy and plan across your organization.

| Functional area | Technical definition | Business translation |
| --- | --- | --- |
| Identities | Human and non-human identities, including users, computers, and service principals. Anything that can authenticate. | Anything human or machine based that is able to sign in or use your services. |
|Endpoints  | End user computing devices, including computers, laptops, mobile phones, and tablets. | The devices our users use to connect to your services and operate on your data. |
| Apps | Cloud or datacenter-based applications that require users to sign in and consume those services or applications. | All apps that are used by your organization, including SaaS apps that you subscribe to and other applications, whether in the cloud or on-premises. |
| Infrastructure | Infrastructure as a Service (IaaS) or datacenter-based infrastructure, including network components, servers, and data storage. | These are the technical foundations and components that support your organization, including physical and virtual servers hosted in your datacenter or a cloud service. |
| Data | Structured, unstructured, and application- contained data. | Your businesses data contained in files, databases, or other applications (such as CRM). |
| Network | LAN, WAN, wireless, or internet connection, including mobile (such as 3G and 5G) or even the coffee shop wireless network. | The network used to connect your users to the services they need. This may be a corporate-run local area network (LAN), the wider network encompassing access to your digital estate, or the internet connections used by your workers to connect. |

When applying Zero Trust strategy across a digital estate, it’s less helpful to think about tackling each of these domain areas independently. It’s not as if the identity team can accomplish all the recommendations and then the Zero Trust focus can move to the team that manages endpoints. Zero Trust strategy applies these functional areas together to secure an area within a digital estate and then broaden the scope of the protection across it. 

For example, the identity team can only make so much progress in utilizing Microsoft Entra Conditional Access policies before coordinating with the endpoints team to weave together protection.

The following diagram integrates these functional areas into a unified Zero Trust architecture.

:::image type="content" source="../media/zero-trust-ramp-overview/zero-trust-architecture.svg" alt-text="The overall architecture for Zero Trust" lightbox="../media/zero-trust-ramp-overview/zero-trust-architecture.svg":::

In the diagram:

- Each of the functional areas are represented: Identities, Endpoints, Network, Data, Apps, Infrastructure
- Zero Trust integrates protection across all the functional areas through policies and Policy Optimization.
- Threat protection brings together signals across the organization in real-time to provide visibility into attacks and to streamline remediation through automated actions and incident response tracking.

The next section discusses how to get started on the Zero Trust journey. We’ll use the **Identities** functional area as an example.  

## The Zero Trust adoption motion

Customers who are familiar with the Cloud Adoption Framework for Azure have asked, “Where’s the Zero Trust adoption framework?”

The [Cloud Adoption Framework for Azure](https://azure.microsoft.com/solutions/cloud-enablement/cloud-adoption-framework) is a methodical process for introducing new apps and services into an organization. The focus is primarily on a proven process an organization can follow to introduce an app or service into the environment. The scale motion is repeating the process for each app that is added to a digital estate.

Adoption of a Zero Trust strategy and architecture requires a different scope. It is about introducing new security configurations *across an entire digital estate*. The scale motion is two dimensional:

- Taking a piece of the Zero Trust architecture, such as data protection, and scaling out this protection across the entire digital estate.
- Repeating the process with each additional piece of the Zero Trust architecture, starting with strategic quick wins and foundational pieces, and then advancing to more complex pieces.

Like the Cloud Adoption Framework for Azure, this Zero Trust adoption guidance addresses the work through adoption scenarios as described in the next section.

The following diagram summarizes the differences between these two types of adoption motions.

:::image type="content" source="../media/adoption-guide/azure-and-zero-trust-frameworks.svg" alt-text="The differences between the Azure and Zero Trust adoption frameworks." lightbox="../media/adoption-guide/azure-and-zero-trust-frameworks.svg":::

This Zero Trust adoption guidance uses the same lifecycle phases as the Cloud Adoption Framework for Azure but adapted for Zero Trust.

:::image type="content" source="../media/adoption-guide/zero-trust-framework-lifecycle-phases.svg" alt-text="Zero Trust adoption guidance uses the same lifecycle phases" lightbox="../media/adoption-guide/zero-trust-framework-lifecycle-phases.svg":::

The following table describes the lifecycle phases.

| Lifecycle phase | Description |
| --- | --- |
| Define strategy | Build a business case focused on the outcomes most closely aligned with your organization’s risks and strategic goals. |
| Plan | <ul><li> Prioritize quick wins and incremental progress. </li><li> Embrace existing technologies already deployed or licensed. </li><li> Structure coherent initiatives with clear outcomes, benefits, and ownership. </li></ul> |
| Ready | <ul><li> Create a multi-layer strategy for your Zero Trust deployment and prioritize early actions based on business needs. </li><li> 	Identify adjustments to the prescriptive deployment guidance necessary for your environment.</li></ul>  |
| Adopt | Incrementally implement the strategy across functional areas. |
| Govern | Track and measure the success of your deployment. |
| Manage | <ul><li> Use monitoring and detection technologies. </li><li> Incrementally mature each functional area. </li></ul> |

## Business scenarios

This Zero Trust adoption guidance recommends building a Zero Trust strategy and architecture through these business scenarios:

- [Rapidly modernize your security posture](rapidly-modernize-security-posture.md)
- [Secure remote and hybrid work](secure-remote-hybrid-work.md)
- [Prevent or reduce business damage from a breach](prevent-reduce-business-damage-breach.md)
- [Identify and protect sensitive business data](identify-protect-sensitive-business-data.md)
- [Meet regulatory and compliance requirements](meet-regulatory-compliance-requirements.md)

Each business scenario is described in an article that describes how to progress the technical work through each of the lifecycle phases, starting with building the business case. The most appropriate resources are provided along the way.

Each of these business scenarios breaks down the work of Zero Trust into manageable pieces that can be implemented over four implementation stages. This helps you prioritize, move forward, and track work as you move through the different layers of implementing a Zero Trust architecture.

This guidance includes a [PowerPoint slide deck](https://download.microsoft.com/download/a/b/5/ab51ac2a-e9de-4c8f-8323-6bc7c2f78c1f/ZeroTrust-Adoption-Resources.pptx) with progress slides that you can use to present the work and track your progress at a high level for business leaders and other stakeholders. The slides include features that help you keep track of and present progress to stakeholders. Here's an example.

:::image type="content" source="../media/adoption-guide/zero-trust-remote-work-progress-tracking.png" alt-text="Example of a progress slide." lightbox="../media/adoption-guide/zero-trust-remote-work-progress-tracking.png":::

Across the business scenarios, the implementation stages are roughly aligned so that accomplishing the objectives of Stage 1 across the scenarios help keep your organization progressing on all fronts together.

## Starting a Zero Trust journey

If you are embarking on a Zero trust journey that is aligned to a business scenario or looking to embrace Zero Trust as a strategic defense doctrine, success can be difficult to measure. This is because security doesn't pass a simple pass/fail type of evaluation. Rather, security is a commitment and a journey, to which Zero Trust supplies guiding principles.

Using this adoption guidance as a process framework, first establish and document our security strategy, very similar to a Project Initiation Document (PID).  Using the principles that apply to strategy, at minimum, you should document:

- What are you doing?
- Why are you doing it?
- How do you agree on and measure success?

Each business scenario encompasses a different set of assets with different tools to take inventory. Methodically, you begin with an inventory and classification of the assets for each business scenario:

1. **Asset Identification:** What assets do you want to protect, such as identities, data, apps, services, and infrastructure? You may use the functional areas called out above as a guide of where to start. Asset identification forms part of your **Define strategy** and **Plan** lifecycle phases. The **Define strategy** phase can articulate a specific scenario, while the **Plan** phase documents the digital estate.
2. **Asset Classification:** How important is each one of the identified assets, such as identities, business critical data, and human resources data? Asset classification is part of the **Ready** phase where you begin to identify the protection strategy for each asset.
3. **Asset Management:** How do you choose to protect (govern) and administer (manage) these assets?
4. **Asset Recovery:** How do you recover from compromise or loss of control of an asset (govern)?

Each business scenario recommends how to take inventory as well as how to protect the assets and report on progress. While there is inevitably some overlap across the business scenarios, this adoption guidance attempts to simplify as much as possible by addressing asset types in predominantly one business scenario.

## Tracking progress

Tracking your progress throughout the Zero Trust adoption process is crucial as it allows your organization to monitor and measure strategic goals and objectives.

Microsoft recommends taking two approaches to tracking your progress:

1. Measure your progress against mitigating risks to your business.
2. Measure your progress towards achieving strategic objectives across the Zero Trust architecture.

Many organizations use International Organization for Standardization (ISO) standards resources and tools to gauge an organization’s risk. Specifically:

- ISO/IEC 27001:2022 

  - Information security, cybersecurity and privacy protection
  - Information security management systems
  - Requirements

- ISO 31000

  - Risk management

The requirements and guidelines in these standards are generic and can apply to any organization. They provide a structured and comprehensive way for you to review and gauge the risks that apply to your organization, as well as mitigations.

Identifying and understanding the specific risks that apply to your organization will help you prioritize your most strategic objectives across the Zero Trust architecture.

Once your organization has identified and prioritized your most strategic technical objectives, you can map out a staged roadmap for implementation. You can then track your progress by using various tools:

- A downloadable [PowerPoint slide deck](https://download.microsoft.com/download/a/b/5/ab51ac2a-e9de-4c8f-8323-6bc7c2f78c1f/ZeroTrust-Adoption-Resources.pptx) with progress tracking slides. These are designed to help you track and communicate progress at a high level. Customize these slides for your own use.
- [Secure Score](/microsoft-365/security/defender/microsoft-secure-score) is an aggregated score of technical controls that contribute to your current security posture. Secure Score gives your organization a global view of the controls that have and are still to be implemented.
- [Cloud Security Posture Management (CSPM) tools](/azure/defender-for-cloud/concept-cloud-security-posture-management) provided with Microsoft Defender for Cloud.

Note that the progress percentage provided by Secure Score might not be accurate for organizations that aren't willing to implement all controls due to reasons such as:

- Scope of the business
- Licensing
- Capacity

Additionally, several portals and reports can assist you in creating an overview of risk within your business, including:

- Reports within Microsoft Defender XDR provide information regarding security trends and track the protection status of your identities, data, devices, applications and infrastructure.
- The Cloud Security Explorer allows you to proactively hunt for security risks.

For example, within Microsoft Defender XDR, the device inventory provides a clear view into newly discovered devices in your network that aren't yet protected. At the top of each **Device inventory** tab, you can see the total number of devices that aren't onboarded. Here's an example.

:::image type="content" source="../media/adoption-guide/microsoft-365-defender-device-inventory-example.png" alt-text="Example of the Inventory tab in the Microsoft Defender portal" lightbox="../media/adoption-guide/microsoft-365-defender-device-inventory-example.png":::

For more information on using Microsoft Defender XDR to track your progress, see [Strengthen your security posture with Microsoft Defender XDR](/microsoft-365/security/security-posture-solution-overview).

For more information about how to use Secure Score, see [Secure Score documentation](/microsoft-365/security/defender/microsoft-secure-score). 

## Additional articles for adoption

- [Rapidly modernize your security posture](rapidly-modernize-security-posture.md)
- [Secure remote and hybrid work with Zero Trust](secure-remote-hybrid-work.md)
- [Prevent or reduce business damage from a breach](prevent-reduce-business-damage-breach.md)
- [Identify and protect sensitive business data](identify-protect-sensitive-business-data.md)
- [Meet regulatory and compliance requirements](meet-regulatory-compliance-requirements.md)

## Additional Zero Trust documentation

See additional Zero Trust content based on the documentation set or your role in your organization.

### Documentation set

Follow this table for the best Zero Trust documentation sets for your needs.

| Documentation set | Helps you... | Roles |
| --- | --- | --- |
| [Concepts and deployment objectives](deploy/overview.md) for general deployment guidance for technology areas | Apply Zero Trust protections aligned with technology areas. | IT teams and security staff |
| [Zero Trust for small businesses](guidance-smb-partner.md) | Apply Zero Trust principles to small business customers. | Customers and partners working with Microsoft 365 for business |
| [Zero Trust Rapid Modernization Plan (RaMP)](zero-trust-ramp-overview.md) for project management guidance and checklists for easy wins | Quickly implement key layers of Zero Trust protection. | Security architects and IT implementers |
| [Zero Trust deployment plan with Microsoft 365](/microsoft-365/security/microsoft-365-zero-trust?bc=%2fsecurity%2fzero-trust%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fzero-trust%2ftoc.json) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to your Microsoft 365 tenant. | IT teams and security staff |
| [Zero Trust for Microsoft Copilots](zero-trust-microsoft-365-copilot.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to your Copilots. | IT teams and security staff |
| [Zero Trust for Azure services](azure-infrastructure-overview.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Azure workloads and services. | IT teams and security staff |
| [Partner integration with Zero Trust](integrate/overview.md) for design guidance for technology areas and specializations | Apply Zero Trust protections to partner Microsoft cloud solutions. | Partner developers, IT teams, and security staff |
| [Develop using Zero Trust principles](develop/overview.md) for application development design guidance and best practices | Apply Zero Trust protections to your application. | Application developers |

### Your role

Follow this table for the best documentation sets for your role in your organization.

| Role | Documentation set | Helps you... |
| --- | --- | --- |
| Member of an IT or security team | [Concepts and deployment objectives](deploy/overview.md) for general deployment guidance for technology areas | Apply Zero Trust protections aligned with technology areas. |
| Customer or partner for Microsoft 365 for business | [Zero Trust for small businesses](guidance-smb-partner.md) | Apply Zero Trust principles to small business customers.  |
| Security architect <br><br> IT implementer | [Zero Trust Rapid Modernization Plan (RaMP)](zero-trust-ramp-overview.md) for project management guidance and checklists for easy wins | Quickly implement key layers of Zero Trust protection. |
| Member of an IT or security team for Microsoft 365 | [Zero Trust deployment plan with Microsoft 365](/microsoft-365/security/microsoft-365-zero-trust?bc=%2fsecurity%2fzero-trust%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fzero-trust%2ftoc.json) for stepped and detailed design and deployment guidance for Microsoft 365 | Apply Zero Trust protections to your Microsoft 365 tenant. |
| Member of an IT or security team for Microsoft Copilots | [Zero Trust for Microsoft Copilots](zero-trust-microsoft-365-copilot.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to your Copilots. |
| Member of an IT or security team for Azure services | [Zero Trust for Azure services](azure-infrastructure-overview.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Azure workloads and services. |
| Partner developer or member of an IT or security team | [Partner integration with Zero Trust](integrate/overview.md) for design guidance for technology areas and specializations | Apply Zero Trust protections to partner Microsoft cloud solutions. |
| Application developer | [Develop using Zero Trust principles](develop/overview.md) for application development design guidance and best practices | Apply Zero Trust protections to your application. |
