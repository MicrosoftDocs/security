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

With hybrid IT infrastructure models, your organization’s assets and data are located on both on-premises and in the cloud and bad actors can employ many different methods to attack them. Your organization must be able to prevent these attacks as much as possible and, when breached, minimize the damage of the attack.

Traditional approaches that focus on establishing perimeter-based security for on-premises, where you trust everyone inside your organization’s private network perimeter, are no longer relevant. If an attacker gains access to your private network, they can, with the appropriate permissions, access any data, applications, or resource within it. They may breach your network by stealing user credentials, taking advantage of a security vulnerability, or introducing a malware infection. Such attacks can result in loss of revenue and high cyber insurance premiums, which can be a significant setback for your organization’s financial health and market reputation.

Forester concluded the following for 2021:

- Nearly two-thirds of organizations were breached in the past year, and it cost them an average of $2.4 million per breach. – Forester, [The 2021 State of Enterprise Breaches (April 2022)](https://www.forrester.com/report/the-2021-state-of-enterprise-breaches/RES177333). 

With the cloud, bad actors don’t need to physically breach your private network perimeter. They can attack your cloud-based digital assets from anywhere in the world. 

Your organization’s health and reputation depend on your security strategy. With the widespread adoption of cloud-based enterprise environments and the growth of the mobile workforce, data footprints exist beyond the traditional boundaries of corporate networks. This table summarizes key differences between traditional and modern threat protection with Zero Trust.

| Traditional threat protection with private network controls | Modern threat protection with Zero Trust |
| --- | --- |
| Traditional protection relies on perimeter-based security, where you trust everyone inside the private network. <br><br> Perimeter networks can include: <br><br> - Little network segmentation or security perimeters and open, flat networks. <br> - Minimal threat protection and static traffic filtering. <br> - Unencrypted internal traffic.	| The Zero Trust model moves network defenses from static, network-based perimeters to focus on users, devices, assets, and resources. <br><br> Assume that a breach can and will happen. Security risks can exist inside and outside your network, you're constantly under attack, and a security incident can happen at any time. A comprehensive and modern threat protection infrastructure can provide timely attack detection and response. <br><br> Minimize the blast radius of security incidents with layers of protection that, together, reduce the extent of the damage and how fast it can spread. |

To reduce the impact of a significant incident, all the following are essential:

- Identify the business risk of a breach
- Plan a risk-based approach for your breach response
- Understand the resulting damage to your organization’s reputation and relationships with other organizations
- Add defense-in-depth layers

The guidance in this article walks through how you can get started on your strategy for preventing and reducing damage from a breach. Two additional articles give you the specifics of how to implement that strategy using:

- [A security breach prevention and recovery infrastructure](prevent-reduce-business-damage-breach-infrastructure.md)
- [Threat protection and eXtended detection and response (XDR) tools](prevent-reduce-business-damage-breach-threat-protection.md)

The first step toward a robust security posture is determining how your organization is vulnerable through risk assessment. 

## Assessing risk and your security posture

When you decide to adopt a strategy to prevent breach and reduce the damage caused from one, it's important to consider and quantify the metric of risk. Strategically, the exercise of quantifying risk allows you to set a metric for your appetite for risk. This requires that you conduct a baseline risk assessment along with an analysis of the business-critical breaches that may affect your business. The combination of your documented risk appetite against breach scenarios that you’re willing to address forms the basis of a breach preparation and remediation strategy.

Note that it's virtually impossible to prevent breaches as an absolute. As described in [Attacker return on investment](rapidly-modernize-security-posture.md#attacker-roi), the aim is to incrementally increase cyberattack friction to a point where the attackers that you’re able or willing to defend against no longer gain a viable return on investment from their attacks. The kind of attacks and the economic viability to defend should be captured as part of your risk analysis.

Reducing damage from a breach gives considerable energy to options during and post breach, which allows your organization to recover quickly from an expected breach or type of breach. These breach types and the readiness to recover are defined in subsequent sections in this article.

Recognizing breach intent must be part of your breach preparation. All breaches have an element of malice or criminal intent attached, however financially driven breaches have the potential for much greater damage compared to “drive by” or opportunistic breaches.

For more information on security posture and risk assessment, see [Rapidly modernize your security posture](rapidly-modernize-security-posture.md).

### Examples of risks by business type

Business requirements are dependent on the resulting risk analysis for your business type. The following discusses several business verticals and how their specific needs drive the segmented risk analysis:

- Mining

  The mining industry is looking more towards the mine of the future where Operational Technology (OT) systems use fewer manual processes. An example is the use of Human Machine Interfaces (HMI) that leverage an application interface to complete jobs and tasks within a processing plant. Because these HMIs are designed as applications, the cyber security risks for this industry vertical can be higher.

  The threat no longer becomes one of loss of data or theft of company assets. The threat becomes one of external actors who use identity theft to access critical systems and interfere with production processes.

- Retail

  The major risks related to breach within the retail industry can arise when there are multiple domains for multiple brands that live within the same tenant. The complexities of managing on-premises or cloud-based identities can create vulnerabilities.

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

In all these cases, skilling and education are essential for both users as the target of phishing attacks and helpdesks as the target of vishing attacks. Helpdesks should have protocols in place to authenticate requesting users before performing sensitive actions on user accounts or permissions.

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

Before starting any technical work, it’s important to understand the different motivations for investing in preventing and reducing business damage from a breach as these motivations help inform the strategy, objectives, and measures for success.

The following table provides reasons why business leaders across an organization should invest in preventing or reducing damage from a breach.

| Role | Why preventing or reducing business damage from a breach is important |
| --- | --- |
| Chief Executive Officer (CEO) | The business must be empowered to achieve its strategic goals and objectives, irrespective of the cybersecurity climate. Business agility and business execution shouldn’t be constrained because of an incident or breach. Business leaders should understand that security is part of business imperatives and investment in both breach prevention and breach preparedness is required to ensure business continuity. The cost of a successful and destructive cyberattack can be a lot more than the price of implementing security measures. |
| Chief Marketing Officer (CMO) | How the business is perceived both internally and externally shouldn’t be restricted based on a breach occurring or breach readiness. Learning how to communicate breach readiness and messaging internally and externally in response to a breach is a matter of preparation. A successful attack can become public knowledge, potentially harming brand value, unless a breach communication plan exists. |
| Chief Information Officer (CIO) | The applications used by your organization must be resilient to attack while securing your organization's data. Security should be a measurable outcome and aligned with IT strategy. Breach prevention and breach management must be aligned with data integrity, privacy, and availability. |
| Chief Information Security Officer (CISO) | Security must be aligned as a business imperative to the C-Suite. Breach readiness and response is aligned to achieving the primary business strategies, with technology security aligned to mitigation of business risk.  | 
|Chief Operations Officer (COO) | The incident response process hinges on the leadership and strategic guidance provided by this role. It's imperative that preventive and responsive actions are carried out as aligned to corporate strategy. <br><br> Breach preparation in an “assume breach” posture means that all disciplines reporting to the COO must function at a level of breach readiness, ensuring that a breach can be isolated and mitigated quickly without pausing your business. |
| Chief Financial Officer (CFO) | Breach preparation and mitigation are functions of budgeted security spend. Financial systems must be robust and can survive a breach. Financial data must be classified, secured, and backed up as a sensitive dataset. |

A Zero Trust approach solves several security problems arising from security breaches. You can emphasize the following benefits of a Zero Trust approach with your business leaders.

| Benefits | Description |
| --- | --- |
| Ensure survival | Depending on the nature or motivation of the attacker, a breach may be designed to significantly impact or disrupt your organization’s ability to perform normal business activities. Preparing for a breach significantly improves the likelihood of your organization surviving a breach designed to cripple or disable. |
| Control damage to your reputation | A breach that results in access to confidential data can have severe impacts, such as damage to brand reputation, loss of sensitive intellectual property, disruption to customers, regulatory fines, and financial harm to your business. Zero Trust security helps to reduce the attack area by continuously assessing, monitoring, and analyzing your IT infrastructure both on-premises and in the cloud. A Zero Trust architecture helps define policies that are updated automatically when risks are identified. |
| Reduce blast radius within your organization | Deploying a Zero Trust model can help minimize the impact of an external or insider breach. It enhances your organization’s ability to detect and respond to threats in real time and reduces the blast zone of attacks by restricting lateral movement. |
| Demonstrate robust security and risk posture | A Zero Trust approach allows triage alerts, correlation of additional threat signals, and remediation actions. Analyzing signals helps improve your posture by evaluating your security culture and identifying areas for improvement or best practices. Any change in your network automatically triggers analysis for potentially malicious activity. You gain complete visibility of all assets and resources within your networks and how they’re performing, which results in a significant overall reduction in risk exposure. |
| Lower cyber insurance premiums | To evaluate the cost of cyber insurance, you need a robust and well-defined security model and architecture. By implementing Zero Trust security, you have control, visibility, and governance with real-time analysis for protecting your network and endpoints. Your security team can detect and overcome gaps in your overall security posture and prove to insurers that you have proactive strategies and systems. A Zero Trust approach also improves cyber-resilience and may even help pay for itself by reducing insurance premiums. |
| Increase security team efficiency and morale | Zero Trust deployments reduce manual efforts for your security team by automating routine tasks such as resource provisioning, access reviews, and attestation. As a result, you can empower your security teams with the time and telemetry they need to detect, deter, and defeat the most critical attacks and risks, both internally and externally, which in turn boosts IT and security team morale. |

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
