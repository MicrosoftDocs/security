---
title: Visibility, automation, and orchestration Zero Trust integration overview
description: Independent software vendors (ISVs) can integrate their solutions with Azure Sentinel to help customers adopt a Zero Trust model and keep their organizations secure.
ms.date: 09/17/2021
ms.service: security
author: knicholasa
ms.author: nichola
ms.topic: conceptual
---

# Visibility, automation, and orchestration integrations

:::image type="icon" source="../media/icon-visibility-automation-orchestration-medium.png":::

Organizations today have to contend with an increasingly complex threat landscape. A key tenant of Zero Trust is assuming breach, and doing that effectively means having a threat detection approach that provides breadth of visibility across the entire estate as well as the depth security teams need to drill down into individual threats.

Visibility, automation, and orchestration integrations are about building robust solutions for monitoring security signals. They are key to ensuring the ongoing security of an environment by detecting suspicious behavior and enabling proactive hunting for threats. They allow customers to scan for unexpected behavior and access and proactively search for bad actors already in the network.

This guidance is for software providers and technology partners who want to enhance their visibility, automation, and orchestration security solutions by integrating with Microsoft products.

## Visibility, automation, and orchestration Zero Trust integration guide

This integration guide includes instructions for integrating with Azure Sentinel. Azure Sentinel is Microsoft’s cloud-native Security Information and Event Management (SIEM)service. Independent software vendors (ISVs) can integrate with Azure Sentinel to enable new use-cases for customers with data connectors, analytics rules, interactive workbooks, and automation playbooks to deliver end-to-end product or domain or industry vertical value for customers.

### Azure Sentinel

Microsoft’s approach to threat protection is to combine both Security Information and Event Management (SIEM) and Extended Detection and Response (XDR) into an integrated experience, with Azure Sentinel, Microsoft 365 Defender, and Azure Defender. This gives organizations the best of both worlds: end-to-end threat visibility across all of your resources; correlated, prioritized alerts based on the deep understanding Microsoft has of specific resources and AI that stitches that signal together; and coordinated action across the organization.

Azure Sentinel, Microsoft’s cloud-native SIEM, provides a bird’s eye view across your entire digital estate. It provides intelligent security analytics across all users, devices, applications, and infrastructure, both on-premises and in multiple clouds, cross-correlates and detects threats using machine learning, and streamlines investigations with AI and powerful hunting tools.

Azure Sentinel has many integrations with partner solutions, including other security solutions, clouds, threat intelligence vendors, and more. ISVs can integrate with Azure Sentinel to enable new use-cases for customers with data connectors, analytics rules, interactive workbooks, and automation playbooks to deliver end-to-end product or domain or industry vertical value for customers.

The following guidance will help you create solutions that integrate with Azure Sentinel.

**What you can build**: [Integration Opportunities Guide for Azure Sentinel](foo.md)

Partners can engage with Azure Sentinel in several key scenarios to deliver mutual customer value. This article outlines these scenario opportunities and technical integrations, how to decide what integrations to build, how to get started, how to deliver to Azure Sentinel customers, and finally how to promote Azure Sentinel Integrations.

:::image type="content" source="../media/integrate/visibility-automation-orchestration/integration-opportunities.png" alt-text="Alt text that describes the content of the image.":::

**How to build it**: [Integration Components for Azure Sentinel](https://github.com/Azure/Azure-Sentinel/wiki#get-started)

Once you have identified the scenarios you want to support with your solution, you will come up with a list of artifacts to implement. This resource contains a list of all the artifacts that you can build and guidance on how to build them. It is available as part of the Threat Hunters program, which is Azure Sentinel's community of content contributors inclusive of both partners and the community.

**How to package it**: [Guide to Building Azure Sentinel Solutions](https://github.com/Azure/Azure-Sentinel/tree/master/Solutions#readme)

Once you have created a solution, you will want to publish it. This guide provides an overview of Azure Sentinel Solutions and how to build and publish a solution for Azure Sentinel.

Azure Sentinel Solutions allows partners to deliver combined product, domain, or vertical value via solutions in Azure Sentinel and be able to productize investments. It supports discoverability, deployment, and enablement of scenarios in Azure Sentinel. It is powered by [Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/) as well as the [Microsoft Partner Center](/partner-center/overview).

:::image type="content" source="../media/integrate/visibility-automation-orchestration/package-solutions.png" alt-text="Visualization of the three steps for creating a solution. First, create content. Then, package that content. Finally, publish the solution.":::

## Next steps
- [Integration Opportunities Guide for Azure Sentinel](foo.md)
- [Integration Components for Azure Sentinel](https://github.com/Azure/Azure-Sentinel/wiki#get-started)
- [Guide to Building Azure Sentinel Solutions](https://github.com/Azure/Azure-Sentinel/tree/master/Solutions#readme)
