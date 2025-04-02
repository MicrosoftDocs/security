---
title: Build a strong security posture for AI
description: How to approach security for AI apps and data, including building a strong security posture for AI.
ms.date: 04/01/2025
ms.service: security
author: BrendaCarter
ms.author: bcarter
ms.topic: concept-article
ms.collection: 
  - msftsolution-security-for-ai
  - msftsolution-overview
  - zerotrust-solution
---

# Build a strong security posture for AI

Your AI security posture is an important part of your overall security strategy. AI places priority on specific elements of a cybersecurity strategy, such as data protection. This article helps you develop your strategy and priorities for securing AI. Subsequent articles in this collection help you identify the specific elements of cybersecurity to prioritize as you adopt AI companions, tools, and new apps.

Your [security posture](../zero-trust/adopt/rapidly-modernize-security-posture.md) is defined as your organization’s overall cybersecurity defense capability, along with the level of preparation and operational status to deal with ongoing cyber-security threats. This posture should be quantifiable and measurable, similarly to any other major metric that pertains to the operational status or well-being of your organization.

:::image type="content" source="media/security-posture.svg" alt-text="Diagram that shows the organization's security posture." lightbox="media/security-posture.svg":::

Building a strong security posture for AI involves working within your organization, especially leaders across your organization, to develop a strategy and a set of priorities and objectives. You then identify the technical work necessary to achieve the objectives and lead the various teams to accomplish them. The articles in this library provide a methodology with guidance that is specific to AI: 

  - [**Prepare**](prepare.md) your environment with foundation security protections. You likely already have many of these protections in place. 
  - [**Discover**](discover.md) the AI apps that are being used in your organization, including the types of data the apps are using. 
  - [**Protect**](protect.md) the usage of AI tools in your organization. This involves AI-specific data protection capabilities and ensuring your organization has implemented strong threat protection. 
  - [**Govern**](govern.md) AI for compliance. 
  
  :::image type="content" source="media/security-for-ai-step-no-highlight.svg" alt-text="Diagram that shows the process of implementing security for AI.":::

Use this library together with the following frameworks on Microsoft Learn: 
- [Zero Trust adoption framework](../zero-trust/adopt/zero-trust-adoption-overview.md) 
- [Cloud Adoption Framework for AI](/azure/cloud-adoption-framework/scenarios/ai/)

:::image type="content" source="media/security-for-ai-framework-comparison.svg" alt-text="Diagram that shows the framework of security for AI." lightbox="media/security-for-ai-framework-comparison.svg":::

In the image: 

- Use this library (Security for AI library) to learn how to implement capabilities to secure AI apps and data in your environment. These protections help build your Zero Trust foundation. 
- Use the [Zero Trust adoption framework](../zero-trust/adopt/zero-trust-adoption-overview.md) to continue to make progress toward end-to-end security. Each of the Zero Trust business scenarios also increases your security for AI apps and data. 
- Use the [Cloud Adoption Framework for AI](/azure/cloud-adoption-framework/scenarios/ai/) to develop your end-to-end roadmap for adoption of AI, including generative and non-generative AI. This library includes strategy, prescriptive guidance for people roles and organization processes, and deeper guidance for developing AI apps in Azure, including design and implementation guidance. 

## Understand the motivations of your business leaders

Begin developing your strategy and priorities by gaining alignment with your business leaders. What motivates your leaders and why do they care about your security posture for AI? The following table provides example perspectives, but it’s important for you to meet with each of these leaders and teams and come to a shared understanding of each other’s motivations.

| Role | Why building a strong security posture for AI is important |
|-----|------|
| Chief Executive Officer (CEO) | |
| Chief Marketing Officer (CMO) | |
| Chief Information Officer (CIO)  | |
| Chief Information Security Officer (CISO) | |
| Chief Technology Officer (CTO) | |
| Chief Operations Officer (COO) | |
| Chief Financial Officer (CFO) | |

Additionally, different parts of your organization will have different motivations and incentives for doing this work. The following table summarizes some of these motivations. Be sure to connect with your stakeholders to understand their motivations. 

| Area | Motivations |
|----|----|
| Business needs | |
| IT needs | |
| Operational needs  | |
| Strategic needs | |

## Address the evolving threat landscape for AI

GenAI introduces new attack surfaces, effectively changing the risk landscape. In addition to managing traditional threat vectors, security and risk leaders also need to address amplified risks such as data leakage and data oversharing, and new risks such as prompt injections and model vulnerabilities. Addressing the evolving threat landscape is crucial to enabling trustworthy AI. 

:::image type="content" source="media/ai-introduces-new-amplified-risks.png" alt-text="Diagram that shows the GenAI introducing new risks." lightbox="media/ai-introduces-new-amplified-risks.png":::

In the illustration: 

 - GenAI attack surfaces introduce new and amplified risks. 
 - Threat vectors that remain unchanged include your applications, identities, endpoints, network, data, and cloud resources. 
 - GenAI introduces new attack surfaces, including prompts, responses, AI orchestration, training data, RAG data (Retrieval-Augmented Generation data, meaning data that results from interactions of your data or other outside data with language models), AI models, and AI plugins.
 - GenAI introduces new amplified risks, including data leakage, jailbreak (compromising devices that are otherwise secured), indirect prompt injection, and model vulnerability.  

Currently, the most common security incidents in AI include: 

 - Data leakage and oversharing—Users might leak sensitive data to shadow AI apps (apps not approved by your IT team). Users might also access sensitive data by using AI apps. 
 - Vulnerabilities and emerging threats—Bad actors might exploit vulnerabilities in AI apps to access valuable resources. 
 - Noncompliance—Regulations, including emerging AI regulations, can increase uncertainty. Noncompliant AI adoption can increase liability. 
 
The following two example scenarios highlight the need for building a strong security posture for AI. 

### How does oversharing and leakage of data happen? 

In this example, a Contoso employee, Adele, finds, and uses sensitive data with several AI apps.

| Step | Description | Unmitigated risks |
| ---- | ---------- | ------------ |
| 1 | Adele overhears a team member referencing Project Obsidian. She uses Microsoft 365 Copilot to find more information about it. Copilot provides her with a summary and a link to the documents. | Copilot can process sensitive data without limitations. Sensitive data is overexposed to employees, including those who shouldn’t have access. |
| 2 | Adele continues using Copilot to find and gather more information about Project Obsidian.| There are no controls in place to detect anomalies in AI apps.|
| 3 | Out of curiosity, Adele wants to see what ChatGPT would summarize, so she pastes the content of the file into ChatGTP. | There's no data loss prevention (DLP) in place to prevent data leakage to consumer AI apps.|
| 4 | The project details were prematurely revealed, resulting in data breaches. So, Contoso banned all AI apps in the workplace. | Banning consumer AI outright can lead to increased dark usage.|

Contoso could have mitigated these risks by doing the work of preparing, discovering, and protecting AI app usage.

| Phase | Description |
| -------- | --------- |
| Prepare  | Use **Entra and SharePoint Advanced Management** to right-size employees’ access to resources. <br> Use **Purview Information Protection** to classify and label sensitive data.  |
| Discover | Use **Purview DSPM for AI** to discover data risks. <br> Use an **oversharing assessment report** to assess oversharing risks. |
| Protect  | Enforce **Purview DLP for Microsoft 365 Copilot** to prevent Copilot from summarizing sensitive data. <br> Use **Purview Insider Risk Management** to detect and investigate anomaly activities. Use **Adaptive Protection** to dynamically restrict access for high-risk users. <br> Use **Defender for Cloud Apps** to block high-risk apps. <br> Use **Entra Conditional Access** to require Adele to accept Terms of Use before granting access to ChatGPT. <br> Use **Purview endpoint DLP** to block pasting sensitive data to consumer AI apps. |

### How can AI introduce risk for compliance? 

In this next example, Jane is assigned to lead AI governance for Contoso. 

| Step | Description| Unmitigated risks|
| ---- | ---------------------| ---------------------- |
| 1 | Jane struggles to interpret regulatory requirements into actionable controls for IT teams to implement. | Lack of experts who are well-versed in both regulatory requirements and technology.|
| 2 | Jane starts preparing for risk assessments but is unaware of the AI systems being built and used at Contoso. She also doesn’t have visibility into the usage and potential compliance risks.| No visibility into AI systems deployed in the environment. No governance of AI usage. |
| 3 | After several internal interviews, Jane realizes that developers are building around 14 AI apps simultaneously, which various standards of security, safety, and privacy controls implemented. | No visibility into the controls built in AI systems by developers.  |
| 4 | Some AI apps use personal data with no standard guardrails to assess risks.| No risk assessment in place. |
| 5 | Customers are complaining about Contoso AI creating harmful and ungrounded content.| Lack of controls for AI outputs.|

AI regulations bring uncertainty and overwhelming liability risk to leaders responsible for AI governance. Without any changes, Contoso risks violating AI regulatory requirements and potentially faces penalties and reputation damage.

Contoso could have mitigated these risks by doing the work of preparing, discovering, and protecting AI app usage.

| Phase | Description |
| -------- | --------------- |
| Prepare  | Use **Purview Compliance Manager** to get guidance on implementing controls that can help meet compliance requirements.  |
| Discover | Use **Defender for Cloud** to discover AI resources deployed in cloud environments. Use **Defender for Cloud Apps** to discover SaaS AI apps in use. |
| Govern| Govern AI usage with **Microsoft Purview Audit, Data Lifecycle Management, Communication Compliance,** and **eDiscovery**. <br> Use **AI reports in Azure AI Foundry** for developers to document AI project details. <br> Use **Priva Privacy Assessments** to proactively evaluate privacy risks for each AI project. <br> Use **Azure AI Content Safety** to mitigate risks of harmful or ungrounded content. |

With the proactive use of governance capabilities, organizations can assess and address risk while adopting AI. 

## Five steps to implement effective security for AI 

As awareness of the risks associated with the rapid implementation of GenAI increases, many organizations are responding proactively by dedicating substantial resources to enhance their security measures. Security and risk leaders can take several actionable steps to create a path toward safe and secure AI innovation. 

These recommended practices focus on fostering a collaborative environment and implementing effective security measures that will support GenAI advancements while safeguarding organizational interests. 

### Step 1—Build a security team for AI 

A majority of companies recognize the need to form dedicated, cross-functional teams to manage the unique security challenges posed by AI. Dedicated security teams ensure that AI systems are rigorously tested, vulnerabilities are swiftly identified and mitigated, and security protocols are continuously updated to keep pace with evolving threats. 

Eighty percent of survey respondents either currently have (45%) or plan to have (35%) a dedicated team to address security for AI. Over 6 in 10 said their teams will report to a security decision-maker, ensuring not only vigilant oversight but also strategic vision and leadership in addressing AI-related risks. 

Notably, the median team size, or intended team size, of these dedicated security teams was 24 employees—underscoring the substantial resources that companies are committing to safeguarding their AI initiatives. When the size of company was factored in, team sizes varied. 

Here are a few best practices that organizations can use to successfully build an effective cross-functional security team for AI. 

#### Form an AI committee to foster collaboration across departments 

Security for AI is a collective effort that goes beyond the IT department. Encourage collaboration among teams like security, IT, legal, compliance, and risk management to create comprehensive security strategies. Having varying perspectives and expertise will enhance the effectiveness of security protocols.

#### Hire diverse skill sets 

Forming a successful security team for AI requires a balance of skills. Look for team members with expertise in data science, cybersecurity, software engineering, and machine learning. This diversity ensures that various aspects of security are covered, from technical development to threat prevention. 

#### Establish clear roles and responsibilities 

For effective productivity, clearly define each team member’s role. Ensure everyone understands their specific responsibilities, which promotes accountability and avoids overlap in efforts. 

#### Invest in continuous training and development 

The rapid evolution of AI technologies mandates ongoing education for security teams. Provide access to training programs and workshops that focus on practices, emerging threats, and ethical considerations related to security for AI. This investment not only empowers team members but also ensures that the organization stays ahead of potential vulnerabilities. 

### Step 2—Optimize resources to secure GenAI 

The introduction of AI applications within organizations isn't only revolutionizing operations but also necessitating significant changes in resource and budget allocation, especially in IT security.  

A significant majority of security and risk leaders (78%) believe their IT security budget will increase to accommodate the unique challenges and opportunities brought about by AI. This adjustment is crucial for several reasons. AI systems require a robust security infrastructure to operate securely. This might involve upgrading existing security systems, implementing more stringent access controls, and enhancing data security and governance. Other resources might also be needed to meet emerging new AI regulatory requirements. 

Earlier in this article, Microsoft recommends doing the work to understand the motivations of business leaders and different business units across your organization. Identifying top concerns and shared business objectives is an important step toward negotiating resources to accomplish the objectives.  

Allocating funds for compliance assessments, legal consultations, and audits become essential to align an organization’s AI strategy to an industry framework and enable more secure, safe, and compliant AI usage and systems. Prioritizing funds for ongoing employee training and skills development, which could include specialized training on security tools for AI, risk management strategies, and ethical considerations in AI use is also important to consider when allocating budget and resources. 

### Step 3—Take a Zero Trust approach 

When preparing for AI adoption, a [Zero Trust](../zero-trust/zero-trust-overview.md) strategy provides security and risk leaders with a set of principles that help address some of their top concerns, including data oversharing or overexposure and shadow IT. A Zero Trust approach shifts from a network-centric focus to an asset and data-centric focus and treats every access request as a potential threat, regardless of its origin.  

Zero Trust constantly validates the identities of every user and device, ensuring that only those with clear permissions can reach sensitive information. By dynamically adjusting security measures based on real-time assessments, Zero Trust minimizes the risk of data leakage and protects an organization from both internal and external threats. Continuous verification, least privilege access, and dynamic risk management are the cornerstones of this approach, providing a robust and adaptable security framework that supports the success of an organization’s end-to-end security.  

By embracing Zero Trust, organizations can secure their AI deployments and know that their security is continuously validated and protected. Zero Trust empowers organizations to embrace AI confidently, ensuring that AI’s powerful capabilities are harnessed safely and effectively. 

All security guidance for AI provided by Microsoft is anchored to Zero Trust principles. By following security guidance recommended for GenAI, you're building a strong Zero Trust foundation.  

### Step 4—Invest in shared responsibility with partners you trust 

A resource that is often used to help inform strategy and priorities is the shared responsibility model. Your responsibility for securing AI use in your organization is based on the type of apps used. The partners you invest in share responsibility with you.  

A shared responsibility model helps security teams guide their organization to choose: 
 - GenAI apps that reduce responsibility for their organizations. 
 - Partners that have earned their trust. 

:::image type="content" source="media/ai-shared-responsibility-model-illustration.svg" alt-text="Diagram that shows the AI shared responsibilities model." lightbox="media/ai-shared-responsibility-model-illustration.svg":::

This diagram summarizes the balance of responsibilities for both you and Microsoft. Many organizations use the shared responsibility model to prioritize use of SaaS apps in partnership with trusted providers and to reduce the number of custom-built apps.

For more information, see [AI shared responsibility model - Microsoft Azure](/azure/security/fundamentals/shared-responsibility-ai). 

In addition to investing with partners that have earned your trust, many security professionals recommend consolidating security tools and vendors. Microsoft offers a comprehensive security solution for AI with tools that work together, greatly reducing the volume of integration work for security teams.

### Step 5—Adopt a comprehensive security solution for AI 

AI introduces specific risks that traditional security measures might not fully address. Security for AI is designed to mitigate these risks.  

A significant majority of companies plan to procure specialized tools and platforms to secure both the usage and development of AI applications. When asked how they plan on securing and protecting the usage and development of AI applications in their organizations, most survey respondents (72%) said they plan to procure a new dedicated security solution to secure the usage and development of AI, while 64% stated they plan to use existing security solutions to secure AI.  

IT and security leaders believe that the primary budget contributors for new solutions for the protection and governance of AI will be IT departments (63%) and information security/ cybersecurity departments (57%). These findings show that in addition to continuing to use existing security solutions, organizations see the need to look for new solutions that can help address the amplified and emerging risks of AI.

On top of Microsoft’s end-to-end security platform, Microsoft provides comprehensive security tooling to secure AI, from discovery of AI tools and data to protections designed specifically to mitigate AI threats. These tools include sophisticated dashboards and compliance resources, helping you stay on top of risks and regulatory obligations.  

This library guides you through the process of implementing security for AI in a staged approach.

:::image type="content" source="media/security-for-ai-step-no-highlight.svg" alt-text="Diagram that shows the process of implementing security for AI.":::

See the following articles:

| Phase | Capabilities |
|----|-----|
| Prepare | |
| Discover | |
| Protect | |
| Govern | |

## Next steps for securing AI 

Follow the guidance in this series of articles to learn more about securing AI and to identify and implement capabilities to achieve your organization’s objectives.  

 - [Prepare for AI](prepare.md) 
 - [Discover AI apps and data](discover.md)
 - [Protect AI data and apps](protect.md)
 - [Govern for AI compliance](govern.md) 

To learn more about optimizing your overall security posture and Zero Trust, see [Rapidly modernize your security posture](../zero-trust/adopt/rapidly-modernize-security-posture.md). 

To get started with recommended security protections for AI companions, see [Use Zero Trust security to prepare for AI companions, including Microsoft Copilots](../zero-trust/copilots/apply-zero-trust-copilots-overview.md).  

