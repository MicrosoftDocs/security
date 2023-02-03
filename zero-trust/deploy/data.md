---
title: Secure data with Zero Trust
description: Protecting data is one of the primary responsibilities of security and compliance teams. To ensure protection and that data access is restricted to authorized users, data should be inventoried, classified, labeled, and, where appropriate, encrypted. 
ms.date: 09/30/2020
ms.service: security
author: garycentric
ms.author: v-gmoor
ms.topic: conceptual
---

# Secure data with Zero Trust

:::image type="icon" source="../media/icon-data-medium.png":::

**Background**

Zero Trust is a security strategy used to design security principles for your organization. Zero Trust helps secure corporate resources by implementing the following security principles:

-   **Verify explicitly**. Always authenticate and authorize based on all available data points, including user identity, location, device health, service or workload, data classification, and anomalies.

-   **Use least privilege access**. Limit user access with just-in-time (JIT) and just-enough-access (JEA), risk-based adaptive policies, and data protection to help secure both data and productivity.

-   **Assume breach**. Minimize the blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses.

Microsoft Purview proposes five core elements for a data defense in depth strategy and a Zero Trust implementation for data:

1.  Data classification and labeling  
    If you don't know what sensitive data you have on-premises and in cloud services, you can't adequately protect it. Discover and detect data across your entire organization and classify it by sensitivity level.

2.  Information Protection  
    Conditional and least privilege access to sensitive data reduce data security risks. Apply sensitivity-based access control guardrails, rights management and encryption where environmental controls are insufficient. Use information sensitivity markings to increase awareness and security policy compliance.

3.  Data Loss Prevention  
    Access control resolves only part of the problem. Checking and controlling risky data activities and movements which may result in a data security or compliance incident allows organizations to prevent oversharing of sensitive data.

4.  Insider Risk Management  
    Data access may not always provide the whole story. Minimize risks to data by enabling behavioral detection from a broad array of signals, and acting on potentially malicious and inadvertent activities in your organization that could be precursors to or an indication of a data breach.

5.  Data Governance  
    Proactively managing the lifecycle of sensitive data reduces its exposure. Limit the number of copies or propagation of sensitive data and delete data that is no longer needed to minimize data breach risks.


## Data Zero Trust deployment objectives

<table border="0">
   <tr>
      <td colspan="2">
         <p>We recommend you focus on these initial deployment objectives when implementing an end-to-end Zero Trust framework for data:</p>
	  </td>
   </tr>
   <tr>
      <td>
		 <p><img src="../media/icon-initial-deployment-small.png" alt="List icon with one checkmark."></p>
      </td>
      <td>
	     <p><b>I.</b> <a href="#i-classify-label-and-discover-sensitive-data">Classify and label data. </a>Automatically classify and label data where possible. Apply manually where it is not.</p>
         <p><b>II.</b> <a href="#ii-apply-encryption-access-control-and-content-markings>Apply encryption, access control, and content markings. </a> Apply encryption where protection and access control are insufficient.</p>
        <p><b>III.</b> <a href="#iii-control-access-to-data">Control access to data.</a> Ensure that access and usage policy decisions are inclusive of data sensitivity.</p>
      </td>
   </tr>
   <tr>
      <td colspan="2">
         <p>As you make progress achieving the above objectives, add these additional deployment objectives:</p>
      </td>
   </tr>
   <tr>
      <td>
		 <p><img src="../media/icon-additional-deployment-small.png" alt="List icon with two checkmarks."></p>
      </td>
      <td>
         <p><b>IV.</b> <a href="#iv-prevent-data-leakage">Prevent data leakage. </a>Use DLP policies that are driven by risky signals and data sensitivity.</p>
         <p><b>V.</b> <a href="#manage-insider-risks">Manage risks.</a> Manage risks that may lead to a data security incident by checking risky security related user activities and data activity patterns that may result in a data security or compliance incident.</p>
         <p><b>VI.</b> <a href="#vi-delete-unnecessary-sensitive-information">Reduce data exposure.</a> Reduce data exposure through data governance and continual data minimization</p>
      </td>
   </tr>
</table>

##   Zero Trust deployment guide for data

This guide will walk you step-by-step through a Zero Trust approach to data protection. Please keep in mind that these items will vary widely depending on the sensitivity of your information and the size and complexity of your organization.

As a precursor to any data security implementation, Microsoft recommends that you create a data classification framework and sensitivity label taxonomy that defines high level categories of data security risk. That taxonomy will be used to simplify everything from data inventory or activity insights, to policy management to investigation prioritization.

For more information, see:

-   [Create a well-designed data classification framework](/compliance/assurance/assurance-create-data-classification-framework)

<br/><br/>
<!-- H2 heading, "Initial deployment objectives" -->
[!INCLUDE [H2 heading, Initial deployment objectives](../includes/deployment-objectives-initial.md)]


### I. Classify, label and discover sensitive data

An information protection strategy needs to encompass your organization's entire digital content.

Classifications and sensitivity labels let you understand where your sensitive data is located, how it moves, and implement appropriate access and usage controls consistent with zero trust principles:

-   Use automated classification and labeling to detect sensitive information and scale discovery across your data estate.

-   Use manual labeling for documents and containers, and manually curate data sets used in analytics where classification and sensitivity is best established by knowledgeable users.

Follow these steps:

-   [Learn about sensitive information types](/microsoft-365/compliance/sensitive-information-type-learn-about)

-   [Learn about trainable classifiers](/microsoft-365/compliance/classifier-learn-about)

-   [Learn about sensitivity labels](/microsoft-365/compliance/sensitivity-labels)

Once you have configured and tested classification and labeling, scale up data discovery across your data estate.

Follow these steps to extend discovery beyond Microsoft 365 services:

-   [Get started with the Microsoft Purview on-premises scanner](/microsoft-365/compliance/dlp-on-premises-scanner-get-started)

-   [Discover and protect sensitive information in SaaS applications](/defender-cloud-apps/tutorial-dlp)

-   [Learn about scans and ingestion in the Microsoft Purview governance portal](/azure/purview/concept-scans-and-ingestion#scanning)

As you discover, classify and label your data, use those insights to remediate risk and inform your policy management initiatives.

Follow these steps:

-   [Get started with Content Explorer](/microsoft-365/compliance/data-classification-content-explorer)

-   [Review labeling activity with Activity Explorer](/microsoft-365/compliance/data-classification-activity-explorer)

-   [Learn about Data Insights](/azure/purview/concept-insights)


### II. Apply encryption, access control and content markings

Simplify your least privilege implementation by using sensitivity labels to protect your most sensitive data with encryption and access control. Use content markings to enhance user awareness and traceability.

#### Protect document and emails

Microsoft Purview Information Protection enables access and usage control based on sensitivity labels or user defined permissions for documents and emails. It can also optionally apply markings and encrypt information that resides in or flows out to lesser trust environments internal or external to your organization. It provides protection at rest, in motion, and in use for enlightened applications.

Follow these steps:

-   [Review encryption options in Microsoft 365](/microsoft-365/compliance/encryption)
-   [Restrict access to content and usage by using sensitivity labels](/microsoft-365/compliance/encryption-sensitivity-labels)

#### Protect documents in Exchange, SharePoint, and OneDrive

For data stored in Exchange, SharePoint, and OneDrive, automatic classification with sensitivity labels can be deployed via policies to targeted locations to restrict access and manage encryption on authorized egress.

Take this step:

-   [Configure auto-labeling policies](/microsoft-365/compliance/apply-sensitivity-label-automatically#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange for SharePoint, OneDrive, and Exchange.



### III. Control access to data 
Providing access to sensitive data must be controlled so that they are better protected. Ensure that access and usage policy decisions are inclusive of data sensitivity.


#### Control data access and sharing in Teams, Microsoft 365 Groups and SharePoint sites

Use container sensitivity labels to implement conditional access and sharing restrictions to Microsoft Teams, Microsoft 365 Groups or SharePoint sites.

Take this step:

-   [Use sensitivity labels with Microsoft Teams, Microsoft 365 Groups, and SharePoint sites](/microsoft-365/compliance/sensitivity-labels-teams-groups-sites#how-to-configure-groups-and-site-settings)


#### Control access to data in SaaS applications

Microsoft Defender for Cloud Apps provides additional capabilities for conditional access and to manage sensitive files in Microsoft 365 and third-party environments such as Box or Google Workspace, including:

-   Removing permissions to address excessive privilege and prevent data leakage.

-   Quarantining files for review.

-   Applying labels to sensitive files.

Follow these steps:

-   [Integrate Microsoft Purview Information Protection](/defender-cloud-apps/azip-integration)


>[!TIP]
>Check out [Integrate SaaS apps for Zero Trust with Microsoft 365](/security/zero-trust/integrate-saas-apps) to learn how to apply Zero Trust principles to help manage your digital estate of cloud apps. 

#### Control access to in IaaS/PaaS storage

Deploy mandatory access control policies to IaaS/PaaS resources that contain sensitive data.

Take this step:

-   [Learn about Microsoft Purview DevOps policies](/azure/purview/concept-policies-devops)

### IV. Prevent data leakage

Controlling access to data is necessary but insufficient in exerting control over data movement and in preventing inadvertent or unauthorized data leakage or loss. That is the role of data loss prevention and insider risk management, which is described in section IV.

Use Microsoft Purview DLP policies to identify, check, and automatically protect sensitive data across:

-   Microsoft 365 services such as Teams, Exchange, SharePoint, and OneDrive

-   Office applications such as Word, Excel, and PowerPoint

-   Windows 10, Windows 11 and macOS (three latest released versions) endpoints

-   on-premises file shares and on-premises SharePoint

-   non-Microsoft cloud apps.

Follow these steps:

-   [Plan for data loss prevention](/microsoft-365/compliance/dlp-overview-plan-for-dlp)

-   [Create, test, and tune DLP policies](/microsoft-365/compliance/dlp-create-deploy-policy)

-   [Learn about the data loss prevention Alerts dashboard](/microsoft-365/compliance/dlp-alerts-dashboard-learn)

-   [Review data activity with Activity Explorer](/microsoft-365/compliance/data-classification-activity-explorer)

### V. Manage insider risks

Least privilege implementations help minimize known risks, but it is also important to correlate additional security related user behavioral signals, check sensitive data access patterns, and to broad detection, investigation and hunting capabilities.

Take these steps:

-   [Learn about Insider Risk Management](/microsoft-365/compliance/insider-risk-management-solution-overview)

-   [Investigate insider risk management activities](/microsoft-365/compliance/insider-risk-management-activities)

### VI. Delete unnecessary sensitive information

Organizations can reduce their data exposure by managing the lifecycle of their sensitive data.

Remove all privileges where you can by deleting the sensitive data itself when it is no longer valuable or permissible for your organization.

Take this step:

- [Implement Data Lifecycle Management and Records Management](https://microsoft.github.io/ComplianceCxE/dag/mig-rm/)

Minimize duplication of sensitive data by favoring in-place sharing and use rather than data transfers.

Take this step:

-   [Learn about in-place data sharing with Microsoft Purview](/azure/purview/concept-data-share)

## Products covered in this guide

[Microsoft Purview](/security/business/microsoft-purview)

[Microsoft Defender for Cloud Apps](/microsoft-365/enterprise-mobility-security/cloud-app-security)

For further information or help with implementation, please contact your Customer Success team.





<br/><br/>
<!-- Include the nav bar. -->
[!INCLUDE [navbar, bottom](../includes/navbar-bottom.md)]
