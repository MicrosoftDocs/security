---
title: Overview - Apply Zero Trust principles to Azure services
description: This article gives an overview of how to apply Zero Trust principles to Microsoft Azure services.
ms.date: 06/08/2023    
ms.service: security
author: sikovatc
ms.author: sikovatc
ms.topic: conceptual
ms.collection: 
  - msftsolution-azureiaas
  - msftsolution-overview
  - zerotrust-solution
---

# Overview – Apply Zero Trust principles to Azure services

This series of articles help you apply the principles of Zero Trust to your services in Microsoft Azure using a multi-disciplinary approach to applying the Zero Trust principles. Zero Trust is a security strategy. It is not a product or a service, but an approach in designing and implementing the following set of security principles:

- Verify explicitly
- Use least privileged access
- Assume breach

Implementing the Zero Trust “never trust, always verify” mindset requires changes to cloud infrastructure, deployment strategy, and implementation.

These articles show you how to apply Zero Trust approach to these new or already deployed Azure services:

- [Azure IaaS overview](azure-infrastructure-overview.md)
  - [Azure storage](azure-infrastructure-storage.md)
  - [Virtual machines](azure-infrastructure-virtual-machines.md)
  - [Spoke virtual networks](azure-infrastructure-iaas.md)
  - [Hub virtual networks](azure-infrastructure-networking.md)
- [Azure Virtual Desktop](azure-infrastructure-avd.md)
- [Azure Virtual WAN](azure-virtual-wan.md)
- [IaaS applications in Amazon Web Services](secure-iaas-apps.md)
- [Microsoft Sentinel and Microsoft 365 Defender](/security/operations/siem-xdr-overview)

For more information about recommendations in your Cloud Adoption Framework and Azure landing zones, see these resources:

- [Get started with the Cloud Adoption Framework](/azure/cloud-adoption-framework/get-started/index)
- [What is an Azure landing zone?](/azure/cloud-adoption-framework/ready/landing-zone/index)

## Content architecture

The following figure shows the content architecture for this Zero Trust guidance.

:::image type="content" source="media/apply-zero-trust-azure-services-overview/content-architecture.png" alt-text="Diagram of the content architecture for applying Zero Trust to Azure services." lightbox="media/apply-zero-trust-azure-services-overview/content-architecture.png":::

This architecture contains the set of platform and workload articles to apply Zero Trust principles to Azure services. You apply the guidance in the articles in a stack from the bottom up. The articles don't need to be followed in the order indicated in all cases but all of the platform articles should be implemented for the workload for Zero Trust-based protection.

| Workload | Platform set of articles |
| --- | --- |
| IaaS apps in Amazon Web Services (AWS) | Cloud identity infrastructure > Microsoft Sentinel and Microsoft 365 Defender |
| Azure Virtual Desktop | Cloud identity infrastructure > Microsoft Sentinel and Microsoft 365 Defender > Hub VNets (traditional) OR vWAN (Microsoft-managed) |
| Virtual machines | Cloud identity infrastructure > Microsoft Sentinel and Microsoft 365 Defender > Hub VNets (traditional) OR vWAN (Microsoft-managed) > Spoke VNets with Azure IaaS services > Storage <br><br> For Windows and Linux servers, onboard them to Microsoft Defender for Endpoint |

It’s important to note that the guidance in this series of articles is more specific for this type of architecture than the guidance provided in the Cloud Adoption Framework and Azure landing zone architectures. If you have applied the guidance in either of these resources, be sure to also review this series of articles for additional recommendations.  

## Recommended training for Zero Trust

The following are the recommended training modules for Zero Trust.

### Azure management and governance

|Training  |[Describe Azure management and governance](/training/paths/describe-azure-management-governance/)  |
|---------|---------|
|:::image type="icon" source="media/describe-azure-management-governance-resized.png" border="false":::    | The Microsoft Azure Fundamentals training is composed of three learning paths: Microsoft Azure Fundamentals: Describe cloud concepts, Describe Azure architecture and services, and Describe Azure management and governance. Microsoft Azure Fundamentals: Describe Azure management and governance is the third learning path in Microsoft Azure Fundamentals. This learning path explores the management and governance resources available to help you manage your cloud and on-premises resources. <br>This learning path helps prepare you for [Exam AZ-900: Microsoft Azure Fundamentals.](/certifications/exams/az-900)|
> [!div class="nextstepaction"]
> [Start >](/training/modules/describe-cost-management-azure/1-introduction)

### Configure Azure Policy

|Training  |[Configure Azure Policy](/training/modules/configure-azure-policy/)|
|---------|---------|
|:::image type="icon" source="media/azure-policy-configure.png" border="false"::: | Learn how to configure Azure Policy to implement compliance requirements.<br> In this module, you learn how to: <li>Create management groups to target policies and spending budgets. <li>Implement Azure Policy with policy and initiative definitions. <li>Scope Azure policies and determine compliance.|
> [!div class="nextstepaction"]
> [Start >](/training/modules/configure-azure-policy/1-introduction)

### Manage security operation

|Training  |[Manage Security operation](/training/paths/manage-security-operation/)|
|---------|---------|
| :::image type="icon" source="media/operation-manage-security-resized.png" border="false":::   | Once you have deployed and secured your Azure environment, learn to monitor, operate, and continuously improve the security of your solutions.<br> This learning path helps prepare you for [Exam AZ-500: Microsoft Azure Security Technologies](/certifications/exams/az-500).|
> [!div class="nextstepaction"]
> [Start >](/training/modules/azure-monitor/1-introduction)

## Next Steps

See these additional articles for applying Zero Trust principles to Azure services:

- For Azure IaaS:
  - [Azure storage](azure-infrastructure-storage.md)
  - [Virtual machines](azure-infrastructure-virtual-machines.md)
  - [Spoke virtual networks](azure-infrastructure-iaas.md)
  - [Hub virtual networks](azure-infrastructure-networking.md)
- [Azure Virtual Desktop](azure-infrastructure-avd.md)
- [Azure Virtual WAN](azure-virtual-wan.md)
- [IaaS applications in Amazon Web Services](secure-iaas-apps.md)
- [Microsoft Sentinel and Microsoft 365 Defender](/security/operations/siem-xdr-overview)

## Technical illustrations

This poster provides a single-page, at-a-glance view of the content architecture of applying the "never trust, always verify" principles of the Zero Trust to Azure services.

| Item | Related solution guides |
|:-----|:-----|
|[![Illustration of applying Zero Trust to Azure infrastructure services.](media/tech-illus/apply-zero-trust-to-azure-services-poster-thumb.png)](https://microsoft.sharepoint-df.com/:u:/t/ZeroTrustAdvisoryV-Team/Eb5YW2wc2mVOvN6-pgj8hMsBT16-FdpybfnviQUEQaPMRQ?e=WVelVw) <br/> [PDF](https://microsoft.sharepoint-df.com/:u:/t/ZeroTrustAdvisoryV-Team/Eb5YW2wc2mVOvN6-pgj8hMsBT16-FdpybfnviQUEQaPMRQ?e=WVelVw) \| [Visio](https://microsoft.sharepoint-df.com/:u:/t/ZeroTrustAdvisoryV-Team/Eb5YW2wc2mVOvN6-pgj8hMsBT16-FdpybfnviQUEQaPMRQ?e=WVelVw) <br/> Updated June 2023 | <ul><li>[Azure IaaS services](azure-infrastructure-overview.md)</li><li>[Azure Virtual Desktop](azure-infrastructure-avd.md)</li><li>[Azure Virtual WAN](azure-virtual-wan.md)</li><li>[IaaS applications in Amazon Web Services](secure-iaas-apps.md)</li><li>[Microsoft Sentinel and Microsoft 365 Defender](/security/operations/siem-xdr-overview)</li></ul>|

For additional technical illustrations, click [here](zero-trust-tech-illus.md).

<!---

TO DO: Add section to zero-trust-tech-illus.md. 

--->

## References

Refer to the links below to learn about the various services and technologies mentioned in this article.

- [What is Azure - Microsoft Cloud Services](https://azure.microsoft.com/resources/cloud-computing-dictionary/what-is-azure/)
- [Introduction to Azure security](/azure/security/fundamentals/overview)
- [Zero Trust implementation guidance](/security/zero-trust/zero-trust-overview)
- [Overview of the Microsoft cloud security benchmark](/security/benchmark/azure/overview)
- [Security baselines for Azure overview](/security/benchmark/azure/security-baselines-overview)
- [Building the first layer of defense with Azure security services](/azure/architecture/solution-ideas/articles/azure-security-build-first-layer-defense)
- [Microsoft Cybersecurity Reference Architectures](/security/cybersecurity-reference-architecture/mcra)
