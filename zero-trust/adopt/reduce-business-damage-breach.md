---
title: Reduce business damage from a breach with Zero Trust
description: Reduce business damage from a breach with Zero Trust.  
ms.date: 11/31/2023
ms.service: security
author: BrendaCarter
ms.author: bcarter
ms.topic: conceptual
ms.collection: 
  - zerotrust-adopt
---

# Deploy business damage mitigation and recovery (reduce business damage from a breach)

Intro

## The adoption cycle for deploying business damage mitigation and recovery

This article walks through this business scenario using the same lifecycle phases as the [Cloud Adoption Framework for Azure](/azure/cloud-adoption-framework/overview)—Define strategy, Plan, Ready, Adopt, and Govern and manage—but adapted for Zero Trust.

:::image type="content" source="../media/adoption-guide/objective-adoption-process.svg" alt-text="Diagram of the adoption process for an objective." lightbox="../media/adoption-guide/objective-adoption-process.svg":::

The following table is an accessible version of the illustration.

| Define strategy| Plan| Ready| Adopt| Govern and manage |
| --- | --- | --- | --- | --- |
| Outcomes <br><br> Organizational alignment <br><br> Strategic goals| Stakeholder team <br><br> Technical plans <br><br> Skills readiness| Evaluate <br><br> Test <br><br> Pilot| Incrementally implement across your digital estate | Track and measure <br><br> Monitor and detect <br><br> Iterate for maturity |

Read more about the Zero Trust adoption cycle in the [Zero Trust adoption framework overview](zero-trust-adoption-overview.md).

## Define strategy phase

:::image type="content" source="../media/adoption-guide/define-strategy-phase.svg" alt-text="The define strategy phase." lightbox="../media/adoption-guide/define-strategy-phase.svg":::

The **Define strategy** phase is critical to define and formalize our efforts – it formalizes the “Why?” of this scenario. In this phase, you understand the scenario through business, IT, operational and strategic perspectives. You define the outcomes against which to measure success in the scenario, understanding that security is an incremental and iterative journey.

This article suggests motivations and outcomes that are relevant to many organizations. Use these suggestions to hone the strategy for your organization based on your unique needs.

### Motivations for deploying business damage mitigation and recovery

The motivations for reducing business damage from a breach are straightforward, but different parts of your organization have different incentives for doing this work. The following table summarizes some of these motivations.

| Area | Motivations |
| --- | --- |
| Business needs |  |
| IT needs |  |
| Operational needs |  |
| Strategic needs |  |


### Outcomes for deploying business damage mitigation and recovery

Applying the overall goal of Zero Trust to “never trust, always verify” adds a significant layer of protection to your environment. It’s important to be clear on the outcomes you expect to achieve so that you can strike the right balance of protection for all teams involved. The following table provides suggested objectives and outcomes.

| Objective | Outcome |
| --- | --- |
| Business outcomes |  |
| Governance |  |
| Organizational resilience |  |
| Security |  |

## Plan phase

:::image type="content" source="../media/adoption-guide/plan-phase.svg" alt-text="The plan phase." lightbox="../media/adoption-guide/plan-phase.svg":::

Adoption plans convert the principles of Zero Trust strategy into an actionable plan. Your collective teams can use the adoption plan to guide their technical efforts and align them with your organization's business strategy.

The motivations and outcomes you define, together with your business leaders and teams, support the “Why?” for your organization and become the North Star for your strategy. Next comes the technical planning to achieve the objectives.

Technical adoption for reducing business damage from a breach involves:

- 
- 

reducing business damage from a breach also involves a few related activities, including:

- 
- 

Many organizations can take a four-staged approach to these deployment objectives, summarized in the following table.

| Stage 1 | Stage 2 | Stage 3 | Stage 4 |
| --- | --- | --- | --- |
| Secure privileged accounts <br><br> Implement Azure Backup for critical business data <br><br> Implement Site Recovery for critical workload continuity <br><br> Encrypt network communication | Segment your network <br><br> Implement a patching plan <br><br> Protect against ransomware <br><br> Create honeypot resources <br><br> Adopt a cybersecurity framework	 | Implement Microsoft 365 Backups, Azure Backups, and Azure Site Recovery for all business data  <br><br> Gain visibility to network traffic <br><br> Update security team skills | Discontinue legacy network security technology <br><br> Practice threat and disaster recovery response <br><br> Gather industry specific threat intelligence |

If this staged approach works for your organization, you can share your progress with your teams and business leaders by downloading [this PowerPoint slide deck](https://download.microsoft.com/download/a/b/5/ab51ac2a-e9de-4c8f-8323-6bc7c2f78c1f/ZeroTrust-Adoption-Resources.pptx) to track your progress through these stages and objectives. Here's the initial slide for this business scenario.

:::image type="content" source="../media/adoption-guide/placeholder.svg" alt-text="PowerPoint slide for the deployment stages of reducing business damage from a breach." lightbox="../media/adoption-guide/placeholder.svg":::

### Understand your organization

This recommended staged approach for technical implementation can help give context to the exercise of understanding your organization. 

A foundational step in the Zero Trust adoption lifecycle for every business scenario includes taking inventory. For this business scenario, you...

The following actions apply:

- 
- 

### Organizational planning and alignment

The technical work of reducing business damage from a breach crosses several overlapping areas and roles:

- Network
- Infrastructure

This table summarizes roles that are recommended when building a sponsorship program and project management hierarchy to determine and drive results.

| Program leaders and technical owners | Accountability |
| --- | --- |
| CISO, CIO, or Director of Data Security | Executive sponsorship |
| Program lead from Data Security | Drive results and cross-team collaboration |
| Security Architect | Advise on configuration and standards, especially around encryption, key management, and other fundamental technologies |
| Network Architect | Advise on network standards and practices |
| Compliance Officers | Map compliance requirements and risks to specific controls and available technologies |
| Data Security Admin | Implement configuration changes |
| IT Admin | Update standards and policy documents |
| Security Governance and/or IT Admin | Monitor to ensure compliance |

The [PowerPoint deck of resources](https://download.microsoft.com/download/a/b/5/ab51ac2a-e9de-4c8f-8323-6bc7c2f78c1f/ZeroTrust-Adoption-Resources.pptx) for this adoption content includes the following slide with a stakeholder view that you can customize for your own organization.

:::image type="content" source="../media/adoption-guide/placeholder.svg" alt-text="PowerPoint slide to identify key stakeholders." lightbox="../media/adoption-guide/placeholder.svg":::

### Technical planning and skills readiness

Before you embark on the technical work, Microsoft recommends getting to know the capabilities, how they work together, and best practices for approaching this work. The following table includes several resources to help your teams gain skills.

| Resource | Description |
|:-----|:-----|
|  |  |

#### Stage 1

The Stage 1 deployment objectives include the process of...

In this stage, you:

- Secure privileged accounts
- Implement Azure Backup for critical business data
- Implement Site Recovery for critical workload continuity
- Encrypt network communication

##### Secure privileged accounts

| Resource | Description |
|:-----|:-----|
|  |  |

##### Implement Azure Backup for critical business data

| Resource | Description |
|:-----|:-----|
|  |  |

##### Implement Site Recovery for critical workload continuity

| Resource | Description |
|:-----|:-----|
|  |  |

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
- Protect against ransomware
- Create honeypot resources
- Adopt a cybersecurity framework

##### Segment your network

This objective is

| Resource | Description |
| --- | --- |
|  |  |

##### Implement a patching plan

This objective is

| Resource | Description |
| --- | --- |
|  |  |

##### Protect against ransomware

This objective is

| Resource | Description |
| --- | --- |
|  |  |

##### Create honeypot resources

This objective is

| Resource | Description |
| --- | --- |
|  |  |

##### Adopt a cybersecurity framework

This objective is

| Resource | Description |
| --- | --- |
|  |  |

#### Stage 3

In this stage, you:

- Implement Microsoft 365 Backups, Azure Backups, and Azure Site Recovery for all business data
- Gain visibility into network traffic
- Update security team skills

##### Implement Microsoft 365 Backups, Azure Backups, and Azure Site Recovery for all business data

This objective is

| Resource | Description |
| --- | --- |
|  |  |

##### Gain visibility into network traffic

This objective is

| Resource | Description |
| --- | --- |
|  |  |

##### Update security team skills

This objective is

| Resource | Description |
| --- | --- |
|  |  |

#### Stage 4

In this stage, you:

- Discontinue legacy network security technology
- Practice threat and disaster recovery response
- Gather industry-specific threat intelligence

##### Discontinue legacy network security technology

This objective is

| Resource | Description |
| --- | --- |
|  |  |

##### Practice threat and disaster recovery response

This objective is

| Resource | Description |
| --- | --- |
|  |  |

##### Gather industry-specific threat intelligence

This objective is

| Resource | Description |
| --- | --- |
|  |  |

## Ready phase

:::image type="content" source="../media/adoption-guide/ready-phase.svg" alt-text="The ready phase." lightbox="../media/adoption-guide/ready-phase.svg":::

The staged approach recommended in this article includes cascading the work in a methodical way across your digital estate. At this Ready phase, revisit these elements of the plan to be sure everything is ready to go:

- 
- 

This list summarizes the high-level methodical process for doing this work.

## Adopt phase

:::image type="content" source="../media/adoption-guide/adopt-phase.svg" alt-text="The adopt phase." lightbox="../media/adoption-guide/adopt-phase.svg":::

Microsoft recommends a cascading, iterative approach to reducing business damage from a breach. This allows you to refine your strategy and policies as you go to increase the accuracy of the results. 

There’s no need to wait until one phase is complete before beginning the next. Your results are more effective if you iterate along the way.

## Govern and manage phases

:::image type="content" source="../media/adoption-guide/govern-manage-phase.svg" alt-text="The govern and manage phase." lightbox="../media/adoption-guide/govern-manage-phase.svg":::

Use the following exercises to help you start building your foundation:

- 
-  
- 

## Next Steps

- [Zero Trust adoption framework overview](zero-trust-adoption-overview.md)
- [Rapidly modernize your security posture](rapidly-modernize-security-posture.md)
- [Secure remote and hybrid work](secure-remote-hybrid-work.md)
- [Identify and protect sensitive business data](identify-protect-sensitive-business-data.md)
- [Meet regulatory and compliance requirements](meet-regulatory-compliance-requirements.md)
