---
title: Implement security breach prevention and recovery infrastructure
description: Implement security breach prevention and recovery infrastructure.  
ms.date: 12/18/2023
ms.service: security
author: BrendaCarter
ms.author: bcarter
ms.topic: conceptual
ms.collection: 
  - zerotrust-adopt
---

# Implement security breach prevention and recovery infrastructure

As part of Zero Trust adoption guidance, this article is part of the part of the Prevent or reduce business damage from a breach (link to be added) business scenario and describes how to protect your organization from cyberattacks. This article focuses on how to deploy additional security measures to prevent a breach and limit its spread and to create and test a business continuity and disaster recovery (BCDR) infrastructure to more quickly recover from a destructive breach.

For the elements of the “assume breach” Zero Trust guiding principle:

- Minimize blast radius and segment access

  Described in this article.

 - Verify end-to-end encryption

  Described in this article.
 
- Use analytics to get visibility, drive threat detection, and improve defenses

  Described in the [implement threat protection and XDR](prevent-reduce-business-damage-breach-threat-protection.md) article.

This article assumes that you have already [modernized your security posture](rapidly-modernize-security-posture.md).

## The adoption cycle for implementing security breach prevention and recovery infrastructure

This article walks through implementing security breach prevention and recovery infrastructure of the [Prevent or reduce business damage from a breach](prevent-reduce-business-damage-breach.md) business scenario using the same lifecycle phases as the [Cloud Adoption Framework for Azure](/azure/cloud-adoption-framework/overview)—Define strategy, Plan, Ready, Adopt, and Govern and manage—but adapted for Zero Trust.

:::image type="content" source="../media/adoption-guide/objective-adoption-process.svg" alt-text="Diagram of the adoption process for an objective." lightbox="../media/adoption-guide/objective-adoption-process.svg":::

The following table is an accessible version of the illustration.

| Define strategy| Plan| Ready| Adopt| Govern and manage |
| --- | --- | --- | --- | --- |
| Outcomes <br><br> Organizational alignment <br><br> Strategic goals| Stakeholder team <br><br> Technical plans <br><br> Skills readiness| Evaluate <br><br> Test <br><br> Pilot| Incrementally implement across your digital estate | Track and measure <br><br> Monitor and detect <br><br> Iterate for maturity |

Read more about the Zero Trust adoption cycle in the [Zero Trust adoption framework overview](zero-trust-adoption-overview.md).

For more information about the "Prevent or reduce business damage from a breach" business scenario, see:

- The [overview](prevent-reduce-business-damage-breach.md)
- The additional elements of [implementing threat protection and XDR](prevent-reduce-business-damage-breach-threat-protection.md)


## Define strategy phase

:::image type="content" source="../media/adoption-guide/define-strategy-phase.svg" alt-text="The define strategy phase." lightbox="../media/adoption-guide/define-strategy-phase.svg":::

The **Define strategy** phase is critical to define and formalize our efforts – it formalizes the “Why?” of this scenario. In this phase, you understand the scenario through business, IT, operational and strategic perspectives. You define the outcomes against which to measure success in the scenario, understanding that security is an incremental and iterative journey.

This article suggests motivations and outcomes that are relevant to many organizations. Use these suggestions to hone the strategy for your organization based on your unique needs.

### Motivations for implementing security breach prevention and recovery infrastructure

The motivations for security breach prevention and recovery infrastructure are straightforward, but different parts of your organization have different incentives for doing this work. The following table summarizes some of these motivations.

| Area | Motivations |
| --- | --- |
| Business needs | To operate your business with a posture of breach prevention and recovery as an extension of security. Your business can recover from a breach containing damage within one or more areas while continuing business as normal. |
| IT needs | To implement technologies and disciplines to lower the probability of a breach, such as updating on-premises systems and endpoints and deploying honeypot resources to distract and deceive attackers, all while maintaining an uncompromising approach to identity security and provisioning. |
| Operational needs | To implement breach prevention and recovery as standard operating procedures. Breaches are expected and while undesired can be mitigated for your business vertical. |
| Strategic needs | To incrementally raise the ability of your business to recover from breaches, which can lower the return of investment to cyber attackers while increasing operating resiliency. The “assume breach” principle of Zero Trust forces you to plan for and execute changes and updates to ensure business survival, minimize breaches, and reduce breach recovery time. |


### Outcomes for implementing security breach prevention and recovery infrastructure

Applying the overall goal of Zero Trust to “never trust, always verify” to your breach damage prevention and reduction infrastructure adds a significant layer of protection to your environment. It’s important to be clear on the outcomes you expect to achieve so that you can strike the right balance of protection for all teams involved. The following table provides suggested objectives and outcomes.

| Objective | Outcome |
| --- | --- |
| Business outcomes | Breach prevention and recovery practices result in minimal costs associated with breaches and quick recovery of business processes. |
| Governance | Breach prevention and recovery tools and systems are deployed and internal processes are tested and ready for breaches. |
| Organizational resilience | Between security breach prevention and recovery and proactive threat protection (link to be added), your organization can recover from an attack quickly and prevent future attacks of its type. |
| Security | Breach prevention and recovery is integrated into your overall security requirements and policies. |

## Plan phase

:::image type="content" source="../media/adoption-guide/plan-phase.svg" alt-text="The plan phase." lightbox="../media/adoption-guide/plan-phase.svg":::

Adoption plans conAdoption plans convert the principles of Zero Trust strategy into an actionable plan. Your collective teams can use the adoption plan to guide their technical efforts and align them with your organization's business strategy.

The motivations and outcomes you define, together with your business leaders and teams, support the “Why?” for your organization and become the North Star for your strategy. Next comes the technical planning to achieve the objectives.

Technical adoption for implementing breach prevention and recovery involves:

•	Setting up Entra Privileged Identity Management (PIM) to protect your administrator and other privileged accounts for just-in time (JIT) access.
•	Increasing the security of your networking infrastructure.
•	Deploying honeypot resources on your network to lure attackers and detect their presence early.
•	Implementing a comprehensive patching infrastructure to keep servers and devices up to date.
•	Begin using Microsoft Purview Insider Risk Management.
•	Deploying a BCDR infrastructure to quickly recover from a destructive cyberattack.

Many organizations can take a four-staged approach to these deployment objectives, summarized in the following table.

| Stage 1 | Stage 2 | Stage 3 | Stage 4 |
| --- | --- | --- | --- |
| Secure privileged accounts <br><br> Implement Microsoft 365 Backup and Azure Backup for **critical** business data <br><br> Implement Site Recovery for **critical** workload continuity <br><br> Encrypt network communication | Segment your network <br><br> Implement a patching plan <br><br> Create honeypot resources <br><br> Get started with Microsoft Purview Insider Risk Management | Implement Microsoft 365 Backup and Azure Backups for **all** business data <br><br> Implement Azure Site Recovery for **all** workloads <br><br> Gain visibility to network traffic <br><br> Design your threat and business continuity/disaster recovery (BCDR) response | Discontinue legacy network security technology <br><br> Practice threat and BCDR response |

If this staged approach works for your organization, you can share your progress with your teams and business leaders by downloading [this PowerPoint slide deck](https://download.microsoft.com/download/a/b/5/ab51ac2a-e9de-4c8f-8323-6bc7c2f78c1f/ZeroTrust-Adoption-Resources.pptx) to track your progress through these stages and objectives. Here's the initial slide for this business scenario.

:::image type="content" source="../media/adoption-guide/zero-trust-breach-prevention-recovery-progress-tracking.svg" alt-text="PowerPoint slide for the deployment stages of implementing breach prevention and recovery." lightbox="../media/adoption-guide/zero-trust-breach-prevention-recovery-progress-tracking.svg":::

### Understand your organization

This recommended staged approach for technical implementation can help give context to the exercise of understanding your organization. 

A foundational step in the Zero Trust adoption lifecycle for every business scenario includes taking inventory and determining the current state of your infrastructure. For this business scenario, you need to collect information on your current:

•	Privileged identity security policies and requirements.
•	Network security practices and technologies.
•	Insider risks and priorities for managing them.
•	Server and device patching policies and requirements.
•	BCDR systems and policies.


### Organizational planning and alignment

The technical work of preventing a breach and implementing a recovery infrastructure crosses several overlapping areas and roles:

•	Privileged identities
•	Networking
•	Insider risk management
•	Device patching
•	BCDR

This table summarizes roles that are recommended when building a sponsorship program and project management hierarchy to determine and drive results.

| Program leaders and technical owners | Accountability |
| --- | --- |
| CISO, CIO, or Director of Data Security | Executive sponsorship |
| Program lead from Security | Drive results and cross-team collaboration |
| Security Architect | Advise on configuration and standards, especially around privileged identities, networking, and the design of honeypot resources |
| IT Lead | Maintain honeypot resources, implement patching and system update requirements and policies, and implement and practice BCDR procedures |
| Network Architect | Advise on and implement network security standards and practices |
| Compliance Officers | Map compliance requirements and risks to specific controls and available technologies and advise on insider risks to be detected and managed |
| Security Governance and/or IT Lead | Monitor to ensure compliance with defined policies and requirements |

The [PowerPoint deck of resources](https://download.microsoft.com/download/a/b/5/ab51ac2a-e9de-4c8f-8323-6bc7c2f78c1f/ZeroTrust-Adoption-Resources.pptx) for this adoption content includes the following slide with a stakeholder view that you can customize for your own organization.

:::image type="content" source="../media/adoption-guide/zero-trust-breach-prevention-recovery-stakeholders.svg" alt-text="PowerPoint slide for the stakeholders of implementing breach prevention and recovery." lightbox="../media/adoption-guide/zero-trust-breach-prevention-recovery-stakeholders.svg":::

### Technical planning and skills readiness

Before you embark on the technical work, Microsoft recommends getting to know the capabilities, how they work together, and best practices for approaching this work. The following table includes several training resources to help your teams gain skills.

| Resource | Description |
|:-----|:-----|
| Module: [ Plan and implement privileged access](https://learn.microsoft.com/en-us/training/modules/plan-implement-privileged-access/) | Learn how to use PIM to protect your data and resources. |
| Module: [Design a solution for backup and disaster recovery](https://learn.microsoft.com/en-us/training/modules/design-solution-for-backup-disaster-recovery/) | 	Learn how to select appropriate backup solutions and disaster recovery solutions for Azure workloads. |
| Module: [Protect your on-premises infrastructure from disasters with Azure Site Recovery](https://learn.microsoft.com/en-us/training/modules/protect-on-premises-infrastructure-with-azure-site-recovery/) | Learn how to provide disaster recovery for your on-premises infrastructure by using Azure Site Recovery. |
| Module: [Protect your Azure infrastructure with Azure Site Recovery](https://learn.microsoft.com/en-us/training/modules/protect-infrastructure-with-site-recovery/) | Learn how to provide disaster recovery for your Azure infrastructure by customizing replication, failover, and failback of Azure virtual machines. |
| Module: [Design and implement network security](https://learn.microsoft.com/en-us/training/modules/design-implement-network-security-monitoring/) | 	Learn how to design and implement network security solutions such as Azure DDoS, Network Security Groups, Azure Firewall, and Web Application Firewall. |
| Module: [Secure and isolate access to Azure resources by using network security groups and service endpoints](https://learn.microsoft.com/en-us/training/modules/secure-and-isolate-with-nsg-and-service-endpoints/) | Learn how to use network security groups and service endpoints to secure your virtual machines and Azure services from unauthorized network access. |
| Module: [Windows Server update management](https://learn.microsoft.com/en-us/training/modules/windows-server-update-management/) | Learn how to use Windows Server Update Services to deploy operating system updates to computers on your network. |

#### Stage 1

The Stage 1 deployment objectives include locking down administrator and other privileged access accounts, using Microsoft cloud products to back up critical business data, and ensuring that all network traffic is encrypted.

##### Secure privileged accounts

Cybersecurity incidents typically begin with a credential theft of some sort. Attackers discover the account name, which can be a well-known or easily discovered email address, and then proceed to determine the password of the account. This type of attack can be thwarted in most cases by multi-factor authentication (MFA). However, the “assume breach” Zero Trust principle implies that an attacker can and will access your network using an identity.

Once in your network, attackers try to elevate their level of privilege by compromising accounts with more and more access. The goal is to compromise a privileged account that has access to a wide swath of not only sensitive data, but to administrative settings as well. Therefore, it is imperative that you prevent this level of access to attackers.

First, for hybrid identity organizations, you must ensure that administrator accounts or accounts holding privileged roles that are used for cloud services aren’t synchronized with and stored in on-premises Active Directory Domain Services (AD DS). If they are stored in stored in on-premises and AD DS or Microsoft Entra Connect is compromised, an attacker can have administrative control to your Microsoft cloud services. Review your synchronization settings to prevent and test whether your cloud administrator accounts are present in your AD DS.

All organizations with a Microsoft cloud subscription have an Entra ID tenant that contains cloud accounts, which include user and administrative accounts. Administrators need to perform privileged operations in Microsoft Entra ID, Azure, Microsoft 365, or SaaS apps. 

The first step to protecting privileged accounts is to require strong passwords and MFA. Additionally, pursuant to the “Use least privilege access” Zero Trust principle, use Microsoft Entra Privileged Identity Management (PIM) in your Microsoft Entra production environment to provide an additional layer of protection. Entra PIM provides time-based and approval-based role activation to mitigate the risks of excessive, unnecessary, or misused access permissions.

Features of Entra PIM include:

•	JIT privileged access to Microsoft Entra ID and Azure resources
•	Time-bound access to resources using start and end dates
•	Requiring approval to activate privileged roles
•	Enforcing MFA to activate any role
•	Require justification to understand why users activate
•	Get notifications when privileged roles are activated
•	Conduct access reviews to ensure users still need roles


| Resource | Description |
|:-----|:-----|
| []() |  |
| []() |  |
| []() |  |
| []() |  |
| []() |  |

##### Implement Microsoft 365 and Azure Backup for critical business data

| Resource | Description |
|:-----|:-----|
| []() |  |
| []() |  |
| []() |  |
| []() |  |
| []() |  |

##### Implement Site Recovery for critical workload continuity

| Resource | Description |
|:-----|:-----|
| []() |  |
| []() |  |
| []() |  |
| []() |  |
| []() |  |

##### Encrypt network communication

This objective is more of a check to be sure your network traffic is encrypted. Check in with your networking team to make sure these recommendations are satisfied.

| Resource | Description |
| --- | --- |
| [Secure networks with Zero Trust-Objective 3: User-to-app internal traffic is encrypted](/security/zero-trust/deploy/networks#iii-encryption-user-to-app-internal-traffic-is-encrypted) | Ensure user-to-app internal traffic is encrypted: <ul><li> Enforce HTTPS-only communication for your internet-facing web applications. </li><li> Connect remote employees and partners to Microsoft Azure using [Azure VPN Gateway](/azure/vpn-gateway/vpn-gateway-about-vpngateways). </li><li> Access your Azure virtual machines securely using encrypted communication through [Azure Bastion](/azure/bastion/bastion-overview). </li></ul> |
| [Secure networks with Zero Trust-Objective 6: All traffic is encrypted](/security/zero-trust/deploy/networks#vi-encryption-all-traffic-is-encrypted) | Encrypt application backend traffic between virtual networks.<br><br> Encrypt traffic between on-premises and cloud. |
| [Networking up (to the cloud)-One architect's viewpoint](/microsoft-365/solutions/networking-design-principles) | For network architects, this article helps put recommended networking concepts into perspective. Ed Fisher, Security & Compliance Architect at Microsoft, describes how to optimize your network for cloud connectivity by avoiding the most common pitfalls. |

#### Stage 2

In this stage, you:

- Segment your network
- Implement a patching plan
- Create honeypot resources
- Get started with Microsoft Purview Insider Risk Management

##### Segment your network

This objective is

| Resource | Description |
|:-----|:-----|
| []() |  |
| []() |  |
| []() |  |
| []() |  |
| []() |  |

##### Implement a patching plan

This objective is

| Resource | Description |
|:-----|:-----|
| []() |  |
| []() |  |
| []() |  |
| []() |  |
| []() |  |

##### Create honeypot resources

This objective is

| Resource | Description |
|:-----|:-----|
| []() |  |
| []() |  |
| []() |  |
| []() |  |
| []() |  |

#### Get started with Microsoft Purview Insider Risk Management

| Resource | Description |
|:-----|:-----|
| []() |  |
| []() |  |
| []() |  |
| []() |  |
| []() |  |

#### Stage 3

In this stage, you:

- Implement Microsoft 365 Backup and Azure Backup for **all** business data
- Implement Azure Site Recovery for **all** workloads
- Gain visibility into network traffic
- Design your threat and BCDR response

##### Implement Microsoft 365 Backup and Azure Backup for all business data

This objective is

| Resource | Description |
|:-----|:-----|
| []() |  |
| []() |  |
| []() |  |
| []() |  |
| []() |  |

##### Implement Azure Site Recovery for all workloads

This objective is

| Resource | Description |
|:-----|:-----|
| []() |  |
| []() |  |
| []() |  |
| []() |  |
| []() |  |

##### Gain visibility into network traffic

This objective is

| Resource | Description |
|:-----|:-----|
| []() |  |
| []() |  |
| []() |  |
| []() |  |
| []() |  |

##### Design your threat and BCDR response

This objective is

| Resource | Description |
|:-----|:-----|
| []() |  |
| []() |  |
| []() |  |
| []() |  |
| []() |  |

#### Stage 4

In this stage, you:

- Discontinue legacy network security technology
- Practice threat and BCDR response

##### Discontinue legacy network security technology

This objective is

| Resource | Description |
|:-----|:-----|
| []() |  |
| []() |  |
| []() |  |
| []() |  |
| []() |  |

##### Practice threat and BCDR response

This objective is

| Resource | Description |
|:-----|:-----|
| []() |  |
| []() |  |
| []() |  |
| []() |  |
| []() |  |

### Cloud adoption plan

## Ready phase

:::image type="content" source="../media/adoption-guide/ready-phase.svg" alt-text="The ready phase." lightbox="../media/adoption-guide/ready-phase.svg":::

The staged approach recommended in this article includes cascading the work in a methodical way across your digital estate. At this Ready phase, revisit these elements of the plan to be sure everything is ready to go:

- 

This list summarizes the high-level methodical process for doing this work.

## Adopt phase

:::image type="content" source="../media/adoption-guide/adopt-phase.svg" alt-text="The adopt phase." lightbox="../media/adoption-guide/adopt-phase.svg":::

Microsoft recommends a cascading, iterative approach to preventing business damage from a breach. This allows you to refine your strategy and policies as you go to increase the accuracy of the results. 

There’s no need to wait until one phase is complete before beginning the next. Your results are more effective if you iterate along the way.

## Govern and manage phases

:::image type="content" source="../media/adoption-guide/govern-manage-phase.svg" alt-text="The govern and manage phase." lightbox="../media/adoption-guide/govern-manage-phase.svg":::

Use the following exercises to help you start building your foundation:

- 

## Next Steps

For this business scenario:

- [Prevent or reduce business damage from a breach](prevent-reduce-business-damage-breach.md)
- [Implement threat protection and XDR](prevent-reduce-business-damage-breach-threat-protection.md)

Additional articles in the Zero Trust adoption framework:

- [Zero Trust adoption framework overview](zero-trust-adoption-overview.md)
- [Rapidly modernize your security posture](rapidly-modernize-security-posture.md)
- [Secure remote and hybrid work](secure-remote-hybrid-work.md)
- [Identify and protect sensitive business data](identify-protect-sensitive-business-data.md)
- [Meet regulatory and compliance requirements](meet-regulatory-compliance-requirements.md)
