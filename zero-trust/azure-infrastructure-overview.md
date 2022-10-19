---
title: Overview of how to secure Azure infrastructure with Zero Trust
description: This article gives an overview of how to secure Azure infrastructure with Zero Trust.  
ms.date:     
ms.service: security
author: brendacarter
ms.author: bcarter
ms.topic: conceptual
ms.collection: 
  - msftsolution-accesscontrol
  - msftsolution-overview
  - zerotrust-solution
---

# Overview - Secure Azure infrastructure with Zero Trust

The following series of articles help you to apply the principles of Zero Trust to your workloads in Azure based on a multi-disciplinary approach of applying the Zero Trust principles.

Zero Trust is a security strategy. It is not a product or a service, but an approach in designing and implementing the following set of security principles:

- Verify explicitly
- Use least privilege access
- Assume breach

Zero Trust is a mindset shift to "never trust, always verify" and will require changes to cloud infrastructure, deployment strategy, and implementation.

The following series of articles (including this overview) help you to apply Zero Trust approach to a scenario based on infrastructure services, that will be broken into units of work that can be configured together as:

- Azure Storage
- Virtual machines (VMs)
- Spoke Vnet for VM-based workloads
- Hub Vnet to support access to many workloads in Azure

More articles will be added to the series in the future, including how companies may apply Zero Trust approach for applications, virtual desktop, data and devOps services based on real customer's environment, that will explain in detail what Azure security services and companies will have to work with to accomplish Zero Trust approach.

> [!IMPORTANT]
> Zero Trust approach takes into consideration several security solutions and features available on Azure. But, you will also find many of these security services in different security perspectives, such as:
> - [Microsoft Cloud Security Benchmark](/security/benchmark/azure/introduction)
> - [Microsoft Cloud Security Baseline](/security/benchmark/azure/security-baselines-overview)

The application of Zero Trust principles will be demonstrated based on a real IT business environment, using a real customer scenario found in many companies around the world, especially the ones that have just migrated into Azure based on a lift-n-shift strategy and are planning to get a better secure posture.

This real IT business environment we are using as a reference to apply Zero Trust approach, doesn't take into consideration the best practices that are documented under Microsoft CAF and Enterprise Landscape Scale Zone (ELSZ), as this is intended to focus on scenarios where CAF and ELSZ was not applied, that is the majority of situation that we find in the field.

For more information about CAF and ELSZ best practices, refer:

- [Get started with the Cloud Adoption Framework - Cloud Adoption Framework | Microsoft Learn](/azure/cloud-adoption-framework/get-started/index)
- [What is an Azure landing zone? - Cloud Adoption Framework | Microsoft Learn](/azure/cloud-adoption-framework/ready/landing-zone/index)

## Reference architecture

The reference architecture for this Zero Trust guidance is illustrated below.

Illustration

It’s important to note that the guidance in this series of articles is more specific for this type of architecture than the guidance provided in the Cloud Adoption Framework and Azure landing zone architectures. If you have applied the guidance in either of these resources, be sure to also review this set of articles for additional recommendations.  

## Infrastructure components covered in this series

This is an environment with multiple IaaS components and elements, including different types of users and IT consumers accessing the app from different sites — Azure, on-premises, internet, and branch offices. 
This is a common three-tier application containing a web server tier, application tier, and data tier. All tiers run on virtual machines within a VNet called Spoke. Access to the app is protected by another VNet called Hub that contains security services that are part of the environment. 
The architecture also contains some of the most used PaaS services on Azure that support IaaS applications, including RBAC and Azure AD. These contribute to the Zero Trust security approach. 
Storage Blobs and Storage Files complete this example environment by providing object storage for the applications and files shared by users.
This series of articles walk through the recommendations for implementing Zero Trust for the reference article by addressing each of these larger pieces illustrated below. 

Image

The illustration outlines the larger areas of the architecture that are addressed by each article in this series: 
1. Azure Storage Service 
2. Virtual machines 
3. Spoke VNet 
4. Hub VNet 

## Understanding Azure components

The previous illustration of the reference architecture provides a topology view of the environment. It’s also valuable to see logically how each of the components can be organized within the Azure environment. The following illustration provides a view. Your Azure subscriptions might be organized differently and that is OK.

Illustration
    
In this illustration, the Azure infrastructure is contained within one Azure tenant. The following table describes the different sections shown in the illustration. 

|Section |Description  |
|---------|---------|
|(a) Azure Subscription    |  You can distribute the resources in more than one subscription, where each subscription may hold different roles, such as network subscription, security subscription, etc. This is described in the Cloud Adoption Framework and Azure Landing Zone documentation described earlier in this article. <p> The different subscriptions may also hold different environments, such as production, development, and tests environments. It depends on how you want to separate your environment and the number of resources you will have in each. One or more subscriptions can be managed together using a Management group. This will provide you some functionalities such as applying permission (Role based access control (RBAC)) and Azure policies to a group of subscriptions instead of you setting up each subscription individually.       |
|(b) Virtual machines Resource Group     | Virtual machines are contained in one resource group. You can have each virtual machine type of workload like front end, application, and database in a different resource group to further isolate access control.        |
|(c) Storage Resource group     | The storage account is contained in a dedicated resource group. You can isolate each storage account in a different resource group for more granular permission control.        |
|(d) Storage accounts     | Azure storage services are contained within a dedicated storage account. You can have one storage account for each type of storage workload, for example an Object Storage (also called “Blob”) and Azure Files. This provides more granular access control and might improve performance.         |
|(e) Network and Security Resource group    | The network and other resources for each of the virtual networks in the reference architecture are isolated within a resource group for each virtual network. This organization works well when responsibility for these live on different teams. Another option is to organize these components by putting all network resources in one resource group and security resources in another. It depends on how your organization is set up to manage these resources.          |
|(f)) Azure Monitor and Microsoft Defender for Cloud (MDC)   | For each Azure subscription, a set of Azure Monitor solutions and a Microsoft Defender for Cloud (MDC) is available. If you manage these subscriptions through Management Group, you will be able to consolidate in a single panel (same screen) all the functionalities of Azure Monitor and Microsoft Defender for Cloud. For example, Secure Score, provided by MDC, will be consolidated for all your subscriptions, using Management Group as the scope.         |

## Threat Protection with Microsoft Defender for Cloud

**Microsoft Defender for Cloud** is an extended detection and response (XDR) solution that automatically collects, correlates, and analyzes signal, threat, and alert data from across your environment. Defender for Cloud is intended to be used together with Microsoft 365 Defender to provide a greater breadth of correlated protection of your environment, as you can see in the diagram below.

For more information about configuring management groups and enabling Defender for Cloud, see:

- [Organize subscriptions into management groups and assign roles to users](/azure/defender-for-cloud/management-groups-roles)
- [Enable Defender for Cloud on all subscriptions in a management group](/azure/defender-for-cloud/onboard-management-group)

image

## Security solutions in this series of articles

Zero Trust involves applying multiple disciplines of security and information protection together. In this series of articles, this multi-discipline approach is applied to each of the units of work for infrastructure components as follows:

**Virtual Machines**
- Configure logical isolation by deploying virtual machines to a dedicated resource group
- Leverage Role Based Access Control (RBAC)
- Secure virtual machine boot components — boot loaders, OS kernels, and drivers. Securely protect keys, certificates, and secrets in the Trusted Platform Module (TPM)
- Enable customer-managed keys and double encryption
- Control the applications that are installed on virtual machines
- Configure secure access (not illustrated)
- Set up secure maintenance of virtual machines (not illustrated)
- Enable advanced threat detection and protection (not illustrated)

**Storage**
- Protect data in all three modes: data at rest, data in transit, and data in use
- Verify users and control access to storage data with the least privilege
- Logically separate or segregate critical data with network controls
- Use Defender for Storage for automated threat detection and protection

**Spoke (Workload) Virtual Network**

- Leverage Azure AD RBAC or set up custom roles for networking resources
- Isolate infrastructure into its own resource group
- Create a network security group for each subnet
- Create an application security group for each virtual machine role
- Secure traffic and resources within the virtual network
- Deploy baseline deny rules for network security groups
- Deploy application specific rules for application security groups
- Plan for management traffic into the virtual network (might be covered in subsequent section)
- Deploy network security group flow logging
- Secure access to the virtual network and application
- Enable advanced threat detection and protection

**Hub Virtual Network**
- Secure Azure Firewall Premium
- Deploy Azure DDoS Protection Standard
- Configure network gateway routing to the firewall
- Threat protection

## Recommended training for Zero Trust 

- Describe Azure management and governance 
- Configure Azure Policy 
- Manage Security operation 
- Configure Storage security 
- Configure Azure Firewall 

## Next Steps

- Article 2 (link to be added)
- Article 3 (link to be added)
- Article 4 (link to be added)
- Article 5 (link to be added)

## References

See links below for the related services and technologies:

- Service 1
- Service 2
- Service 3
- Service 4
- Service 5
- Service 6

## Technical illustrations

You can download the illustrations used in this series of articles. Use the Visio file to modify these illustrations for your own use.


Illustration

Image
[PDF](https://download.microsoft.com/download/f/d/b/fdb6ab0c-34bb-4cb8-84e6-5de8f13298da/m365-zero-trust-deployment-plan.pdf) | [Visio](https://download.microsoft.com/download/f/d/b/fdb6ab0c-34bb-4cb8-84e6-5de8f13298da/m365-zero-trust-deployment-plan.vsdx)
Updated October 2022

