---
title: Prevent or reduce business damage from a breach with Zero Trust
description: Prevent or reduce business damage from a breach with Zero Trust.  
ms.date: 12/18/2023
ms.service: security
author: BrendaCarter
ms.author: bcarter
ms.topic: conceptual
ms.collection: 
  - zerotrust-adopt
---

# Prevent or reduce business damage from a breach

As part of Zero Trust adoption guidance, this article describes the business scenario of preventing or reducing business damage from a cybersecurity breach. This scenario  addresses the “assume breach” Zero Trust guiding principle, which includes:

- Minimize blast radius and segment access
- Verify end-to-end encryption		
- Use analytics to get visibility, drive threat detection, and improve defenses

With hybrid IT infrastructure models, your organization’s assets and data are both on-premises and in the cloud and bad actors can employ many different methods to attack them. Your organization must be able to prevent these attacks as much as possible and, when breached, minimize the damage of the attack.

Traditional approaches that focus on establishing perimeter-based security for on-premises, where you trust everyone inside your organization’s private network perimeter, are no longer relevant. If an attacker gains access to your private network, they can, with the appropriate permissions, access any data, applications, or resource within it. They may breach your network by stealing user credentials, taking advantage of a security vulnerability, or introducing a malware infection. Such attacks can result in loss of revenue and high cyber insurance premiums, which can be a significant setback for your organization’s financial health and market reputation.

Forester concluded the following for 2021:

   Nearly two-thirds of organizations were breached in the past year, and it cost them an average of $2.4 million per breach. – Forester, [The 2021 State of Enterprise Breaches (April 2022)](https://www.forrester.com/report/the-2021-state-of-enterprise-breaches/RES177333). 

With the cloud, bad actors don’t need to physically breach your private network perimeter. They can attack your cloud-based digital assets from anywhere in the world. 

Your organization’s health and reputation depend on your security strategy. With the widespread adoption of cloud-based enterprise environments and the growth of the mobile workforce, data footprints exist beyond the traditional boundaries of corporate networks. This table summarizes key differences between traditional and modern threat protection with Zero Trust.

| Traditional threat protection with private network controls | Modern threat protection with Zero Trust |
| --- | --- |
| Traditional protection relies on perimeter-based security, where you trust everyone inside the private network. <br><br> Perimeter networks can include: <br><br> - Little network segmentation or security perimeters and open, flat networks. <br> - Minimal threat protection and static traffic filtering. <br> - Unencrypted internal traffic.	| The Zero Trust model moves network defenses from static, network-based perimeters to focus on users, devices, assets, and resources. <br><br> A Zero Trust model assumes that a breach can and will happen. Security risks can exist inside and outside your network, you are constantly under attack, and a security incident can happen at any time. <br><br> A Zero Trust approach minimizes the blast radius of security incidents with layers of protection that, together, reduce the extent of the damage and how fast it can spread. |

To reduce the impact of a significant incident, all the following are essential:

- Identify the business risk of a breach
- Understand the resulting damage to your organization’s reputation and relationships with other organizations
- Add defense-in-depth layers
- Plan a risk-based approach for your breach response

The guidance in this article walks through how you can get started on your strategy for preventing and reducing damage from a breach. Two additional articles give you the specifics of how to implement that strategy using:

- [A security breach prevention and recovery infrastructure](prevent-reduce-business-damage-breach-infrastructure.md)
- [Threat protection and eXtended detection and response (XDR) tools](prevent-reduce-business-damage-breach-threat-protection.md)

The first step toward a robust security posture is determining how your organization is vulnerable through risk assessment. 

## Assessing risk and your security posture

When you decide to adopt a strategy to prevent breach and reduce the damage caused from one, it is important to consider and quantify the metric of risk. Strategically, the exercise of quantifying risk allows you to set a metric to what your appetite for risk should be. This requires that you conduct a baseline risk assessment, along with an analysis of the business-critical breaches that may affect your business. The combination of the documented risk appetite against breach scenarios which you are willing to address forms the basis of a breach preparation and remediation strategy. 

Note that it is virtually impossible to prevent breaches as an absolute. As described in [Attacker return on investment](rapidly-modernize-security-posture.md# attacker-roi), the aim is to incrementally increase cyberattack friction to a point where the attackers that you’re able or willing to defend against no longer gain a viable return on investment from their attacks. The kind of attacks and the economic viability to defend are captured as part of your risk analysis.

Reducing damage from a breach gives considerable energy to options during and post breach, which allows your organization to recover quickly from an expected breach or type of breach. These breach types and the readiness to recover are defined following the risk analysis described in this article.

Recognizing breach intent must be part of your breach preparation. All breaches have an element of malice or criminal intent attached, however financially driven breaches have the potential for much greater damage compared to “drive by” or opportunistic breaches.

For more information on security posture and risk assessment, see [Rapidly modernize your security posture](rapidly-modernize-security-posture.md).

### Examples of risks by business type

Business requirements are dependent on the resulting business risk analysis. The following discusses several business verticals and how their specific needs drive the segmented risk analysis:

- Mining 

  The mining industry is looking more towards the mine of the future where Operational Technology (OT) systems use fewer manual processes. An example is the use of Human Machine Interfaces (HMI) that leverage an application interface to complete jobs and tasks within a processing plant. Because these HMIs are designed as applications, the cyber security risks for this industry vertical can be higher. 

  The threat no longer becomes one of loss of data or theft of company assets. The threat becomes one of external actors who use identity theft to access critical systems and interfere with production processes. 

-	Retail

  The major risks related to breach within the retail industry can arise with there are multiple domains for multiple brands that live within the same tenant. The complexities of managing on-premises or cloud-based identities can create vulnerabilities. 

- Health Sector

  The major risks within the health sector are data loss. The unauthorized disclosure of confidential medical records may be a direct threat to data and information privacy laws that are reserved for patients and clients alike and, based on local regulations, can incur substantial penalties. 

- Government Sector

  Government sector organizations pose the highest risks for information security. Reputational damage, national security, and data loss are at stake. This is largely why government organizations are required to subscribe to stricter standards such as the [National Institute of Standards and Technology (NIST)](https://www.nist.gov/cyberframework).

As part of your breach preparation and response, take advantage of [Microsoft Defender Threat Intelligence](https://www.microsoft.com/security/business/siem-and-xdr/microsoft-defender-threat-intelligence) to search for and learn about the types of attacks and threat vectors that are most relevant to your vertical.

### Risks of common types of attacks

Preventing or reducing business damage from a cybersecurity breach includes awareness of the most common types of attacks. Although the following attack types are currently the most common, your cybersecurity team should also be aware of new types of attacks, some of which may augment or replace them.

#### Identities

Cyber security incidents typically begin with a credential theft of some sort. Credentials may be stolen using a variety of methods:

- Phishing

  An attacker masquerades as a trusted entity and dupes employees into opening emails, texts or IMs. Can also include spear-phishing, in which an attacker uses information specifically about a user to construct a more plausible phishing attack. Technical credential theft may occur due to a user clicking on a URL or an MFA phishing attack. 

- Vishing

  An attacker uses social engineering methods to target supporting infrastructure such as helpdesks to obtain or change credentials. 

- Password spray

  Attacker tries a large list of possible passwords for a given account or set of accounts. Possible passwords can be based on public data about a user, such as birthdates in social media profiles.

In all these cases, skilling and education is essential for both users as the target of phishing attacks and helpdesks as the target of vishing attacks. Helpdesks should have protocols in place to authenticate requesting users before performing sensitive actions on user accounts or permissions.

#### Devices

User devices are another way in for attackers, who typically rely on device compromise to install malware such as viruses, spyware, ransomware, and other unwanted software that installs without consent.

Attackers can also use the device's credentials to gain access to your applications and data.

#### Network

Attackers can also use your networks to either impact your systems or determine sensitive data. Common types of network attacks include:

- Distributed denial of service (DDos)

  Attacks that aim to overwhelm online services with traffic to make the service inoperable.

- Eavesdropping

  An attacker intercepts network traffic and aims to obtain passwords, credit card numbers, and other confidential information.

- Code and SQL injection

  An attacker transmits malicious code instead of data values over a form or through an API.

- Cross site scripting

  An attacker uses third-party web resources to run scripts in the victim’s web browser.

## How business leaders think about preventing or reducing business damage from a breach

Before starting any technical work, it’s important to understand the different motivations for investing in preventing and reducing business damage from a breach as these help inform the strategy, objectives, and measures for success.

The following table provides reasons why business leaders across an organization should invest in preventing or reducing damage from a breach.

| Role | Why preventing or reducing business damage from a breach is important |
| --- | --- |
| Chief Executive Officer (CEO) | The business must be empowered to achieve its strategic goals and objectives, irrespective of the cybersecurity climate. Business agility and business execution should not be constrained because of an incident or breach. Business leaders should understand that security is part of business imperatives and will invest in both breach prevention and breach preparedness, to ensure business continuity. The cost of a successful cyberattack can be a lot more than the price of implementing security measures. |
| Chief Marketing Officer (CMO) | How the business is perceived both internally and externally should not be restricted based on a breach occurring or breach readiness. Learning how to communicate breach readiness and messaging internally and externally in response to a breach is a matter of preparation. A successful attack can become public knowledge, potentially harming brand value, unless a breach communication plan exists. |
| Chief Information Officer (CIO) | The applications used by the company must be resilient to attack while securing the company's data. Security should be a measurable outcome and aligned with IT strategy. Breach prevention and breach management must be aligned with data integrity, privacy, and availability. |
| Chief Information Security Officer (CISO) | The technologies used to prevent a breach do not scale to a zero-day attack, nor can they defend a poorly maintained IT infrastructure. For example, technology three years old or older cannot prevent attacks that use modern attack methods. | 
|Chief Operations Officer (COO) | The incident response process hinges on the leadership and strategic guidance provided by this role. It is imperative that preventive and responsive actions are carried out as aligned to corporate strategy. |
| Chief Financial Officer (CFO) | Breach preparation in an “assume breach” posture means that all disciplines reporting to the COO must function at a level of breach readiness, ensuring that a breach can be isolated and mitigated quickly without pausing your business. |
| Chief Compliance Officer (CCO) | Breach preparation and mitigation is a function of budgeted security spend. Financial systems must be robust and can survive a breach. Financial data must be classified, secured, and backed up as a sensitive dataset. |

A Zero Trust approach solves several security problems arising from security breaches. You can emphasize the following benefits of a Zero Trust approach with your business leaders.

| Benefits | Description |
| --- | --- |
| Ensure survival | Depending on the nature or motivation of the attacker, a breach may be designed to significantly impact or disrupt your organization’s ability to perform normal business activities. Preparing for a breach significantly improves the likelihood of your organization surviving a breach designed to cripple or disable. |
| Control damage to your reputation | A breach that results in access to confidential data can have severe impacts, such as damage to brand reputation, loss of sensitive intellectual property, disruption to customers, regulatory fines, and financial harm to your business. Zero Trust security helps to reduce the attack area by continuously assessing, monitoring, and analyzing your IT infrastructure both on-premises and in the cloud. A Zero Trust architecture helps define policies that are updated automatically when risks are identified. |
| Reduce blast radius within your organization | Deploying a Zero Trust model can help minimize the impact of an external or insider breach. It enhances your organization’s ability to detect and respond to threats in real time and reduces the blast zone of attacks by restricting lateral movement. |
| Demonstrate robust security and risk posture | A Zero Trust approach allows triage alerts, correlation of additional threat signals, and remediation actions. Analyzing signals helps improve your posture by evaluating your security culture and identifying areas for improvement or best practices. Any change in your network automatically triggers analysis for potentially malicious activity. You gain complete visibility of all assets and resources within your networks and how they’re performing, which results in a significant overall reduction in risk exposure. |
| Lower cyber insurance premiums | To evaluate the cost of cyber insurance, you need a robust and well-defined security model and architecture. By implementing Zero Trust security, you have control, visibility, and governance with real-time analysis for protecting your network and endpoints. Your security team can detect and overcome gaps in your overall security posture and prove to insurers that you have proactive strategies and systems. A Zero Trust approach also improves cyber-resilience and may even help pay for itself by reducing insurance premiums. |
| Increase security team efficiency and morale | To evaluate the cost of cyber insurance, you need a robust and well-defined security model and architecture. By implementing Zero Trust security, you have control, visibility, and governance with real-time analysis for protecting your network and endpoints. Your security team can detect and overcome gaps in your overall security posture and prove to insurers that you have proactive strategies and systems. A Zero Trust approach also improves cyber-resilience and may even help pay for itself by reducing insurance premiums. |

For additional information to share with business leaders, see the [Minimize the impact of internal or external bad actors e-book](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RWZlng).

## The adoption cycle for preventing or reducing business damage from a breach

This set of articles walk through this business scenario using the same lifecycle phases as the [Cloud Adoption Framework for Azure](/azure/cloud-adoption-framework/overview)—Define strategy, Plan, Ready, Adopt, and Govern and manage—but adapted for Zero Trust.

:::image type="content" source="../media/adoption-guide/objective-adoption-process.svg" alt-text="Diagram of the adoption process for an objective." lightbox="../media/adoption-guide/objective-adoption-process.svg":::

The following table is an accessible version of the illustration.

| Define strategy| Plan| Ready| Adopt| Govern and manage |
| --- | --- | --- | --- | --- |
| Outcomes <br><br> Organizational alignment <br><br> Strategic goals| Stakeholder team <br><br> Technical plans <br><br> Skills readiness| Evaluate <br><br> Test <br><br> Pilot| Incrementally implement across your digital estate | Track and measure <br><br> Monitor and detect <br><br> Iterate for maturity |

Read more about the Zero Trust adoption cycle in the [Zero Trust adoption framework overview](zero-trust-adoption-overview.md).

To prevent or reduce business damage from a breach, use the information in these additional articles: 

- [Implement security breach prevention and recovery infrastructure](prevent-reduce-business-damage-breach-infrastructure.md)
- [Implement threat protection and XDR](prevent-reduce-business-damage-breach-threat-protection.md)

Note that the deployment recommendations for these two separate tracks require the participation of separate groups of your IT department and **the activities for each track can be done in parallel**.

## Next Steps

For this business scenario:

- [Implement security breach prevention and recovery infrastructure](prevent-reduce-business-damage-breach-infrastructure.md)
- [Implement threat protection and XDR](prevent-reduce-business-damage-breach-threat-protection.md)

Additional articles in the Zero Trust adoption framework:

- [Zero Trust adoption framework overview](zero-trust-adoption-overview.md)
- [Rapidly modernize your security posture](rapidly-modernize-security-posture.md)
- [Secure remote and hybrid work](secure-remote-hybrid-work.md)
- [Identify and protect sensitive business data](identify-protect-sensitive-business-data.md)
- [Meet regulatory and compliance requirements](meet-regulatory-compliance-requirements.md)

<!---

## Define strategy phase

:::image type="content" source="../media/adoption-guide/define-strategy-phase.svg" alt-text="The define strategy phase." lightbox="../media/adoption-guide/define-strategy-phase.svg":::

The **Define strategy** phase is critical to define and formalize our efforts – it formalizes the “Why?” of this scenario. In this phase, you understand the scenario through business, IT, operational and strategic perspectives. You define the outcomes against which to measure success in the scenario, understanding that security is an incremental and iterative journey.

This article suggests motivations and outcomes that are relevant to many organizations. Use these suggestions to hone the strategy for your organization based on your unique needs.

### Motivations for preventing or reducing business damage from a breach

The motivations for preventing or reducing business damage from a breach are straightforward, but different parts of your organization have different incentives for doing this work. The following table summarizes some of these motivations.

| Area | Motivations |
| --- | --- |
| Business needs |  |
| IT needs |  |
| Operational needs |  |
| Strategic needs |  |


### Outcomes for preventing or reducing business damage from a breach

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

Technical adoption for preventing or reducing business damage from a breach involves:

- 
- 

Preventing or reducing business damage from a breach also involves a few related activities, including:

- 
- 

Many organizations can take a four-staged approach to these deployment objectives, summarized in the following table.

| Stage 1 | Stage 2 | Stage 3 | Stage 4 |
| --- | --- | --- | --- |
| Secure privileged accounts <br><br> Implement Azure Backup for critical business data <br><br> Implement Azure Site Recovery for critical workload continuity <br><br> Encrypt network communication | Segment your network <br><br> Implement a patching plan <br><br> Protect against ransomware <br><br> Create honeypot resources <br><br> Adopt a cybersecurity framework	 | Implement Microsoft 365 Backups, Azure Backups, and Azure Site Recovery for all business data  <br><br> Gain visibility to network traffic <br><br> Update security team skills | Discontinue legacy network security technology <br><br> Practice threat and disaster recovery response <br><br> Gather industry specific threat intelligence |

If this staged approach works for your organization, you can share your progress with your teams and business leaders by downloading [this PowerPoint slide deck](https://download.microsoft.com/download/a/b/5/ab51ac2a-e9de-4c8f-8323-6bc7c2f78c1f/ZeroTrust-Adoption-Resources.pptx) to track your progress through these stages and objectives. Here's the initial slide for this business scenario.

:::image type="content" source="../media/adoption-guide/placeholder.svg" alt-text="PowerPoint slide for the deployment stages of preventing or reducing business damage from a breach." lightbox="../media/adoption-guide/placeholder.svg":::

### Understand your organization

This recommended staged approach for technical implementation can help give context to the exercise of understanding your organization. 

A foundational step in the Zero Trust adoption lifecycle for every business scenario includes taking inventory. For this business scenario, you...

The following actions apply:

- 
- 

### Organizational planning and alignment

The technical work of preventing or reducing business damage from a breach crosses several overlapping areas and roles:

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
- Implement Azure Site Recovery for critical workload continuity
- Encrypt network communication

##### Secure privileged accounts

| Resource | Description |
|:-----|:-----|
|  |  |

##### Implement Azure Backup for critical business data

| Resource | Description |
|:-----|:-----|
|  |  |

##### Implement Azure Site Recovery for critical workload continuity

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

Microsoft recommends a cascading, iterative approach to preventing and reducing business damage from a breach. This allows you to refine your strategy and policies as you go to increase the accuracy of the results. 

There’s no need to wait until one phase is complete before beginning the next. Your results are more effective if you iterate along the way.

## Govern and manage phases

:::image type="content" source="../media/adoption-guide/govern-manage-phase.svg" alt-text="The govern and manage phase." lightbox="../media/adoption-guide/govern-manage-phase.svg":::

Use the following exercises to help you start building your foundation:

- 
-  
- 


--->
