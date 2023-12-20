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

As part of Zero Trust adoption guidance, this article is part of the [Prevent or reduce business damage from a breach](prevent-reduce-business-damage-breach.md) business scenario and describes how to protect your organization from cyberattacks. This article focuses on how to deploy additional security measures to prevent a breach and limit its spread and to create and test a business continuity and disaster recovery (BCDR) infrastructure to more quickly recover from a destructive breach.

For the elements of the “assume breach” Zero Trust guiding principle:

- **Minimize blast radius and segment access**

  Described in this article.

 - **Verify end-to-end encryption**

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
| Outcomes <br><br> Organizational alignment <br><br> Strategic goals| Stakeholder team <br><br> Technical plans <br><br> Skills readiness| Evaluate <br><br> Test <br><br> Pilot | Incrementally implement across your digital estate | Track and measure <br><br> Monitor and detect <br><br> Iterate for maturity |

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
| Organizational resilience | Between security breach prevention and recovery and [proactive threat protection](prevent-reduce-business-damage-breach-threat-protection.md), your organization can recover from an attack quickly and prevent future attacks of its type. |
| Security | Breach prevention and recovery are integrated into your overall security requirements and policies. |

## Plan phase

:::image type="content" source="../media/adoption-guide/plan-phase.svg" alt-text="The plan phase." lightbox="../media/adoption-guide/plan-phase.svg":::

Adoption plans convert the principles of Zero Trust strategy into an actionable plan. Your collective teams can use the adoption plan to guide their technical efforts and align them with your organization's business strategy.

The motivations and outcomes you define, together with your business leaders and teams, support the “Why?” for your organization and become the North Star for your strategy. Next comes the technical planning to achieve the objectives.

Technical adoption for implementing breach prevention and recovery involves:

- Setting up Entra Privileged Identity Management (PIM) to protect your administrator and other privileged accounts for just-in time (JIT) access.
- Increasing the security of your networking infrastructure.
- Deploying honeypot resources on your network to lure attackers and detect their presence early.
- Implementing a comprehensive patching infrastructure to keep servers and devices up to date.
- Begin using Microsoft Purview Insider Risk Management.
- Deploying a BCDR infrastructure to quickly recover from a destructive cyberattack.

Many organizations can take a four-staged approach to these deployment objectives, summarized in the following table.

| Stage 1 | Stage 2 | Stage 3 | Stage 4 |
| --- | --- | --- | --- |
| Secure privileged accounts <br><br> Implement Microsoft 365 Backup and Azure Backup for **critical** business data <br><br> Implement Azure Site Recovery for **critical** workload continuity <br><br> Encrypt network communication | Segment your network <br><br> Implement a patching plan <br><br> Create honeypot resources <br><br> Get started with Microsoft Purview Insider Risk Management | Implement Microsoft 365 Backup and Azure Backup for **all** business data <br><br> Implement Azure Site Recovery for **all** workloads <br><br> Gain visibility to network traffic <br><br> Design your threat and business continuity/disaster recovery (BCDR) response | Discontinue legacy network security technology <br><br> Practice threat and BCDR response |

If this staged approach works for your organization, you can share your progress with your teams and business leaders by downloading [this PowerPoint slide deck](https://download.microsoft.com/download/a/b/5/ab51ac2a-e9de-4c8f-8323-6bc7c2f78c1f/ZeroTrust-Adoption-Resources.pptx) to track your progress through these stages and objectives. Here's the initial slide for this business scenario.

:::image type="content" source="../media/adoption-guide/zero-trust-breach-prevention-recovery-progress-tracking.png" alt-text="PowerPoint slide for the deployment stages of implementing breach prevention and recovery." lightbox="../media/adoption-guide/zero-trust-breach-prevention-recovery-progress-tracking.png":::

### Understand your organization

This recommended staged approach for technical implementation can help give context to the exercise of understanding your organization. 

A foundational step in the Zero Trust adoption lifecycle for every business scenario includes taking inventory and determining the current state of your infrastructure. For this business scenario, you need to collect information on your current:

- Privileged identity security policies and requirements.
- Network security practices and technologies.
- Insider risks and priorities for managing them.
- Server and device patching policies and requirements.
- BCDR systems and policies.


### Organizational planning and alignment

The technical work of preventing a breach and implementing a recovery infrastructure crosses several overlapping areas and roles:

- Privileged identities
- Networking
- Insider risk management
- Device patching
- BCDR

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

:::image type="content" source="../media/adoption-guide/zero-trust-breach-prevention-recovery-stakeholders.png" alt-text="PowerPoint slide for the stakeholders of implementing breach prevention and recovery." lightbox="../media/adoption-guide/zero-trust-breach-prevention-recovery-stakeholders.png":::

### Technical planning and skills readiness

Before you embark on the technical work, Microsoft recommends getting to know the capabilities, how they work together, and best practices for approaching this work. The following table includes several training resources to help your teams gain skills.

| Resource | Description |
|:-----|:-----|
| Module: [ Plan and implement privileged access](/training/modules/plan-implement-privileged-access/) | Learn how to use PIM to protect your data and resources. |
| Module: [Design a solution for backup and disaster recovery](/training/modules/design-solution-for-backup-disaster-recovery/) | 	Learn how to select appropriate backup solutions and disaster recovery solutions for Azure workloads. |
| Module: [Protect your on-premises infrastructure from disasters with Azure Site Recovery](/training/modules/protect-on-premises-infrastructure-with-azure-site-recovery/) | Learn how to provide disaster recovery for your on-premises infrastructure by using Azure Site Recovery. |
| Module: [Protect your Azure infrastructure with Azure Site Recovery](/training/modules/protect-infrastructure-with-site-recovery/) | Learn how to provide disaster recovery for your Azure infrastructure by customizing replication, failover, and failback of Azure virtual machines. |
| Module: [Design and implement network security](/training/modules/design-implement-network-security-monitoring/) | 	Learn how to design and implement network security solutions such as Azure DDoS, Network Security Groups, Azure Firewall, and Web Application Firewall. |
| Module: [Secure and isolate access to Azure resources by using network security groups and service endpoints](/training/modules/secure-and-isolate-with-nsg-and-service-endpoints/) | Learn how to use network security groups and service endpoints to secure your virtual machines and Azure services from unauthorized network access. |
| Module: [Windows Server update management](/training/modules/windows-server-update-management/) | Learn how to use Windows Server Update Services to deploy operating system updates to computers on your network. |

#### Stage 1

The Stage 1 deployment objectives include locking down administrator and other privileged access accounts, using Microsoft cloud products to back up critical business data, and ensuring that all network traffic is encrypted.

##### Secure privileged accounts

Cybersecurity incidents typically begin with a credential theft of some sort. Attackers discover the account name, which can be a well-known or easily discovered email address, and then proceed to determine the password of the account. This type of attack can be thwarted in most cases by multi-factor authentication (MFA). However, the “assume breach” Zero Trust principle implies that an attacker can and will access your network using an identity.

Once in your network, attackers try to elevate their level of privilege by compromising accounts with more and more access. The goal is to compromise a privileged account that has access to a wide swath of not only sensitive data, but to administrative settings as well. Therefore, it's imperative that you prevent this level of access to attackers.

First, for hybrid identity organizations, you must ensure that administrator accounts or accounts holding privileged roles that are used for cloud services aren’t synchronized with and stored in on-premises Active Directory Domain Services (AD DS). If they're stored on-premises and AD DS or Microsoft Entra Connect is compromised, an attacker can have administrative control to your Microsoft cloud services. Review your synchronization settings to prevent and test whether your cloud administrator accounts are present in your AD DS.

All organizations with a Microsoft cloud subscription have an Entra ID tenant that contains cloud accounts, which include user and administrative accounts. Administrators need to perform privileged operations in Microsoft Entra ID, Azure, Microsoft 365, or SaaS apps. 

The first step to protecting privileged accounts is to require strong passwords and MFA. Additionally, pursuant to the “Use least privilege access” Zero Trust principle, use Microsoft Entra PIM in your Microsoft Entra production environment to provide an additional layer of protection. Entra PIM provides time-based and approval-based role activation to mitigate the risks of excessive, unnecessary, or misused access permissions.

Features of Entra PIM include:

- JIT privileged access to Microsoft Entra ID and Azure resources
- Time-bound access to resources using start and end dates
- Requiring approval to activate privileged roles
- Enforcing MFA to activate any role
- Require justification to understand why users activate
- Get notifications when privileged roles are activated
- Conduct access reviews to ensure users still need roles

| Resource | Description |
|:-----|:-----|
| [What is hybrid identity with Microsoft Entra ID?](/entra/identity/hybrid/whatis-hybrid-identity) | Get started with the documentation set for Entra ID Connect. |
| [What is Microsoft Entra Privileged Identity Management?](/entra/id-governance/privileged-identity-management/pim-configure) | Get started with the documentation set for Entra PIM. |
| [Plan an Entra PIM deployment](/azure/active-directory/privileged-identity-management/pim-deployment-plan) | 	Step through the planning process for deploying PIM for your privileged accounts. |
| Module: [Plan and implement privileged access](/training/modules/plan-implement-privileged-access/) | Learn how to use PIM to protect your data and resources. |

##### Implement Microsoft 365 and Azure Backup for critical business data

BCDR is an important element of breach mitigation and a crucial part of a BCDR infrastructure is backup and restore. For cyberattacks, you also need to protect your backups against deliberate erasure, corruption, or encryption. In a ransomware attack, the attacker can encrypt, corrupt, or destroy both your live data and the backups, leaving your organization susceptible to a ransom to restore your business operations. To address this vulnerability, copies of your backed-up data must be immutable.

Microsoft offers Microsoft 365 Backup and Azure Backup for native backup and restore functions.

Microsoft 365 Backup is a new offering (currently in preview) that backs up your Microsoft 365 tenant data for Exchange, OneDrive and SharePoint workloads at scale and provides quick restores. Microsoft 365 Backup or applications built on top of the Microsoft 365 Backup Storage platform deliver the following benefits regardless of the size or scale of your tenant:

- Fast, immutable backup within hours
- Fast restore within hours
- Full SharePoint site and OneDrive account restore fidelity, meaning the site and OneDrive are restored to their exact state at specific prior points in time via a rollback operation
- Full Exchange mailbox item restores or granular item restores using search
- Consolidated security and compliance domain management

For more information, see the [Microsoft 365 Backup overview](/microsoft-365/syntex/backup/backup-overview).

The Azure Backup service provides simple, secure, and cost-effective solutions to back up your data and recover it from the Microsoft Azure cloud. Azure Backup can back up:

- On-premises files, folders, system state, on-premises VMs (Hyper-V and VMware) and other on-premises workloads.
- Azure VMs or files, folders, and system state.
- Azure Managed Disks
- Azure Files shares
- SQL Server in Azure VMs
- SAP HANA databases in Azure VMs
- Azure Database for PostgreSQL servers
- Azure Blobs


| Resource | Description |
|:-----|:-----|
| Module: [Design a solution for backup and disaster recovery](/training/modules/design-solution-for-backup-disaster-recovery/) | Learn how to select appropriate backup solutions and disaster recovery solutions for Azure workloads. |
| [Overview of Microsoft 365 Backup]() | Get started with the documentation set for Microsoft 365 Backup. |
| [What is the Azure Backup service?]() | Get started with the documentation set for Azure Backup. |
| [Azure Backup and ransomware]() | Learn how Azure Backup protects against a ransomware attack. |

You can use Microsoft 365 Backup and Azure Backup as part of your BCDR solution.

You can also use [incremental snapshots in Azure](/azure/virtual-machines/disks-incremental-snapshots?tabs=azure-cli) for forensic investigation after a breach. Incremental snapshots are point-in-time backups for managed disks that, when taken, consist only of the changes since the last snapshot. Snapshots allow you to establish the last point in time before a breach occurred and restore it to that state. 

Identity protection for the user accounts used to administer backups must use strong authentication with MFA and should use PIM for JIT access. Also ensure that your backup infrastructure is protected using secondary identities from another identity provider, such as local identities or local system identities. These are known as break glass accounts.

For example, if the cyberattack has compromised your Entra ID tenant and you are now locked out of using an Entra ID administrator account to access your backups, the backup infrastructure must allow for a sign-in that is separate from the compromised Entra ID tenant.


##### Implement Site Recovery for critical workload continuity

Azure Site Recovery is a native disaster recovery as a service (DRaaS) that offers ease of deployment, cost effectiveness, and dependability. Deploy replication, failover, and recovery processes through Site Recovery to help keep your applications running during planned and unplanned outages, such as an outage based on a cyberattack.

Azure Site Recovery has two main components:

- **Site Recovery service:** Site Recovery helps ensure business continuity by keeping business apps and workloads running during outages. Site Recovery [replicates](/azure/site-recovery/azure-to-azure-quickstart) workloads running on physical and virtual machines (VMs) from a primary site to a secondary location. When an outage occurs at your primary site, you fail over to a secondary location, and access apps from there. After the primary location is running again, you can fail back to it.
- **Backup service:** The [Azure Backup service](/azure/backup/backup-overview) keeps your data safe and recoverable. See the previous section for more information.

Site Recovery can manage replication for:

- Azure VMs replicating between Azure regions
- Replication from Azure Public Multi-Access Edge Compute (MEC) to the region
- Replication between two Azure Public MECs
- On-premises VMs, Azure Stack VMs, and physical servers

Use Azure Site Recovery as part of your BCDR solution.

| Resource | Description |
|:-----|:-----|
| [Site Recovery overview](/azure/site-recovery/site-recovery-overview) | Get started with the documentation set. |
| Module: [Protect your on-premises infrastructure from disasters with Azure Site Recovery](/training/modules/protect-on-premises-infrastructure-with-azure-site-recovery/) | Learn how to provide disaster recovery for your on-premises infrastructure by using Azure Site Recovery. |
| Module: [Protect your Azure infrastructure with Azure Site Recovery](/training/modules/protect-infrastructure-with-site-recovery/) | Learn how to provide disaster recovery for your Azure infrastructure by customizing replication, failover, and failback of Azure virtual machines. |

##### Encrypt network communication

This objective is more of a check to be sure your network traffic is encrypted. Check in with your networking team to make sure these recommendations are satisfied.

| Recommendations | Resource |
| --- | --- |
| Ensure user-to-app internal traffic is encrypted: <br><br> - Enforce HTTPS-only communication for your internet-facing web applications. <br> - Connect remote employees and partners to Microsoft Azure using [Azure VPN Gateway](/azure/vpn-gateway/vpn-gateway-about-vpngateways). <br>- Access your Azure virtual machines securely using encrypted communication through [Azure Bastion](/azure/bastion/bastion-overview). | [Secure networks with Zero Trust-Objective 3: User-to-app internal traffic is encrypted](/security/zero-trust/deploy/networks#iii-encryption-user-to-app-internal-traffic-is-encrypted) |
| Encrypt application backend traffic between virtual networks.<br><br> Encrypt traffic between on-premises and cloud. | [Secure networks with Zero Trust-Objective 6: All traffic is encrypted](/security/zero-trust/deploy/networks#vi-encryption-all-traffic-is-encrypted) |
| For network architects, this article helps put recommended networking concepts into perspective. Ed Fisher, Security & Compliance Architect at Microsoft, describes how to optimize your network for cloud connectivity by avoiding the most common pitfalls. | [Networking up (to the cloud)-One architect's viewpoint](/microsoft-365/solutions/networking-design-principles) |

#### Stage 2

The Stage 2 deployment objectives include segmenting your network to exercise better control for traffic to sensitive resources, ensuring your servers and devices are patched with updates in a timely manner, creating honeypot resources to deceive and distract attackers, and beginning the management of your insider risks.

##### Segment your network

This objective is to create boundaries on your network so that intermediate analysis and filtering can protect sensitive servers, applications, and data. Network segmentation can occur for on-premises servers or in the cloud, for example, with virtual machines hosted on virtual networks (VNets) in Azure IaaS.

| Recommendations | Resource |
|:-----|:-----|
| Use many ingress/egress cloud micro-perimeters with some micro-segmentation. | [Secure networks with Zero Trust](/security/zero-trust/deploy/networks#i-network-segmentation-many-ingressegress-cloud-micro-perimeters-with-some-micro-segmentation) |
| Use multiple subnets and network security groups to host multiple tiers of an app and restrict traffic. | [Apply Zero Trust principles to a spoke VNet in Azure](/security/zero-trust/azure-infrastructure-iaas) <br><br> [Apply Zero Trust principles to a spoke VNet with Azure PaaS Services](/security/zero-trust/azure-infrastructure-paas) |

##### Implement a patching plan

A patching plan includes configuring automatic updating across all your entire operating system estate so that patches are rolled out quickly to avoid attackers who rely on unpatched systems as attack vectors.

| Resource | Description |
|:-----|:-----|
| [Endpoint management at Microsoft](/mem/endpoint-manager-overview) | Get started with an overview of endpoint management solutions from Microsoft. |
| [Endpoint management](/mem/) | Get started with the documentation to manage your endpoints. |
| [Apply Zero Trust to Azure IaaS: Automate virtual machine updates](/security/zero-trust/azure-infrastructure-virtual-machines#automate-virtual-machine-updates) | Configure automatic updates for Windows and Linux-based virtual machines. |
| [Windows Update settings that you can manage through Intune policy](/mem/intune/protect/windows-update-settings) | Manage Windows Update settings for Windows 10 and Windows 11 with Microsoft Intune. |

Also consider updates and patches needed by other devices, especially those that:

- Provide security.

  Examples include internet access routers, firewalls, packet filtering devices, and other intermediate security analysis devices.

- Are part of your BCDR infrastructure.

  Examples include on-premises or on-line third-party backup services.


##### Create honeypot resources

You deliberately create honeypot resources—such as [identities](https://techcommunity.microsoft.com/t5/microsoft-365-defender-blog/deceptive-defense-best-practices-for-identity-based-honeytokens/ba-p/3851641), file shares, applications, and service accounts—so they can be discovered by attackers. These resources are dedicated to attracting and deceiving attackers and aren’t part of your normal IT infrastructure. 

Your honeypot resources should reflect typical targets for attackers. 
For example:

- User account names that imply administrator access but have no privileges beyond the honeypot resources. 
- File share resources that have file names implying sensitive data, such as CustomerDatabase.xlxs, but the data is fictional.

After deploying your honeypot resources, use your threat protection infrastructure to monitor them and detect an attack early. Ideally the detection occurs before the attacker has determined that the honeypot resources are fake and uses lateral transfer techniques to live off the land, in which the attacker uses your own apps and tools to attack your assets. During the attack on the honeypot resources, you can also collect information about the attacker’s identity, methods, and motivations.

##### Get started with Microsoft Purview Insider Risk Management

Microsoft Purview Insider Risk Management helps you quickly identify, triage, and act on potentially risky activity. By using logs from Microsoft 365 and Microsoft Graph, insider risk management allows you to define specific policies to identify risk indicators. Examples of internal risks from users include:

- Leaks of sensitive data and data spillage
- Confidentiality violations
- Intellectual property (IP) theft
- Fraud
- Insider trading
- Regulatory compliance violations

After identifying the risks, you can take action to mitigate these risks, and if necessary open investigation cases and take appropriate legal action.

| Resource | Description |
|:-----|:-----|
| [Insider risk management](/purview/insider-risk-management-solution-overview) | Get started with the documentation set. |
| Module: [Manage insider risk in Microsoft Purview](/training/modules/m365-compliance-insider-manage-insider-risk/) | Learn about insider risk management and how Microsoft technologies can help you detect, investigate, and act on risky activities in your organization. |
| Module: [Implement Microsoft Purview Insider Risk Management](/training/modules/implement-insider-risk-management/) | Learn how to use Microsoft Purview Insider Risk Management to plan your insider risk solution, create insider risk management policies and manage insider risk management alerts and cases. |

#### Stage 3

In this stage, you extend your backup and site recovery scope to include all business data and workloads, further your ability to prevent network-based attacks, and create a more formal design and plan for your threat and BCDR response.

##### Implement Microsoft 365 Backup and Azure Backup for all business data

Once you are satisfied that Microsoft 365 Backup and Azure Backup is working for your critical data and has been tested in recovery exercises, you can now extend it to include all your business data.

##### Implement Azure Site Recovery for all workloads

Once you are satisfied that Azure Site Recovery is working for your critical data and has been tested in recovery exercises, you can now extend it to include all your business data.

##### Gain visibility into network traffic

Cloud applications that have opened endpoints to external environments, such as the internet or on-premises, are at risk of attacks coming in from those environments. To prevent these attacks, you must scan the traffic for malicious payloads or logic.

For more information, see [Cloud native filtering and protection for known threats](/security/zero-trust/deploy/networks#ii-threat-protection-cloud-native-filtering-and-protection-for-known-threats).

##### Design your threat and BCDR response

The consequences of a breach can run the spectrum of an attacker infecting devices with malware, which might be detected and contained relatively easily, to ransomware attacks in which the attacker has already exfiltrated, encrypted, or destroyed some or all your organization’s sensitive data and is ransoming its exposure or restoration.

In a crippling ransomware attack, your organization can suffer a long-term business disruption that is similar in many respects to a crisis or a natural disaster. Think about a breach and its resulting destructive cyberattack as a human-made crisis or disaster. 

Therefore, it's important to include breaches and the possibility of a highly destructive cyberattack in your BCDR planning. The same infrastructure that you would use to continue your business operations in a crisis or after a natural disaster can and should be used to recover from an attack.

If you already have a BCDR plan in place, review it to ensure that it includes the data, devices, applications, and processes that could be impacted in a cyberattack. 

If not, begin your planning process for general BCDR and include cyberattacks as a source of crisis or disaster. Note that:

- BC plans ensure that the business can function normally in the event of a crisis.
- DR plans include contingencies to recover from loss of data or infrastructure through backups of data and replacement or recovery of infrastructure. 

  DR plans should include detailed procedures for recovering your IT systems and processes to restore business operations. These plans should have an off-line backup, such as on portable media stored in a location with physical security in place. Attackers can hunt for these types of IT recovery plans in your on-premises and cloud locations and destroy them as part of a ransomware attack. Because the destruction of these plans will make it more costly for you to restore your business operations, the attackers can demand more ransom.

Microsoft 365 Backup, Azure Backup, and Azure Site Recovery described in this article are examples of BCDR technologies.

| Resource | Description |
|:-----|:-----|
| Module: [Design a solution for backup and disaster recovery](/training/modules/design-solution-for-backup-disaster-recovery/) | Learn how to select appropriate backup solutions and disaster recovery solutions for Azure workloads. |

#### Stage 4

In this stage, you further secure your network and ensure that your BCDR plan and process works by practicing it for destructive cyberattack situations.

##### Discontinue legacy network security technology

Examine the set of technologies and products that your organization uses to provide network security and determine whether they're necessary or redundant with other network security capabilities. Each network security technology can also be a target for attackers. For example, if the technology or product isn’t being updated on a timely basis, consider removing it.

For more information, see [Discontinue legacy network security technology](/security/zero-trust/deploy/networks#vii-discontinue-legacy-network-security-technology), which describes the types of network security technologies that you might no longer need.

##### Practice threat and BCDR response

To ensure that your business operations can quickly recover from a devastating cyberattack, you should regularly practice your BCDR plan in conjunction with your SecOps team. Consider performing BCDR practice for cyberattacks once a month or quarter and when elements of your BCDR infrastructure change, such as the use of a different backup product or method.

### Cloud adoption plan

An adoption plan is an essential requirement for a successful cloud adoption. Key attributes of a successful adoption plan for Implementing security breach prevention and recovery include:

- **Strategy and planning are aligned:** As you draw up your plans for testing, piloting, and rolling out breach prevention and attack recovery capabilities across your digital estate, be sure to revisit your strategy and objectives to ensure your plans are aligned. This includes priority and target milestones of goals for breach prevention and recovery.
- **The plan is iterative:** As you start to roll out your plan, you'll learn many things about your environment and the capability set you're using. At each stage of your roll-out, revisit your results compared to the objectives and fine tune the plans. For example, you can revisit earlier work to fine tune your policies.
- **Training your staff and users is well-planned:** From your security architects to your IT specialists for networking, devices, and BCDR, everybody has been trained to be successful with their breach prevention and recovery responsibilities.

For more information from the Cloud Adoption Framework for Azure, see [Plan for cloud adoption](/azure/cloud-adoption-framework/plan/plan-intro).

## Ready phase

:::image type="content" source="../media/adoption-guide/ready-phase.svg" alt-text="The ready phase." lightbox="../media/adoption-guide/ready-phase.svg":::

Use the resources listed in this article to prioritize your plan. The work of implementing breach prevention and recovery represents one of the layers in your multi-layer Zero Trust deployment strategy.

The staged approach recommended in this article includes cascading breach prevention and recovery work in a methodical way across your digital estate. At this phase, revisit these elements of the plan to be sure everything is ready to go:

- Use of Entra PIM has been tested for administrator accounts and your IT admins are trained to use it
- Your networking infrastructure has been tested for data encryption as needed, segmenting to filter access has been tested, and redundant legacy networking technologies have been determined and tests run to ensure operation if they're removed
- Your system patching practices have been tested for successful installation of updates and detection of failed updates
- You have begun analysis of your insider risks and how to manage them
- Your honeypot resources are deployed and have been tested along with your threat protection infrastructure to detect access
- Your BCDR infrastructure and practices have been tested on a subset of data

## Adopt phase

:::image type="content" source="../media/adoption-guide/adopt-phase.svg" alt-text="The adopt phase." lightbox="../media/adoption-guide/adopt-phase.svg":::

Microsoft recommends a cascading, iterative approach to implementing breach prevention and recovery. This allows you to refine your strategy and policies as you go to increase the accuracy of the results. There’s no need to wait until one phase is complete before beginning the next. Your results are more effective if you iterate along the way.

The main elements of your organization’s adopt phase should include:

- Enabling Entra PIM for all your administrator and other privileged accounts
- Implementing network traffic encryption, segmentation, and removal of legacy systems
- Deploying honeypot resources
- Deploying your patch management infrastructure
- Analyzing your insider risks and mapping them to Insider Risk Management
- Deploying  and practicing your BCDR infrastructure for critical data (Stage 1) or all business data (Stage 3) 

## Govern and manage phases

:::image type="content" source="../media/adoption-guide/govern-manage-phase.svg" alt-text="The govern and manage phase." lightbox="../media/adoption-guide/govern-manage-phase.svg":::

Governance of your organization’s ability to implement breach prevention and recovery is an iterative process. By thoughtfully creating your implementation plan and rolling it out across your digital estate you have created a foundation. Use the following tasks to help you start building your initial governance plan for this foundation.

| Objective | Tasks |
|:-----|:-----|
| Track and measure | Assign owners for critical actions and projects, such as IT admin education and honeypot resource management, patch management, networking security, and BCDR procedures. <br><br> Create actionable plans with dates for each action and project, and instrument progress using reports and dashboards. |
| Monitor | - Track PIM requests and resulting actions. <br>- Monitor access to honeypot resources. <br>- Monitor systems to be patched for update installation failures. <br>- Test BCDR procedures for completeness and restoration integrity.  |
| Iterate for maturity | - Survey networking infrastructure for additional legacy systems that can be removed. <br>- Adapt BCDR infrastructure for new resources and features.  |

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
