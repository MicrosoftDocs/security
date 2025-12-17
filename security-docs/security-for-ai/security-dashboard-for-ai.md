---
title: Assess your organization's AI risk with Microsoft Security Dashboard for AI (Preview)
description: Use the Microsoft Security Dashboard for AI dashboard to discover, assess, and mitigate AI risks across your organization.
ms.date: 12/05/2025
ms.update-cycle: 90-days
ms.service: security
ms.subservice: security-for-ai
author: guywi-ms
ms.author: guywild
ms.topic: concept-article
ms.collection: 
  - msftsolution-security-for-ai
  - msftsolution-overview
  - zerotrust-solution
  - msec-ai-copilot
---

# Assess your organization's AI risk with Microsoft Security Dashboard for AI (Preview)

[Microsoft Security Dashboard for AI](https://ai.security.microsoft.com) is a unified security dashboard that helps security leaders understand and address the AI risk in their organization. The dashboard equips leadership with a governance tool that provides clear and comprehensive AI security insights and answers the most pressing questions about AI risk, including:

- Which AI assets exist in our environment?
- What’s their current security posture?
- Where must we take action?

This article explains the core capabilities of the Security Dashboard for AI and how to use the dashboard to manage AI security across your enterprise.

## End-to-end AI security visibility and management

Security Dashboard for AI provides a real-time view of AI security posture and risk across Microsoft Security solutions - including Microsoft Entra, Microsoft Purview, and Microsoft Defender - enabling proactive governance and reactive threat protection. This lets security teams keep using the tools they trust while empowering security leaders to govern and collaborate seamlessly.

The dashboard provides:

- **Real-time visibility of AI risk**: Aggregated insights across Microsoft Entra, Defender, and Purview.
- **Comprehensive inventory of AI assets**: The dashboard covers Microsoft AI solutions - including Microsoft 365 Copilot, Microsoft Copilot Studio agents, and Microsoft Foundry apps and agents - as well as third-party AI models, applications, and agents such as Google Gemini, OpenAI ChatGPT, and MCP servers.
- **Recommendations and remediation paths**: Direct integration with Microsoft productivity tools and practitioner portals.
- **AI-powered insights**: Microsoft Security Copilot provides suggested prompts that help you drill down to key insights, and quickly access intelligent risk assessments, summaries, and recommendations.  
- **Executive reporting**: Board-ready analytics and compliance insights.

<br>

:::image type="content" source="media/security-dashboard-for-ai/security-for-ai-dashboard-overview.png" alt-text="A screenshot showing the Overview page of the Security Dashboard for AI." lightbox="media/security-dashboard-for-ai/security-for-ai-dashboard-overview.png":::

## How Security Dashboard for AI works

Security Dashboard for AI doesn't require any special licensing beyond the underlying Microsoft Security products. It's available to all customers to support secure, and govern AI deployments.

Microsoft Security and partner products provide the sensors and signals the dashboard uses. If you haven't deployed a required service, the dashboard guides you on which capabilities are missing and how to strengthen your AI security.

**Supported products:**


| **Product**      | **Key capabilities and dashboard insights**                                                                 |
|----------------------------|--------------------------------------------------------------------------------------|
| **Microsoft Entra**        | <ul><li>**Identity management**: Centralized user and application identity governance</li><li>**Conditional access**: Risk-based access controls for AI applications</li><li>**Privileged identity management**: Elevated access monitoring and control</li></ul> For more information, see [What is Microsoft agent identity platform](/entra/agent-id/identity-platform/what-is-agent-id-platform).|
| **Microsoft Defender**     | <ul><li>**Threat protection**: Real-time monitoring of AI workloads and endpoints</li><li>**Cloud security posture**: Infrastructure vulnerability assessment</li><li>**App security**: SaaS AI application risk evaluation</li></ul> For more information, see [Microsoft Defender AI security posture management](/azure/defender-for-cloud/ai-security-posture).|
| **Microsoft Purview**      | <ul><li>**Data classification**: Automated labeling and protection of AI-accessible data</li><li>**Data loss prevention**: Prevent sensitive information exposure through AI</li><li>**Insider risk management**: Detect anomalous AI usage patterns</li></ul> For more information, see [Microsoft Purview data security and compliance protections for generative AI apps](/purview/ai-microsoft-purview). |
| **Microsoft Security Copilot**| <ul><li>**Prompt-based exploration**: Explore AI risks, agent activity, and security recommendations via prompts</li><li>**Enhanced AI risk insights**: Aggregate signals across Microsoft and partner security solutions for deeper analysis</li><li>**Enhanced agent discovery and categorization**: Improve identification of managed, unmanaged, and shadow AI agents to strengthen your AI security posture</li></ul> For more information, see [What is Microsoft Security Copilot?](/copilot/security/microsoft-security-copilot)|


## Permissions

 By default, only Global Administrators have access to all dashboard data. This table outlines the data access levels for Microsoft Entra built-in roles:

| Role | Dashboard access |
|:-----|:-----------------|
| **Global Administrator** | View all data |
| **AI Administrator** | View all data except Microsoft Entra conditional access, Microsoft Purview audit, and most Microsoft Defender capabilities |
| **Compliance Administrator** | View all data except Microsoft Entra conditional access and some Microsoft Defender data |
| **Security Administrator** | View all data except Microsoft Purview audit and app governance recommendations |
| **Global Reader** | View all data except app governance recommendations |
| **Agent Registry Administrator** | View recommendations for communication compliance, insider risk, DLP |
| **Agent ID Administrator** | View recommendations for communication compliance, insider risk, DLP, and data related to identity and access risk |

For more information about Microsoft Entra roles, see [Microsoft Entra built-in roles](/entra/identity/role-based-access-control/permissions-reference).

## Review and delegate security recommendations

The **Overview** page of the dashboard provides key insights about your AI assets and related security risks. It also assesses your organization's implementation of Microsoft security for AI capabilities and provides recommendations for improving your organization's AI security posture. 

These roles can view security recommendations and delegate tasks on the **Overview** page:

| Recommendation category | Global Administrator | AI Administrator | Compliance Administrator | Security Administrator | Global Reader |
|:------------------------|:---------------------|:-----------------|:-------------------------|:-----------------------|:--------------|
| **Prevent agent sprawl and unauthorized access** (Microsoft Entra) | ✅ | ✅ | ✅ | ✅ Except configure global collection in Entra agent registry | ✅ |
| **Prevent data leaks and oversharing** (Microsoft Purview) | ✅ | ✅ Except turn on audit | ✅ | ✅ Except turn on audit | ✅ |
| **Address AI risk and vulnerability** (Microsoft Defender) | ✅ | ✅ | ✅ | ✅ Except enable app governance | ✅ |


To delegate the implementation of these recommendations to a specific group or user:

1. Select a recommendation on the **Overview** page.

   :::image type="content" source="media/security-dashboard-for-ai/security-dashboard-for-ai-delegate-recommendation.png" alt-text="A screenshot showing the Overview page with one of the security recommendations highlighted." lightbox="media/security-dashboard-for-ai/security-dashboard-for-ai-delegate-recommendation.png":::

1. On the recommendation details page, select **Delegate**.

   :::image type="content" source="media/security-dashboard-for-ai/security-dashboard-for-ai-recommendation-details.png"  alt-text="A screenshot showing the recommendation details page with the Delegate button highlighted." lightbox="media/security-dashboard-for-ai/security-dashboard-for-ai-recommendation-details.png"::: 

1. On the **Delegate to** page, select a user or group to assign the recommendation to and click **Select**.
1. Select the Microsoft Outlook or Microsoft Teams icons to notify the assignee of the delegated recommendation. Select the ellipsis (...) next to the icons to remove or change the delegation.

## Explore AI assets and manage asset security risks 

The **AI inventory** page of the dashboard provides detailed views to help you discover AI assets, assess risks, and implement remediation actions across all of the AI agents, AI models, and MCP servers, and AI applications in your organization.

These roles can view data on the **AI Inventory** page:

| Asset type | Global Administrator | AI Administrator | Compliance Administrator | Security Administrator | Global Reader |
|:-----------|:---------------------|:-----------------|:-------------------------|:-----------------------|:--------------|
| **AI agents** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **AI models** | ✅ | ❌ | ❌ | ✅ | ✅ |
| **MCP servers** | ✅ | ❌ | ✅ | ✅ | ✅ |
| **Other AI apps** | ✅ | ❌ | ✅ | ✅ | ✅ |

To discover and manage AI asset security risks:

1. Select **AI Inventory** review the complete list of discovered AI applications and agents.
1. Apply filters to focus on specific asset types or risk levels.
1. Select any AI asset to view detailed information, review security configuration and compliance status, and analyze user access patterns and data interactions.
1. Select **Export** to export filtered views for targeted analysis and reporting.
   
### AI agents 

The **AI agents** tab of the **AI inventory** page presents all of the AI agents operating in your environment and provides key insights from the [Microsoft Entra Agent Registry](/entra/agent-id/identity-platform/what-is-agent-registry) and [Microsoft Purview Data Security Posture Management (DSPM) for AI](/purview/data-security-posture-management-learn-about).

:::image type="content" source="media/security-dashboard-for-ai/security-dashboard-for-ai-inventory.png" alt-text="A screenshot showing the Agents tab of the AI inventory page of Security Dashboard for AI." lightbox="media/security-dashboard-for-ai/security-dashboard-for-ai-inventory.png":::

Select an AI agent to:
- View agent details and activities. Select **View all activities** to open the [Activity Explorer in DSPM for AI](/purview/data-security-posture-management-considerations#activity-explorer-events-in-data-security-posture-management) and review agent activity related to content that contains sensitive information or has labels applied.

   :::image type="content" source="media/security-dashboard-for-ai/security-dashboard-for-ai-agent-overview.png" alt-text="A screenshot showing the Agent Overview page of Security Dashboard for AI." lightbox="media/security-dashboard-for-ai/security-dashboard-for-ai-agent-overview.png":::

- Review and apply security recommendations for protecting sensitive data in agent activities.

   :::image type="content" source="media/security-dashboard-for-ai/security-dashboard-for-ai-agent-recommendations.png" alt-text="A screenshot showing the Agent Recommendations page of Security Dashboard for AI." lightbox="media/security-dashboard-for-ai/security-dashboard-for-ai-agent-recommendations.png":::


### AI models

The **AI models** tab of the **AI inventory** page presents all of the AI models in use across your organization. Select **Show more in Defender** to open the [Microsoft Defender cloud asset inventory](/azure/defender-for-cloud/asset-inventory?pivots=defender-portal) for detailed information and risk mitigation.

:::image type="content" source="media/security-dashboard-for-ai/security-dashboard-for-ai-models.png" alt-text="A screenshot showing the AI models page of Security Dashboard for AI." lightbox="media/security-dashboard-for-ai/security-dashboard-for-ai-models.png":::


### MCP servers and other AI applications

View and manage the security of all AI models in use across your organization. Select **Show more in Defender** to open the [Microsoft Defender for Cloud Apps applications inventory](/defender-cloud-apps/applications-inventory)for detailed information and risk mitigation.


:::image type="content" source="media/security-dashboard-for-ai/security-dashboard-for-ai-mcp-and-other-ai-apps.png" alt-text="A screenshot showing the Other AI apps page of Security Dashboard for AI." lightbox="media/security-dashboard-for-ai/security-dashboard-for-ai-mcp-and-other-ai-apps.png":::

## View and prioritize AI security risks across your organization

The **AI risk** page of the dashboard provides a consolidated view of AI-related security risks, enabling you to prioritize and address threats effectively. Each risk category links directly to the relevant Microsoft Security product for remediation.

These roles can view data on the **AI risk** page:

| Risk category | Global Administrator | AI Administrator | Compliance Administrator | Security Administrator | Global Reader |
|:--------------|:---------------------|:-----------------|:-------------------------|:-----------------------|:--------------|
| **Identity and access risk** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Data security risk** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Cloud security risk** | ✅ | ❌ | ✅ | ✅ | ✅ |
| **Misconfigurations and Attack Paths** | ✅ | ❌ | ❌ | ✅ | ✅ |
| **Agents with Sensitive Interactions** | ✅ | ✅ | ✅ | ✅ | ✅ |

To investigate and remediate AI security risks:

1. Review risk summary cards for immediate priorities, examine trend charts to identify emerging threats, and use Microsoft Security Copilot's suggested prompts to explore complex risk scenarios.
1.  Select **View in Microsoft Purview** or **View in Microsoft Defender** to navigate to the relevant Microsoft Security product for detailed risk analysis and remediation. 

:::image type="content" source="media/security-dashboard-for-ai/security-dashboard-for-ai-risks.png" alt-text="A screenshot showing the AI risk page of the Security Dashboard for AI." lightbox="media/security-dashboard-for-ai/security-dashboard-for-ai-risks.png":::





