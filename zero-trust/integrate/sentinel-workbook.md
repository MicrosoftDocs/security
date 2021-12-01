---
title: Install the Microsoft Sentinel Zero Trust (TIC 3.0) workbook
description: Install and learn how to use the Microsoft Sentinel Zero Trust (TIC3.0) workbook for an automated visualization of Zero Trust principles, cross-walked to the Trusted Internet Connections framework.
ms.date: 11/30/2021
ms.service: security
author: batamig
ms.author: bagol
ms.topic: how-to
---

# Visualize Zero Trust in your environment with the Microsoft Sentinel

The Microsoft Sentinel Zero Trust (TIC 3.0) workbook provides an automated visualization of Zero Trust principles, cross-walked to the Trust Internet Connections framework, and helps organizations to monitor configurations over time.

The Zero Trust workbook uses the full breadth of Microsoft Security offerings across Azure, Microsoft 365, Teams, Intune, Windows Virtual Desktop, and more. It uses automation to visualize your Zero Trust security architecture and helps users across your teams to gain situational awareness for cloud workloads' security posture. The workbook is designed to augment staffing through automation, artificial intelligence, machine learning, query/alerting generation, visualizations, tailored recommendations, and respective documentation references.

This article describes how to install and use the Microsoft Sentinel Zero Trust workbook in your Microsoft Sentinel workspace.

## The Zero Trust workbook and the Trusted Internet Connections framework

While the Microsoft Sentinel Zero Trust (TIC 3.0) workbook provides best practice guidance, Microsoft does not guarantee nor imply compliance. All Trusted Internet Connection (TIC) requirements, validations, and controls are governed by the [Cybersecurity & Infrastructure Security Agency](https://www.cisa.gov/trusted-internet-connections).

The Zero Trust workbook provides visibility and situational awareness for control requirements delivered with Microsoft technologies in predominantly cloud-based environments. Customer experience will vary by user, and some panes may require additional configurations and query modification for operation.

Recommendations do not imply coverage of respective controls, as they are often one of several courses of action for approaching requirements, which is unique to each customer. Recommendations should be considered a starting point for planning full or partial coverage of respective control requirements.

> [!NOTE]
> Zero Trust and TIC 3.0 are not the same, but they share many common themes and together provide a common story. The Microsoft Sentinel Zero Trust workbook offers detailed crosswalks between the Microsoft Zero Trust model with the TIC 3.0 framework and helps users to better understand the overlaps between the two.
>

## Workbook use cases and user types

The Microsoft Sentinel Zero Trust (TIC 3.0) workbook is useful for any of the following users and use cases:

- **Security architect**: Build and design a cloud security architecture to compliance requirements.
- **Managed security services provider** (MSSP): Use the workbook for Zero Trust (TIC3.0) Assessments.
- **Security operations analyst**: Review activity in query, configure alerts, deploy SOAR automation.
- **IT professional**: Identify performance issues, investigate issues, set alerts for remediation monitoring.
- **Security Engineer**: Assess security controls, review alerting thresholds, adjust configurations.
- **Security Manager**: Review requirements, analyze reporting, evaluate capabilities, adjust accordingly.

For example, the following process show how a security operations analyst can use the workbook to review requirements, explore queries, configure alerts, and implement automation.

1. **Review current query output**, for example for Adaptive Access Control:

    :::image type="content" source="../media/integrate/sentinel-workbook/review-query-output-sample.png" alt-text="Screenshot of the Adaptive Access Control card.":::

1. **Explore query**. At the top right of the pane, select the options **:** menu > **Open the last run query in the Logs view.**

    :::image type="content" source="../media/integrate/sentinel-workbook/explore-query-logs.png" alt-text="Screenshot of the selected query in the Microsoft Sentinel Logs page.":::

3. **Configure alert**. In the Microsoft Sentinel **Analytics** area, configure a new alert or update an existing alert as needed. For example:

    :::image type="content" source="../media/integrate/sentinel-workbook/create-a-new-rule.png" alt-text="Screenshot of the Analytics rule wizard.":::

    For more information, see [Create custom analytics rules to detect threats](/azure/sentinel/detect-threats-custom).

4. **Respond with SOAR**. In the Microsoft Sentinel **Automation** area, create or update an automation playbook to take required actions automatically. For example, in the Logic app designer:

    :::image type="content" source="../media/integrate/sentinel-workbook/logic-app-sample.png" alt-text="Screenshot of the Logic app designer showing a sample playbook.":::

    For more information, see [Use triggers and actions in Microsoft Sentinel playbooks](/azure/sentinel/playbook-triggers-actions).

## Prerequisites

### Install and verify relevant data connectors

Before you use the Zero Trust (TIC 3.0) workbook, we recommend that you have the following log sources connected via Microsoft Sentinel data connectors, and have verified that you have logs streaming into Microsoft Sentinel:

:::row:::
   :::column span="":::
      - [Azure Active Directory](/azure/sentinel/data-connectors-reference#azure-active-directory)
      - [Azure Activity](/azure/sentinel/data-connectors-reference#azure-activity)
      - [Azure DDoS Protection](/azure/sentinel/data-connectors-reference#azure-ddos-protection)
      - [Azure Firewall](/azure/sentinel/data-connectors-reference#azure-firewall)
      - [Azure Information Protection](/azure/sentinel/data-connectors-reference#azure-information-protection)
      - [Azure Web Application Firewall](/azure/sentinel/data-connectors-reference#azure-web-application-firewall-waf)
   :::column-end:::
   :::column span="":::
      - [Microsoft 365 Defender](/azure/sentinel/connect-microsoft-365-defender)
      - [Microsoft Defender for Cloud](/azure/sentinel/connect-defender-for-cloud)
      - [Microsoft Defender for Cloud Apps](/azure/sentinel/data-connectors-reference#microsoft-defender-for-cloud-apps)
      - [Microsoft Defender for Office 365](/azure/sentinel/data-connectors-reference#microsoft-defender-for-office-365)
      - [Security events](/azure/sentinel/data-connectors-reference#security-events-via-legacy-agent-windows) via Legacy Agent (Windows)
      - [Syslog](/azure/sentinel/connect-syslog)
   :::column-end:::
   :::column span="":::
      - [Threat Intelligence](/azure/sentinel/connect-threat-intelligence-tip#enable-the-threat-intelligence-platforms-data-connector-in-microsoft-sentinel)
      - [Threat Intelligence - TAXII](/azure/sentinel/connect-threat-intelligence-taxii#enable-the-threat-intelligence---taxii-data-connector-in-microsoft-sentinel)
      - [Windows DNS Server](/azure/sentinel/data-connectors-reference#windows-dns-server)
      - [Windows Firewall](/azure/sentinel/data-connectors-reference#windows-firewall)
      - [Windows Security Events](/azure/sentinel/data-connectors-reference#windows-security-events-via-ama) via AMA
   :::column-end:::
:::row-end:::


Many data connectors are available both as standalone data connectors, and as Microsoft Sentinel solutions. For more information, see:

- [Connect Microsoft Sentinel to Azure, Windows, Microsoft, and Amazon services](/azure/sentinel/connect-azure-windows-microsoft-services)
- [Centrally discovery and deploy out-of-the-box content and solutions](/azure/sentinel/sentinel-solutions-deploy)

### Required user permissions

To deploy the Zero Trust workbook, you must have access to your Microsoft Sentinel workspace with [Security Reader](/azure/active-directory/roles/permissions-reference#security-reader) permissions.

## Deploy and navigate the workbook

To deploy the Zero Trust (TIC 3.0) workbook from the Azure portal:

1. In Microsoft Sentinel, select **Workbooks > Templates**.

1. Search for Zero Trust, and then select **Save** to install the workbook in your Microsoft Sentinel workspace.

1. After your workbook is deployed in your workspace, use the **Guides** toggle at the top left to view or hide recommendations and guide panes. For example, these may be helpful when you first access the workbook, but unnecessary once you've understood the relevant concepts.

1. Make sure that the correct details are selected in the [**Subscription**, **Workspace**, and **TimeRange** options](/azure/azure-monitor/visualize/workbooks-parameters) so that you can view the specific data you want to find.

    For example, these options might be most helpful for MSSPs or large enterprises using Azure Lighthouse to view multiple workspaces and assess data from the perspective of both the aggregate and individual workspace. Time range parameters allow options for daily, monthly, quarterly, and even custom time ranges.

    For more information, see [Azure Monitor workbook parameters].

1. From the **TIC 3.0 Capabilities** options, select the capabilities you want to view data for.  Each area displayed in the workbook shows relevant data and links for more information or for performing specific tasks relevant to the selected capability.

    For example, for each capability selected, the workbook may show the following types of information, and more:

    - Understanding requirements
    - Viewing your data
    - Adjusting SIEM queries
    - Exporting artifacts
    - Onboarding Microsoft controls
    - Navigating configuration pages
    - Accessing reference materials
    - Viewing correlated compliance frameworks

    > [!TIP]
    > Select **Overview** to view information about the overlaps between the Microsoft Zero Trust model and the TIC 3.0 framework.
    >

### Zero Trust workbook template legend

Use the following legend to navigate through the Zero Trust workbook template.

- **Green panes** provide definitions, guides, and references. For example:
    :::image type="content" source="../media/integrate/sentinel-workbook/example-info.png" alt-text="Screenshot of a sample green pane showing guide information.":::

- **Blue panes** list controls, best practices, and recommendations. For example:

    :::image type="content" source="../media/integrate/sentinel-workbook/example-info.png" alt-text="Screenshot of a sample blue pane for an informational message.":::

- **Red panes** list customer responsibilities and items not covered in the workbook. For example:

    :::image type="content" source="../media/integrate/sentinel-workbook/example-not-included.png" alt-text="Screenshot of a sample red pane for items not included in the workbook.":::

- :::image type="icon" source="../media/integrate/sentinel-workbook/icon-requirement.png" border="false"::: **Items with a blue diamond** list requirements, such as required logs for that pane.

- :::image type="icon" source="../media/integrate/sentinel-workbook/icon-get-started.png" border="false"::: **Items with a green star** provide links to get started with other Microsoft products.

- :::image type="icon" source="../media/integrate/sentinel-workbook/icon-security-portals.png" border="false"::: / :::image type="icon" source="../media/integrate/sentinel-workbook/icon-security-portals-switch.png" border="false"::: **Items with a blue circle or switch icon** provide links to other Microsoft security portals and admin centers.

- :::image type="icon" source="../media/integrate/sentinel-workbook/icon-references.png" border="false"::: **Yellow light bulbs** list extra references for more information.

- :::image type="icon" source="../media/integrate/sentinel-workbook/icon-permissions.png" border="false"::: **Items with a magnifying glass** indicate recommended roles or permissions.

### Watch a demo

:::image type="content" source="../media/integrate/sentinel-workbook/zero-trust-overview.gif" alt-text="Gif file showing a quick tour of the Zero Trust workbook.":::

## Configure and troubleshoot your workbook

The Zero Trust workbook provides visibility and situational awareness for control requirements delivered with Microsoft technologies in mostly cloud-based environments. Depending on your system configuration, you may need to perform additional configurations and modify queries in order for the data to show correctly.

Many issues can be resolved by confirming the log source's licensing, availability, and health, ensuring that the log source is connected to your Microsoft Sentinel workspace correctly, and adjusting time thresholds for larger data sets.

> [!TIP]
> It is unlikely that all panes in the workbook will populate data for every customer. When you see panes without any data, you might want to consider evaluating these areas of maturing cybersecurity capabilities.
>

### Edit or adjust workbook panes

Ultimately, the Zero Trust workbook is customer-controlled content, and each pane is customizable for your own requirements.

For example, while we recommend using the out-of-the-box Microsoft offerings for the Zero Trust workbook, you may rely on many security providers and solutions. In such cases, you may want to adjust your workbook panes to include notes about third-party tooling.

You can also customize the error messages displayed for panes without data in order to fit your needs.

**To customize panes in your workbook**:

1. In the Zero Trust (TIC3.0) workbook, select **Edit**. Your workbook switches to an editing view, with an **Edit** button under each pane.
1. Select **Edit** for the pane you want to customize, and then make the changes you need.
1. When you're finished, select **Done Editing**.

For more information, see the [Azure Monitor workbook documentation](/azure/azure-monitor/visualize/workbooks-overview#editing-mode).


## Next steps

For more information, see:

- [Get Started with Microsoft Sentinel](https://azure.microsoft.com/services/azure-sentinel/)
- [Visualize and monitor your data with workbooks](/azure/sentinel/monitor-your-data)
- [Microsoft Zero Trust Model](https://www.microsoft.com/security/business/zero-trust)
- [Zero Trust Deployment Center](/security/zero-trust/?WT.mc_id=Portal-fx)
- [Zero Trust: 7 Adoption Strategies from Security Leaders](https://www.microsoft.com/security/blog/2021/03/31/zero-trust-7-adoption-strategies-from-security-leaders/)
- [Microsoft Zero Trust Video](https://www.microsoft.com/videoplayer/embed/RE4J3ms)
