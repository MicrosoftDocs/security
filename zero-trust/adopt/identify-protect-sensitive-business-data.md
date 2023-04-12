---
title: Identify and protect sensitive business data with Zero Trust
description: Learn how to identify and protect sensitive business data with Zero Trust.  
ms.date: 04/14/2023
ms.service: security
author: JoeDavies-TechWriter
ms.author: v-joedavies
ms.topic: conceptual
ms.collection: 
  - zerotrust-solution
---

# Identify and protect sensitive business data

As part of Zero Trust adoption guidance, this article describes the business scenario of safeguarding your most critical data assets. This scenario focuses on how to identify and protect sensitive business data.

Digital transformation has led organizations to deal with increasing volumes of data. However, external collaborators such as partners, vendors, and customers access much of that shared data outside the corporate network. This shift has created a complex data landscape, especially when you consider the proliferation of hybrid workforces and cloud migrations, growing cyberthreats, evolving security, and changing regulatory requirements around how data is governed and protected.

With hybrid work models, corporate assets and data are on the move. Your organization needs to control wherever the data is stored and transferred on devices, inside apps, and with partners. For modern-day security, however, you can no longer rely on traditional network protection controls.

| Traditional data protection with network controls | Modern data protection with Zero Trust |
| --- | --- |
| In traditional networks, network perimeter control governs critical data access, not data sensitivity. You typically apply labels on sensitive data manually, which can result in inconsistent data classification. | A Zero Trust model applies strong authentication to data access requests, using policies to verify every identity, and ensuring identities have access to apps and data. <br><br> A Zero Trust model involves identifying sensitive data and applying classification and protection, including data loss prevention (DLP). Zero Trust includes defenses that protect your data even after it has left your controlled environment. It also includes adaptive protection to reduce insider risk. <br><br> In addition to these protections, Zero Trust includes continuous monitoring and threat protection to prevent and limit the scope of a data breach. |

The guidance in this article walks through how to get started with and progress your strategy for identifying and protecting sensitive data. If your organization is subject to regulations that protect data, use the **Proactively meet regulatory and compliance requirements** article in this series (under development) to learn how to apply what you learn in this article to protecting data that is regulated.

## Why business leaders think about protecting sensitive data

Before starting any technical work, it’s important to understand the different motivations for investing in protecting business data as these help inform the strategy, objectives, and measures for success.

The following table provides reasons why business leaders across an organization should invest in Zero Trust-based data protection.

| Role | Why protecting sensitive data is important |
| --- | --- |
| Chief Executive Officer (CEO) | Intellectual property is the backbone of many organizations’ business models. Preventing it from leaking while allowing seamless collaboration with authorized parties is essential to the business. In organizations dealing with customers’ personally identifiable information (PII), the risk of leakage can result not only in financial penalties but also damage the company's reputation. Finally, sensitive business conversations (like mergers and acquisitions, business restructuring, strategy, and legal matters) can seriously damage an organization if leaked. |
| Chief Marketing Officer (CMO) | Product planning, messaging, branding, and upcoming product announcements must be released at the right time and in the right way to maximize impact. Untimely leakage can reduce investment returns and tip off competitors to upcoming plans. |
| Chief Information Officer (CIO) | While traditional approaches for protecting information relied on limiting access to it, protecting sensitive data adequately by using modern technologies enables more flexible collaboration with external parties, as needed, without increasing risk. Your IT departments can fulfill their mandate to ensure productivity while minimizing risk. |
| Chief Information Security Officer (CISO) | As the primary function of this role, securing sensitive business data is an integral part of information security. This outcome directly affects the organization’s larger cybersecurity strategy. Advanced security technology and tools provide the ability to monitor data and prevent leakage and loss. |
| Chief Technology Officer (CTO) | Intellectual property can differentiate a successful business from a failing one. Protecting this data from oversharing, unauthorized access, and theft is key to ensure future growth of the organization. | 
|Chief Operations Officer (COO) | Operations data, procedures, and production plans are a key strategic advantage to an organization. These plans can also reveal strategic vulnerabilities that can be exploited by competitors. Protecting this data from theft, oversharing, and misuse is critical to the continued success of the business. |
| Chief Financial Officer (CFO) | Publicly traded companies have a duty to protect specific financial data before it's made public. Other financial data can reveal plans and strategic strengths or weaknesses. This data must all be protected to both ensure compliance with existing regulations and maintain strategic advantages. |
| Chief Compliance Officer (CCO) | Regulations across the world mandate protection of PII of customers or employees and other sensitive data. The CCO is responsible for ensuring the organization abides by such regulations. A comprehensive information protection strategy is key to achieving that goal. |
| Chief Privacy Officer (CPO) | A CPO is typically responsible for ensuring protection of personal data. In organizations that deal with large amounts of customer personal data and organizations operating in regions with strict privacy regulations, failure to protect sensitive data can result in steep fines. These organizations also risk losing customer trust as a consequence. CPOs must also prevent personal data from being misused in ways that violate customer agreements or laws, which can include improper sharing of the data within the organization and with partners. |

## The adoption cycle for protecting critical business data

This article walks through this business scenario using the same lifecycle phases as the [Cloud Adoption Framework for Azure](/azure/cloud-adoption-framework/overview)—Define strategy, Plan, Ready, Adopt, Govern, and Manage—but adapted for Zero Trust.

:::image type="content" source="../media/adoption-guide/zero-trust-framework-lifecycle-phases.svg" alt-text="Zero Trust adoption guidance uses the same lifecycle phases." lightbox="../media/adoption-guide/zero-trust-framework-lifecycle-phases.svg":::

Read more about the Zero Trust adoption cycle in the [Zero Trust adoption framework overview](zero-trust-adoption-overview.md).

## Define strategy phase

The **Define strategy** phase is critical to define and formalize our efforts – it formalizes the “Why?” of this scenario. In this phase, you understand the scenario through business, IT, operational and strategic perspectives. You define the outcomes against which to measure success in the scenario, understanding that security is an incremental and iterative journey.

This article suggests motivations and outcomes that are relevant to many organizations. Use these suggestions to hone the strategy for your organization based on your unique needs.

### Data protection motivations

The motivations for identifying and protecting sensitive business data are straightforward, but different parts of your organization have different incentives for doing this work. The following table summarizes some of these motivations.

| Area | Motivations |
| --- | --- |
| Business needs | To safeguard sensitive business data, especially when shared with partners. |
| IT needs | A standardized data classification schema that can be applied consistently throughout the digital estate. |
| Operational needs | Implement data protection in a consistent and standard way, using automation where possible. |
| Strategic needs | Reduce the damage that an insider can cause (intentionally or unintentionally) or by a bad actor who gains access to the environment. |

Note that meeting regulatory requirements might be the primary driving motivation for some organizations. If this is true for you, go ahead and add this to your organization strategy and use this business scenario together with the **Proactively meet regulatory and compliance requirements** article in this series (under development).

### Data protection outcomes

Applying the overall goal of Zero Trust to “never trust, always verify” to your data adds a significant layer of protection to your environment. It’s important to be clear on the outcomes you expect to achieve so that you can strike the right balance of protection and usability for all teams involved, including your users.
The following table provides suggested objectives and outcomes.

| Objective | Outcome |
| --- | --- |
| Productivity | Users can easily collaborate on creating business data or perform their job functions by using business data. |
| Safe access | Access to data and apps is secured at the appropriate level. Highly sensitive data requires stricter safeguards, but these protections shouldn't burden users who are expected to contribute to or use this data. <br><br> Sensitive business data is limited to those in need of using it and you've put controls in place to limit or discourage users from sharing or replicating this data outside the intended usage group. |
| Support end users | Controls for securing data have been integrated into the overall Zero Trust architecture. These controls include single sign-on, multifactor authentication (MFA), and Azure Active Directory (Azure AD) Conditional Access, so that users aren't continually challenged with authentication and authorization requests. <br><br> Users receive training on how to classify and share data securely. Users are enabled to take control of their important data, allowing them to revoke access in case of need, or track usage of the information after it has been shared. <br><br> Data protection policies are automated where possible to lessen the burden on users. |
| Increase security | The addition of data protection across the digital estate protects these critical business assets and helps reduce the potential damage from a data breach. <br><br> Data protections include safeguards to protect against intentional, unintentional, or negligent data breaches by current or former employees and partners. |
| Empower IT | Your IT team is empowered with a clear understanding of what qualifies as sensitive business data. They have a well-reasoned schema to align with and the technology tools and capabilities to both implement the plans and monitor status and success. |

## Plan phase

Adoption plans convert the principles of Zero Trust strategy into an actionable plan. Your collective teams can use the adoption plan to guide their technical efforts and align them with your organization's business strategy.

The motivations and outcomes you define, together with your business leaders and teams, support the “Why?” for your organization and become the North Star for your strategy. Next comes the technical planning to achieve the objectives.

Technical adoption for identifying and protecting sensitive business data involves:

- Discovering and identifying sensitive data across your digital estate.
- Curating a classification and protection schema, including DLP.
- Rolling out the schema across your digital estate, starting with data in Microsoft 365 and extending the protection to all SaaS apps, your cloud infrastructure, and data in on-premises repositories. SaaS apps are apps that are outside your Microsoft 365 subscription but are integrated with your Azure AD tenant.

Protecting your sensitive business data also involves a few related activities, including:

- Encrypting network communication.
- Managing external access to Teams and projects where sensitive data is shared.
- Setting up and using dedicated and isolated teams in Microsoft Teams for projects that include highly sensitive business data, which should be rare. Most organizations do not require this level of data security and isolation.

Many organizations can take a four-staged approach to these technical activities, summarized in the following table.

| Stage 1 | Stage 2 | Stage 3 | Stage 4 |
| --- | --- | --- | --- |
| Discover and identify sensitive business data <br><br> Discover non-sanctioned SaaS apps <br><br> Encrypt network communication | Develop and test a classification schema <br><br> Apply labels to data across Microsoft 365 <br><br> Introduce basic DLP policies <br><br> Set up secure Microsoft Teams for sharing data internally and externally with business partners | Add protection to specific labels (encryption and other protection settings) <br><br> Introduce automatic and recommended labeling in Office apps and services <br><br> Enable mandatory labeling of new content <br><br> Extend DLP policies across Microsoft 365 services <br><br> Implement key insider risk management policies | Extend labels and protection to data in SaaS apps, including DLP <br><br> Extend automated classification to all services <br><br> Extend labels and protection to data at-rest in on-premises repositories <br><br> Protect organization data in your cloud infrastructure |

If this staged approach works for your organization, you can share your progress with your teams and business leaders by downloading [this PowerPoint deck](add link) and updating the slides that correspond to this business scenario. Here is an example.

:::image type="content" source="../media/adoption-guide/zero-trust-protect-data-stakeholders.png" alt-text="PowerPoint slide to identify key stakeholders." lightbox="../media/adoption-guide/zero-trust-protect-data-stakeholders.png":::

>>ADD LINK TO PPT

### Understand your organization

This recommended staged approach for technical implementation can help give context to the exercise of understanding your organization. Each organization’s needs for protecting sensitive business data and the composition and volume of data are different.

A foundational step in the Zero Trust adoption lifecycle for every business scenario includes taking inventory. For this business scenario, you take inventory of your organization’s data.

The following actions apply:

- Inventory your data.

  First, take stock of where all your data resides, which can be as simple as listing the apps and repositories with your data. After technologies like sensitivity labeling have been deployed, you may discover other locations where sensitive data is being stored. These locations are sometimes referred to as dark or grey IT. It’s also helpful to estimate how much data you plan to inventory (the volume). Throughout the recommended technical process, you use the tool set to discover and identify business data. You’ll learn what kinds of data you have and where this data resides across services and cloud apps, enabling you to correlate the sensitivity of the data with the level of exposure of the locations in which it's present. For example, Microsoft Defender for Cloud Apps helps you identify SaaS apps you might not have been aware of. The work of discovering where your sensitive data resides begins in Stage 1 of the technical implementation and cascades through all four stages.
- Document the goals and plan for incremental adoption based on priorities.

  The four stages recommended represent an incremental adoption plan. Adjust this plan based on your organization’s priorities and the composition of your digital estate. Be sure to take account of any timeline milestones or obligations for completing this work.

- Inventory any data sets or dedicated projects that require compartmentalized protection (for example, tented or special projects).

  Not every organization requires compartmentalized protection.

### Organizational planning and alignment

The technical work of protecting sensitive business data crosses several overlapping areas and roles:

- Data
- Apps
- Endpoints
- Network
- Identities

This table summarizes roles that are recommended when building a sponsorship program and project management hierarchy to determine and drive results.

| Program leaders and technical owners | Accountability |
| --- | --- |
| CISO, CIO, or Director of Data Security | Executive sponsorship |
| Program lead from Data Security | Drive results and cross-team collaboration |
| Security Architect | Advise on configuration and standards, especially around encryption, key management, and other fundamental technologies |
| Compliance Officers | Map compliance requirements and risks to specific controls and available technologies |
| Microsoft 365 Admins | Implement changes to your Microsoft 365 tenant for OneDrive and Protected Folders |
| Application Owners | Identify critical business assets and ensure compatibility of applications with labeled, protected, and encrypted data |
| Data Security Admin | Implement configuration changes |
| IT Admin | Update standards and policy documents |
| Security Governance and/or IT Admin | Monitor to ensure compliance |
| User Education Team | Ensure guidance for users reflects policy updates and provide insights into user acceptance of the labeling taxonomy  |

The [PowerPoint deck of resources](add link) for this adoption content includes the following slide with a stakeholder view that you can customize for your own organization.

>> ADD LINK TO PPT DOWNLOAD

>> RESOLVE THIS LIST

- CISO (remains the same)
- Compliance Officer: Responsible for maintaining organizational compliance with legislative requirements related to both data privacy & residency.
- Internal Audit: Ensures that controls identified within organizational policies & procedures related to sensitive data management, are regularly followed and adhered to. 
- IT Manager: Determines the technological controls required to ensure sensitive data protection.  
- Information Protection Admin: Create, edit, and delete DLP policies, sensitivity labels and their policies, and all classifier types.

### Technical planning and skills readiness

Before you embark on the technical work, Microsoft recommends getting to know the capabilities, how they work together, and best practices for approaching this work. The following table includes several resources to help your teams gain skills.

| Resource | Description |
|:-----|:-----|
| Deployment Acceleration Guide-[Information Protection and Data Loss Prevention](https://microsoft.github.io/ComplianceCxE/dag/mip-dlp/) | Learn best practices from the Microsoft Customer Engagement teams. This guidance leads organizations to maturity through a crawl, walk, run model, which aligns with the recommended stages in this adoption guidance.  |
| [RaMP checklist-Data protection](/security/zero-trust/data-compliance-gov-data) ![Image of Rapid Modernization Plan](../media/ramp.png) | Another resource for listing and prioritizing the recommended work, including stakeholders. |
| [Introduction to Microsoft Purview Data Loss Prevention](/microsoft-365/compliance/dlp-learn-about-dlp) (beginner) | In this resource, you learn about DLP in Microsoft Purview Information Protection. |
|  :::image type="icon" source="../media/adoption-guide/introduction-information-governance.svg" border="false"::: <br> Learn module-[Introduction to information protection and data lifecycle management in Microsoft Purview](/training/modules/m365-compliance-information-governance/) (Intermediate) | Learn how Microsoft 365 information protection and data lifecycle management solutions help you protect and govern your data, throughout its lifecycle – wherever it lives and travels. |
| :::image type="icon" source="../media/adoption-guide/microsoft-certified-associate-badge.svg" border="false"::: <br> Certifications-[Microsoft Certified: Information Protection Administrator Associate](/certifications/information-protection-administrator/) | Recommended learning paths for becoming a Certified Information Protection Administrator Associate. |

### Stage 1

The Stage 1 objectives include the process of taking inventory of your data. This includes identifying unsanctioned SaaS apps your organization uses to store, process, and share data. You can either bring these unsanctioned apps into your app management process and apply protections, or you can prevent your business data from being used with these apps.

#### Discover and identify sensitive business data

Starting with Microsoft 365, some of the primary tools you use to identify sensitive information that needs to be protected are sensitive information types (SITs) and other classifiers, including trainable classifiers and fingerprints. These identifiers help find common sensitive data types, such as credit card numbers or governmental identification numbers, and identifying sensitive documents and emails using machine learning and other methods. You can also create custom SITs to identify data that is unique to your environment, including using exact data matching to differentiate data pertaining to specific people—for example, customer PII—that needs special protection.

When data is added to your Microsoft 365 environment or modified, it's automatically analyzed for sensitive content using any SITs that are presently defined in your tenant.

You can use content explorer in the Microsoft Purview compliance portal to see any occurrences of detected sensitive data across the environment. The results let you know if you need to customize or tune the SITs for your environment for greater accuracy. The results also give you a first picture of your data stock and your information protection status. For example, if you're receiving too many false positives for a SIT, or not finding known data, you can create custom copies of the standard SITs and modify them so they work better for your environment. You can also refine these using exact data matching.

Additionally, you can use built-in trainable classifiers to identify documents that belong to certain categories, such as contracts or freight documents. If you have specific classes of documents you know you have to identify and potentially protect, you can use samples in the Microsoft Purview compliance portal to train your own classifiers. These samples can be used to discover the presence of other documents with similar patterns of content.

In addition to the content explorer, organizations have access to the Content search capability to produce custom searches for data in the environment, including using advanced search criteria and custom filters.

The following table lists resources for discovering sensitive business data.

| Resource | Description |
| --- | --- |
| [Deploy an information protection solution with Microsoft 365 Purview](/microsoft-365/compliance/information-protection-solution) | Introduces a framework, process, and capabilities you can use to accomplish your specific business objectives for information protection. |
| [Sensitive information types](/microsoft-365/compliance/sensitive-information-type-learn-about) | Start here to get started with sensitive information types. This library includes many articles for experimenting with and optimizing SITs. |
| [Content explorer](/microsoft-365/compliance/data-classification-content-explorer) | Scan your Microsoft 365 environment for the occurrence of SITs and view the results in the content explorer tool. |
| [Trainable classifiers](/microsoft-365/compliance/classifier-learn-about) | Trainable classifiers allow you to bring samples of the type of content you want to discover (seeding) and then let the machine learning engine learn how to discover more of this data. You participate in the classifier training by validating the results until the accuracy is improved. |
| [Exact data matching](/microsoft-365/compliance/sit-get-started-exact-data-match-based-sits-overview) | Exact data matching allows you to find sensitive data that matches existing records—for example, your customers’ PII as recorded in your line of business apps—which enables you to precisely target such data with information protection policies, virtually eliminating false positives. |
| [Content search](/microsoft-365/compliance/search-for-content) | Use Content search for advanced searches, including custom filters. You can use keywords and Boolean search operators. You can also build search queries using Keyword Query Language (KQL). |
| [RaMP checklist-Data protection: Know your data](/security/zero-trust/data-compliance-gov-data#1-know-your-data) | A checklist of implementation steps with step owners and links to documentation. |

#### Discover non-sanctioned SaaS apps

Your organization likely subscribes to many SaaS apps, such as Salesforce or apps that are specific to your industry. The SaaS apps that you know about and manage are considered sanctioned. In later stages, you extend the data protection schema and DLP policies you create with Microsoft 365 to protect data in these sanctioned SaaS apps.

However, at this stage it’s important to discover non-sanctioned SaaS apps that your organization is using. This enables you to monitor traffic to and from these apps to determine if your organization’s business data is being shared to these apps. If so, you can bring these apps into management and apply protection to this data, starting with enabling single sign-on with Azure AD. 

The tool for discovering SaaS apps that your organization uses is Microsoft Defender for Cloud Apps.

| Resource | Description |
| --- | --- |
| [Integrate SaaS apps for Zero Trust with Microsoft 365](/security/zero-trust/integrate-saas-apps) | This solution guide walks through the process of protecting SaaS apps with Zero Trust principles. The first step in this solution includes adding your SaaS apps to Azure AD and to the scopes of policies. This should be a priority. |
| [Evaluate Microsoft Defender for Cloud Apps](/microsoft-365/security/defender/eval-defender-mcas-overview) | This guide helps you get Microsoft Defender for Cloud Apps up and running as quickly as possible. You can discover unsanctioned SaaS apps as early as the trial and pilot phases. |

#### Encrypt network communication

This task is more of a check to be sure your network traffic is encrypted. Check in with your networking team to make sure these recommendations are satisfied.

| Resource | Description |
| --- | --- |
| [Secure networks with Zero Trust-Objective 3: User-to-app internal traffic is encrypted](/security/zero-trust/deploy/networks#iii-encryption-user-to-app-internal-traffic-is-encrypted) | Ensure user-to-app internal traffic is encrypted: <ul><li> Enforce HTTPS-only communication for your internet-facing web applications. </li><li> Connect remote employees and partners to Microsoft Azure using [Azure VPN Gateway](/azure/vpn-gateway/vpn-gateway-about-vpngateways). </li><li> Access your Azure virtual machines securely using encrypted communication through [Azure Bastion](/azure/bastion/bastion-overview). </li></ul> |
| [Secure networks with Zero Trust-Objective 6: All traffic is encrypted](/security/zero-trust/deploy/networks#vi-encryption-all-traffic-is-encrypted) | Encrypt application backend traffic between virtual networks.<br><br> Encrypt traffic between on-premises and cloud. |
| [Networking up (to the cloud)-One architect's viewpoint](/microsoft-365/solutions/networking-design-principles) | For network architects, this article helps put recommended networking concepts into perspective. Ed Fisher, Security & Compliance Architect at Microsoft, describes how to optimize your network for cloud connectivity by avoiding the most common pitfalls. |

### Stage 2

After you've taken inventory and discovered where your sensitive data resides, move on to Stage 2 in which you develop a classification schema and begin to test this with your organization data. This stage also includes identifying where data or projects require increased protection.

When developing a classification schema, it’s tempting to create many categories and levels. However, organizations that are most successful limit the number of classification tiers to a small number, like 3-5. Fewer is better.

Before translating your organization’s classification schema to labels and adding protection to labels, it’s helpful to think about the big picture. It’s best to be as uniform as possible when applying any type of protection across an organization and especially a large digital estate. This applies to data as well.

So, for example, many organizations are well-served by a three-tier model of protection across data, devices, and identities. In this model, most data can be protected at a baseline level. A smaller amount of data might require increased protection. Some organizations have a very small amount of data that requires protection at much higher levels. Examples include trade-secret data or data that is highly regulated due to the extremely sensitive nature of the data or projects.

:::image type="content" source="../media/adoption-guide/three-tiers-of-protection.svg" alt-text="The three tiers of data protection." lightbox="../media/adoption-guide/three-tiers-of-protection.svg":::

If three tiers of protection work for your organization, this helps simplify how you translate this to labels and the protection you apply to labels.

For this stage, develop your sensitivity labels and start using them across data in Microsoft 365. Don’t worry about adding protection to the labels yet, that is preferably done at a later stage once users have become familiar with the labels and have been applying these without concerns regarding their constraints for some time. Adding protection to labels is included in the next stage. However, it's recommended to also get started with basic DLP policies. Finally, in this stage you apply specific protection to projects or data sets that require highly sensitive protection.

#### Develop and test a classification schema

| Resource | Description |
| --- | --- |
| [Sensitivity labels](/microsoft-365/compliance/sensitivity-labels) | Learn about and get started with sensitivity labels. <br><br> The most critical consideration in this phase is to ensure that the labels reflect both the needs of the business and the language used by users. If the names of the labels don't intuitively resonate with users or their meanings don't map consistently to their intended use, adoption of labeling can end up being hampered, and accuracy of label application is likely to suffer. |

#### Apply labels to data across Microsoft 365

| Resource | Description |
| --- | --- |
| [Enable sensitivity labels for Office files in SharePoint and OneDrive](/microsoft-365/compliance/sensitivity-labels-sharepoint-onedrive-files) | Enable built-in labeling for supported Office files in SharePoint and OneDrive so that users can apply your sensitivity labels in Office for the web.  |
| [Manage sensitivity labels in Office apps](/microsoft-365/compliance/sensitivity-labels-office-apps) | Next, start introducing labels to users where they can see and apply them. When you've published sensitivity labels from the Microsoft Purview compliance portal, they start to appear in Office apps for users to classify and protect data as it's created or edited. |
| [Apply labels to Microsoft Teams and Microsoft 365 groups](/microsoft-365/compliance/sensitivity-labels-teams-groups-sites) | When you’re ready, include Microsoft Teams and Microsoft 365 groups into the scope of your labeling deployment. |

#### Introduce basic DLP policies

| Resource | Description |
| --- | --- |
| [Prevent data loss](/microsoft-365/compliance/information-protection-solution) | Get started with DLP policies. <br><br> It's recommended to start with “soft” DLP policies, which provide warnings but don't block actions, or at most block actions while allowing users to override the policy. This allows you gauge the impact of these policies without harming productivity. You can fine-tune the policies to become stricter as you gain confidence in their accuracy and compatibility with the business needs. |

 #### Set up secure teams for sharing data internally and externally with business partners

If you've identified projects or data that require highly sensitive protection, these resources describe how to set this up in Microsoft Teams. If the data is stored in SharePoint without an associated team, use the instructions in these resources for SharePoint settings.

| Resource | Description |
| --- | --- |
| [Configure teams with protection for highly sensitive data](/microsoft-365/solutions/configure-teams-highly-sensitive-protection) | Provides prescriptive recommendations for securing projects with highly sensitive data, including securing and managing guest access (your partners who might be collaborating with you on these projects). |
| [Configure a team with security isolation](/microsoft-365/solutions/secure-teams-security-isolation) | This article provides you with recommendations and steps to configure a private team in Microsoft Teams and use a unique sensitivity label to encrypt files so that only team members can decrypt them. |

### Stage 3

In this stage, you continue to roll out the data classification schema you refined. You also apply the protections you planned.

Once you add protection to a label (such as encryption and rights management):

- All documents that newly receive the label include the protection.
- Any document stored in SharePoint Online or OneDrive for Business that received the label before the protection was added has the protection applied when the document is opened or downloaded. 

Files at rest in the service or residing on a user’s computer don't receive the protection that was added to the label AFTER these files received the label. In other words, if the file was previously labeled and then you later add protection to the label, the protection isn't applied to these files.

#### Add protection to labels

| Resource | Description |
| --- | --- |
| [Learn about sensitivity labels](/microsoft-365/compliance/sensitivity-labels) | See this article for many ways you can configure specific labels to apply protection. <br><br> It's recommended that you start with basic policies like “encrypt only” for emails, and “all employees – full control” for documents. These policies provide strong levels of protection while providing easy ways out for users when they find situations in which the introduction of encryption causes compatibility problems or conflicts with business requirements. You can incrementally tighten restrictions later as you gain confidence and understanding in the way users need to consume the sensitive data. |
| [Common scenarios for sensitivity labels](/microsoft-365/compliance/get-started-with-sensitivity-labels#common-scenarios-for-sensitivity-labels) | See this list of scenarios that are supported by sensitivity labels. |

#### Introduce automatic labeling in Office apps 

| Resource | Description |
| --- | --- |
| [Apply a sensitivity label to content automatically](/microsoft-365/compliance/apply-sensitivity-label-automatically) | Automatically assign a label to files and emails when it matches conditions that you specify. It's recommended that you initially configure the labels to provide an interactive labeling recommendation to users. Once you confirm these are generally accepted, switch them to automatically applying the label. |

#### Extend DLP policies across Microsoft 365

| Resource | Description |
| --- | --- |
| [Prevent data loss](/microsoft-365/compliance/information-protection-solution) | Continue to use these steps to apply DLP across your Microsoft 365 environment, extending the policies to more locations and services and tightening the rule actions by removing unnecessary exceptions. |

#### Implement basic insider risk management policies

| Resource | Description |
| --- | --- |
| [Insider risk management](/microsoft-365/compliance/insider-risk-management-solution-overview) | Get started with the recommended actions. You can begin by using policy templates to quickly get started, including data theft by departing users. |

### Stage 4

In this stage, you extend the protections you developed in Microsoft 365 to data in your SaaS apps. You also transition to automation of as much of the data classification and governance as possible. 

#### Extend labels and protection to data in SaaS apps, including DLP

| Resource | Description |
| --- | --- |
| [Deploy information protection for SaaS apps](/security/zero-trust/deploy-information-protection-saas) | Using Microsoft Defender for Cloud Apps, you extend the classification schema you developed with Microsoft 365 capabilities to protect data in your SaaS apps. |

#### Extend automated classification

| Resource | Description |
| --- | --- |
| [Apply a sensitivity label to content automatically](/microsoft-365/compliance/apply-sensitivity-label-automatically) | Continue to roll out the automated methods for applying labels to your data. Extend them to documents at-rest in SharePoint, OneDrive, and Teams, and to emails being sent or received by users. |

#### Extend labels and protection to data in on-premises repositories

| Resource | Description |
| --- | --- |
| [Microsoft 365 Purview Information Protection Scanner](/microsoft-365/compliance/deploy-scanner) | Scan data in on-premises repositories, including Microsoft Windows file shares and SharePoint Server. The information protection scanner can inspect any files that Windows can index. If you've configured sensitivity labels to apply automatic classification, the scanner can label discovered files to apply that classification, and optionally apply or remove protection. |

#### Protect organization data in cloud infrastructure

| Resource | Description |
| --- | --- |
| [Microsoft Purview data governance documentation](/en-us/azure/purview/) | Learn how to use the Microsoft Purview governance portal so your organization can find, understand, govern, and consume data sources. Tutorials, REST API reference, and other documentation show you how to plan and configure your data repository where you can discover available data sources and manage rights use. |

### Cloud adoption plan
An adoption plan is an essential requirement for a successful cloud adoption. Key attributes of a successful adoption plan for protecting data include:

- **Strategy and planning are aligned:** As you draw up your plans for testing, piloting, and rolling out data classification and protection capabilities across your digital estate, be sure to revisit your strategy and objectives to ensure your plans are aligned. This includes priority of data sets, goals for data protection, and target milestones.
- **The plan is iterative:** As you start to roll out your plan, you'll learn many things about your environment and the capability set you're using. At each stage of your roll-out, revisit your results compared to the objectives and fine tune the plans. This can include revisiting earlier work to fine-tune policies, for example.
- **Training your staff and users is well-planned:** From your administration staff to helpdesk and your users, everybody is trained to be successful with their data identification and protection responsibilities. 

For more information from the Cloud Adoption Framework for Azure, see [Plan for cloud adoption](/azure/cloud-adoption-framework/plan/plan-intro).

## Ready phase

Use the resources previously listed to prioritize your plan for identifying and protecting sensitive data. The work of protecting sensitive business data represents one of the layers in your multi-layer Zero Trust deployment strategy.

The staged approach recommended in this article includes cascading the work in a methodical way across your digital estate. At this Ready phase, revisit these elements of the plan to be sure everything is ready to go:

- Data that is sensitive for your organization is well defined. You'll likely adjust these definitions as you search for data and analyze the results.
- You have a clear map of which data sets and apps to start with and a prioritized plan for increasing the scope of your work until it encompasses your entire digital estate.
- Adjustments to the prescribed technical guidance that are appropriate for your organization and environment have been identified and documented.

This list summarizes the high-level methodical process for doing this work:

- Get to know the data classification capabilities such as sensitive information types, trainable classifiers, sensitivity labels, and DLP policies. 
- Begin using these capabilities with data in Microsoft 365 services. This experience helps you refine your schema.
- Introduce classification into Office apps.
- Move on to protection of data on devices by experimenting with and then rolling out endpoint DLP.
- Extend the capabilities you’ve refined within your Microsoft 365 estate to data in cloud apps by using Defender for Cloud Apps.
- Discover and apply protection to data on-premises using Microsoft Purview Information Protection scanner
- Use Microsoft Purview data governance to discover and protect data in cloud data storage services, including Azure Blobs, Cosmos DB, SQL databases, and Amazon Web Services S3 repositories.

This diagram shows the process.

:::image type="content" source="../media/adoption-guide/process-for-data-identification.svg" alt-text="Process for identifying and protecting your sensitive data." lightbox="../media/adoption-guide/process-for-data-identification.svg":::

Your priorities for data discovery and protection might differ.

Note the following dependencies on other business scenarios:

- Extending information protection to endpoint devices requires coordination with Intune (included in the [Secure remote and hybrid work](secure-remote-hybrid-work.md) article).
- Extending information protection to data in SaaS apps requires Microsoft Defender for Cloud Apps. Piloting and deploying Defender for Cloud Apps is included in the “Prevent or reduce business damage from a breach” scenario (coming soon). In the meantime, see [Evaluate Microsoft Defender for Cloud Apps](/microsoft-365/security/defender/eval-defender-mcas-overview).

As you finalize your adoption plans, be sure to revisit the [Information Protection and Data Loss Prevention](https://microsoft.github.io/ComplianceCxE/dag/mip-dlp/) Deployment Acceleration Guide to review the recommendations and fine-tune your strategy.

## Adopt phase

Microsoft recommends a cascading, iterative approach to discovering and protecting sensitive data. This allows you to refine your strategy and policies as you go to increase the accuracy of the results. For example, begin working on a classification and protection schema as you discover and identify sensitive data. The data you discover informs the schema and the schema helps you improve the tools and methods you use to discover sensitive data. Similarly, as you test and pilot the schema, the results help you improve the protection policies you created earlier. There’s no need to wait until one phase is complete before beginning the next. Your results are more effective if you iterate along the way.

:::image type="content" source="../media/adoption-guide/adoption-information-protection.svg" alt-text="Process for technical adoption of information protection." lightbox="../media/adoption-guide/adoption-information-protection.svg":::

## Govern and Manage phases

Governance of your organization’s data is an iterative process. By thoughtfully creating your classification schema and rolling it out across your digital estate you have created a foundation. Use the following exercises to help you start building your initial governance plan for this foundation:

- **Establish your methodology:** Establish a basic methodology for reviewing your schema, how it's applied across your digital estate, and the success of the results. Decide how you'll monitor and evaluate the success of your information protection protocol, including your current state and future state.
- **Establish an initial governance foundation:** Begin your governance journey with a small, easily implemented set of governance tools. This initial governance foundation is called a minimum viable product (MVP). 
- **Improve your initial governance foundation:** Iteratively add governance controls to address tangible risks as you progress toward the end state.

Microsoft Purview provides several capabilities to help you govern your data, including:

- Retention policies
- Mailbox retention and archive capabilities
- Records management for more sophisticated retention and deletion policies and schedules

See [Govern your data with Microsoft Purview](/microsoft-365/compliance/manage-data-governance). Additionally, [activity explorer](/microsoft-365/compliance/data-classification-activity-explorer) gives you visibility into what content has been discovered and labeled, and where that content is. For SaaS apps, Microsoft Defender for Cloud Apps provides rich reporting for sensitive data that is moving into and out of SaaS apps. See the many tutorials in the [Microsoft Defender for Cloud Apps content library](/defender-cloud-apps/).

## Next Steps

- [Zero Trust adoption framework overview](zero-trust-adoption-overview.md)
- [Secure remote and hybrid work with Zero Trust](secure-remote-hybrid-work.md)
