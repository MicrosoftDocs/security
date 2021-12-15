---
title: View Zero Trust in your environment with Microsoft Sentinel
description: Install and learn how to use the Microsoft Sentinel Zero Trust (TIC3.0) workbook for an automated visualization of Zero Trust principles, cross-walked to the Trusted Internet Connections framework.
ms.date: 12/15/2021
ms.service: security
author: batamig
ms.author: bagol
ms.topic: how-to
---

# View Zero Trust in your environment with Microsoft Sentinel

The Microsoft Sentinel **Zero TrustTIC30** solution enables governance and compliance teams to design, build, monitor, and respond to Zero Trust (TIC 3.0) requirements. The solution includes a workbook, analytics rules, and a playbook, which provide an automated visualization of Zero Trust principles, cross-walked to the Trust Internet Connections framework, helping organizations to monitor configurations over time.

This article describes how to install and use the Microsoft Sentinel Zero Trust workbook in your Microsoft Sentinel workspace.

While only Microsoft Sentinel is required to get started, the solution is enhanced by integrations with other Microsoft Services, such as:

- [Microsoft 365 Defender](https://www.microsoft.com/microsoft-365/security/microsoft-365-defender)
- [Microsoft Information Protection](/microsoft-365/compliance/information-protection)
- [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)
- [Microsoft Defender for Cloud](https://azure.microsoft.com/services/active-directory/)
- [Microsoft Defender for Endpoint](https://www.microsoft.com/microsoft-365/security/endpoint-defender)
- [Microsoft Defender for Identity](https://www.microsoft.com/microsoft-365/security/identity-defender)
- [Microsoft Defender for Cloud Apps](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/cloud-app-security)
- [Microsoft Defender for Office 365](https://www.microsoft.com/microsoft-365/security/office-365-defender)

For more information, see [Guiding principles of Zero Trust](../index.md#guiding-principles-of-zero-trust).

## The Zero Trust solution and the TIC 3.0 framework

Zero Trust and TIC 3.0 are not the same, but they share many common themes and together provide a common story. The Microsoft Sentinel Zero Trust solution offers detailed crosswalks between the Microsoft Zero Trust model with the TIC 3.0 framework and helps users to better understand the overlaps between the two.

While the Microsoft Sentinel **Zero TrustTIC30** solution provides best practice guidance, Microsoft does not guarantee nor imply compliance. All Trusted Internet Connection (TIC) requirements, validations, and controls are governed by the [Cybersecurity & Infrastructure Security Agency](https://www.cisa.gov/trusted-internet-connections).

The Zero Trust solution provides visibility and situational awareness for control requirements delivered with Microsoft technologies in predominantly cloud-based environments. Customer experience will vary by user, and some panes may require additional configurations and query modification for operation.

Recommendations do not imply coverage of respective controls, as they are often one of several courses of action for approaching requirements, which is unique to each customer. Recommendations should be considered a starting point for planning full or partial coverage of respective control requirements.

The Microsoft Sentinel **Zero TrustTIC30** solution is useful for any of the following users and use cases:

- **Security governance, risk, and compliance professionals**, for compliance posture assessment and reporting
- **Engineers and architects**, who need to design Zero Trust and TIC 3.0-aligned workloads
- **Security analysts**, for alert and automation building
- **Managed security service providers (MSSPs)** for consulting services
- **Security managers**, who need to review requirements, analyze reporting, evaluating capabilities


## Install the Zero TrustTIC30 solution

## Sample usage scenario

The following process shows how a security operations analyst could use the resources deployed with the Zero TrustTIC30 solution to review requirements, explore queries, configure alerts, and implement automation.

1. In Microsoft Sentinel navigate to the **Workbooks** > **Zero Trust (TIC 3.0)** workbook, and select **View saved workbook**.

    In the **Zero Trust (TIC 3.0)** workbook, select TIC 3.0 capabilities to view. For this procedure, select **Intrusion Detection**.

1. **Review control cards**. For example, scroll down to view the Adaptive Access Control card:

    :::image type="content" source="../media/integrate/sentinel-workbook/review-query-output-sample.png" alt-text="Screenshot of the Adaptive Access Control card.":::

1. **Explore query**. At the top right of the Adaptive Access Control card, select the **:** More button, and then select the :::image type="icon" source="../media/integrate/sentinel-workbook/icon-open-in-logs.png" border="false"::: **Open the last run query in the Logs view.** option.

    The query is opened in the Microsoft Sentinel **Logs** page:

    :::image type="content" source="../media/integrate/sentinel-workbook/explore-query-logs.png" alt-text="Screenshot of the selected query in the Microsoft Sentinel Logs page.":::

1. **Configure alert**. Close the **Logs** page and the workbook, and go to the Microsoft Sentinel **Analytics** area. There, view out-of-the-box analytics rules deployed with the **Zero TrustTIC30** solution by searching for **TIC3.0**. Update the rules as needed or configure a new one.

    :::image type="content" source="../media/integrate/sentinel-workbook/edit-rule.png" alt-text="Screenshot of the Analytics rule wizard.":::

    For more information, see [Create custom analytics rules to detect threats](/azure/sentinel/detect-threats-custom).

4. **Respond with SOAR**. In the Microsoft Sentinel **Automation** > **Active playbooks** tab, find the the out-of-the-box **Notify-GovernanceComplianceTeam** playbook, which was deployed with the you can use  to have the governance compliance team automatically notified for any risks in the environment. create or update an automation playbook to take required actions automatically. For example, in the Logic app designer:

    :::image type="content" source="../media/integrate/sentinel-workbook/logic-app-sample.png" alt-text="Screenshot of the Logic app designer showing a sample playbook.":::

    For more information, see [Use triggers and actions in Microsoft Sentinel playbooks](/azure/sentinel/playbook-triggers-actions).

## Prerequisites

Before installing the **Zero TrustTIC30** solution, make sure you have the following prerequisites:

- **Onboard Microsoft services**: Make sure that you have both [Microsoft Sentinel](/azure/sentinel/quickstart-onboard) and [Microsoft Defender for Cloud](/azure/defender-for-cloud/get-started) enabled in your Azure subscription.

- **Microsoft Defender for Cloud requirements**: In Microsoft Defender for Cloud:

    - Add required regulatory standards to your dashboard. Make sure to add both the *Azure Security Benchmark* and *NIST SP 800-53 R5 Assessments* to your Microsoft Defender for Cloud dashboard. For more information, see [add a regulatory standard to your dashboard](/azure/security-center/update-regulatory-compliance-packages?WT.mc_id=Portal-fx#add-a-regulatory-standard-to-your-dashboard) in the Microsoft Defender for Cloud documentation.

    - Continuously export Microsoft Defender for Cloud data to your Log Analytics workspace. For more information, see [Continuously export Microsoft Defender for Cloud data](/azure/defender-for-cloud/continuous-export?tabs=azure-portal).

- **Required user permissions**. To install the **Zero TrustTIC30** solution, you must have access to your Microsoft Sentinel workspace with [Security Reader](/azure/active-directory/roles/permissions-reference#security-reader) permissions.

## Deploy and navigate the workbook

To deploy the **Zero TrustTIC30** solution from the Azure portal:

1. In Microsoft Sentinel, select **Content hub** and locate the **Zero TrustTIC30** solution

1. Select **Configure deployment options > Create** to install the solution in your Microsoft Sentinel workspace and deploy the Zero Trust workbook. For more information, see [Deploy out-of-the-box content and solutions](/azure/sentinel/sentinel-solutions-deploy).

1. After your workbook is deployed in your workspace, use the **Guides** toggle at the top left to view or hide recommendations and guide panes. For example, these may be helpful when you first access the workbook, but unnecessary once you've understood the relevant concepts.

1. Make sure that the correct details are selected in the [**Subscription**, **Workspace**, and **TimeRange** options](/azure/azure-monitor/visualize/workbooks-parameters) so that you can view the specific data you want to find.

    For example, these options might be most helpful for MSSPs or large enterprises using Azure Lighthouse to view multiple workspaces and assess data from the perspective of both the aggregate and individual workspace. Time range parameters allow options for daily, monthly, quarterly, and even custom time ranges.

    For more information, see [Azure Monitor workbook parameters](/azure/azure-monitor/visualize/workbooks-parameters).

1. From the **TIC 3.0 Capabilities** options, select the capabilities you want to view data for.  Each area displayed in the workbook shows relevant data and links for more information or for performing specific tasks relevant to the selected capability.

    For example, for each capability selected, the workbook may show the following types of information, and more:

    :::row:::
       :::column span="":::
        - Understanding requirements
        - Viewing your data
        - Adjusting SIEM queries
        - Exporting artifacts
       :::column-end:::
       :::column span="":::
        - Onboarding Microsoft controls
        - Navigating configuration pages
        - Accessing reference materials
        - Viewing correlated compliance frameworks
       :::column-end:::
    :::row-end:::

    > [!TIP]
    > Select **Overview** to view information about the overlaps between the Microsoft Zero Trust model and the TIC 3.0 framework.
    >

### Zero Trust workbook template legend

Use the following legend to navigate through the Zero Trust workbook template. Panes are no longer colored after you've saved the workbook in your workspace.

In the workbook template:
- **Green panes** provide definitions, guides, and references. For example:

    :::image type="content" source="../media/integrate/sentinel-workbook/example-guides.png" alt-text="Screenshot of a sample green pane showing guide information.":::

- **Blue panes** list controls, best practices, and recommendations. For example:

    :::image type="content" source="../media/integrate/sentinel-workbook/example-info.png" alt-text="Screenshot of a sample blue pane for an informational message.":::

- **Red panes** list customer responsibilities and items not covered in the workbook. For example:

    :::image type="content" source="../media/integrate/sentinel-workbook/example-not-included.png" alt-text="Screenshot of a sample red pane for items not included in the workbook.":::

In both the workbook template and the saved workbook:

- :::image type="icon" source="../media/integrate/sentinel-workbook/icon-requirement.png" border="false"::: **Items with a blue diamond** list requirements, such as required logs for that pane.

- :::image type="icon" source="../media/integrate/sentinel-workbook/icon-get-started.png" border="false"::: **Items with a green star** provide links to get started with other Microsoft products.

- :::image type="icon" source="../media/integrate/sentinel-workbook/icon-security-portals.png" border="false"::: / :::image type="icon" source="../media/integrate/sentinel-workbook/icon-security-portals-switch.png" border="false"::: **Items with a blue circle or switch icon** provide links to other Microsoft security portals and admin centers.

- :::image type="icon" source="../media/integrate/sentinel-workbook/icon-references.png" border="false"::: **Yellow light bulbs** list extra references for more information.

- :::image type="icon" source="../media/integrate/sentinel-workbook/icon-permissions.png" border="false"::: **Items with a magnifying glass** indicate recommended roles or permissions.

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

Watch our videos:

- [About the Zero Trust (TIC 3.0) workbook](https://www.youtube.com/watch?v=RpDas8fXzdU&feature=youtu.be)
- [Demo: Microsoft Sentinel Zero Trust (TIC 3.0) solution](https://www.youtube.com/watch?v=OVGgRIzAvCI)

Read our blogs!

- [Zero Trust: 7 Adoption Strategies from Security Leaders](https://www.microsoft.com/security/blog/2021/03/31/zero-trust-7-adoption-strategies-from-security-leaders/)
- [Announcing the Microsoft Sentinel: Zero Trust (TIC3.0) Solution](https://techcommunity.microsoft.com/t5/microsoft-sentinel-blog/announcing-the-microsoft-sentinel-zero-trust-tic3-0-solution/ba-p/3031685)
- [Building and monitoring Zero Trust (TIC 3.0) workloads for federal information systems with Microsoft Sentinel](https://devblogs.microsoft.com/azuregov/building-and-monitoring-zero-trust-tic-3-0-workloads-for-federal-information-systems-with-microsoft-sentinel/)
