---
title: Install the Microsoft Sentinel Zero Trust (TIC 3.0) workbook
description: Install and learn how to use the Microsoft Sentinel Zero Trust (TIC3.0) workbook for an automated visualization of Zero Trust principles, cross-walked to the Trusted Internet Connections framework.
ms.date: 09/17/2021
ms.service: security
author: batamig
ms.author: bagol
ms.topic: how-to
---

# Visualize Zero Trust in your environment with the Microsoft Sentinel

The Microsoft Sentinel Zero Trust (TIC 3.0) workbook provides an automated visualization of Zero Trust principles, cross-walked to the Trust Internet Connections framework, and helps organizations to monitor configurations over time.

The Zero Trust workbook uses the full breadth of Microsoft Security offerings across Azure, Microsoft 365, Teams, Intune, Windows Virtual Desktop, and more, and enables users across your teams to gain  situational awareness for cloud workloads' security posture. The workbook is designed to augment staffing through automation, artificial intelligence, machine learning, query/alerting generation, visualizations, tailored recommendations, and respective documentation references.

This article describes how to install and use the Microsoft Sentinel Zero Trust workbook in your Microsoft Sentinel workspace.

> [!IMPORTANT]
> While the Microsoft Sentinel Zero Trust (TIC 3.0) workbook provides best practice guidance, Microsoft does not guarantee nor imply compliance. All TIC requirements, validations, and controls are governed by the [Cybersecurity & Infrastructure Security Agency](https://www.cisa.gov/trusted-internet-connections).
>
> The Zero Trust workbook provides visibility and situational awareness for control requirements delivered with Microsoft technologies in predominantly cloud-based environments. Customer experience will vary by user, and some panels may require additional configurations and query modification for operation.
>
> Recommendations do not imply coverage of respective controls, as they are often one of several courses of action for approaching requirements, which is unique to each customer. Recommendations should be considered a starting point for planning full or partial coverage of respective control requirements.
>

This workbook leverages automation to visualize your Zero Trust security architecture. Is Zero Trust the same as TIC 3.0? No, they’re not the same, but they share numerous common themes which provide a powerful story. The workbook offers detailed crosswalks of Microsoft's Zero Trust model with the Trusted Internet Connections (TIC3.0) framework to better understand the overlaps.


## Workbook use cases and user types

The Microsoft Sentinel Zero Trust (TIC 3.0) workbook is useful for any of the following users and use cases:

- **Security architect**: Build and design a cloud security architecture to compliance requirements.
- **Managed security services provider** (MSSP): Use the workbook for Zero Trust (TIC3.0) Assessments.
- **Security operations analyst**: Review activity in query, configure alerts, deploy SOAR automation.
- **IT professional**: Identify performance issues, investigate issues, set alerts for remediation monitoring.
- **Security Engineer**: Assess security controls, review alerting thresholds, adjust configurations.
- **Security Manager**: Review requirements, analyze reporting, evaluate capabilities, adjust accordingly.

For example, the following image shows how a security operations analyst can use the workbook to review requirements, explore queries, configure alerts, and implement automation.

## Deploy the workbook

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

Many data connectors are available both as standalone data connectors, and as Microsoft Sentinel solutions. For more information, see [Centrall discovery and deploy out-of-the-box content and solutions](/azure/sentinel/sentinel-solutions-deploy).

Additionally, you must have access to your Microsoft Sentinel workspace with [Security Reader](/azure/active-directory/roles/permissions-reference#security-reader) permissions.

## Deploy and navigate the workbook

To deploy the Zero Trust (TIC 3.0) workbook from the Azure portal;

1. In Microsoft Sentinel, select **Workbooks > Templates**.

1. Search for Zero Trust, and then select **Save** to install the workbook in your Microsoft Sentinel workspace.

Once installed in your workspace, you can navigate the following areas of the Zero Trust workbook:

### Workbook legend

The Legend Panel provides a helpful reference for navigating the workbook with respective colors, features, and reference indicators.

### Show or guide workbook guides

Workbook Navigation

The Guide Toggle is available in the top left of the workbook. This toggle allows you to view panels such as recommendations and guides, which will help you first access the workbook but can be hidden once you’ve grasped respective concepts.


### Resource parameter options

The Resource Parameter Options provide configuration options to sort control cards by Subscription, Workspace, and Time Range. The Parameter Options are beneficial for Managed Security Service Providers (MSSP) or large enterprises that leverage Azure Lighthouse for visibility into multiple workspaces. It facilitates assessment from both the aggregate and individual workspace perspectives. Time range parameters allow options for daily, monthly, quarterly, and even custom time range visibility.

### Capabilities ribbon

The Capabilities Ribbon provides a mechanism for navigating the desired security capabilities sections highlighted in the TIC3.0 framework. Selecting a capability tab will display Control Cards in the respective area. An Overview tab provides more granular detail of the overlaps between the Microsoft Zero Trust model and the TIC3.0 framework.


 
The Microsoft Sentinel Zero Trust (TIC3.0) Workbook displays each control in a Capability Card. The Capability Card provides respective control details to understand requirements, view your data, adjust SIEM queries, export artifacts, onboard Microsoft controls, navigate configuration blades, access reference materials, and view correlated compliance frameworks.

## Configure and troubleshoot your workbook

Configurations & Troubleshooting
It's important to note that this workbook provides visibility and situational awareness for control requirements delivered with Microsoft technologies in predominantly cloud-based environments. Customer experience will vary by user, and some panels may require additional configurations and query modification for operation. It’s unlikely that all 76+ panels will populate data, but this is expected as panels without data highlight respective areas for evaluation in maturing cybersecurity capabilities. Capability Cards without data will display the custom error message below. Most issues are resolved by confirming the log source's licensing/availability/health, ensuring the log source is connected to the Sentinel workspace, and adjusting time thresholds for larger data sets. Ultimately this workbook is customer-controlled content, so panels are configurable per customer requirements. You can edit/adjust Control Card queries as follows:

 

Zero Trust (TIC3.0) Workbook > Edit > Edit Panel > Adjust Panel KQL Query > Save
thumbnail image 11 captioned Custom Error Messaging
Custom Error Messaging

While using Microsoft offerings for the Zero Trust (TIC3.0) Workbook is recommended, it’s not a set requirement as customers often rely on many security providers and solutions. Below is a use-case example for adjusting a Control Card to include third-party tooling. The default KQL query provides a framework for target data, and it is readily adjusted with the desired customer controls/solutions.

 

thumbnail image 12 captioned 3rd Party Tool Use-Case

## Next steps

3rd Party Tool Use-Case

Get Started with Microsoft Sentinel and Learn More About Zero Trust with Microsoft
Below are additional resources for learning more about Zero Trust (TIC3.0) with Microsoft. Bookmark the Security blog to keep up with our expert coverage on security matters and follow us at @MSFTSecurity or visit our website for the latest news and cybersecurity updates.

Get Started with Microsoft Sentinel
Tutorial: Visualize and Monitor your Data with Workbooks
Microsoft Zero Trust Model
Zero Trust Deployment Center
Zero Trust: 7 Adoption Strategies from Security Leaders
Microsoft Zero Trust Video
