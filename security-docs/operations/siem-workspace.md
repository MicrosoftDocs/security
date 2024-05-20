---
title: Step 2. Architect your Microsoft Sentinel workspace
description: Learn how to design for and implement Zero Trust principles for your Microsoft Sentinel workspaces. 
ms.date: 03/29/2023
author: mjcaparas
ms.author: macapara
ms.topic: article
ms.service: microsoft-365-zero-trust
ms.collection: 
  - zerotrust-solution
  - msftsolution-secops
  - msftsolution-scenario
  - zerotrust-azure
  - usx-security
appliesto: 
    - Microsoft Sentinel in the Microsoft Defender portal
    - Microsoft Sentinel in the Azure portal
---

# Step 2. Architect your Microsoft Sentinel workspace

Deploying the Microsoft Sentinel environment involves designing a workspace configuration to meet your security and compliance requirements. The provisioning process includes creating Log Analytics workspaces and configuring the appropriate Microsoft Sentinel options.

This article provides recommendations on how to design and implement Microsoft Sentinel workspaces for the principles of Zero Trust.

## Step 1: Design a governance strategy

If your organization has many Azure subscriptions, you may need a way to efficiently manage access, policies, and compliance for those subscriptions. Management groups provide a governance scope for subscriptions. When you organize your subscriptions within management groups, the governance conditions you configure for a management group apply to the subscriptions it contains. For more information, see [Organize your resources with management groups](/azure/governance/management-groups/overview).

For example, the Microsoft Sentinel workspace in the following diagram is in the **Security** subscription under the **Platform** management group, which is part of the Microsoft Entra tenant.

:::image type="content" source="./media/sentinel-workspaces.svg" alt-text="Example of a Microsoft Sentinel workspace in a Microsoft Entra tenant." lightbox="./media/sentinel-workspaces.svg":::

The Security Azure subscription and the Microsoft Sentinel workspace inherit the role-based access control (RBAC) and Azure policies that are applied to the Platform management group.

## Step 2: Create Log Analytics workspaces

To use Microsoft Sentinel, the first step is to create your Log Analytics workspaces. A single Log Analytics workspace might be sufficient for many environments, but many organizations create multiple workspaces to optimize costs and better meet different business requirements. 

It is a best practice to create separate workspaces for the operational and security data for data ownership and cost management for Microsoft Sentinel. For example, if there’s more than one person administering operational and security roles, your first decision for Zero Trust is whether to create separate workspaces for those roles.

The unified security operations platform, which provides access to Microsoft Sentinel in the Defender portal, supports only a single workspace.

For more information, see [Design criteria for Log Analytics workspaces](/azure/azure-monitor/logs/workspace-design#design-criteria).

For an example of separate workspaces for operation and security roles, see [Contoso's solution](/azure/sentinel/sample-workspace-designs#contosos-solution).

### Log Analytics workspace design considerations

For a single tenant, there are two ways Microsoft Sentinel workspaces can be configured:

- **Single tenant with a single Log Analytics workspace.** In this case, the workspace becomes the central repository for logs across all resources within the tenant.

    |Advantages  |Disadvantages  |
    |---------|---------|
    |- Central consolidation of logs. <br><br>- Easier to query information. <br><br>- Azure role-based access control (Azure RBAC) to control access to Log Analytics and Microsoft Sentinel. For more information, see [Manage access to Log Analytics workspaces - Azure Monitor](/azure/azure-monitor/logs/manage-access?tabs=portal), and [Roles and permissions in Microsoft Sentinel](/azure/sentinel/roles).     |  - May not meet governance requirements. <br><br>- There is a bandwidth cost between regions.       |

- **Single tenant with regional Log Analytics workspaces.** 

    |Advantages  |Disadvantages  |
    |---------|---------|
    |- No cross-region bandwidth costs. <br><br>- May be required to meet governance.<br><br> - Granular data access control.<br><br> - Granular retention settings.<br><br>- Split billing.   | - No central pane of glass.<br><br> - Analytics, workbooks, and other configurations must be deployed multiple times.       |

For more information, see [Design a Log Analytics workspace architecture](/azure/azure-monitor/logs/workspace-design).

## Step 3: Architect the Microsoft Sentinel workspace

Onboarding Microsoft Sentinel requires selecting a Log Analytics workspace. The following are considerations for setting up Log Analytics for Microsoft Sentinel:

- Create a *Security* resource group for governance purposes, which allows for isolation of Microsoft Sentinel resources and role-based access to the collection. For more information, see [Design a Log Analytics workspace architecture](/azure/azure-monitor/logs/workspace-design).
- Create a Log Analytics workspace in the *Security* resource group and onboard Microsoft Sentinel into it. 
This automatically gives you [31 days of data ingestion up to 10 Gb a day](/azure/sentinel/billing?tabs=commitment-tier#free-trial) free as part of a free trial. 
- Set your Log Analytics Workspace supporting Microsoft Sentinel to [90 day retention](/azure/sentinel/billing?tabs=commitment-tier#data-retention-and-archived-logs-costs) at a minimum.

Once you onboard Microsoft Sentinel to a Log Analytics workspace, you get 90 days of data retention at no additional cost. You will incur costs for the total amount of data in the workspace after 90 days. Setting it to 90 days ensures a 90-day rollover of log data. You may consider retaining log data for longer based on governmental requirements.

For more information, see [Create Log Analytics workspaces](/azure/azure-monitor/logs/quick-create-workspace?tabs=azure-portal) and [Quickstart: Onboard in Microsoft Sentinel](/azure/sentinel/quickstart-onboard).

### Zero Trust with Microsoft Sentinel

To implement zero-trust architecture, consider extending the workspace to query and analyze your data across workspaces and tenants. Use [Sample Microsoft Sentinel workspace designs](/azure/sentinel/sample-workspace-designs) and [Extend Microsoft Sentinel across workspaces and tenants](/azure/sentinel/extend-sentinel-across-workspaces-tenants) to determine best workspace design for your organization.

In addition, use the [Cloud Roles and Operations Management prescriptive guidance](https://github.com/Azure/cloud-rolesandops) and its Excel spreadsheet ([download](https://github.com/Azure/cloud-rolesandops/releases/download/v0.91b/cromv09.xlsx)). From this guide, the Zero Trust tasks to consider for Microsoft Sentinel are:

- Define Microsoft Sentinel RBAC roles with associated Microsoft Entra groups.
- Validate that implemented access practices to Microsoft Sentinel still meet your organization’s requirements.
- Consider the use of customer-managed keys.

### Zero Trust with RBAC

To comply with Zero Trust, we recommend that you configure Azure RBAC based on the resources that are allowed to your users instead of providing them with access to the entire Microsoft Sentinel environment.

The following table lists some of the Microsoft Sentinel-specific roles.

| Role name | Description |
| --- | --- |
| **Microsoft Sentinel Reader** | View data, incidents, workbooks, and other Microsoft Sentinel resources. |
| **Microsoft Sentinel Responder** | In addition to the capabilities of the Microsoft Sentinel Reader role, manage incidents (assign, dismiss, etc.). This role is applicable to user types of security analysts. |
| **Microsoft Sentinel Playbook Operator** | List, view, and manually run playbooks. This role is also applicable to user types of security analysts. This role is for granting a Microsoft Sentinel responder the ability to run Microsoft Sentinel playbooks with the least amount of privilege. |
| **Microsoft Sentinel Contributor** | In addition to the capabilities of the Microsoft Sentinel Playbook Operator role, create and edit workbooks, analytics rules, and other Microsoft Sentinel resources. This role is applicable to user types of security engineers. |
| **Microsoft Sentinel Automation Contributor** | Allows Microsoft Sentinel to add playbooks to automation rules. It isn't meant for user accounts. |

When you assign Microsoft Sentinel-specific Azure roles, you may come across other Azure and Log Analytics roles that may have been assigned to users for other purposes. For example, the *Log Analytics Contributor* and *Log Analytics Reader* roles grant access to a Log Analytics workspace. 

For more information, see [Roles and permissions in Microsoft Sentinel](/azure/sentinel/roles) and [Manage access to Microsoft Sentinel data by resource](/azure/sentinel/resource-context-rbac).

### Zero Trust in multi-tenant architectures with Azure Lighthouse

Azure Lighthouse enables multi-tenant management with scalability, higher automation, and enhanced governance across resources. With Azure Lighthouse you can manage multiple Microsoft Sentinel instances across Microsoft Entra tenants at scale. Here’s an example.

:::image type="content" source="./media/sentinel-workspaces-multi-tenant.svg" alt-text="Example of using Azure Lighthouse across multiple Microsoft Entra tenants." lightbox="./media/sentinel-workspaces-multi-tenant.svg":::

With Azure Lighthouse, you can run queries across multiple workspaces or create workbooks to visualize and monitor data from your connected data sources and gain additional insight. It’s important to consider Zero Trust principles. See [Recommended security practices](/azure/lighthouse/concepts/recommended-security-practices) to implement least privileges access controls for Azure Lighthouse.

Consider the following questions when implementing security best practices for Azure Lighthouse:

- Who is responsible for data ownership?
- What are the data isolation and compliance requirements?
- How to implement least privileges across tenants.
- How will multiple data connectors in multiple Microsoft Sentinel workspaces be managed?
- How to monitor office 365 environments?
- How to protect intellectual properties&ndash;for example, playbooks, notebooks, analytics rules&ndash;across tenants?

See [Manage Microsoft Sentinel workspaces at scale: Granular Azure RBAC](/azure/lighthouse/how-to/manage-sentinel-workspaces#granular-azure-role-based-access-control-azure-rbac) for the security best practices of Microsoft Sentinel and Azure Lighthouse.

## Onboard your workspace to the unified security operations platform (preview)

If you're working with a single workspace, we recommend that you onboard your workspace to the unified security operations platform to view all your Microsoft Sentinel data together with XDR data in the Microsoft Defender portal.

The unified security operations platform also provides improved capabilities, such as automatic attack disruption for SAP system, unified queries from the Defender **Advanced hunting** page, and unified incidents and entities across both Microsoft Defender and Microsoft Sentinel.

For more information, see:

- [Connect Microsoft Sentinel to Microsoft Defender XDR](/microsoft-365/security/defender/microsoft-sentinel-onboard)
- [Microsoft Sentinel in the Microsoft Defender portal](/azure/sentinel/microsoft-sentinel-defender-portal)

## Recommended training

The following are the recommended training modules for this step. Training content focuses on general availability features, and therefore doesn't include content for the unified security operations platform, which is in Preview.

### Introduction to Microsoft Sentinel

|Training  |[Introduction to Microsoft Sentinel](/training/modules/intro-to-azure-sentinel/)|
|---------|---------|
|:::image type="icon" source="media/intro-to-azure-sentinel.svg" border="false"::: | Learn how Microsoft Sentinel enables you to start getting valuable security insights from your cloud and on-premises data quickly. |
> [!div class="nextstepaction"]
> [Start >](/training/modules/intro-to-azure-sentinel/)

### Configure your Microsoft Sentinel environment

|Training  |[Configure your Microsoft Sentinel environment](/training/paths/sc-200-configure-azure-sentinel-environment/)|
|---------|---------|
|:::image type="icon" source="media/configure-your-azure-sentinel-environment.svg" border="false"::: | Get started with Microsoft Sentinel by properly configuring the Microsoft Sentinel workspace. |
> [!div class="nextstepaction"]
> [Start >](/training/paths/sc-200-configure-azure-sentinel-environment/)

### Create and manage Microsoft Sentinel workspaces

|Training  |[Create and manage Microsoft Sentinel workspaces](/training/modules/create-manage-azure-sentinel-workspaces/)|
|---------|---------|
|:::image type="icon" source="media/create-and-manage-azure-sentinel-workspaces.svg" border="false"::: | Learn about the architecture of Microsoft Sentinel workspaces to ensure you configure your system to meet your organization's security operations requirements. |
> [!div class="nextstepaction"]
> [Start >](/training/modules/create-manage-azure-sentinel-workspaces/)

## Next step

Continue with [Step 3](ingest-data-sources.md) to configure Microsoft Sentinel to ingest data sources and configure incident detection.

[![Image of Microsoft Sentinel and XDR solution steps with step 3 highlighted](./media/siem-xdr-solution-3.png)](ingest-data-sources.md)

## References

Refer to these links to learn about the services and technologies mentioned in this article.


|Service area |Learn more  |
|---------|---------|
|**Microsoft Sentinel**     | - [Quickstart: Onboard in Microsoft Sentinel](/azure/sentinel/quickstart-onboard) <br>- [Manage access to Microsoft Sentinel data by resource](/azure/sentinel/resource-context-rbac)        |
|**Microsoft Sentinel governance**     |  - [Organize your resources with management groups](/azure/governance/management-groups/overview) <br>- [Roles and permissions in Microsoft Sentinel](/azure/sentinel/roles)       |
|**Log Analytics workspaces**     | - [Design a Log Analytics workspace architecture](/azure/azure-monitor/logs/workspace-design)<br>- [Design criteria for Log Analytics workspaces](/azure/azure-monitor/logs/workspace-design#design-criteria)<br>- [Contoso's solution](/azure/sentinel/sample-workspace-designs#contosos-solution)<br>- [Manage access to Log Analytics workspaces - Azure Monitor](/azure/azure-monitor/logs/manage-access?tabs=portal)<br>- [Design a Log Analytics workspace architecture](/azure/azure-monitor/logs/workspace-design)<br>- [Create Log Analytics workspaces](/azure/azure-monitor/logs/quick-create-workspace?tabs=azure-portal)        |
|**Microsoft Sentinel workspaces and Azure Lighthouse**     |       - [Manage Microsoft Sentinel workspaces at scale: Granular Azure RBAC](/azure/lighthouse/how-to/manage-sentinel-workspaces#granular-azure-role-based-access-control-azure-rbac)<br>- [Recommended security practices](/azure/lighthouse/concepts/recommended-security-practices) |