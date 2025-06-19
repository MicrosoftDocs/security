---
title: How do I govern AI apps and data for regulatory compliance?
description: How to use Microsoft capabilities to meet regulatory compliance requirements with AI apps and data. 
ms.date: 04/02/2025
ms.service: security
author: BrendaCarter
ms.author: bcarter
ms.topic: concept-article
ms.collection: 
  - msftsolution-security-for-ai
  - msftsolution-scenario
  - zerotrust-solution
  - magic-ai-copilot



---

# Govern AI apps and data for regulatory compliance

AI regulations and standards are emerging across regions and industries, providing a robust framework for organizations to assess, implement, and test their controls to develop and use trustworthy AI. This article helps risk and compliance teams prepare for the compliance effort. It describes how to:
- Assess and strengthen your compliance posture against regulations.
- Implement controls to govern usage of AI apps and data.

This is the fourth article in a series. If you haven’t yet accomplished the tasks in [Prepare for AI security](prepare.md), [Discover AI apps and data](discover.md), and [Protect AI apps and data](protect.md), start with these articles to prepare your environment with capabilities prescribed in this article.

:::image type="content" source="media/security-for-ai-step-govern.svg" alt-text="Diagram that highlights the Govern from the security for AI articles.":::

Use this article together with these resources:

- Zero Trust adoption framework business scenario—[Meet regulatory and compliance requirements with Zero Trust](../zero-trust/adopt/meet-regulatory-compliance-requirements.md)
- Cloud Adoption Framework (CAF) for AI—[Process to govern AI](/azure/cloud-adoption-framework/scenarios/ai/govern)

## What are new considerations for governing AI apps and data?

Just as AI introduces new attack surfaces which change the risk landscape, AI also introduces new methods of processing and using data that affect regulatory compliance. These new characteristics of AI affect both existing regulations, such as privacy regulations, and new regulations targeted specifically at AI use.

The following illustration highlights emerging AI regulations, including the Artificial intelligence and Data Act (AIDA) in North America, the EU AI Act, the AI Action Plan in Australia, and global standards produced by ISO.

:::image type="content" source="media/world-map-govern.png" alt-text="Screenshot that shows the global standards produced by ISO for AI regulations." lightbox="media/world-map-govern.png":::

Broadly, governing AI for regulatory compliance includes:

- Logging and retaining AI interactions.
- Detecting potential noncompliant usage.
- Using tools, such as eDiscovery on AI interactions, when needed.

This helps organizations meet their compliance requirements and respond to potential litigation effectively.

For organizations building AI, risk and compliance teams need to enable development teams to document their project details, such as model name, version, purpose of the AI systems, and their evaluation metrics for addressing quality, safety, and security risks. This effort can help risk and compliance teams have a standardized format of information to prepare for audits and respond to regulatory requests.

Another best practice is using privacy impact assessments, a control that many companies have already implemented for regulations like the GDPR, to ensure AI apps have all the assessments and controls in place to protect privacy. Microsoft provides capabilities like Priva Privacy Assessments that can be easily integrated into your AI development lifecycle to ensure developers keep privacy top of mind.

Lastly, to build responsible AI applications and adhere to new regulatory requirements, organizations need to create guardrails to detect and block harmful content, such as violence, hate, sexual, and self-harm content. Additionally, you want your AI apps to produce reliable content. The guardrails should help detect and correct incorrect information to reduce the risk of wrongful decisions based on ungrounded output. They should also identify content that violates copyrights. These guardrails can help organizations build responsible and trustworthy AI applications.

## Capabilities for governing AI apps and data

Microsoft includes capabilities to help organizations connect the dots between regulatory standards and technology solutions.

:::image type="content" source="media/security-for-ai-govern-capabilities.svg" alt-text="Diagram that shows capabilities of AI, regulatory standards, and technology solutions." lightbox="media/security-for-ai-govern-capabilities.svg":::

The following steps describe the illustration and also walk through the steps of implementing these capabilities.

| Step | Task | Scope |
| --- | --- | --- |
| 1   | Build and manage assessments in Microsoft Purview Compliance Manager | Enterprise-wide |
| 2   | Use Defender for Cloud Apps to manage AI apps based on compliance risk | SaaS AI apps |
| 3   | Use Cloud Security Posture Management (CSPM) for AI workloads to discover and manage custom-built apps based on compliance risk | Custom-built Azure AI based AI applications |
| 4   | Configure Purview Communication Compliance to minimize communication risks by helping you detect, capture, and act on potentially inappropriate messages in your organization | Microsoft 365 apps and services <br> AI apps connected by Microsoft Entra or Microsoft Purview Data Map connectors <br> Azure AI services |
| 5   | Configure Purview Data Lifecycle Management to retain the content that you need to keep, and delete the content that you don't. | Retention policies for AI apps include user prompts and responses for Microsoft 365 Copilot and Copilot Studio, and also user prompts and responses for other Microsoft copilots and generative AI apps when they have a collection policy with the setting to capture content. These messages can then be retained and deleted for compliance reasons.<br> To integrate AI apps developed on other cloud providers, use the Purview SDK.|
| 6   | Use eDiscovery together with audit logs for Microsoft 365 Copilot for investigations, as needed | Audit logs are automatically generated when a user interacts with Copilot or an AI Application. <br> To integrate AI apps developed on other cloud providers, use the Purview SDK. |
| 7   | Use Priva Privacy Assessments to initiate privacy impact assessments for AI apps you build | Any app, any location |
| 8   | Use AI reports in AI Foundry to document AI project details for apps you develop | AI apps in Azure |
| 9  | Implement Azure AI Content Safety to block harmful content, and detect and correct ungrounded responses | AI apps in Azure |

### Step 1—Build and manage assessments in Microsoft Purview Compliance Manager

Microsoft Purview Compliance Manager is a solution that helps you automatically assess and manage compliance across your multicloud environment. Compliance Manager can help you throughout your compliance journey, from taking inventory of your data protection risks to managing the complexities of implementing controls, staying current with regulations and certifications, and reporting to auditors.

Currently Compliance Manager includes regulatory templates for the following AI-related regulations:

- EU Artificial Intelligence Act
- ISO/IEC 23894:2023
- ISO/IEC 42001:2023
- NIST AI Risk Management Framework (RMF) 1.0

:::image type="content" source="media/eu-ai-act.png" alt-text="Screenshot that shows the EU Artificial Intelligence Act." lightbox="media/eu-ai-act.png":::

Use the following resources to get started with Compliance Manager.

| Task | Recommended resources |
| --- | --- |
| Learn about and get started | [Microsoft Purview Compliance Manager](/purview/compliance-manager) <br> [Get started with Microsoft Purview Compliance Manager](/purview/compliance-manager-setup) <br> [Build and manage assessments in Microsoft Purview Compliance Manager](/purview/compliance-manager-assessments#assessments-for-ai-regulations) |
| See if Compliance Manager includes a template for a regulation | [Regulations list](/purview/compliance-manager-regulations-list) |
| Build a custom assessment | [Build custom assessments (preview) in Microsoft Purview Compliance Manager](/purview/compliance-manager-assessments-custom) |

### Step 2—Use Defender for Cloud Apps

Use Defender for Cloud Apps to manage AI apps based on compliance risk. Previous articles in this series describe how to use Defender for Cloud Apps to discover, manage, and protect use of AI apps. Regulatory compliance introduces extra criteria for triaging and assessing the risk of these apps.

After building one or more assessments for specific regulations in Purview Compliance Manager, work with your Defender for Cloud Apps team to integrate your compliance obligations into the criteria for assessing the risk of AI apps, sanctioning or blocking these apps, and applying session policies to control how these apps can be accessed (for example, with a compliant device only).

See the previous articles in this series to get started with and use Defender for Cloud Apps.

| Task | Recommended resources |
| --- | --- |
| Discover, sanction, and block AI apps with Microsoft Defender for Cloud Apps | See [Step 3 in Discover AI apps and data](discover.md#step-3discover-sanction-and-block-ai-apps-with-microsoft-defender-for-cloud-apps) |
| Use Defender for Cloud Apps to triage and protect use of AI apps | See [Get the most out of threat protection for AI in Protect AI apps and data](protect.md#step-2--Protect-data-through-dspm-for-ai) |

### Step 3—Use Cloud Security Posture Management (CSPM) for AI workloads

Use the Defender Cloud Security Posture Management (CSPM) plan in Microsoft Defender for Cloud to discover and manage custom-built apps based on compliance risk. Just like Defender for Cloud Apps, regulatory compliance introduces extra criteria for triaging and assessing the risk of your custom built apps with CSPM for AI.

Work with your Defender for Cloud team to integrate your compliance obligations into the criteria for assessing the risk of and governing your custom-built apps.

See the previous articles in this series to get started with and use Defender for Cloud.

| Task | Recommended resources |
| --- | --- |
| Discover deployed AI workloads in your environment and gain security insights with Microsoft Defender for Cloud | See [Step 4 in Discover AI apps and data](discover.md#step-4discover-deployed-ai-workloads-in-your-environment-and-gain-security-insights-with-microsoft-defender-for-cloud)] |
| Apply AI protections in Defender for Cloud | See [Step 2 on Get the most out of threat protection for AI in Protect AI apps and data](protect.md#step-2Protect-data-through-dspm-for-ai) |

### Step 4—Configure Purview Communication Compliance

Configure Purview Communication Compliance to minimize communication risks by helping you detect, capture, and act on potentially inappropriate messages in your organization. For Generative AI, you can use communication compliance policies to analyze interactions (prompts and responses) entered into generative AI applications to help detect inappropriate or risky interactions or sharing of confidential information. Coverage is supported for Microsoft 365 Copilot, Copilots built using Microsoft Copilot Studio, AI applications connected by Microsoft Entra or Microsoft Purview Data Map connectors, and more.

Use the following resources to get started.

| Task | Recommended resources |
| --- | --- |
| Learn about and get started. | [Learn about communication compliance](/purview/communication-compliance) <br> [Plan for communication compliance](/purview/communication-compliance-plan) <br> [Get started with communication compliance](/purview/communication-compliance-configure?tabs=purview-portal) |
| Configure policies | [Configure a communication compliance policy to detect for generative AI interactions](/purview/communication-compliance-copilot?tabs=purview-portal) <br> [Create and manage communication compliance policies](/purview/communication-compliance-policies?tabs=purview-portal) |



### Step 5—Configure Purview Data Lifecycle Management

Microsoft Purview Data Lifecycle Management provides you with tools and capabilities to retain the content that you need to keep, and delete the content that you don't. Proactively deleting content you’re no longer required to keep helps reduce the risk of data overexposure in AI tools. Key features include:

- Retention policies and retention labels
- Mailbox archiving and inactive mailboxes—User mailboxes include a hidden folder with Copilot prompts and responses

Use the following resources to get started.

| Task | Recommended resources |
| --- | --- |
| Learn about and get started | [Learn about Microsoft Purview Data Lifecycle Management](/purview/data-lifecycle-management) <br>[Get started with data lifecycle management](/purview/get-started-with-data-lifecycle-management) |
| Learn about retention for Copilot & AI apps  | [Learn how retention works with AI apps](/purview/retention-policies-copilot)  |
| For AI apps developed in other cloud providers, integrate with the Purview SDK | [Learn about the Microsoft Purview SDK](/purview/developer/microsoft-purview-sdk-documentation-overview)  | 

### Step 6—Use eDiscovery together with audit logs for Microsoft 365 Copilot

Use Microsoft Purview eDiscovery to search for keywords in Copilot prompts and responses that might be inappropriate. You can also include this info in an eDiscovery case to review, export, or put this data on hold for an ongoing legal investigation.

Use Microsoft Purview audit logs to identify how, when, and where Copilot interactions occurred and which items were accessed, including any sensitivity labels on those items.

| Task | Recommended resources |
| --- | --- |
| Learn where Copilot usage data is stored and how you can audit it | [Microsoft 365 Copilot data protection and auditing architecture](/copilot/microsoft-365/microsoft-365-copilot-architecture-data-protection-auditing#where-copilot-usage-data-is-stored-and-how-you-can-audit-it) |
| Get started with eDiscovery | [Learn about eDiscovery solutions](/purview/edisc) |
| Learn about Purview audit logs | [Learn about auditing solutions in Microsoft Purview](/purview/audit-solutions-overview) |
|Learn about audit logs for AI apps  | [Learn which admin and user activities are logged for AI apps](/purview/audit-copilot) |
| For AI apps developed in other cloud providers, integrate with the Purview SDK | [Learn about the Microsoft Purview SDK](/purview/developer/microsoft-purview-sdk-documentation-overview)  | 

### Step 7—Use Priva Privacy Assessments

Use Priva Privacy Assessments (preview) to initiate privacy impact assessments for AI apps you build. This helps ensure AI apps are being built in a privacy-respectful way. Privacy Assessments automate the discovery, documentation, and evaluation of personal data use across your entire data estate.

Use the following resources to get started with Priva Privacy Assessments and to initiate a privacy impact assessment.

| Task | Recommended resources |
| --- | --- |
| Learn about and get started | [Learn about privacy assessments](/privacy/priva/privacy-assessments) <br> [Get started with privacy assessments](/privacy/priva/privacy-assessments-setup) |
| Create an assessment | [Create and manage privacy assessments](/privacy/priva/privacy-assessments-create) |

### Step 8—Use AI reports in AI Foundry

AI reports in Azure AI Foundry can help developers document their project details. Developers can create a report that shows all the details of an AI project, such as model cards, model versions, content safety filter configurations, and evaluation metrics. This report can be exported in PDF or SPDX formats, helping development teams demonstrate production readiness within governance, risk, and compliance (GRC) workflows and facilitate easier, ongoing audits of applications in production.

:::image type="content" source="media/azure-ai-studio-reports.png" alt-text="Screenshot that shows AI reports in Azure AI Studio." lightbox="media/azure-ai-studio-reports.png":::

Use the following resources to get started.

| Task | Recommended resources |
| --- | --- |
| Read about AI Reports in AI Foundry (blog) | [AI reports: Improve AI governance and GenAIOps with consistent documentation](https://techcommunity.microsoft.com/blog/aiplatformblog/ai-reports-improve-ai-governance-and-genaiops-with-consistent-documentation/4301914) |
| Learn about and get started with AI Foundry | [What is Azure AI Foundry?](/azure/ai-foundry/what-is-ai-foundry) |

### Step 9—Implement Azure AI Content Safety

Azure AI Content Safety is an AI service that detects harmful user-generated and AI-generated content in applications and services. Azure AI Content Safety includes text and image APIs that allow you to detect material that is harmful. The interactive Content Safety Studio allows you to view, explore, and try out sample code for detecting harmful content across different modalities.

Use the following resources to get started.

| Task | Recommended resources |
| --- | --- |
| Learn about and get started | [What is Azure AI Content Safety? - Azure AI services \| Microsoft Learn](/azure/ai-services/content-safety/overview) <br> [Use Content Safety in Azure AI Foundry portal](/azure/ai-services/content-safety/how-to/foundry) |

## Next step for securing AI
Continue to make progress on end-to-end security with Zero Trust resources:
- [Zero Trust guidance center](/security/zero-trust/)
- [Zero Trust adoption framework](/security/zero-trust/adopt/zero-trust-adoption-overview)
- [Zero Trust deployment plan with Microsoft 365](/microsoft-365/security/microsoft-365-zero-trust)
- [Incident response with XDR and integrated SIEM](/security/zero-trust/siem-xdr-overview)
- [Apply Zero Trust principles to Azure services](/security/zero-trust/apply-zero-trust-azure-services-overview)