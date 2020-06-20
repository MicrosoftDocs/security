---
title: "Microsoft information protection and storage capabilities"
ms.author: dansimp
author: dansimp
manager: dansimp
audience: Admin
ms.topic: article
localization_priority: Normal
description: "Lists capabilities that can help with information protection and storage."
---

# Microsoft information protection and storage capabilities
This article lists the capabilities that can help with information protection and storage.

## Capabilities that work with Microsoft 365 

Microsoft 365 and Office 365 include capabilities that can be applied to specific types of data to protect information across Microsoft 365 tools, including OneDrive, SharePoint Online, and mail. Some capabilities, like sensitive information types, can be used with Microsoft Cloud App Security to protect information across other SaaS apps in your environment.


|**Capability**|**More information**|
|:-----|:-----|
|[Sensitivity labels](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide) <br/> |With sensitivity labels you can classify and help protect your sensitive content. Protection options include labels, watermarks, and encryption. Sensitivity labels use Azure Information Protection. If you are using Azure Information Protection labels, for now we recommend that you avoid creating new labels in other admin centers until after you've completed your migration. See [Azure Information Protection migration](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels). <br/> [Retention labels](https://docs.microsoft.com/microsoft-365/compliance/retention-policies?view=o365-worldwide) are different than sensitivity labels. Retention labels help you retain or delete content based on policies that you define. These help organizations comply with industry regulations and internal policies.|
|[Data loss prevention](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies?view=o365-worldwide) (DLP)  <br/> |With DLP policies, you can identify, monitor, and automatically protect sensitive information across Office 365. Data loss prevention policies can use sensitivity labels and sensitive information types to identify sensitive information. <br/> |
|[Sensitive information types](https://docs.microsoft.com/microsoft-365/compliance/what-the-sensitive-information-types-look-for?view=o365-worldwide) <br/> |Microsoft 365 includes many sensitive information types that are ready for you to use in DLP policies and for automatic classification with sensitivity and retention labels. Sensitive information types can also be used with the [Azure Information Protection scanner](https://docs.microsoft.com/azure/information-protection/deploy-aip-scanner) to classify and protect files on premises. Sensitive information types define how the automated process recognizes specific information types such as health service numbers and credit card numbers.   <br/> |
|[Office 365 Message Encryption](https://docs.microsoft.com/microsoft-365/compliance/ome?view=o365-worldwide) (OME)  <br/> |With Office 365 Message Encryption, your organization can send and receive encrypted email messages between people inside and outside your organization. Office 365 Message Encryption works with Outlook.com, Yahoo!, Gmail, and other email services. Email message encryption helps ensure that only intended recipients can view message content. <br/> |
|[Azure Information Protection](https://docs.microsoft.com/azure/information-protection/)<br/> |Azure Information Protection (sometimes referred to as AIP) helps an organization to classify, label, and optionally, protect documents and emails. Administrators can automatically apply labels by defining rules and conditions. Users can manually apply labels to files and mail. You can also give users recommendations about when to apply labels.<br/> If you're using sensitivity labels or Office Message Encryption, you're already using classification and protection capabilities. If you haven't yet migrated Azure Information Protection labels to Office 365, continue to manage these in Azure Information Protection.  <br/>You can run the [Azure Information Protection scanner](https://docs.microsoft.com/azure/information-protection/deploy-aip-scanner) on premises to classify and protect files on Windows Server, network shares, and SharePoint Server sites and libraries. This can be a first step toward identifying data to migrate to Office 365.
|Azure Information Protection with customer managed encryption key <br/> |Some organizations have a business need or compliance requirement to retain control of an encryption key. This is not common. Azure Information Protection allows organizations to bring your own key (BYOK) to the service. For more information, see [Bring your own key (BYOK) for Azure Information Protection](https://docs.microsoft.com/azure/information-protection/byok-price-restrictions). Another more complex option is offered for customers who have a requirement to retain an encryption key on premises, referred to as hold your own key (HYOK).  For more information, see [Hold your own key (HYOK) for Azure Information Protection](https://docs.microsoft.com/azure/information-protection/configure-adrms-restrictions). <br/> |
| | | |


## Azure storage and encryption
<br>

|Capability  |Description |More information  |
|---------|---------|---------|
|Azure Storage |Azure Storage includes Azure Blobs (objects), Azure Data Lake Storage Gen2, Azure Files, Azure Queues, and Azure Tables. |[Azure Storage documentation](https://docs.microsoft.com/azure/storage/)|
|Azure encryption | Azure encryption options include encryption at rest, encryption in flight, and key management with Azure Key Vault| [Azure encryption overview](https://docs.microsoft.com/azure/security/fundamentals/encryption-overview)|
| | | |



## Azure SQL Database
<br>

|Capability  |Description |More information  |
|---------|---------|---------|
| Azure SQL Database| Azure SQL Database is a general-purpose relational database, provided as a managed service. With it, you can create a highly available and high-performance data storage layer for the applications and solutions in Azure. |[Azure SQL Database documentation](https://docs.microsoft.com/azure/sql-database/) |
| Azure SQL Database security capabilities| Security capabilities for data include Always encrypted and Transparent Data Encryption (TDE)| [An overview of Azure SQL Database security capabilities](https://docs.microsoft.com/azure/sql-database/sql-database-security-overview)|
| | | |

## Next steps
For additional security guidance from Microsoft, see [Microsoft security documentation](https://docs.microsoft.com/security/).

