---
title: Secure data with Zero Trust
description: Protecting data is one of the primary responsibilities of security and compliance teams. To ensure protection and that data access is restricted to authorized users, data should be inventoried, classified, labeled, and, where appropriate, encrypted. 
ms.date: 09/01/2020
ms.service: security
author: garycentric
ms.author: v-gmoor
ms.topic: conceptual
---

# Secure data with Zero Trust

:::image type="content" source="./media/icon-ones-and-zeroes-medium.png" alt-text="Ones and zeroes icon." border="false":::

**Background**

Protecting data is one of the primary responsibilities of security and compliance teams. Data should remain protected while at rest, in use, and when it leaves the [endpoints](https://aka.ms/ZTEndpoints), [apps](https://aka.ms/ZTApplications), [infrastructure](https://aka.ms/ZTInfrastructure), and [networks](https://aka.ms/ZTNetwork) that are within the control of the organization. To ensure protection and that data access is restricted to authorized users, data should be inventoried, classified, labeled, and, where appropriate, encrypted.

The three core elements of a data protection strategy are:

1.  **Know your data**

    If you don't know what sensitive data you have on-premises and in cloud services, you can't adequately protect it. You need to discover data across your entire organization and classify all data by sensitivity level.

1.  **Protect your data and prevent data loss**

    Sensitive data needs to be protected by data protection policies that label and encrypt data or block over-sharing. This ensures only authorized users are able to access the data, even when data travels outside of your corporate environment.

1.  **Monitor and remediate**

    You should continuously monitor sensitive data to detect policy violations and risky user behavior. This allows you to take appropriate action, such as revoking access, blocking users, and refining your protection policies.

:::image type="content" source="./media/diagram-monitor-remediate-data.png" lightbox="./media/diagram-monitor-remediate-data.png" alt-text="Diagram of monitoring activiting and remediation." border="false":::

When data and sensitive content is understood, labeled, and classified, organizations can:

-   **Inform and enforce policy decisions to** block or remove emails, attachments, or documents.

-   **Encrypt files** with sensitivity labels on device endpoints.

-   **Auto-classify content with sensitivity labels** through policy and machine learning.

-   **Track and monitor sensitive content** using policies as the content travels inside and outside your digital estate.


## Data Zero Trust deployment objectives

An information protection strategy needs to encompass your organization's entire digital content. As a baseline, you need to define labels, discover sensitive data, and monitor the use of labels and actions across your environment. Use of sensitivity labels is discussed at the end of this guide.

> [!NOTE]
> **Before** many organizations **start the Zero Trust journey**, their data security is characterized by the following:
> 
> -   Access is governed by perimeter control, not data sensitivity.
> 
> -   Sensitivity labels are applied manually, with inconsistent data classification.


The initial deployment objectives for information protection are:

1.  Defining your organization's label taxonomy.

1.  Defining your organization's information protection features that are in scope for deployment.

1.  Mapping the features in scope to your project timeline.

1.  Reviewing the Microsoft product roadmap to be aware of features that are coming that will align to your organization's information protection journey.

The above activities are consistent for all organizations planning an
information protection project, not just those focused on implementing a
Zero Trust approach to securing data. We won't further discuss these
activities in this guide. For more information, see:

-   Microsoft Documents: [Getting started with sensitivity labels](https://docs.microsoft.com/microsoft-365/compliance/get-started-with-sensitivity-labels?view=o365-worldwide&preserve-view=true)

-   MIP and Compliance: [Deployment Acceleration Guide](https://aka.ms/MIPC/DAG)

-   Microsoft Trust Center: [Data Classification and Sensitivity Label Taxonomy](https://aka.ms/MIPC/DataClassification)

When implementing an end-to-end Zero Trust framework for data, we recommend you focus first on these **initial deployment objectives**:


<table border="0">
   <tr>
      <td>
		 <p><img src="./media/icon-initial-deployment-small.png" alt="List icon with one checkmark, first instance."></p>
      </td>
      <td>
	     <p><b>I.</b> <a href="#i-access-decisions-are-governed-by-encryption">Access decisions are governed by encryption.</a></p>
         <p><b>II.</b> <a href="#ii-data-is-automatically-classified-and-labeled">Data is automatically classified and labeled.</a></p>
      </td>
   </tr>
</table>


After these are completed, focus on these **additional deployment objectives**:


<table border="0">
   <tr>
      <td>
		 <br/>
		 <p><img src="media/icon-additional-deployment-small.png" alt="List icon with two checkmarks."></p>
      </td>
      <td>
         <p><b>III.</b> <a href="#iii-classification-is-augmented-by-smart-machine-learning-models">Classification is augmented by smart machine learning models.</a></p>
         <p><b>IV.</b> <a href="#iv-access-decisions-are-governed-by-a-cloud-security-policy-engine">Access decisions are governed by a cloud security policy engine.</a></p>
         <p><b>V.</b> <a href="#v-dlp-policies-secure-sharing-with-encryption-and-tracking">Prevent data leakage through DLP policies based on a sensitivity label and content inspection.</a></p>
      </td>
   </tr>
</table>


## Products covered in this guide

**Microsoft Azure**

[Azure Information Protection](https://azure.microsoft.com/services/information-protection/) with Unified Labeling Client and Scanner 

**Microsoft 365**

[Microsoft Cloud App Security](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/cloud-app-security)


**Capabilities**

|  Client | File Types |         Scanner        | Label Management |   Reporting and Audit  | DLP | CASB |
|---------|------------|-------------|----------|------------------|------------------------|-----|------|
|         |            | **On-Prem** | **M365** |                  | **Current** | **Next** |     |      |
| Unified Labeling     | Office + Non-Office Files | Unified Labeling Scanner | M365 Data Classification | M365 Compliance Center  | AIP Analytics | M365 Activity Explorer | M365 Data Loss Prevention | Microsoft Cloud App Security |
| Office Native Labeling | Office Files   |       |       |       | N/A    |     |      |   |




<table>
   <thead>
      <tr class="header">
         <th><strong>Client</strong></th>
         <th><strong>File Types</strong></th>
         <th><strong>Scanner</strong></th>
         <th><strong>Label Management</strong></th>
         <th><strong>Reporting and Audit</strong></th>
         <th><strong>DLP</strong></th>
         <th><strong>CASB</strong></th>
         <th></th>
         <th></th>
      </tr>
   </thead>
   <tbody>
      <tr class="odd">
         <td></td>
         <td></td>
         <td><strong>On-Prem</strong></td>
         <td><strong>M365</strong></td>
         <td></td>
         <td><strong>Current</strong></td>
         <td><strong>Next</strong></td>
         <td></td>
         <td></td>
      </tr>
      <tr class="even">
         <td>Unified Labeling</td>
         <td>Office + Non-Office Files</td>
         <td>Unified Labeling Scanner</td>
         <td>M365 Data Classification</td>
         <td>M365 Compliance Center</td>
         <td>AIP Analytics</td>
         <td>M365 Activity Explorer</td>
         <td>M365 Data Loss Prevention</td>
         <td>Microsoft Cloud App Security</td>
      </tr>
      <tr class="odd">
         <td>Office Native Labeling</td>
         <td>Office Files</td>
         <td></td>
         <td></td>
         <td></td>
         <td>N/A</td>
         <td></td>
         <td></td>
         <td></td>
      </tr>
   </tbody>
</table>




## Data Zero Trust deployment guide

This guide will walk you step-by-step through a Zero Trust approach to data protection maturity. Please keep in mind that these items will vary widely depending on the sensitivity of your information and the size and complexity of your organization.


<table border="0">
   <tr>
      <td>
         <p><img src="media/icon-initial-deployment.png" alt="Checklist icon with one checkmark."></p>
      </td>
      <td>
         <h2>Initial deployment objectives</h2>
      </td>
   </tr>
</table>


### I. Access decisions are governed by encryption

Protect your most sensitive data with encryption to restrict access to content that sensitivity labels are applied to.

When a document or email is encrypted, access to the content is restricted so that it:

-   Is encrypted both at rest and in transit.

-   Remains encrypted no matter where it resides (inside or outside your organization), even if the file is renamed.

-   Can be decrypted only by users authorized by the label's encryption settings.

Take this step:

 - [Configure sensitivity labels for encryption](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels#understand-how-the-encryption-works).


### II. Data is automatically classified and labeled

To avoid issues with data not being labeled manually, or labels being applied inaccurately, automate data classification.

#### Automatically label content in Microsoft 365 Apps for Enterprise or Unified Labeling client

A strategic client selection for Windows leverages [built-in information protection features in Microsoft Office](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide&preserve-view=true#support-for-sensitivity-label-capabilities-in-apps). If this is not possible, an alternative solution would be to use the Azure Information Protection unified labeling client.

Follow these steps:

1.  [Learn how to configure auto-labeling](https://docs.microsoft.com/microsoft-365/compliance/apply-sensitivity-label-automatically?view=o365-worldwide&preserve-view=true#how-to-configure-auto-labeling-for-office-apps) for Office apps.

1.  [Apply sensitivity labels to content automatically](https://docs.microsoft.com/microsoft-365/compliance/apply-sensitivity-label-automatically?view=o365-worldwide&preserve-view=true).


#### Automatically classify, label, and protect business critical content with sensitive data on-premises

You can use the Azure Information Protection (AIP) scanner to automatically classify and protect files for SharePoint 2013 and above and on-premise file servers.

Take this step:

 - Configure the scanner to [use **enforce** mode and automatically classify, label, and protect files](https://docs.microsoft.com/azure/information-protection/deploy-aip-scanner with sensitive data.


<table border="0">
   <tr>
      <td>
         <p><img src="./media/icon-additional-deployment.png" alt="Checklist icon with two checkmarks."></p>
      </td>
      <td>
         <h2>Additional deployment objectives</h2>
      </td>
   </tr>
</table>


### III. Classification is augmented by smart machine learning models

Enterprises have vast amounts of data that can be challenging to adequately label and classify. Once you've completed the first two steps, the next step is to use machine learning for smarter classification.

Microsoft 365 provides three ways to classify content, including [manually](https://docs.microsoft.com/microsoft-365/compliance/classifier-getting-started-with?view=o365-worldwide&preserve-view=true#manually) and with [automated pattern matching](https://docs.microsoft.com/microsoft-365/compliance/classifier-getting-started-with?view=o365-worldwide&preserve-view=true#automated-pattern-matching).

[Trainable classifiers](https://docs.microsoft.com/microsoft-365/compliance/classifier-getting-started-with?view=o365-worldwide&preserve-view=true#trainable-classifiers) (preview) are a third method well-suited to content that isn't easily identified by manual or automated pattern matching methods. A classifier learns how to identify a type of content by looking at hundreds of examples of the content you\'re interested in classifying. You start by feeding it examples that are definitely in the category. Once it processes those, you test it by giving it a mix of both matching and non-matching examples. The classifier then makes predictions as to whether any given item falls into the category you\'re building. You then confirm its results, sorting out the positives, negatives, false positives, and false negatives to help increase the accuracy of its predictions. When you publish the trained classifier, it sorts through items in locations like SharePoint Online, Exchange, and OneDrive, and classifies the content.

Follow these steps:

1.  Learn [where you can use trainable classifiers](https://docs.microsoft.com/microsoft-365/compliance/classifier-getting-started-with?view=o365-worldwide&preserve-view=true#where-you-can-use-trainable-classifiers).

2.  [Create a trainable classifier](https://docs.microsoft.com/microsoft-365/compliance/classifier-creating-a-trainable-classifier?view=o365-worldwide&preserve-view=true) (preview).


### IV. Access decisions are governed by a cloud security policy engine

For data stored in Exchange, SharePoint, and OneDrive, automatic classification with sensitivity labels can be deployed via policies to targeted locations. Microsoft Cloud App Security provides additional capabilities to manage sensitive files, including:

-   The removal of collaborators to prevent excessive privilege and data leakage.

-   Placing files into quarantine for additional review.

-   Creating policies that proactively apply labels to sensitive files or in specific risky user scenarios.

Follow these steps:

1.  [Configure auto-labeling policies](https://docs.microsoft.com/microsoft-365/compliance/apply-sensitivity-label-automatically?view=o365-worldwide&preserve-view=true#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) for SharePoint, OneDrive, and Exchange.

2.  [Integrate Microsoft Cloud App
Security](https://docs.microsoft.com/cloud-app-security/azip-integration) and Microsoft Information Protection and use it to also protect data in third-party environments such as Box or G-Suite. 


### V. DLP policies secure sharing with encryption and tracking

To comply with business standards and industry regulations, organizations must protect sensitive information and prevent its inadvertent disclosure. Sensitive information can include financial data or personally identifiable information (PII) such as credit card numbers, social security numbers, or health records. With a data loss prevention (DLP) policy in the Office 365 Security & Compliance Center, you can identify, monitor, and automatically protect sensitive information across Office 365.

Follow these steps:

1.  [Learn how to protect data](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies?view=o365-worldwide&preserve-view=true) with DLP policies.

2.  [Create, test, and tune](https://docs.microsoft.com/microsoft-365/compliance/create-test-tune-dlp-policy?view=o365-worldwide&preserve-view=true#where-to-start-with-data-loss-prevention) a DLP policy.

3.  Use DLP to enforce actions (e.g., protect content, restrict access, or, in the case of an email, block from being transmitted) when content matches a set of conditions.

### Traditional data security objectives

Sensitivity labels are the foundation of the Zero Trust model for data. Defining sensitivity levels is a process of [identifying stakeholders to discuss and determine data types that are critical](https://aka.ms/MIPC/DataClassification) for enterprise businesses and that are subject to government regulation. Then a taxonomy can be made so that this type of data can be classified as Highly Confidential or Confidential, and the documents that contain this data are labelled accordingly. Similarly, a security policy decision should be made about other data-type sensitivity levels and document labels, such as General Public or Non-Business. With policy determination completed, discover files in all locations, validate contents in the files, compare them with the policy decision, and label the documents appropriately.

These activities help address risk by identifying and marking sensitive information to prevent accidental sharing of information with unauthorized entities. They also cause minimal impact to productivity as data sharing continues uninterrupted.

The following guidance will help you get started with sensitivity labels.

:::image type="content" source="./media/steps-box-data-5.png" alt-text="Diagram of the steps within phase 5 of the additional deployment objectives." border="true":::

#### Sensitivity labels are applied manually

Defining the right label taxonomy and protection policies is the most critical step in an Information Protection deployment, so start **with creating a labeling strategy** that reflects your organization's sensitivity requirements for information.

Labels indicate content sensitivity and what company policies apply. Labels are also the primary way for users to flag content that needs to be protected.

A good label taxonomy is intuitive, easy to use, and aligned with business needs. It helps prevent data leakage and misuse and addresses compliance requirements but does not prevent users from doing their job.

Follow these steps:

-   Review the [Data Classification and Sensitivity Label Taxonomy](https://aka.ms/MIPC/DataClassification) white paper.

-   Review the [Microsoft 365 Information Protection and Compliance Deployment Acceleration Guide](https://aka.ms/MIPC/DAG).

-   [Get started with sensitivity labels](https://docs.microsoft.com/microsoft-365/compliance/get-started-with-sensitivity-labels?view=o365-worldwide&preserve-view=true).


#### Automatically discover business-critical content with sensitive data on-premises

The Azure Information Protection (AIP) scanner helps discover, classify, label, and protect sensitive information in your on-premises file repositories and on-premises SharePoint 2013+ sites. The AIP scanner provides immediate insight into types of data risk before moving to the cloud.

Follow these steps:

1.  [Review prerequisites for installing the AIP scanner](https://techcommunity.microsoft.com/t5/azure-information-protection/installation-configuration-and-usage-of-the-aip-scanner/ba-p/221792).

2.  Configure the scanner in the Azure portal.

3.  Install the scanner.

4.  Get an Azure AD token for the scanner.

5.  Run a discovery cycle and view reports for the scanner.


#### Labels and classifications available to Office users on any device and manually applied to content

Once sensitivity labels have been published from Microsoft 365 Compliance Center or equivalent labeling center, there are client apps that users can leverage to classify and protect data as it is created or edited, such as the native Microsoft Office built-in labeling client or the [Azure Information Protection Unified Labeling](https://docs.microsoft.com/azure/information-protection/rms-client/aip-clientv2) client.

Follow these steps:

1.  [Compare labeling client features](https://docs.microsoft.com/azure/information-protection/rms-client/use-client#compare-the-labeling-clients-for-windows-computers) for Windows computers and [review support for sensitivity label](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide&preserve-view=true#support-for-sensitivity-label-capabilities-in-apps) capabilities in Office apps to determine what sensitivity features and platform requirements are important to your scenarios.

2.  [Start using sensitivity labels](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide&preserve-view=true) in Office apps, including [Microsoft Team sites, Microsoft 365 groups (formerly Office 365 groups), and SharePoint sites](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites?view=o365-worldwide&preserve-view=true). Sensitivity labels can also be used to [classify and label sensitive data in Power BI service](https://docs.microsoft.com/power-bi/collaborate-share/service-security-apply-data-sensitivity-labels&preserve-view=true) and can be applied to datasets, reports, dashboards, and data flows.


#### Default label applied to new content created by users

When publishing a label policy, you can identify a specific label to be applied by default to all content created by users and groups included in the policy. This label can set a floor of protection, even if no other action is taken by users or system settings.

Take this step:

 - [Learn what label policies can do](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide&preserve-view=true#what-label-policies-can-do) and what to consider when setting default labels.


#### Visual markings to indicate sensitive documents across apps and services

After a sensitivity label is created and applied to an email or document, any configured protection settings for that label are enforced on the content. When you use Office apps, watermarks can be applied to headers or footers of emails or documents that have the label applied.

:::image type="content" source="./media/data/screenshot-office-document-header-watermark-highly-confidential.png" alt-text="Screenshot of an Office document with a watermark and header about confidentiality." border="false":::

Take this step:

 - [Learn when content markings are applied](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide&preserve-view=true#when-office-apps-apply-content-marking-and-encryption).


#### Audit data to understand user labeling, classification, and protection behaviors

Once sensitivity labels have been published to your organization, you can use [data classification](https://docs.microsoft.com/microsoft-365/compliance/data-classification-overview?view=o365-worldwide&preserve-view=true) to identify sensitive content, where it's located, and exposure from user activities.

The **content explorer** tab in the Microsoft 365 Compliance Center provides a view of data at risk by displaying the amount and types of sensitive data in a particular document which can be filtered by label or sensitivity type to get a detailed view of locations where sensitive data is stored. The **Activity explorer** tab provides a view of activities related to sensitive data, sensitivity, and retention labels (such as decreased protection due to label downgrade or changes). Activity explorer also helps investigate events that could be leading towards a data leak scenario (e.g., removal of labels). Understanding these activities provides the ability to identify the right policies for protection or data loss prevention to ensure your most sensitive data is secure.

Follow these steps:

1.  [Get started with content explorer](https://docs.microsoft.com/microsoft-365/compliance/data-classification-content-explorer?view=o365-worldwide&preserve-view=true) to natively view the items summarized on the data classification overview page.

1.  [Get started with activity explorer](https://docs.microsoft.com/microsoft-365/compliance/data-classification-activity-explorer?view=o365-worldwide&preserve-view=true) to monitor the history of activities related to labeled content. 

## Conclusion

[Microsoft Information Protection](https://www.microsoft.com/security/business/information-protection) (MIP) is a comprehensive, flexible, integrated, and extensible approach to protecting sensitive data.

:::image type="content" source="./media/data/diagram-microsoft-information-protection-corporate-egress-highlighted.png" lightbox="./media/data/diagram-microsoft-information-protection-corporate-egress-highlighted.png" alt-text="Diagram of Microsoft Information Protection for data with Corporate Egress highlighted." border="false":::

For further information or help with implementation, please contact your Customer Success team.


<!--
**The Zero Trust deployment guide series**

| <img src="./media/data/image12.emf" style="width:0.34215in;height:0.34215in" /> | <img src="./media/data/image13.png" style="width:0.20833in;height:0.26316in" /> | <img src="./media/data/image15.png" style="width:0.28564in;height:0.23809in" /> | <img src="./media/data/image16.emf" style="width:0.26496in;height:0.26496in" /> | <img src="./media/data/image17.png" style="width:0.26189in;height:0.22618in" /> | <img src="./media/data/image18.png" style="width:0.2375in;height:0.26181in" /> | <img src="./media/data/image19.png" style="width:0.24653in;height:0.24653in" /> | <img src="./media/data/image20.png" style="width:0.27908in;height:0.27908in" /> |
|-----------------------------------------------------------------------------|-----------------------------------------------------------------------------|-----------------------------------------------------------------------------|-----------------------------------------------------------------------------|-----------------------------------------------------------------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| [Introduction](https://aka.ms/ZTDeploymentGuideIntroduction)                | [Identity](https://aka.ms/ZTIdentity)                                       | [Endpoints](https://aka.ms/ZTEndpoints)                                     | [Applications](https://aka.ms/ZTApplications)                               | [Data](https://aka.ms/ZTData)                                               | [Network](https://aka.ms/ZTNetwork)                                        | [Infrastructure](https://aka.ms/ZTInfrastructure)                           | [Visibility, Automation, Orchestration](https://aka.ms/ZTCrossPillars)      |
-->
