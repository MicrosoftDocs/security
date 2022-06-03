---
title: Deploy an information protection solution with Microsoft Purview
description: Prescriptive guidance to deploy Microsoft Purview Information Protection for your organization.
ms.date: 05/26/2022
ms.service: security
author: brendacarter
ms.author: bcarter
ms.topic: conceptual
---

# Deploy an information protection solution with Microsoft Purview

[Licensing for Microsoft 365 Security & Compliance](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

> [!NOTE]
> Microsoft 365 compliance is now called Microsoft Purview and the solutions within the compliance area have been rebranded. For more information about Microsoft Purview, see the [blog announcement](https://aka.ms/microsoftpurviewblog).

Your information protection strategy is driven by your business needs. Many organizations must comply with regulations, laws, and business practices. Additionally, organizations need to protect proprietary information, such as data for specific projects.

Microsoft Purview Information Protection (formerly Microsoft Information Protection) provides a framework, process, and capabilities you can use to accomplish your specific business objectives. 

## Microsoft Purview Information Protection framework

Use Microsoft Purview Information Protection to help you discover, classify, protect, and govern sensitive information wherever it lives or travels.

:::image type="content" source="media/mip-solution-overview-extended.png" alt-text="Microsoft Purview Information Protection solution overview":::

Watch the following Ignite session to see how these capabilities support and build on each other: [Know your data, protect your data, and prevent data loss with Microsoft Information Protection](https://myignite.microsoft.com/archives/IG20-OD273).

For data governance, see [Deploy a data governance solution with Microsoft Purview](/microsoft-365/compliance/data-governance-solution?view=o365-worldwide).

## Licensing

Microsoft Purview Information Protection capabilities are included with Microsoft Purview. The licensing requirements can vary even within capabilities, depending on configuration options. To identify licensing requirements and options, see the [Microsoft 365 guidance for security & compliance](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## Know your data

:::image type="content" source="media/knowyourdata-mipsolution.png" alt-text="Know your data for Microsoft Purview Information Protection solution overview":::

Knowing where your sensitive data resides is often the biggest challenge for many organizations. Microsoft Purview Information Protection data classification helps you to discover and accurately classify ever-increasing amounts of data that your organization creates. Graphical representations help you gain insights into this data so you can set up and monitor policies to protect and govern it.


|Step|Description|More information|
|:---|:----------|:---------------|
|1| Describe the categories of sensitive information you want to protect. <br /><br /> You already have an idea of what types of information is most valuable to your org and what types are not. Work with stakeholders to describe these categories because these are your starting place. | [Learn about sensitive information types](/microsoft-365/compliance/sensitive-information-type-learn-about?view=o365-worldwide)<p> [Learn about trainable classifiers](/microsoft-365/compliance/classifier-learn-about?view=o365-worldwide)|
|2| Discover and classify sensitive data. <br /><br /> Sensitive data in items can be found by using many different methods that include default DLP policies, manual labeling by users, and automated pattern recognition using sensitive information types or machine learning. |[Learn about data classification](/microsoft-365/compliance/data-classification-overview?view=o365-worldwide)<p> [Video: Data classification in the compliance center](https://www.microsoft.com/videoplayer/embed/RE4vx8x)|
|3| View your sensitive items.  <br /><br /> Use content explorer and activity explorer for a deeper analysis of sensitive items and the actions that users are taking on these items.| [Get started with content explorer](/microsoft-365/compliance/data-classification-content-explorer?view=o365-worldwide) <p> [Get started with activity explorer](/microsoft-365/compliance/data-classification-activity-explorer?view=o365-worldwide)|

## Protect your data

:::image type="content" source="media/protect-mipsolution.png" alt-text="Protect your data for Microsoft Purview Information Protection solution overview":::

Use the information from knowing where your sensitive data resides to help you more efficiently protect it. But there's no need to wait—you can start to protect your data immediately with a combination of manual, default, and automatic labeling. Then use [content explorer](/microsoft-365/compliance/data-classification-content-explorer?view=o365-worldwide) and [activity explorer](/microsoft-365/compliance/data-classification-activity-explorer?view=o365-worldwide) from the previous section to confirm what items are labeled and how your labels are being used.

|Step|Description|More information|
|:---|-----------|:---------------|
| 1|Define your [sensitivity labels](/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide) and policies that will protect your organization's data. <br /><br />In addition to identifying the sensitivity of content, these labels can apply protection actions, such as headers, footers, watermarks, and encryption. | [Get started with sensitivity labels](/microsoft-365/compliance/get-started-with-sensitivity-labels?view=o365-worldwide) <br /><br /> [Create and configure sensitivity labels and their policies](/microsoft-365/compliance/create-sensitivity-labels?view=o365-worldwide) <br /><br /> [Restrict access to content by using sensitivity labels to apply encryption](/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide)|
| 2|Label and protect items for Microsoft 365 apps and services. <br /><br />Sensitivity labels are supported for Microsoft 365 Word, Excel, PowerPoint, Outlook, and containers that include SharePoint and OneDrive sites, and Microsoft 365 groups. Use a combination of labeling methods such as manual labeling, automatic labeling, a default label, and mandatory labeling.| [Manage sensitivity labels in Office apps](/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide) <br /><br /> [Enable sensitivity labels for Office files in SharePoint and OneDrive](/microsoft-365/compliance/sensitivity-labels-sharepoint-onedrive-files?view=o365-worldwide) <br /><br /> [Enable co-authoring for files encrypted with sensitivity labels](/microsoft-365/compliance/sensitivity-labels-coauthoring?view=o365-worldwide) <br /><br /> [Apply a sensitivity label to content automatically](/microsoft-365/compliance/apply-sensitivity-label-automatically?view=o365-worldwide) <br /><br /> [Use sensitivity labels with Microsoft Teams, Microsoft 365 groups, and SharePoint sites](/microsoft-365/compliance/sensitivity-labels-teams-groups-sites?view=o365-worldwide) <br /><br /> [Use sensitivity labels to set the default sharing link for sites and documents in SharePoint and OneDrive](/microsoft-365/compliance/sensitivity-labels-default-sharing-link?view=o365-worldwide)<br /><br /> [Apply a sensitivity label to a model in Microsoft SharePoint Syntex](/microsoft-365/contentunderstanding/apply-a-sensitivity-label-to-a-model) <br /><br /> [Sensitivity labels in Power BI](/power-bi/admin/service-security-sensitivity-label-overview) |
|3|Discover, label, and protect sensitive items that reside in data stores in the cloud by using [Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security) with your sensitivity labels.| [Discover, classify, label, and protect regulated and sensitive data stored in the cloud](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|4|Discover, label, and protect sensitive items that reside in data stores on premises by deploying the [Azure Information Protection unified labeling scanner](/azure/information-protection/deploy-aip-scanner) with your sensitivity labels.| [Configuring and installing the Azure Information Protection unified labeling scanner](/azure/information-protection/deploy-aip-scanner-configure-install)|
|5|Extend your sensitivity labels to Azure by using [Microsoft Purview Data Map](/azure/purview/overview), to discover and label items for Azure Blob Storage, Azure files, Azure Data Lake Storage Gen1, and Azure Data Lake Storage Gen12. | [Labeling in Microsoft Purview Data Map](/azure/purview/create-sensitivity-label)|

If you are a developer who wants to extend sensitivity labels to line-of-business apps or third-party SaaS apps, see [Microsoft Information Protection (MIP) SDK setup and configuration](/information-protection/develop/setup-configure-mip). 

### Additional protection capabilities

Microsoft Purview includes additional capabilities to help protect data. Not every customer needs these capabilities, and some might be superseded by more recent releases.

Use the [Protect your data with Microsoft Purview](/microsoft-365/compliance/information-protection?view=o365-worldwide) page for the full list of protection capabilities.

## Prevent data loss

:::image type="content" source="media/dlp-mipsolution.png" alt-text="Prevent data loss for Microsoft Purview Information Protection solution overview":::

Deploy Microsoft Purview Data Loss Prevention (DLP) policies to govern and prevent the inappropriate sharing, transfer, or use of sensitive data across apps and services. These policies help users make the right decisions and take the right actions when they're using sensitive data.

|Step|Description|More information|
|:---|:----------|:---------------|
|1|Learn about DLP. <br /><br /> Organizations have sensitive information under their control, such as financial data, proprietary data, credit card numbers, health records, or social security numbers. To help protect this sensitive data and reduce risk, they need a way to prevent their users from inappropriately sharing it with people who shouldn't have it. This practice is called data loss prevention (DLP).| [Learn about data loss prevention](/microsoft-365/compliance/dlp-learn-about-dlp?view=o365-worldwide)|
|2|Plan your DLP implementation. <br /><br /> Every organization will plan for and implement data loss prevention (DLP) differently, because every organization's business needs, goals, resources, and situation are unique to them. However, there are elements that are common to all successful DLP implementations. | [Plan for data loss prevention](/microsoft-365/compliance/dlp-overview-plan-for-dlp?view=o365-worldwide)|
|3|Design and create a DLP policy. <br /><br /> Creating a data loss prevention (DLP) policy is quick and easy, but getting a policy to yield the intended results can be time consuming if you have to do a lot of tuning. Taking the time to design a policy before you implement it will get you to the desired results faster, and with fewer unintended issues, than tuning by trial and error alone.| [Design a DLP policy](/microsoft-365/compliance/dlp-policy-design?view=o365-worldwide) <p> [DLP policy reference](/microsoft-365/compliance/dlp-policy-reference?view=o365-worldwide) <p>[Create, test, and tune a DLP policy](/microsoft-365/compliance/create-test-tune-dlp-policy?view=o365-worldwide)|
|4|Tune your DLP policies. <br /><br /> After you deploy a DLP policy, you'll see how well it meets the intended purpose. Use that information to adjust your policy settings for better performance. | [Create, test, and tune a DLP policy](/microsoft-365/compliance/create-test-tune-dlp-policy?view=o365-worldwide)|


## Training resources

Learning modules for consultants and admins:

- [Introduction to information protection and governance in Microsoft 365](/learn/modules/m365-compliance-information-governance)
- [Classify data for protection and governance](/learn/modules/m365-compliance-information-classify-data)
- [Protect information in Microsoft 365](/learn/modules/m365-compliance-information-protect-information)
- [Prevent data loss in Microsoft 365](/learn/modules/m365-compliance-information-prevent-data-loss)

To help train your users to apply and use the sensitivity labels that you configure for them, see [End-user documentation for sensitivity labels](/microsoft-365/compliance/get-started-with-sensitivity-labels?view=o365-worldwide).

When you deploy data loss prevention policies for Teams, you might find useful the following end-user guidance as an introduction to this technology with some potential messages that they might see: [Teams messages about data loss prevention (DLP) and communication compliance policies ](https://support.microsoft.com/office/teams-messages-about-data-loss-prevention-dlp-and-communication-compliance-policies-c5631c3f-f61b-4306-a6ac-6603d9fc5ff0).
