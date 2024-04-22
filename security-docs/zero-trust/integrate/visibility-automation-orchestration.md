---
title: Visibility, automation, and orchestration Zero Trust integration overview
description: Independent software vendors (ISVs) can integrate their solutions with Microsoft Sentinel to help customers adopt a Zero Trust model and keep their organizations secure.
ms.date: 04/17/2024
ms.service: security
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
ms.collection:
  - zerotrust-partner
---

# Visibility, automation, and orchestration integrations

:::image type="icon" source="../media/icon-visibility-automation-orchestration-medium.png":::

Organizations today have to contend with an increasingly complex threat landscape. Assuming breach is a key principle of Zero Trust. Assuming breach effectively means having a threat detection approach with visibility across the entire estate as well as the level of depth that security teams need to drill down into individual threats.

Visibility, automation, and orchestration integrations are about building robust solutions for monitoring security signals. They're key to ensuring the ongoing security of an environment by detecting suspicious behavior and enabling proactive hunting for threats. They allow customers to scan for unexpected behavior and access and proactively search for bad actors already in the network.

This guidance is for software providers and technology partners who want to enhance their visibility, automation, and orchestration security solutions by integrating with Microsoft products.

## Visibility, automation, and orchestration Zero Trust integration guide

This integration guide includes instructions for integrating with [Microsoft Sentinel](/azure/sentinel). Microsoft Sentinel is Microsoft’s cloud-native Security Information and Event Management (SIEM) service. Independent software vendors (ISVs) can integrate with Microsoft Sentinel. This integration enables new use-cases for customers by providing data connectors, analytics rules, interactive workbooks, and automation playbooks that deliver end-to-end product, domain and industry vertical value for customers.

### Microsoft Sentinel

Microsoft’s approach to threat protection is to combine both Security Information and Event Management (SIEM) and Extended Detection and Response (XDR) into an integrated experience, with Microsoft Sentinel, Microsoft Defender XDR, and Microsoft Defender for Cloud. This approach gives organizations the best of both worlds: end-to-end threat visibility across all of your resources; correlated, prioritized alerts based on the deep understanding Microsoft has of specific resources and AI that stitches that signal together; and coordinated action across the organization.

Microsoft Sentinel, Microsoft’s cloud-native SIEM, provides a bird’s eye view across your entire digital estate. It provides intelligent security analytics across all users, devices, applications, and infrastructure, both on-premises and in multiple clouds. It then cross-correlates and detects threats using machine learning, and streamlines investigations with AI and powerful hunting tools.

Microsoft Sentinel has many integrations with partner solutions, including other security solutions, clouds, threat intelligence vendors, and more. ISVs can integrate with Microsoft Sentinel to enable new use-cases for customers with data connectors, analytics rules, interactive workbooks, and automation playbooks to deliver end-to-end product or domain or industry vertical value for customers.

The following guidance helps you create solutions that integrate with Microsoft Sentinel.

**What you can build**: [Integration Opportunities Guide for Microsoft Sentinel](https://azure.microsoft.com/resources/integration-opportunities-with-microsoft-sentinel-december-2021/)

Partners can engage with Microsoft Sentinel in several key scenarios to deliver mutual customer value. This article outlines these scenario opportunities and technical integrations by describing how to decide what integrations to build, how to get started, how to deliver to Microsoft Sentinel customers, and finally how to promote Microsoft Sentinel Integrations.

:::image type="content" source="../media/integrate/visibility-automation-orchestration/integration-opportunities.png" alt-text="Illustration of the categories of integration opportunities. The opportunities are as follows. Collecting data. Monitoring and detecting with visibility, intelligence, analytics, and hunting. Investigating incidents. Finally, responding with automation.":::

**How to build it**: [Integration Components for Microsoft Sentinel](https://github.com/Azure/Azure-Sentinel/wiki#get-started)

Once you've identified the scenarios you want to support with your solution, create a list of artifacts to implement. This resource contains a list of all the artifacts that you can build and guidance on how to build them. It's available as part of the Threat Hunters program, which is Microsoft Sentinel's community of content contributors inclusive of both partners and the community.

**How to package it**: [Guide to Building Microsoft Sentinel Solutions](https://github.com/Azure/Azure-Sentinel/tree/master/Solutions#readme)

After you've created a solution, you must publish it. This guide provides an overview of Microsoft Sentinel Solutions and how to build and publish a solution for Microsoft Sentinel.

Microsoft Sentinel Solutions allows partners to deliver combined product, domain, or vertical value via solutions in Microsoft Sentinel and be able to productize investments. It supports discoverability, deployment, and enablement of scenarios in Microsoft Sentinel. It is powered by [Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/) and the [Microsoft Partner Center](/partner-center/overview).

:::image type="content" source="../media/integrate/visibility-automation-orchestration/package-solutions.png" alt-text="Value propositions of packaged Microsoft Sentinel Solutions. For customers, they provide discovery of new value, easy deployment, and enablement. For Partners they build combined value, productize investments, and expand customer reach with marketplace offerings.":::

## Next steps

- [Build and monitor Zero Trust (TIC 3.0) security architectures with Microsoft Sentinel](sentinel-solution.md)
- [Integration Opportunities Guide for Microsoft Sentinel](https://azure.microsoft.com/resources/integration-opportunities-with-azure-sentinel-september-2021/)
- [Integration Components for Microsoft Sentinel](https://github.com/Azure/Azure-Sentinel/wiki#get-started)
- [Guide to Building Microsoft Sentinel Solutions](https://github.com/Azure/Azure-Sentinel/tree/master/Solutions#readme)
