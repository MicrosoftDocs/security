---
title: Rapidly modernize your security posture for Zero Trust
description: Learn how to rapidly modernize your security posture for Zero Trust.
ms.date: 06/20/2023
ms.service: security
author: BrendaCarter
ms.author: bcarter
ms.topic: conceptual
ms.collection: 
  - zerotrust-adopt
---

# Rapidly modernize your security posture

As part of Zero Trust adoption guidance, this article describes the business scenario of rapidly modernizing your security posture. Rather than focusing on the technical work required to implement a Zero Trust architecture, this scenario focuses on how to develop your strategy and priorities and then how to systematically implement your priorities, piece by piece, while measuring and reporting your progress.

Your security posture is defined as your organization’s overall cybersecurity defense capability, along with the level of preparation and operational status to deal with ongoing cyber-security threats. This posture should be quantifiable and measurable, similarly to any other major metric that pertains to the operational status or well-being of your organization.

:::image type="content" source="../media/adoption-guide/security-posture.svg" alt-text="Diagram of your organization's security posture." lightbox="../media/adoption-guide/security-posture.svg":::

Rapidly modernizing your security posture involves working within your organization, especially leaders across your organization, to develop a strategy and a set of priorities and objectives. You then identify the technical work necessary to achieve the objectives and lead the various teams to accomplish them. The other business scenarios in this adoption guidance are designed to help accelerate this technical work. Finally, a key part of a strong security posture is the ability to communicate status, progress, and value to business leaders.

:::image type="content" source="../media/adoption-guide/rapid-modernize-sec-posture.svg" alt-text="Diagram of rapidly modernizing your security posture." lightbox="../media/adoption-guide/rapid-modernize-sec-posture.svg":::

Rapidly modernizing your security posture depends on your ability to systematically lead each component piece of your Zero Trust architecture through the adoption lifecycle. Each Zero Trust business scenario article recommends objectives across four stages. You can think of each objective as a technical project that you can lead through the adoption process. A more granular representation of the adoption process for a single objective or set of objectives is illustrated here.

:::image type="content" source="../media/adoption-guide/objective-adoption-process.svg" alt-text="Diagram of the adoption process for an objectives." lightbox="../media/adoption-guide/objective-adoption-process.svg":::

The following table is an accessible version of the illustration.

| Define strategy| Plan| Ready| Adopt| Govern and manage |
| --- | --- | --- | --- | --- |
| Organizational alignment <br><br> Strategic goals <br><br> Outcomes| Stakeholder team <br><br> Technical plans <br><br> Skills readiness| Evaluate <br><br> Test <br><br> Pilot| Incrementally implement across your digital estate | Track and measure <br><br> Monitor and detect <br><br> Iterate for maturity |

*Rapidly modernizing* refers to your ability to accelerate your organization’s capacity to deploy security configurations and threat protection capabilities across your digital estate at a pace that helps you get ahead of threats and mitigate your top risks. Think of it as a flywheel you are building in which you’ve created a repeatable process that you can feed many technical projects through.

:::image type="content" source="../media/adoption-guide/repeatable-process.svg" alt-text="Diagram of a repeatable process for adoption." lightbox="../media/adoption-guide/repeatable-process.svg":::

As you build your organization’s capacity to deploy security configurations, you can begin staggering their implementation. For example, after you’ve defined the strategy and objectives for a business scenario, you can stagger the implementation of the technical objectives. Here is an example.

:::image type="content" source="../media/adoption-guide/staggered-implementation-example.svg" alt-text="Example of a staggered implementation." lightbox="../media/adoption-guide/staggered-implementation-example.svg":::

Some business scenarios are broad, and you might want to prioritize specific elements of the scenario to work on first. Or you can prioritize specific zones of your digital estate for configuration deployment first.

## Define strategy phase

:::image type="content" source="../media/adoption-guide/define-strategy-phase.svg" alt-text="The define strategy phase." lightbox="../media/adoption-guide/define-strategy-phase.svg":::

One of the biggest challenges of adopting Zero Trust is gaining support and contribution from leaders across your organization. This adoption guidance is designed to help you communicate with them so you can gain organizational alignment, define your strategic goals, and identify outcomes.

Defining security as a business-level imperative is the first step toward a modern and scalable security approach. 

| Traditional role of security as an extension of IT responsibility| Modern security posture with Zero Trust |
| --- | --- |
| Traditional protection relies on security specialists that are part of the IT team. Security is an IT function.| Security is a responsibility shared among all levels of the business. Accountability for security rests with the executive, while responsibility is shared using the three Zero trust principles of assume breach, verify explicitly, and least privilege. A Zero Trust model moves security from reactive (who did what and when based on logging) to least privilege (based on just-in-time access to systems as needed). It also implements architecture elements and security operations capabilities to limit the damage from a breach. |

The Zero Trust adoption [overview article](zero-trust-adoption-overview.md) translates how Zero Trust applies to leadership roles across many organizations. This article includes business descriptions of the Zero Trust principles and a business translation of the technical areas included in a Zero Trust architecture, including identities, devices, and app. These topics are good places to begin conversations with your team of leaders. Be sure to probe and gain insights into what motivates the leaders in your organization so you can more easily agree on priorities and gain alignment and participation.

For this business scenario, rapidly modernizing your security posture, you do the work of gaining alignment on the risks to your organization, your security strategy, and your technical priorities. Ideally this helps you recruit funding and resources to do the work.

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

### Achieve business alignment

To succeed at implementing the principles of Zero Trust together with your partner teams, it’s critical that you achieve business alignment. When you agree on the risks and gaps within your current security posture, the steps to mitigate these, and the method you use to track and communicate progress, you build confidence in your evolving security posture.

Business alignment can be achieved using one or both of the following approaches.

- Take a risk-based approach in which you identify the top risks to your organization and the mitigations that are most appropriate.

- Create a defensive strategy, based on understanding where your digital assets are, what they're composed of, and the relative risk profile based on exfiltration or loss of access to your digital assets.

You can progress through this article using either approach. The technical objectives and work described in the other business scenarios support both approaches.

:::image type="content" source="../media/adoption-guide/business-alignment.svg" alt-text="Diagram of the business alignment." lightbox="../media/adoption-guide/business-alignment.svg":::

You can even take a risk-based approach to start (mitigating against your top risks) and then transition to a defensive strategy to fill in the gaps. This section discusses how to use both approaches to rapidly modernize your security posture.

### Risk-based approach

Some organizations choose to prioritize work and measure progress against risk. Two common tools for identifying risks include tabletop exercises and ISO standards.

#### Tabletop exercise evaluation

An easy way to get started is to use [Six Tabletop Exercises to Help Prepare Your Cybersecurity Team](https://www.cisecurity.org/insights/white-papers/six-tabletop-exercises-prepare-cybersecurity-team), provided by the Center for Internet Security (CIS).

These tabletop exercises are designed to help organizations walk through different risk scenarios with the goal of evaluating the organization’s state of preparation. They are each designed to be completed together with your team of stakeholders “in as little as 15 minutes.”

These exercises guide participants through the process of a simulated incident and require departments and teams to respond. The exercises help you evaluate your preparedness in a cross-discipline manner.

These exercises are representative and inclusive of different business units, not just IT or security. Consider working through and modifying the exercises, if needed, to ensure they're relevant for your organization and include representation from different parts of your organization, including marketing, executive leadership, and customer-facing roles that could be impacted by the scenario.

The output of these exercises feed into your overall strategy and priorities. The output helps you identify gaps and prioritize remediations. These priorities then inform your work in the plan phase. These exercises can also help create urgency and investment across your leadership team to mitigate the risks that you identify together. 

#### Using ISO standards resources and tools

Many organizations use International Organization for Standardization (ISO) standards resources and tools to gauge an organization’s risk. These provide a structured and comprehensive way for you to review and gauge the risks that apply to your organization, and mitigations. For more information, see the [Tracking progress section of the overview article](zero-trust-adoption-overview.md#tracking-progress).

Like the tabletop exercises, the output from this more formal review of your organization’s risks feeds into your overall strategy and priorities. The output should also help create urgency and investment across your teams to participate in modernizing your security posture.

### Defensive strategy

With a defensive strategy, you look across your digital estate to identify where your digital assets are, what they're composed of, and the relative risk profile based on the exfiltration or loss of access to your digital assets.

You prioritize defensive areas to focus on by taking each area and estimating the potential damage to your business for these common types of incidents:

- Data loss
- Data leakage
- Data breach
- Data access loss
- Compliance loss due to cyber incident

After you have identified the priority areas to defend, you can work systematically to apply Zero Trust principles to these areas. You can also make a defensible case for the funding and resources required to do this work.

### Develop the strategy for rapidly modernizing your security posture

After taking stock of your risks and defensive areas of your digital estate where you want to invest in defense, several other resources can help inform your strategy.

#### This adoption guidance

Whether you are taking a risk approach or defensive approach (or both), use the Zero Trust adoption guidance in this article as a starting point and prioritize the work based on your organization’s priorities. This article's guidance provides a systematic approach to applying the principles of Zero Trust. It’s based on fortifying the most common targets attackers use to gain access to an environment (identities and devices) and applying protections to your internal environment (like least privileged access and network segmentation) to prevent or limit the damage of a breach.

#### Your current organization and resource strengths

Also consider where you have staff maturity and the resources and can accelerate for quick wins. For example, if you have a highly motivated and well-resourced networking team, you can accelerate the recommendations that require this skill set.

#### Shared responsibility model for the cloud

Another resource that is often used to help inform strategy and priorities is the shared responsibility model. Your responsibility for security is based on the type of cloud service. The following diagram summarizes the balance of responsibilities for both you and Microsoft.

:::image type="content" source="../media/adoption-guide/shared-responsibilities.svg" alt-text="Diagram of shared responsibilities between Microsoft and your organization." lightbox="../media/adoption-guide/shared-responsibilities.svg":::

For more information, see [Shared responsibility in the cloud](/azure/security/fundamentals/shared-responsibility) in the Azure Security Fundamentals library.

Shared responsibility is a planning model frequently used by security teams to help transform the mindset and strategy from “in control of everything” to “sharing responsibility with the cloud provider.” This model emphasizes the strategy of moving apps and resources to trusted cloud providers to reduce the security work that remains for your organization. 

This can become part of your long-term strategy, starting with the acquisition of new cloud-based apps as a motivation to retire legacy apps and servers that your organization personally maintains. 

#### Your industry vertical

The nature or industry vertical of your business is a big driver of your strategy. It greatly influences the contents of your digital estate, your risks, and your legal compliance obligations. 

#### Attacker return on investment

Finally, raising the cost of an attack for attackers makes your organization more resilient to cybersecurity risk. Beyond meeting specific regulatory requirements, your budget spend should make it more expensive and difficult for an attacker to gain access to your environment and perform activities such as data exfiltration or data destruction. In other words, you reduce the return on investment (ROI) of attackers, causing them to possibly move on to another organization.

Attackers are often categorized by level of sophistication and resources (such as existing tools and experienced staff), from lowest to highest: amateur, organized crime, and nation states.

The principles of Zero Trust help your organization identify and prioritize how best to spend your security defense budget to raise the cost of an attack so you can defend against all levels of attackers.

The following figure shows the qualitative relationship between your security defense budget with Zero Trust principles and your defensive strength.

:::image type="content" source="../media/adoption-guide/budget-and-defensive-strength.png" alt-text="Diagram of security budget and defensive strength." lightbox="../media/adoption-guide/budget-and-defensive-strength.png":::

Defensive strength can rapidly increase when you implement and practice basic security hygiene based on Zero Trust principles. Beyond the early gains, you get additional defensive strength by implementing more advanced security measures. Higher defensive strength provides protection against higher levels of attackers.

The following figure shows the qualitative relationship between your defensive strength and the impact of the cost and ROI of an attacker.

:::image type="content" source="../media/adoption-guide/attacker-impact.png" alt-text="Diagram of the impact of defensive strength on an attacker's ROI." lightbox="../media/adoption-guide/attacker-impact.png":::

As your defensive strength increases, the cost to the attacker increases and reduces the ROI of the attack effort.

The attacker ROI model helps leaders understand that there are few absolutes. A security posture is never considered perfect or impenetrable. However, there is a lot of opportunity for your organization to be strategic and prioritize your budget and resources. It’s additional incentive for your team of business leaders to work together to protect your organization.

### Identify outcomes of your security posture

After working together to gain business alignment and identify strategic priorities, be sure to identify specific outcomes. These can guide further prioritization and planning.

The following table lists common target outcomes to rapidly modernize your security posture.

| Objective | Outcome |
| --- | --- |
| Security outcomes| Organizations want to increase security friction enough to thwart attackers without restricting business and technology outcomes. |
| Governance| Company assets, data, and apps need to be secured while adhering to architecture patterns and increasing compliance. |
| Prevention| Access control and asset protection are aligned withing an integrated security toolchain that includes all physical and digital assets. |
| Visibility| The risk and security status of the organization must be measurable and visible to multiple audience types. Predictable security outcomes should lead to predictable spending outcomes. |
| Response| SecOps roles and responsibilities are defined and implemented across the organization, leadership, and operational business functions. Tools and processes correlate security operations and security outcomes. Automation enables quick incident detection and increases the ability of your implementation to respond without manual intervention. |

### Document and report on your security posture

Finally, it’s important that you report on your security posture in an ongoing manner, using one or more mechanisms, including Microsoft scoring mechanisms, and other dashboards. There are many methods and tools you can use. Through this scenario, you'll identify reports and tools that are most helpful for your organization. You'll also develop a method of documenting your security posture that works for your organization.

## Plan phase

:::image type="content" source="../media/adoption-guide/plan-phase.svg" alt-text="The plan phase." lightbox="../media/adoption-guide/plan-phase.svg":::

Adoption plans convert the aspirational goals of a Zero Trust strategy into an actionable plan. Your collective teams can use the adoption plan to guide their technical efforts and align these with your organization's business strategy.

Rapidly modernizing your security posture involves taking a graduated approach to building maturity, including adopting methods to measure and report your progress and status.

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

#### Develop a response readiness plan

Zero Trust assumes breach, considers the impact of a long-running attack on your environment, and allows you to recover quickly from an incident. Your expectation of an attack should lead to the operational readiness to detect, respond, and recover.

In this stage, you develop a response readiness plan for common types of attacks. This plan includes how to respond to your users, your customers, and how to communicate to the public if needed.

For each of the following scenarios, consider a tabletop exercise that documents the current response to the loss of access to:

- Authentication: Azure AD or your on-premises Active Directory Domain Services (AD DS)
- Productivity: Tenant lockout
- Data loss: Malicious deletion or encryption of data, random scenarios
- Data leak: Exfiltration of data for industrial or nation state espionage, WikiLeaks
- Denial of Service: Line of business (LOB) or data (such as structured data or a data lake)

Be sure to include representatives of all roles that will be affected, including HR, marketing, and relevant business groups.

For each scenario:

- Consider the communication strategy for both public and internal communications. Your plan should enable you to communicate responsibly in compliance with the regulations of your government and industry. Your response should also reduce the amount of information that you might inadvertently share with attackers.
- Evaluate the internal state of readiness to respond for IT and business teams and when an external response team such as Microsoft Detection and Response Team (DART) or another breach partner is required to either increase operational readiness/cyber resilience or respond to an incident if internal teams become overwhelmed.

In addition to developing readiness plans for common attacks, this exercise can help gain support and investment across your organization for the work of implementing mitigations.

#### Inventory your digital estate

When planning for breach readiness, you must understand the state of your physical and digital assets. The first objective in this stage is to take inventory. Note that the other business scenarios include taking inventory of the assets that are affected by the scenario. These inventories and the status of the items become part of your security posture. 

For this business scenario, it is recommended that you create a list of all physical and digital assets and services and LOB applications. Physical assets include endpoints (mobile phones, PCs, and laptops), and servers (physical or virtual). Examples of digital assets include services such as emails and retention data in Exchange Online, files and records in SharePoint Online, SQL PaaS services, data lakes, files in on-premises file servers or Azure File Shares. Consider using a Cloud Access Security Broker (CASB) service such as Microsoft Defender for Cloud to expose the services used by users, including shadow IT data locations. 

The following are digital assets to include in your inventory:

- Identities
- Devices
- Data
- Apps
- Infrastructure
- Network

It might not be possible to develop a detailed list of assets and their status at this stage. In some cases, this inventory relies on having tools installed, such as Microsoft Intune and Defender for Cloud Apps. Simply begin the process. As you work through the other business scenarios, these inventories will become more complete. 

Ideally you can accomplish the following:

- Rate your digital assets by content sensitivity and criticality. If you are unaware of the locations of these assets, consider using Microsoft Purview to discover critical data.
- Keep an updated list of vulnerabilities that exist in your digital estate for all assets.

The following Zero Trust architecture diagram illustrates the relationship of these assets to each other.

:::image type="content" source="../media/adoption-guide/zero-trust-architecture.svg" alt-text="Diagram of Zero Trust architecture." lightbox="../media/adoption-guide/zero-trust-architecture.svg":::

#### Implement basic hygiene

This stage also includes implementing basic hygiene practices. According to the [Microsoft Digital Defense Report](https://www.microsoft.com/en-us/security/business/microsoft-digital-defense-report-2022) (2022), “Although nation state actors can be technically sophisticated and employ a wide variety of tactics, their attacks can often be mitigated by good cyber hygiene.” The report estimates, “Ninety eight percent of attacks can be stopped with basic hygiene measures in place.”

| Objectives for Stage 2| Resources |
| --- | --- |
| Develop a response readiness plan| [Cyberattacks Are Inevitable. Is Your Company Prepared?](https://hbr.org/2021/03/cyberattacks-are-inevitable-is-your-company-prepared) (Harvard Business Review) |
| Inventory your digital estate| [How do you manage IT asset inventory and documentation?](https://www.linkedin.com/advice/1/how-do-you-manage-asset-inventory-documentation) (LinkedIn article). <br><br> [IT Asset Valuation, Risk Assessment and Control Implementation Model](https://www.isaca.org/resources/isaca-journal/issues/2017/volume-3/it-asset-valuation-risk-assessment-and-control-implementation-model) by the Information Systems Audit and Control Association (ISACA) includes examples of how to measure and categorize assets. |
| Implement basic hygiene practices| Document the basic hygiene practices for your organization, including how to measure success. Hygiene practices are cybersecurity practices that you practice as a routine to mitigate online breaches. Many of these practices are included in Stage 1 of other business scenarios. Some are included in later stages. <br><br> [How to Have Better Cyber Hygiene](https://www.microsoft.com/en-us/microsoft-365-life-hacks/privacy-and-safety/cyber-hygiene) |
| Update your status for Secure Score| As you work through the recommendations across business scenarios, update your status for Secure Score. The score is a measure of progress and success that you can communicate across your organization. <br><br> [Assess your security posture with Microsoft Secure Score](/microsoft-365/security/defender/microsoft-secure-score-improvement-actions) |
| Capture your status in Compliance Manager| If you’ve started using [Microsoft Purview Compliance Manager](/microsoft-365/compliance/compliance-manager) to track your regulatory compliance work, check back periodically to update your status. Like Secure Score, this is a measure of progress and success that can be included as part of your security posture. |

### Stage 3

A security posture requires instrumentation to create visibility. You'll want to unify your tools and methods into as few views or dashboards as possible for simplification. The first objective in this stage is to visualize your security posture using audience-appropriate dashboards. 

Assuming breach requires us to look for and instrument breach preparedness by implementing and instrumenting continuous monitoring. In this step, document and review the number of portals or views that achieve this function. This internal documentation can be reports that you compile manually or reports from your security tools, like Secure Score, Compliance Manager, Microsoft 365 Defender, Microsoft Defender for Cloud, Microsoft Sentinel, and other tools.

For example:

- An executive summary view of risk, breach preparation, and current incidents.
- A CISO summary view for IT and OT security assets.
- Security Analyst views to respond to incidents.
- A historical view on security information and event management (SIEM) and security orchestration, automation, and response (SOAR) to comply with regulatory demands and long-running threat hunting.

Creating and maintaining role-specific views create transparency with the status of the security posture with your stakeholders who are sharing the burden of security management, from executive leaders through to incident responders. 

Stage 3 also includes maturing the managing shadow IT and patching areas of hygiene.

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

The Ready phase for this business scenario is a bit different than for other business scenarios. Rather than evaluating, testing, and piloting specific security capabilities or configurations, the Ready phase for this scenario includes building your stakeholder team and then working through each stage and objective with an agile approach.

For example, for each objective:

- Evaluate what is needed to accomplish the objective, which includes who is needed.
- Begin with a reasonable approach and test it out. Adjust as needed.
- Pilot the approach and adjust based on what you learn.

the following table is an example of how this can work for the **Identify risks to your organization** objective in Stage 1 of the [Plan phase](#plan-phase).

| Ready task | Actions |
| --- | --- |
| Evaluate| Decide what resources you'll use to evaluate risks and who should be included in the activities. This evaluation can include using the tabletop exercises or the ISO standards. Determine who in your organization should participate. |
| Test| Using the resources you are targeting, review the recommended exercises with a small set of your stakeholders to gauge your readiness to engage your fuller team of stakeholders. |
| Pilot| If you are using the tabletop exercises, try out one of the scenarios with the chosen participants. Review the results and determine if you’re ready to proceed to the other exercises. If you’re using the ISO standards, target a portion of the standard to pilot the evaluation. |

By taking an agile approach like this, you allow opportunities to adjust and optimize your methodology and process. You also build confidence as you go.

## Adopt phase

:::image type="content" source="../media/adoption-guide/adopt-phase.svg" alt-text="The adopt phase." lightbox="../media/adoption-guide/adopt-phase.svg":::

In the adopt phase, you incrementally implement your strategy and deployment plans across functional areas. For this scenario, this involves accomplishing the objectives set out across the four stages, or the objectives and stages you have customized for your organization.

However, modernizing your security posture includes accomplishing the technical objectives recommended in the other business scenarios (or prioritized by your organization). These all accrue to your security posture.

As you transition to the adopt phase for this scenario and the others, be sure to communicate status, progress, and value.

:::image type="content" source="../media/adoption-guide/rapid-modernize-sec-posture.svg" alt-text="Diagram of rapidly modernizing your security posture." lightbox="../media/adoption-guide/rapid-modernize-sec-posture.svg":::

## Govern and manage

:::image type="content" source="../media/adoption-guide/govern-manage-phase.svg" alt-text="The govern and manage phase." lightbox="../media/adoption-guide/govern-manage-phase.svg":::

Security governance is a constant process. As you transition to this phase, shift to tracking and measuring the results of each piece of the Zero Trust architecture you’ve implemented. Together with monitoring and detecting, you'll identify opportunities to iterate for maturity.

### Track and measure

This scenario article suggests different reports and dashboards you can use to assess your status and measure progress. Ultimately you want to develop a set of metrics that you can use to show progress and to identify where a new vulnerability might be emerging. You can use the various reports and dashboards to gather the metrics that are most important for your organization.

The following table lists some example metrics.

| Business enablement | Security posture | Security response | Security improvement |
| --- | --- | --- | --- |
| Mean time for security review | # of new apps reviewed | Mean time to recover (MTTR) | # of modernization projects open |
| # of days for application security review | Score from Secure Score | Mean time to acknowledge (MTTA) | # of modernization project milestones achieved in the last 60 days |
| Average boot and sign-in time for managed devices | % of compliant apps | Time to restore critical systems | Number of repetitive manual steps removed from workflows |
| Number of security interruptions in user workflow | # of privileged accounts meeting 100% of requirements | # of high-severity incidents | # of lessons learned from internal and external incidents |
| % of IT helpdesk time spent on low-value security activities | # of accounts meeting 100% of requirements | Incident growth rate (overall) |  |

### Monitor and detect

As you work through each business scenario, establish how you'll monitor and detect changes to the environment and breaches. Many of the monitoring and detection capabilities are provided through the Extended Detection and Response (XDR) tools, including the suite of Microsoft Defender products and Microsoft Sentinel. These are implemented in the **Prevent or reduce business damage from a breach** business scenario (article is in progress).

### Iterate for maturity

Implementing Zero Trust is a journey. In enterprise-scale organizations, it can take years to fully implement. In this time, attackers also continue to evolve their techniques. It’s important to use your metrics together with your monitoring and detection capabilities to identify where you need to iterate and mature an aspect of your Zero Trust environment. Additionally, continue to evaluate and evolve the way you measure success and communicate progress, status, and value.

## Next Steps

- [Zero Trust adoption framework overview](zero-trust-adoption-overview.md)
- [Secure remote and hybrid work](secure-remote-hybrid-work.md)
- [Identify and protect sensitive business data](identify-protect-sensitive-business-data.md)
- [Meet regulatory and compliance requirements](meet-regulatory-compliance-requirements.md)
