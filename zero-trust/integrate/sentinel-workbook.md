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

The Zero Trust workbook provides visibility and situational awareness for control requirements delivered with Microsoft technologies in predominantly cloud-based environments. Customer experience will vary by user, and some panels may require additional configurations and query modification for operation.

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

For example, the following image shows how a security operations analyst can use the workbook to review requirements, explore queries, configure alerts, and implement automation.

## Prerequisites

### Install and verify relevant data connectors

Before you use the Zero Trust (TIC 3.0) workbook, we recommend that you have the following log sources connected via Microsoft Sentinel data connectors, and have verified that you have logs streaming into Microsoft Sentinel:

:::row:::
   :::column span="":::
      [Azure Active Directory](/azure/sentinel/data-connectors-reference#azure-active-directory)
      [Azure DDoS Protection](/azure/sentinel/data-connectors-reference#azure-ddos-protection)
      [Azure Firewall](/azure/sentinel/data-connectors-reference#azure-firewall)
      [Azure Information Protection](/azure/sentinel/data-connectors-reference#azure-information-protection)
   :::column-end:::
   :::column span="":::
      [Azure Key Vault](/azure/sentinel/data-connectors-reference#azure-key-vault)
      [Azure Web Application Firewall](/azure/sentinel/data-connectors-reference#azure-web-application-firewall-waf)
      [Microsoft 365 Defender](/azure/sentinel/connect-microsoft-365-defender?tabs=MDE)
   :::column-end:::
   :::column span="":::
      [Microsoft Defender for Cloud](/azure/sentinel/connect-defender-for-cloud)
      [Microsoft Defender for Cloud Apps](/azure/sentinel/data-connectors-reference#microsoft-defender-for-cloud-apps)
      [Microsoft Defender for Endpoint](/azure/sentinel/data-connectors-reference#microsoft-defender-for-endpoint)
      [Microsoft Defender for Identity](/azure/sentinel/data-connectors-reference#microsoft-defender-for-identity)
      [Microsoft Defender for Office 365](/azure/sentinel/data-connectors-reference#microsoft-defender-for-office-365)
      [Microsoft Teams](/azure/sentinel/sentinel-solutions-catalog#microsoft)
      [Windows Security Events](/azure/sentinel/data-connectors-reference#windows-security-events-via-ama)
   :::column-end:::
:::row-end:::

Many data connectors are available both as standalone data connectors, and as Microsoft Sentinel solutions. For more information, see [Connect Microsoft Sentinel to Azure, Windows, Microsoft, and Amazon services](/azure/sentinel/connect-azure-windows-microsoft-services) and [Centrally discovery and deploy out-of-the-box content and solutions](/azure/sentinel/sentinel-solutions-deploy).

### Required user permissions

To perform this procedure, you must have access to your Microsoft Sentinel workspace with [Security Reader](/azure/active-directory/roles/permissions-reference#security-reader) permissions.

## Deploy and navigate the workbook

To deploy the Zero Trust (TIC 3.0) workbook from the Azure portal;

1. In Microsoft Sentinel, select **Workbooks > Templates**.

1. Search for Zero Trust, and then select **Save** to install the workbook in your Microsoft Sentinel workspace.

After your workbook is installed, navigate through the panes using the following legend:

- **Green panels** provide definitions, guides, and references
- **Blue panels** list controls, best practices, and recommendations
- **Red panels** list customer responsibilities and items not covered in the workbook
- **Items with a green star** provide links to get started with other Microsoft products
- **Items with a blue diamond** list requirements, such as required logs for that panel
- **Yellow light bulbs** list extra references for more information


> [!TIP]
> At the top left of the workbook, use the **Guides** toggle to view recommendation and guide panels or hide them. Recommendation and guide panels help most when you first access the workbook, and you may want to hide them once you've understood the relevant concepts.
>

### Sort control cards

Use the **Resource Parameter** options to sort the control cards displayed by Subscription, Workspace, and Time Range. For example, Parameter Options are helpful for MSSPs or large enterprises using Azure Lighthouse to view multiple workspaces and assess data from the perspective of both the aggregate and individual workspace.

Time range parameters allow options for daily, monthly, quarterly, and even custom time ranges.

For more information, see [Azure Monitor workbook parameters](/azure/azure-monitor/visualize/workbooks-parameters).


### TIC 3.0 capability cards

Capabilities highlighted in the TIC 3.0 framework are represented by Capability Cards in the Zero Trust workbook, where each card provides details for the following tasks:

- Understanding requirements
- Viewing your data
- Adjusting SIEM queries
- Exporting artifacts
- Onboarding Microsoft controls
- Navigating configuration pages
- Accessing reference materials
- Viewing correlated compliance frameworks

Use the Capabilities ribbon to navigate through the relevant security capabilities sections. Select a capability from the list to display control cards in the selected area.

> [!TIP]
> The **Overview** tab provides more details about the overlaps between the Microsoft Zero Trust model and the TIC 3.0 framework.
>

## Configure and troubleshoot your workbook

The Zero Trust workbook provides visibility and situational awareness for control requirements delivered with Microsoft technologies in mostly cloud-based environments. Depending on your system configuration, you may need to perform additional configurations and modify queries in order for the data to show correctly.

Many issues can be resolved by confirming the log source's licensing, availability, and health, ensuring that the log source is connected to your Microsoft Sentinel workspace correctly, and adjusting time thresholds for larger data sets.

It is unlikely that all panels in the workbook will populate data for every customer. When you see panels without any data, you might want to consider evaluating these areas of maturing cybersecurity capabilities.


### Edit or adjust control card queries

Ultimately, the Zero Trust workbook is customer-controlled content, and each panel is customizable for your own requirements.

**To customize the query for a specific panel in the workbook**:

1. In the Zero Trust (TIC3.0) workbook, select **Edit > Edit Panel > Adjust Panel KQL Query**.
1. Make the required changes to the query, and then select **Save**.

### Customize panel texts

While we recommend using the out-of-the-box Microsoft offerings for the Zero Trust workbook, you may rely on many security providers and solutions and therefore want to adjust your control card text to include notes about third-party tooling.

For example:

Capability cards without data will also display error messages that you can customize to fit your needs.

## Next steps

For more information, see:

- [Get Started with Microsoft Sentinel](https://azure.microsoft.com/services/azure-sentinel/)
- [Visualize and monitor your data with workbooks](/azure/sentinel/monitor-your-data)
- [Microsoft Zero Trust Model](https://www.microsoft.com/security/business/zero-trust)
- [Zero Trust Deployment Center](/security/zero-trust/?WT.mc_id=Portal-fx)
- [Zero Trust: 7 Adoption Strategies from Security Leaders](https://www.microsoft.com/security/blog/2021/03/31/zero-trust-7-adoption-strategies-from-security-leaders/)
- [Microsoft Zero Trust Video](https://www.microsoft.com/videoplayer/embed/RE4J3ms)
