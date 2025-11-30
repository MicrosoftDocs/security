---
title: What's new in Microsoft AI security?
description: What are new Microsoft AI security capabilities and blog articles? 
ms.date: 05/19/2025
ms.update-cycle: 180-days
ms.service: security
ms.subservice: security-for-ai
author: guywi-ms
ms.author: guywild
ms.topic: concept-article
ms.collection: 
  - msftsolution-security-for-ai
  - msftsolution-scenario
  - zerotrust-solution
  - msec-ai-copilot
---

# What's new in Microsoft AI security

This article lists new capabilities and resources (blogs and videos) related to Microsoft AI security. 

## November 2025

|Product | Feature updates |  
| ----  | ----------------------------- | 
|Microsoft Agent 365 (Preview)  | [Microsoft Agent 365 is a unified control plane that lets you secure  AI agents across the enterprise](agent-365-security.md)   |
|Microsoft Purview | - [Data Loss Prevention (DLP) enforcement, insider risk management, audit, and compliance for agents](https://techcommunity.microsoft.com/blog/microsoft-security-blog/announcing-new-microsoft-purview-capabilities-to-protect-genai-agents/4470696)<br>- [Enhanced Data Security Posture Management](https://techcommunity.microsoft.com/blog/microsoft-security-blog/beyond-visibility-the-new-microsoft-purview-data-security-posture-management-dsp/4470984)<br>- [Enhanced security for Microsoft 365 Copilot](https://techcommunity.microsoft.com/blog/microsoft-security-blog/announcing-new-microsoft-purview-capabilities-to-protect-genai-agents/4470696) - Including data loss prevention,priority cleanup for M365 Copilot assets, and on-demand classification for meeting transcripts<br>- [AI regulation compliance capabilities](https://techcommunity.microsoft.com/blog/microsoft-security-blog/announcing-new-microsoft-purview-capabilities-to-protect-genai-agents/4470696) - Including AI-powered regulatory templates,visibility into agent activity, monitoring for risky agent prompts and responses, retention and deletion policies for agent-generated content|
|Microsoft Entra  | - [Microsoft Entra Agent ID](/entra/agent-id/identity-platform/what-is-agent-id-platform) - Identity and access management capabilities specifically designed for AI agents, applying Zero Trust principles to autonomous systems.<br>- [Conditional Access for Agent ID (Preview)](/entra/identity/conditional-access/agent-id?tabs=custom-security-attributes) - Extends the same Zero Trust conditional access controls that already protect human users and apps to your agents. <br>- [Microsoft Entra Agent Platform](/entra/agent-id/identity-platform/what-is-agent-id-platform) - A developer-first platform for managing AI agent identities and access<br> - [Microsoft Entra Agent Registry](/entra/agent-id/identity-platform/what-is-agent-registry) -  Provides a complete inventory of all agents used in your organization, including Microsoft and third-party agents. <br> - [Agent risk management in Microsoft Entra ID Protection (Preview)](/entra/id-protection/concept-risky-agents)<br>- [AI Prompt Shield (Preview)](/entra/global-secure-access/how-to-ai-prompt-shield) - Real-time blocking of prompt injection attacks at the network layer<br>- [Specialized roles for Agent ID management](/entra/agent-id/identity-platform/agent-owners-sponsors-managers) |
|Microsoft Defender | [Security posture management and threat protection for agents](https://techcommunity.microsoft.com/blog/microsoft-security-blog/start-secure-and-stay-secure-on-your-ai-agent-journey-with-microsoft-defender/4469430), including:  <br> - [Microsoft Copilot Studio AI agent protection (Preview)](/defender-cloud-apps/ai-agent-protection)<br> - [Security posture management for AI apps and agents](/azure/defender-for-cloud/ai-security-posture)|
|Microsoft Foundry (formerly called Azure AI Foundry)  | [Agent control plane for Microsoft Foundry](/azure/ai-foundry/control-plane/overview?view=foundry): <br> - Secure, observe, and operate agents directly in Microsoft Foundry<br> - Identify code and runtime risks in Microsoft Defender and auto-fix in GitHub with Copilot  |

**Additional blogs, videos, and other resources**
- [Microsoft Agent 365: The control plane for AI agents](https://www.microsoft.com/en-us/microsoft-365/blog/2025/11/18/microsoft-agent-365-the-control-plane-for-ai-agents/)
- [Security as the core primitive in the agentic era: New innovations to secure AI agents and apps](https://techcommunity.microsoft.com/blog/microsoft-security-blog/security-as-the-core-primitive-in-the-agentic-era-new-innovations-to-secure-ai-a/4470197)

## May 2025

|Product | Feature updates |  
| ----  | ----------------------------- | 
|Microsoft Purview | Microsoft Purview capabilities extended to support custom-built AI apps and agents<br> - [Data security and compliance controls through Microsoft Purview native integration with Azure AI Foundry ](https://www.microsoft.com/security/blog/2025/05/19/microsoft-extends-zero-trust-to-secure-the-agentic-workforce/) <br> - [Data security and compliance controls extended to any new custom AI app with Microsoft Purview Software Development Kit (SDK)](https://aka.ms/SecurityforAIBuildnews) <br> - [Purview data protections extended to Copilot Studio agents grounded in Microsoft Dataverse data](https://aka.ms/SecurityforAIBuildnews) <br> - [Purview DSPM for AI can now provide visibility into unauthenticated interactions with Copilot Studio agents](https://techcommunity.microsoft.com/blog/microsoft-security-blog/enterprise-grade-controls-for-ai-apps-and-agents-built-with-azure-ai-foundry-and/4414757) <br> - [Data Loss Prevention (DLP) for Microsoft 365 Copilot Agents](https://aka.ms/SecurityforAIBuildnews) <br> <br>  [Public Preview of DLP for Microsoft 365 Copilot in Word, Excel, and PowerPoint](https://techcommunity.microsoft.com/blog/microsoft-security-blog/announcing-public-preview-of-dlp-for-m365-copilot-in-word-excel-and-powerpoint/4409809) <br> [DSPM discoverability for Communication Compliance (public preview)](https://techcommunity.microsoft.com/blog/microsoft-security-blog/enhance-ai-security-and-governance-across-multi-model-and-multi-cloud-environmen/4395593)
|Microsoft Entra  | [Microsoft Entra Agent ID](https://techcommunity.microsoft.com/blog/microsoft-entra-blog/announcing-microsoft-entra-agent-id-secure-and-manage-your-ai-agents/3827392)—unified directory of all agent identities created across Microsoft Copilot Studio and Azure AI Foundry |
| Defender for Cloud | [Microsoft Defender security alerts and recommendations now available in Azure AI Foundry (Preview)](https://techcommunity.microsoft.com/blog/microsoft-security-blog/enterprise-grade-controls-for-ai-apps-and-agents-built-with-azure-ai-foundry-and/4414757)<br> [General Availability for Defender for AI Services](/azure/defender-for-cloud/release-notes#general-availability-for-defender-for-ai-services) <br>  [General Availability Data and AI security dashboard](/azure/defender-for-cloud/release-notes#general-availability-data-and-ai-security-dashboard)|
|Azure AI Foundry  | [Azure AI Foundry enhancements for model security and safety](https://techcommunity.microsoft.com/blog/microsoft-security-blog/enterprise-grade-controls-for-ai-apps-and-agents-built-with-azure-ai-foundry-and/4414757): <br> - **Spotlighting** to detect and block prompt injection attacks in real time <br> - **Task adherence evaluation and mitigation** to ensure agents remain within scope <br> - **Continuous evaluation and monitoring of agentic system** <br> [Azure AI Foundry evaluation integrations with Microsoft Purview, Credo AI, and Saidot](https://techcommunity.microsoft.com/blog/microsoft-security-blog/enterprise-grade-controls-for-ai-apps-and-agents-built-with-azure-ai-foundry-and/4414757) | 

**Additional blogs, videos, and other resources**
- [Enterprise-grade controls for AI apps and agents built with Azure AI Foundry and Copilot Studio](https://techcommunity.microsoft.com/blog/microsoft-security-blog/enterprise-grade-controls-for-ai-apps-and-agents-built-with-azure-ai-foundry-and/4414757) (May 19, 2025)
- [Microsoft extends Zero Trust to secure the agentic workforce](https://www.microsoft.com/en-us/security/blog/2025/05/19/microsoft-extends-zero-trust-to-secure-the-agentic-workforce/) (May 19, 2025)
- [Announcing Microsoft Entra Agent ID: Secure and manage your AI agents](https://techcommunity.microsoft.com/blog/microsoft-entra-blog/announcing-microsoft-entra-agent-id-secure-and-manage-your-ai-agents/3827392) (May 19, 2025)
- [Microsoft Purview SDK Public Preview](https://techcommunity.microsoft.com/blog/microsoft-security-blog/microsoft-purview-sdk-public-preview/4414240)


## April 2025

|Product | Feature updates |  
| ----  | ----------------------------- | 
|Microsoft Purview and Edge for Business  |[Enhanced Purview data security capabilities for the browser—inline discovery & protection controls](https://techcommunity.microsoft.com/blog/microsoft-security-blog/building-layered-protection-new-microsoft-purview-data-security-controls-for-the/4395071)  |
|Microsoft Purview  | [New data security capabilities for the network—integration with your SASE technology of choice](https://techcommunity.microsoft.com/blog/microsoft-security-blog/building-layered-protection-new-microsoft-purview-data-security-controls-for-the/4395071) <br>  [On-demand classification for SharePoint and OneDrive (public preview)](https://techcommunity.microsoft.com/blog/microsoft-security-blog/protecting-sensitive-information-in-the-era-of-ai-with-microsoft-purview-informa/4395541) <br>  [Protection policies for Azure SQL, Data Lake, and Blob Storage (public preview)](https://techcommunity.microsoft.com/blog/azurestorageblog/microsoft-purview-protection-policies-for-azure-data-lake--blob-storage-availabl/4382887)  <br> [Optical character recognition enhancements](https://techcommunity.microsoft.com/blog/microsoft-security-blog/protecting-sensitive-information-in-the-era-of-ai-with-microsoft-purview-informa/4395541) <br>  [Dynamic watermarking in Word, Excel, and PowerPoint (general availability)](https://techcommunity.microsoft.com/blog/microsoft-security-blog/general-availability-dynamic-watermarking-for-sensitivity-labels-in-word-excel-a/4382614) | 
|Microsoft Entra Internet Access  |[Granular access controls for generative AI apps](https://techcommunity.microsoft.com/blog/microsoft-entra-blog/new-innovations-in-microsoft-entra-to-strengthen-ai-security-and-identity-protec/3827393) |
| Defender for Cloud | [AI Posture Management in GCP vertex AI (Preview)](/azure/defender-for-cloud/release-notes#ai-posture-management-in-gcp-vertex-ai-preview)|


**Additional blogs, videos, and other resources**
- [Microsoft 365 Copilot: Built for the era of human–agent collaboration](https://www.microsoft.com/en-us/microsoft-365/blog/2025/04/23/microsoft-365-copilot-built-for-the-era-of-human-agent-collaboration/)
- [RSAC™ 2025: Unveiling new innovations in cloud and AI security](https://techcommunity.microsoft.com/blog/microsoftdefendercloudblog/rsac%E2%84%A2-2025-unveiling-new-innovations-in-cloud-and-ai-security/4408140)
- [How to use DSPM for AI Data Risk Assessment to Address Internal Oversharing](https://techcommunity.microsoft.com/blog/microsoft-security-blog/how-to-use-dspm-for-ai-data-risk-assessment-to-address-internal-oversharing/4399785)
- [Explore practical best practices to secure your data with Microsoft Purview](https://www.microsoft.com/en-us/security/blog/2025/04/25/explore-practical-best-practices-to-secure-your-data-with-microsoft-purview/) 
- [Enhance AI security and governance across multi-model and multi-cloud environments](https://techcommunity.microsoft.com/blog/microsoft-security-blog/enhance-ai-security-and-governance-across-multi-model-and-multi-cloud-environmen/4395593)


## Additional what's new resources

- [What's new in Microsoft Purview](/purview/whats-new)
- [What's new in Compliance Manager](/purview/compliance-manager-whats-new)
- [What's new in Microsoft Priva](/privacy/priva/priva-whats-new)
- [What's new in Microsoft Defender for Cloud Apps](/defender-cloud-apps/release-notes)
- [What's new in Defender for Cloud](/azure/defender-for-cloud/release-notes)
- What's new in Azure AI Foundry: [Azure AI Foundry blog](https://devblogs.microsoft.com/foundry/)
- [What's new in Azure AI Content Safety](/azure/ai-services/content-safety/whats-new)