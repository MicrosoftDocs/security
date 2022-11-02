---
title: Overview - Apply Zero Trust principles to Azure infrastructure
description: This article gives an overview of how to apply Zero Trust principles to Azure infrastructure.  
ms.date: 10/20/2022    
ms.service: security
author: rudneir2
ms.author: ruolivei
ms.topic: conceptual
ms.collection: 
  - msftsolution-accesscontrol
  - msftsolution-overview
  - zerotrust-solution
---

# Overview – Apply Zero Trust principles to Azure infrastructure 

This series of articles help you apply the principles of Zero Trust to your workloads in Azure based on a multi-disciplinary approach to applying the Zero Trust principles.
 
Zero Trust is a security strategy. It is not a product or a service, but an approach in designing and implementing the following set of security principles:
- Verify explicitly
- Use least privilege access
- Assume breach

Zero Trust mindset shift to “assume breach, never trust, always verify” requires changes to cloud infrastructure, deployment strategy, and implementation.<br> 
    These initial series of five articles (including this introduction) show you how to apply Zero Trust approach to a very common IT business scenario based on infrastructure services. The work is broken into units that can be configured together as follows:  
- Azure Storage
- Virtual machines (VMs)
- Spoke Vnet for VM-based workloads
- Hub Vnet to support access to many workloads in Azure

> [!NOTE]
> Additional articles will be added to this series in the future, including how organizations can apply a Zero Trust approach to applications, virtual desktop, data and DevOps services based on real IT business environments. 

> [!IMPORTANT]
> This Zero Trust guidance describes how to use and configure several security solutions and features available on Azure for the reference architecture. Several other resources also provide security guidance for these solutions and features, including: 
> - [Microsoft Cloud Security Benchmark](/security/benchmark/azure/introduction)
> - [Microsoft Cloud Security Baseline](/security/benchmark/azure/security-baselines-overview)

To describe how to apply a Zero Trust approach, this guidance targets a common pattern used in production by many organizations — a virtual-machine-based application hosted in a virtual network (IaaS application). This is a common pattern for organizations migrating on-premises applications to Azure (sometimes referred to as ‘lift-n-shift’). The reference architecture includes all components necessary to support this application, including storage services and a Hub virtual network.  

The reference architecture reflects a common deployment pattern in production environments. It is not based on the enterprise-scale landing zones recommended in the Cloud Adoption Framework(CAF), although many of the best practices in CAF are included in the reference architecture, such as using a dedicated virtual network to host components that broker access to the application (hub virtual network).  
If you are interested in learning about the guidance recommended in the Cloud Adoption Framework Azure landing zones, see these resources: 
- [Get started with the Cloud Adoption Framework - Cloud Adoption Framework | Microsoft Learn](/azure/cloud-adoption-framework/get-started/index)
- [What is an Azure landing zone? - Cloud Adoption Framework | Microsoft Learn](/azure/cloud-adoption-framework/ready/landing-zone/index)

## Reference architecture

The reference architecture for this Zero Trust guidance is illustrated below.

:::image type="content" source="media/azure-infra-overview-reference-architecture-1.png" alt-text="Illustration of Reference architecture for Zero Trust." lightbox="media/azure-infra-overview-reference-architecture-1.png":::

It’s important to note that the guidance in this series of articles is more specific for this type of architecture than the guidance provided in the Cloud Adoption Framework and Azure landing zone architectures. If you have applied the guidance in either of these resources, be sure to also review this series of articles for additional recommendations.  

## Infrastructure components covered in this series

This is an environment with multiple IaaS components and elements, including different types of users and IT consumers accessing the app from different sites - Azure, on-premises, internet, and branch offices.<br> 
This is a common three-tier application containing a web server tier, application tier, and data tier. All tiers run on virtual machines within a VNet called Spoke. Access to the app is protected by another VNet called Hub that contains security services that are a part of the environment.<br> 
The architecture also contains some of the most used PaaS services on Azure that support IaaS applications, including Role based access control(RBAC) and Azure AD. These contribute to the Zero Trust security approach.<br> 
Storage Blobs and Storage Files complete this example environment by providing object storage for the applications and files shared by users.<br>
This series of articles walk through the recommendations for implementing Zero Trust for the reference article by addressing each of these larger pieces illustrated below. 

:::image type="content" source="media/azure-infra-overview.png" alt-text="Illustration of Azure infrastructure components." lightbox="media/azure-infra-overview.png":::

The illustration outlines the larger areas of the architecture that are addressed by each article in this series: 
1. Azure Storage Service 
2. Virtual machines 
3. Spoke VNet 
4. Hub VNet 

## Understanding Azure components

The previous illustration of the reference architecture provides a topology view of the environment. It’s also valuable to see logically how each of the components can be organized within the Azure environment. The following illustration provides a view. Your Azure subscriptions might be organized differently and that is OK.

:::image type="content" source="media/azure-infra-overview-subscription-architecture-3.png" alt-text="Diagram of components in Azure infrastructure." lightbox="media/azure-infra-overview-subscription-architecture-3.png":::
    
In this illustration, the Azure infrastructure is contained within one Azure tenant. The following table describes the different sections shown in the illustration. 

|Section |Description  |
|---------|---------|
| Azure Subscription (1)   |  You can distribute the resources in more than one subscription, where each subscription may hold different roles, such as network subscription, security subscription, etc. This is described in the Cloud Adoption Framework and Azure Landing Zone documentation described earlier in this article. <p> The different subscriptions may also hold different environments, such as production, development, and tests environments. It depends on how you want to separate your environment and the number of resources you will have in each. One or more subscriptions can be managed together using a Management group. This will give you the ability to apply permission (Role based access control (RBAC)) and Azure policies to a group of subscriptions instead of you setting up each subscription individually.       |
| Virtual machines Resource Group (3)    | Virtual machines are contained in one resource group. You can have each virtual machine type of workload like front end, application, and database in a different resource group to further isolate access control.        |
| Storage Resource group (2)    | The storage account is contained in a dedicated resource group. You can isolate each storage account in a different resource group for more granular permission control.        |
| Storage accounts (4)    | Azure storage services are contained within a dedicated storage account. You can have one storage account for each type of storage workload, for example an Object Storage (also called “Blob”) and Azure Files. This provides more granular access control and might improve performance.         |
| Network and Security Resource group (5)   | The network and other resources for each of the virtual networks in the reference architecture are isolated within a resource group for each virtual network. This organization works well when responsibility for these live on different teams. Another option is to organize these components by putting all network resources in one resource group and security resources in another. It depends on how your organization is set up to manage these resources.          |
| Azure Monitor and Microsoft Defender for Cloud (MDC)   | For each Azure subscription, a set of Azure Monitor solutions and a Microsoft Defender for Cloud (MDC) is available. If you manage these subscriptions through Management Group, you will be able to consolidate in a single panel (same screen) all the functionalities of Azure Monitor and Microsoft Defender for Cloud. For example, Secure Score, provided by MDC, will be consolidated for all your subscriptions, using Management Group as the scope.  |

## Threat Protection with Microsoft Defender for Cloud

**Microsoft Defender for Cloud** is an extended detection and response (XDR) solution that automatically collects, correlates, and analyzes signal, threat, and alert data from across your environment. Defender for Cloud is intended to be used together with Microsoft 365 Defender to provide a greater breadth of correlated protection of your environment, as you can see in the diagram below.

For more information about configuring management groups and enabling Defender for Cloud, see:
- [Organize subscriptions into management groups and assign roles to users](/azure/defender-for-cloud/management-groups-roles)
- [Enable Defender for Cloud on all subscriptions in a management group](/azure/defender-for-cloud/onboard-management-group)

:::image type="content" source="media/azure-infra-overview-threat-protection.png" alt-text="Illustration of Threat Protection with Microsoft Defender for Cloud." lightbox="media/azure-infra-overview-threat-protection.png":::

In the illustration: 
- Defender for Cloud is enabled for a management group that includes multiple Azure subscriptions. 
- Microsoft 365 Defender is enabled for the Microsoft 365 apps and data, SaaS apps that are integrated with Azure AD, and on-premises Active Directory servers.

## Security solutions in this series of articles

Zero Trust involves applying multiple disciplines of security and information protection together. In this series of articles, this multi-discipline approach is applied to each of the units of work for infrastructure components as follows:

**[Apply Zero Trust principles to Virtual machines in Azure](azure-infrastructure-virtual-machines.md)**
- Configure logical isolation by deploying virtual machines to a dedicated resource group.
- Leverage Role Based Access Control (RBAC).
- Secure virtual machine boot components — boot loaders, OS kernels, and drivers. Securely protect keys, certificates, and secrets in the Trusted Platform Module (TPM).
- Enable customer-managed keys and double encryption.
- Control the applications that are installed on virtual machines.
- Configure secure access (not illustrated).
- Set up secure maintenance of virtual machines (not illustrated).
- Enable advanced threat detection and protection (not illustrated).    

**[Apply Zero Trust principles to Storage in Azure](azure-infrastructure-storage.md)**
- Protect data in all three modes: data at rest, data in transit, and data in use.
- Verify users and control access to storage data with the least privilege.
- Logically separate or segregate critical data with network controls.
- Use Defender for Storage for automated threat detection and protection.

**[Apply Zero Trust principles to Spoke Virtual Network in Azure](azure-infrastructure-iaas.md)**
- Leverage Azure AD RBAC or set up custom roles for networking resources.
- Isolate infrastructure into its own resource group.
- Create a network security group for each subnet.
- Create an application security group for each virtual machine role.
- Secure traffic and resources within the virtual network.
- Deploy baseline deny rules for network security groups.
- Deploy application specific rules for application security groups.
- Plan for management traffic into the virtual network. 
- Deploy network security group flow logging.
- Secure access to the virtual network and application.
- Enable advanced threat detection and protection.

**[Apply Zero Trust principles to Hub Virtual network in Azure](azure-infrastructure-networking.md)**
- Secure Azure Firewall Premium
- Deploy Azure DDoS Protection Standard
- Configure network gateway routing to the firewall
- Threat protection

## Recommended training for Zero Trust 

The following are the recommended training modules for Zero Trust:

### Azure management and governance
|Training  |[Describe Azure management and governance](/training/paths/describe-azure-management-governance/)  |
|---------|---------|
|:::image type="icon" source="media/describe-azure-management-governance-resized.png" border="false":::    | The Microsoft Azure Fundamentals training is composed of three learning paths: Microsoft Azure Fundamentals: Describe cloud concepts, Describe Azure architecture and services, and Describe Azure management and governance. Microsoft Azure Fundamentals: Describe Azure management and governance is the third learning path in Microsoft Azure Fundamentals. This learning path explores the management and governance resources available to help you manage your cloud and on-premises resources.<br>This learning path helps prepare you for [Exam AZ-900: Microsoft Azure Fundamentals.](/certifications/exams/az-900)|
> [!div class="nextstepaction"]
> [Start >](/training/modules/describe-cost-management-azure/1-introduction)

### Configure Azure Policy
|Training  |[Configure Azure Policy](/training/modules/configure-azure-policy/)|
|---------|---------|
|:::image type="icon" source="media/azure-policy-configure.png" border="false"::: | Learn how to configure Azure Policy to implement compliance requirements.<br> In this module, you learn how to: <li>Create management groups to target policies and spending budgets.<li>Implement Azure Policy with policy and initiative definitions.<li>Scope Azure policies and determine compliance.|
> [!div class="nextstepaction"]
> [Start >](/training/modules/configure-azure-policy/1-introduction)

### Manage Security operation 
|Training  |[Manage Security operation](/training/paths/manage-security-operation/)|
|---------|---------|
| :::image type="icon" source="media/operation-manage-security-resized.png" border="false":::   | Once you have deployed and secured your Azure environment, learn to monitor, operate, and continuously improve the security of your solutions.<br> This learning path helps prepare you for [Exam AZ-500: Microsoft Azure Security Technologies](/certifications/exams/az-500).|
> [!div class="nextstepaction"]
> [Start >](/training/modules/azure-monitor/1-introduction)

### Configure Storage security  
|Training  |[Configure Storage security](/training/modules/configure-storage-security/)|
|---------|---------|
|:::image type="icon" source="media/storage-security-configure.png" border="false"::: | Learn how to configure common Azure Storage security features like storage access signatures.<br>In this module, you learn how to:<li>Configure a shared access signature (SAS), including the uniform resource identifier (URI) and SAS parameters.<li>Configure Azure Storage encryption.<li>Implement customer-managed keys.<li>Recommend opportunities to improve Azure Storage security.|
> [!div class="nextstepaction"]
> [Start >](/training/modules/configure-storage-security/1-introduction)

### Configure Azure Firewall  
|Training  |[Configure Azure Firewall](/training/modules/configure-azure-firewall/)|
|---------|---------|
|:::image type="icon" source="media/azure-firewall-configure.png" border="false"::: | You will learn how to configure the Azure Firewall including firewall rules.<br>After completing this module, you will be able to:<li>Determine when to use Azure Firewall.<li>Implement Azure Firewall including firewall rules.|
> [!div class="nextstepaction"]
> [Start >](/training/modules/configure-azure-firewall/1-introduction)

For more training on Security on Azure, see the entire Microsoft catalog:<br> 
[Browse all - Training | Microsoft Learn](/training/browse)

## Next Steps

- [Apply Zero Trust principles to Storage in Azure](azure-infrastructure-storage.md)
- [Apply Zero Trust principles to Virtual machines in Azure](azure-infrastructure-virtual-machines.md)
- [Apply Zero Trust principles to Spoke Virtual Network in Azure](azure-infrastructure-iaas.md)
- [Apply Zero Trust principles to Hub Virtual network in Azure](azure-infrastructure-networking.md)

## References

Refer to the links below to learn about the various services and technologies mentioned in this article. 
- [What is Azure - Microsoft Cloud Services | Microsoft Azure](https://azure.microsoft.com/resources/cloud-computing-dictionary/what-is-azure/)
- [Azure Infrastructure as a Service (IaaS) I Microsoft Azure](https://azure.microsoft.com/resources/cloud-computing-dictionary/what-is-azure/azure-iaas/#benefits)
- [Virtual Machines (VMs) for Linux and Windows | Microsoft Azure](https://azure.microsoft.com/products/virtual-machines/) 
- [Introduction to Azure Storage - Cloud storage on Azure | Microsoft Learn](/azure/storage/common/storage-introduction) 
- [Azure Virtual Network | Microsoft Learn](/azure/virtual-network/virtual-networks-overview)
- [Introduction to Azure security | Microsoft Learn](/azure/security/fundamentals/overview) 
- [Zero Trust implementation guidance | Microsoft Learn](/security/zero-trust/zero-trust-overview)
- [Overview of the Microsoft cloud security benchmark | Microsoft Learn](/security/benchmark/azure/overview) 
- [Security baselines for Azure overview | Microsoft Learn](/security/benchmark/azure/security-baselines-overview)
- [Building the first layer of defense with Azure security services - Azure Architecture Center | Microsoft Learn](/azure/architecture/solution-ideas/articles/azure-security-build-first-layer-defense)
- [Microsoft Cybersecurity Reference Architectures - Security documentation | Microsoft Learn](/security/cybersecurity-reference-architecture/mcra)

## Technical illustrations

You can download the illustrations used in this series of articles. Use the Visio file to modify these illustrations for your own use.

[PDF](https://download.microsoft.com/download/f/d/b/fdb6ab0c-34bb-4cb8-84e6-5de8f13298da/m365-zero-trust-deployment-plan.pdf) | [Visio](https://download.microsoft.com/download/f/d/b/fdb6ab0c-34bb-4cb8-84e6-5de8f13298da/m365-zero-trust-deployment-plan.vsdx)
Updated October 2022

