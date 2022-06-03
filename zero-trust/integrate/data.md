---
title: Data Zero Trust integration overview
description: Independent software vendors (ISVs) can integrate their solutions with Microsoft Information Protection SDK to help customers adopt a Zero Trust model and keep their organizations secure.
ms.date: 09/17/2021
ms.service: security
author: knicholasa
ms.author: nichola
ms.topic: conceptual
---

# Data integrations

:::image type="icon" source="../media/icon-data-medium.png":::

Keeping data protected is a central objective of a Zero Trust strategy. Where possible, data should remain safe even if it leaves the devices, apps, infrastructure, and networks the organization controls. To ensure protection and that data access is restricted to authorized users, data should be inventoried, classified, labeled, and, where appropriate, encrypted.

Zero Trust data solutions help customers classify and label data based on assessed risk, and ensure that the data management is following the organization's compliance requirements.

This guidance is for software providers and technology partners who want to enhance their data security solutions by integrating with Microsoft products.

## Data Zero Trust integration guide

This integration guide includes instructions for [integrating with the Microsoft Information Protection (MIP) SDK](#microsoft-information-protection-sdk), which is the unification of Microsoft's classification, labeling, and protection services.

Independent software vendors (ISVs) can integrate with the MIP SDK to build solutions that help customers understand and protect data, prevent data loss, and govern data storage and access.

:::image type="content" source="../media/integrate/data/microsoft-information-protection-capabilities.png" alt-text="Image with the four ways ISVs can integrate with the MIP SDK. The four categories are: know your data, protect your data, prevent data loss, and govern your data.":::

### Microsoft Information Protection SDK

[Microsoft Purview Information Protection](/information-protection/develop/overview) is the unification of Microsoft's classification, labeling, and protection services. Third parties can use the MIP SDK to integrate with applications, using a standard, consistent data labeling schema and protection service.

ISVs can use the MIP SDK to help customers understand their data landscape, apply flexible protection actions, detect risky behavior to prevent data loss, and maintain data compliance through automatic actions. For example:

- Applying labels automatically to documents based on content
- Enforcing protection and controls based on labels
- Automatically classifying and protecting data coming out of apps to prevent data theft

The [Microsoft Information Protection SDK - API concepts](/information-protection/develop/concept-apis-use-cases) page includes more examples of how you can integrate with the MIP SDK.

> [!VIDEO https://www.youtube.com/embed/MjVXD4OKaLo]

### Getting started with the SDK

We have included the following guidance to help you on the journey to integrating your solutions with Azure AD.

[Microsoft Information Protection SDK](/information-protection/develop/overview#microsoft-information-protection-sdk)
This document describes common use cases for the MIP SDK, including how to get started using the SDK and building integrations. The MIP SDK exposes the labeling and protection services from Microsoft 365 Security and Compliance Center to third-party applications and services. Partners can use the SDK to build solutions with native support for applying labels and protection to files as well as reasoning over MIP-encrypted information and which actions should be taken when specific labels are detected.

[https://aka.ms/mipsdksamples](https://aka.ms/mipsdksamples)
This resource contains sample implementations showing the use of the MIP SDK in code. For example, the [.NET File Quickstart](/samples/azure-samples/mipsdk-dotnet-file-quickstart/mipsdk-dotnet-file-quickstart/) demonstrates labeling and reading labels on files.

## Next steps

- [Microsoft Information Protection SDK - Classification label concepts](/information-protection/develop/concept-classification-labels)
- [Microsoft Compliance Manager](/microsoft-365/compliance/compliance-manager)
- [Microsoft Purview Information Protection in Microsoft 365](/microsoft-365/compliance/information-protection)
- [(Video) Develop Compliance Powered LOB Applications with Microsoft Purview Information Protection](https://www.youtube.com/watch?v=DS_xN-dspKI)