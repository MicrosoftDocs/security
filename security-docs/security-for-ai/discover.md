---
title: How do I discover AI apps and the sensitive data these use in my organization?
description: How to use Microsoft capabilities to discover AI apps and data use in your environment. 
ms.date: 04/01/2025
ms.service: security
author: BrendaCarter
ms.author: bcarter
ms.topic: concept-article
ms.collection: 
  - msftsolution-security-for-ai
  - msftsolution-scenario
  - zerotrust-solution



---

# Discover AI apps and data

Generative AI (GenAI) is being adopted at an unprecedented rate as organizations actively engage with or experiment with GenAI in various capacities. Security teams can mitigate and manage risks more effectively by proactively gaining visibility into AI usage within the organization and implementing corresponding controls. This article describes how to discover AI app use within your organization, including assessing the risk to your sensitive data. 

This is the second article in a series. Before using this article, be sure you accomplished the tasks in [Prepare for AI security](prepare.md) to prepare your environment with capabilities prescribed in this article. 

:::image type="content" source="media/security-for-ai-step-discover.svg" alt-text="Diagram that shows the second article in series of security for ai, that is Discover.":::

Microsoft provides tools to help you gain visibility into data, access, user, and application risks for the AI you build and use. These capabilities help you proactively address vulnerabilities while you build a strong security posture for AI. 

:::image type="content" source="media/security-for-ai-discover-capabilities.svg" alt-text="Diagram that shows the capabilities of dicovering AI.":::

The following table describes the illustration and also walks through the steps of implementing these capabilities. 

| Step | Task | Scope |
| --- | --- | --- |
| 1   | Gain visibility into AI usage Microsoft Purview Data Security Posture Management (DSPM) for AI. Apply policies to protect sensitive data. | Microsoft Copilots <br>[Supported AI sites](/purview/ai-microsoft-purview-supported-sites) |
| 2   | Discover, sanction, and block AI apps with Microsoft Defender for Cloud Apps | SaaS AI apps |
| 3   | Discover deployed AI workloads in your environment and gain security insights with Microsoft Defender for Cloud Security Posture Management (CSPM) | Custom-built Azure AI based AI applications |

## Step 1—Gain visibility into AI usage with Data Security Posture Management (DSPM) for AI

Microsoft Purview Data Security Posture Management (DSPM) for AI focuses on how AI is used in your organization, especially how your data interacts with AI tools. It works with generative AI sites. DSPM for AI provides deeper insights for Microsoft Copilots and third-party SaaS applications like ChatGPT Enterprise and Google Gemini.

The following diagram shows one of the aggregated views into the impact of AI use on your data—Sensitive interactions per generative AI app.

:::image type="content" source="media/ai-hub-sensitive-interactions-report.png" alt-text="Screenshot of the sensitive interactions per generative AI app.":::

DSPM for AI offers a set of capabilities that help you safely adopt AI without having to choose between productivity and protection:

- Insights and analytics into AI activity in your organization
- Ready-to-use policies to protect data and prevent data loss in AI prompts
- Data assessments to identify, remediate, and monitor potential oversharing of data
- Recommended actions based on data in your tenant
- Compliance controls to apply optimal data handling and storing policies

To monitor interactions with third-party AI sites, devices must be onboarded to Microsoft Purview. If you followed the guidance in [Prepare for AI security](prepare.md), you enrolled devices into management with Microsoft Intune, then onboarded these devices into Defender for Endpoint. Device onboarding is shared across Microsoft 365 (including Microsoft Purview) and Microsoft Defender for Endpoint (MDE).

Use the following resources to discover AI apps and data with DSPM for AI.

| Task | Recommended resources |
| --- | --- |
| Ensure devices are onboarded to Microsoft Purview. | If devices aren't yet onboarded to Defender for Endpoint, there are several methods to get them onboarded. See, [Onboard Windows devices into Microsoft 365](/purview/device-onboarding-overview). |
| Understand prerequisites and how DSPM for AI works | [Considerations for deploying Microsoft Purview Data Security Posture Management for AI](/purview/ai-microsoft-purview-considerations) |
| Start using DSPM for AI | [How to use Data Security Posture Management for AI](/purview/ai-microsoft-purview#how-to-use-data-security-posture-management-for-ai) |
| Review supported AI sites | [Supported AI sites by Microsoft Purview for data security and compliance protections](/purview/ai-microsoft-purview-supported-sites) |

## Step 2—Discover, sanction, and block AI apps with Microsoft Defender for Cloud Apps

Microsoft Defender for Cloud Apps helps security teams discover SaaS GenAI apps and usage.

The Defender for Cloud Apps app catalog includes a Generative AI category for large language model (LLM) apps, like Microsoft Bing Chat, Google Bard, ChatGPT, and more. Defender for Cloud Apps has added more than a thousand generative AI-related apps to the catalog, providing visibility into how generative AI apps are used in your organization and helping you manage them securely.

:::image type="content" source="media/generative-ai.png" alt-text="Screenshot of searching apps in cloud app catalogue.":::

With Defender for Cloud Apps, you can:

- Filter on Generative AI apps
- Discover the AI apps which are used at your organization
- View out-of-the-box risk assessments for each app, including 90+ risk factors across security and regulatory compliance
- Sanction or unsanction (block) the usage of specific apps
- Create policies that continue to discover AI apps based on criteria you set, including risk score, number of users per day, and others. You can even automatically unsanction apps that meet the criteria.

:::image type="content" source="media/cloud-discovery-defender-cloud-apps.png" alt-text="Screenshot of the Cloud Discovery page in the Microsoft Defender.":::

Use the following resources for next steps.

| Task | Recommended resources |
| --- | --- |
| Pilot and deploy Defender for Cloud Apps | [How do I pilot and deploy Microsoft Defender for Cloud Apps?](/defender-xdr/pilot-deploy-defender-cloud-apps?toc=%2Fsecurity%2Fzero-trust%2Ftoc.json&bc=%2Fsecurity%2Fbreadcrumb%2Ftoc.json#step-5-discover-and-manage-cloud-apps) |
| Review this video tutorial | [Discover Which Generative AI Apps Are Used in Your Environment Using Defender for Cloud Apps](https://www.youtube.com/watch?v=ZQI4A7W4E_4) |
| View discovered apps | [View discovered apps with the Cloud discovery dashboard](/defender-cloud-apps/discovered-apps) |
| Find your cloud app and calculate risk score | [Cloud app catalog and risk scores - Microsoft Defender for Cloud Apps](/defender-cloud-apps/risk-score) |
| Govern discovered apps | [Govern discovered apps - Microsoft Defender for Cloud Apps](/defender-cloud-apps/governance-discovery) |

## Step 3—Discover deployed AI workloads in your environment and gain security insights with Microsoft Defender for Cloud

The Defender Cloud Security Posture Management (CSPM) plan in Microsoft Defender for Cloud provides AI security posture management capabilities, starting with discovery of AI Apps built in your environments:

- Discovering generative AI Bill of Materials (AI BOM), which includes application components, data, and AI artifacts from code to cloud.
- Strengthening generative AI application security posture with built-in recommendations and by exploring and remediating security risks.
- Using the attack path analysis to identify and remediate risks.

Use the cloud security explorer to identify generative AI workloads and models running in your environment. Cloud security explorer includes preconfigured queries:

- AI workloads and models in use
- Generative AI vulnerable code repositories that provision Azure OpenAI
- Containers running container images with known Generative AI vulnerabilities.

:::image type="content" source="media/defender-for-cloud.png" alt-text="Screenshot of the AI workloads and models in use ":::

You can also configure your own queries.

:::image type="content" source="media/defender-for-cloud-configure.png" alt-text="Screenshot of the configuration page to configure own queries.":::

Use the following resources for next steps.

| Task | Recommended resources |
|---|---|
| Learn about AI security posture management | [AI security posture management with Defender for Cloud](/azure/defender-for-cloud/ai-security-posture)|
|Discover AI workloads | [AI workloads and models in use](/azure/defender-for-cloud/identify-ai-workload-model)|
|Explore risks to predeployment generative AI artifacts |[Risks to predeployment generative AI artifacts](/azure/defender-for-cloud/explore-ai-risk)|

## Next step for securing AI

After discovering the AI usage in your organization, the next step is to apply protections:

- Protect sensitive data used with AI apps
- Implement threat protection specifically for AI use

See the next article in this series: [How do I protect my organization while using AI apps?](protect.md).