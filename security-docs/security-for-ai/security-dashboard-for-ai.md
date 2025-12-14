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

This article explains the core capabilities of the Security Dashboard for AI and how to use the dashboard effectively to manage AI security across your enterprise.

## End-to-end AI security visibility and management

Security Dashboard for AI provides a real-time view of AI security posture and risk across Microsoft Security solutions - including Microsoft Entra, Microsoft Purview, and Microsoft Defender - enabling proactive governance and reactive threat protection. This lets security teams keep using the tools they trust while empowering security leaders to govern and collaborate seamlessly.

The dashboard provides:

- **Real-time visibility of AI risk**: Aggregated insights across Microsoft Entra, Defender, and Purview.
- **Comprehensive inventory of AI assets**: The dashboard covers Microsoft AI solutions - including Microsoft 365 Copilot, Microsoft Copilot Studio agents, and Microsoft Foundry apps and agents - as well as third-party AI models, applications, and agents such as Google Gemini, OpenAI ChatGPT, and MCP servers.
- **Recommendations and remediation paths**: Direct integration with Microsoft productivity tools and practitioner portals.
- **AI-powered insights**: Leverages Security Copilot for intelligent risk assessment and recommendations.  
- **Executive reporting**: Board-ready analytics and compliance insights.

<br>

:::image type="content" source="media/security-dashboard-for-ai/security-for-ai-dashboard-overview.png" alt-text="A screenshot showing the Overview page of the Security Dashboard for AI." lightbox="media/security-dashboard-for-ai/security-for-ai-dashboard-overview.png":::

## How Security Dashboard for AI works

Security Dashboard for AI requires no additional licensing beyond the underlying Microsoft Security products. It's available to all customers to support secure, and govern AI deployments.

Microsoft Security and partner products provide the sensors and signals the dashboard uses. If a required service isn’t deployed, the dashboard guides you on which capabilities are missing and how to strengthen AI security.

**Supported products:**


| **Product**      | **Key capabilities**                                                                 |
|----------------------------|--------------------------------------------------------------------------------------|
| **Microsoft Entra**        | <ul><li>**Identity management**: Centralized user and application identity governance</li><li>**Conditional access**: Risk-based access controls for AI applications</li><li>**Privileged identity management**: Elevated access monitoring and control</li></ul> |
| **Microsoft Defender**     | <ul><li>**Threat protection**: Real-time monitoring of AI workloads and endpoints</li><li>**Cloud security posture**: Infrastructure vulnerability assessment</li><li>**App security**: SaaS AI application risk evaluation</li></ul> |
| **Microsoft Purview**      | <ul><li>**Data classification**: Automated labeling and protection of AI-accessible data</li><li>**Data loss prevention**: Prevent sensitive information exposure through AI</li><li>**Insider risk management**: Detect anomalous AI usage patterns</li></ul> |
| **Microsoft Security Copilot**| <ul><li>**Prompt-based exploration**: Explore AI risks, agent activity, and security recommendations via prompts</li><li>**Enhanced AI risk insights**: Aggregates signals across Microsoft and partner security solutions for deeper analysis</li><li>**Enhanced agent discovery and categorization**: Improves identification of managed, unmanaged, and shadow AI agents to strengthen your AI security posture</li></ul> |


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
| **Agent ID Administrator** | View recommendations for communication compliance, insider risk, DLP and data related to identity and access risk |

For more information about Microsoft Entra roles, see [Microsoft Entra built-in roles](/entra/identity/role-based-access-control/permissions-reference).

## Review and delegate security recommendations

The **Overview** page of the dashboard provides key insights about your AI assets and related security risks. It also assesses your organization's implementation of Microsoft security for AI capabilities and provides recommendations for improving your organization's AI security posture. To delegate the implementation of these recommendations to a specific group or user:

1. Select a recommendation on the **Overview** page.

   :::image type="content" source="media/security-dashboard-for-ai/security-dashboard-for-ai-delegate-recommendation.png" alt-text="A screenshot showing the Overview page with one of the security recommendations highlighted." lightbox="media/security-dashboard-for-ai/security-dashboard-for-ai-delegate-recommendation.png":::

1. On the recommendation details page, select **Delegate**.

   :::image type="content" source="media/security-dashboard-for-ai/security-dashboard-for-ai-recommendation-details.png"  alt-text="A screenshot showing the recommendation details page with the Delegate button highlighted." lightbox="media/security-dashboard-for-ai/security-dashboard-for-ai-recommendation-details.png"::: 

1. On the **Delegate to** page, select a user or group to assign the recommendation to and click **Select**.
1. Select the Microsoft Outlook or Microsoft Teams icons to notify the assignee of the delegated recommendation. Select the ellipsis (...) next to the icons to remove or change the delegation.

## Review AI inventory and manage security risks

The **AI inventory** page of the dashboard provides detailed views to help you discover AI assets, assess risks, and implement remediation actions across all of the AI agents, AI models, and MCP servers, and AI applications in your organization.

### AI agents 

View and manage all AI agents operating in your environment, including key insights from the [Microsoft Entra Agent Registry](/entra/agent-id/identity-platform/what-is-agent-registry) and [Microsoft Purview Data Security Posture Management (DSPM) for AI](/purview/dspm-for-ai).

:::image type="content" source="media/security-dashboard-for-ai/security-dashboard-for-ai-inventory.png" alt-text="A screenshot showing the Agents tab of the AI inventory page of Security Dashboard for AI." lightbox="media/security-dashboard-for-ai/security-dashboard-for-ai-inventory.png":::

Select an AI agent to:
- View agent details and activities. Select **View all activities** to open the [Activity Explorer in DSPM for AI](/purview/dspm-for-ai-considerations#activity-explorer-events) and review agent activity related to content that contains sensitive information or has labels applied.

   :::image type="content" source="media/security-dashboard-for-ai/security-dashboard-for-ai-agent-overview.png" alt-text="A screenshot showing the Agent Overview page of the AI inventory page of Security Dashboard for AI." lightbox="media/security-dashboard-for-ai/security-dashboard-for-ai-agent-overview.png":::

- Review and apply security recommendations specific to the selected agent.

   :::image type="content" source="media/security-dashboard-for-ai/security-dashboard-for-ai-agent-recommendations.png" alt-text="A screenshot showing the Agent Recommendations page of the AI inventory page of Security Dashboard for AI." lightbox="media/security-dashboard-for-ai/security-dashboard-for-ai-agent-recommendations.png":::


### AI models

### MCP servers

### Other AI applications


Access comprehensive visibility into all AI applications and agents across your environment.

**Discovery Capabilities:**
- **Managed AI Applications** - Microsoft-native AI solutions with full governance
- **Unmanaged AI Applications** - Shadow AI and unapproved applications  
- **Third-party AI Solutions** - External AI services and platforms
- **Agent Classification** - Automated categorization by function and risk level

**Asset Details:**
- **Application Profiles** - Detailed information about each AI asset
- **Usage Patterns** - User behavior and access analytics
- **Data Access** - Information about data sources and permissions
- **Security Configuration** - Current protection status and gaps

## View and prioritize AI-related security risks across your organization

The **AI risk** page of the dashboard provides a consolidated view of AI-related security risks, enabling you to prioritize and address threats effectively. Each risk category links directly to the relevant Microsoft Security product for remediation.

:::image type="content" source="media/security-dashboard-for-ai/ security-dashboard-for-ai-risks.png.png" alt-text="A screenshot showing the AI risk page of the Security Dahboard for AI." lightbox="media/security-dashboard-for-ai/ security-dashboard-for-ai-risks.png.png":::

**Risk Categories:**

| **Risk category** | **Subcategory** | **Description** | **Managed by** |
|---|---|---|---|
| **Identity and access risks** | - | Authentication and authorization vulnerabilities across AI platforms | [Microsoft Entra](https://entra.microsoft.com) |
| **Data security risks** | Exfiltration by platform | Unauthorized data extraction through AI applications | [Microsoft Purview](/purview/ai-microsoft-purview)|
| | Oversharing by platform | Excessive data exposure via AI platform interactions | [Microsoft Purview](/purview/ai-microsoft-purview)|
| | Unethical activity by platform | Inappropriate or harmful AI usage patterns | |
| **Cloud security risks** | Misconfiguration by platform | Infrastructure and security setting errors in AI deployments | [Microsoft Defender](https://security.microsoft.com) |
| | Attack paths by platform | Potential exploitation routes through AI infrastructure | |


## Security Copilot Integration

Leverage AI-powered insights for enhanced security intelligence and decision-making.

**Natural Language Queries:**
- Ask questions about AI risks using conversational prompts
- Explore agent activity and security recommendations
- Generate insights by aggregating signals across security solutions

**Guided Prompts:**
- **Risk Exploration** - "What are the highest priority AI risks in my environment?"
- **Agent Discovery** - "Show me all unmanaged AI agents accessing sensitive data"
- **Remediation Guidance** - "What steps should I take to reduce data leakage risks?"
- **Compliance Assessment** - "Are there any AI applications violating our data policies?"

**AI-Generated Insights:**
- **Risk Summaries** - Automated analysis of complex security data
- **Trend Identification** - Pattern recognition across multiple data sources
- **Recommendation Prioritization** - Intelligent ranking of security actions

## Detailed Operational Workflows

### Discovering AI Assets

1. **Navigate to AI Inventory**
   - Access the inventory section from the main dashboard
   - Review the complete list of discovered AI applications and agents

2. **Apply Filters and Search**
   - Use filters to focus on specific asset types or risk levels
   - Search for particular applications or business units
   - Sort by discovery date, risk score, or usage frequency

3. **Investigate Asset Details**
   - Click on any AI asset to view detailed information
   - Review security configuration and compliance status
   - Analyze user access patterns and data interactions

4. **Export Inventory Data**
   - Generate comprehensive reports for stakeholder review
   - Export filtered views for targeted analysis
   - Schedule regular inventory updates

### Assessing and Managing Risks

1. **Risk Dashboard Analysis**
   - Review risk summary cards for immediate priorities
   - Examine trend charts to identify emerging threats
   - Use Security Copilot to explore complex risk scenarios

2. **Individual Risk Investigation**
   - Click on specific risks for detailed analysis
   - Review affected assets and potential business impact
   - Understand the root cause and attack vectors

3. **Remediation Planning**
   - Follow recommended remediation steps
   - Assign responsibilities to appropriate teams
   - Set timelines and track progress

4. **Validation and Monitoring**
   - Verify that remediation actions are effective
   - Monitor for similar risks across other assets
   - Update security policies based on lessons learned
