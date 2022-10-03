---
title: Secure Azure infrastructure with Zero Trust overview
description: Learn how to secure Azure infrastructure with Zero Trust.  
ms.date: 10-03-2022
ms.service: security
author: brendacarter
ms.author: bcarter
ms.topic: conceptual
ms.collection: 
  - msftsolution-accesscontrol
  - msftsolution-overview
  - zerotrust-solution
---

# Secure Azure infrastructure with Zero Trust

The following articles help you to apply the principles of Zero Trust to your workloads in Azure. These articles take a multi-disciplinary approach to apply the principles. This work is broken into units of work that can be configured together: 
- Azure Storage 
- Virtual machines (VMs) 
- Spoke Vnet for VM-based workloads  
- Hub Vnet to support access to many workloads in Azure 

Zero Trust is a security strategy. It is not a product or a service, but an approach in designing and implementing the following set of security principles: 
- Verify explicitly 
- Use least privilege access 
- Assume breach 

Zero Trust is a mindset shift to “never trust, always verify” and will require changes to cloud infrastructure, deployment strategy, and implementation. 

## Reference architecture 
The following reference architecture is used to demonstrate a common environment and to apply the principles of Zero Trust. 

Image


In the above illustration:
- The Azure environment includes: a Hub Vnet, a spoke Vnet with a VM-based workload, Azure Storage Services, and dependent PaaS services like Azure AD, Microsoft Defender for Cloud, RBAC, and Azure Monitor. 
- There are three zones that include users or admins that access the Azure environment. The three zones are Internet, office location, and on-premises data center. 

The reference illustration aligns to the recommendations in the Cloud Adoption Framework. See [Implement Cloud Adoption Framework enterprise-scale landing zones in Azure](/azure/cloud-adoption-framework/ready/enterprise-scale/implementation).  

The following illustration demonstrates how the elements of the reference architecture can sit inside an Azure tenant. This illustration presents one of the many ways to organize these resources. 

Image

In the illustration: 
1. The Azure infrastructure is contained within one Azure tenant. You can distribute the resources in more than one subscriptions. It depends on how you want to separate your environment and the number of resources you have. An Azure subscription might be under a management group. 
1. Virtual machines are contained in one resource group. You can have each virtual machine type of workload (front end, application, and database) in a different resource group to further isolate access control. 
1. The storage account is contained in a dedicated resource group. You can isolate each storage account in a different resource group for more granular permission control. 
1. Azure storage services are contained within a dedicated storage account. You can have one storage account for each type of storage workload, for example Object Storage (also called “blob”) and Azure Files. This provides more granular access control and might improve performance. 
1. The network and other resources for each of the virtual networks in the reference architecture are isolated within a resource group for each virtual network. This organization works well when responsibility for these live on different teams. Another option is to organize these components by putting all network resources in one resource group and security resources in another. It depends on how your organization is set up to manage these resources.  

## What's in this solution?
Zero Trust involves applying multiple disciplines of security and information protection together. The following illustration shows how this multi-discipline approach is applied to each of the units of work: 

Image

The following table lists the units of work illustrated and links to the articles. 

|&nbsp;|Unit of work|Description|Licensing requirements|
|---|---|---|---|
|1| Azure Storage Services  |<li>Secure data at rest, in transit, and in use. <li>Verify users and control access to storage data with least privilege.<li> Logically separate critical data with network controls.<li> Use Defender for Storage for automated threat protection. |E3, E5, F1, F3, F5|
|2|Virtual machines   |<li>Configure logical isolation and protect all components of a VM.<li> Set up multi-factor authentication to VMs and use Privileged Access Workstations.<li> Use Defender for Servers for automated threat protection.  |E3, E5, F1, F3, F5|
|3|Spoke Vnet for vm—based workloads   | <li>Create a stand-alone spoke virtual network for VM-based workloads. <li>Set up custom roles for networking resources.<li> Isolate network infrastructure into its own Resource Group.<li> Create Application Security Groups and Network Security Groups for each VM role.<li> Secure traffic and resources within the environment. Use Defender for Cloud for automated threat protection.  |E3, E5, F3, F5|
|4|Hub Vnet   | Coming soon  |E3, E5, F3, F5|

## Threat protection architecture 
Threat protection for Azure infrastructure is provided by Defender for Cloud. In each of the above articles, there are recommended settings to enable specific capabilities.  

Azure for Cloud is enabled at the Azure subscription level. If your organization is using management groups to manage many Azure subscriptions within a single Azure AD tenant, you can enable Defender for cloud for all the subscriptions within the same management group. 

Image

In the illustration: 
- The Root management group is illustrated and includes two Azure subscriptions with resource groups. Your environment might include more than one management group.  
- Defender for cloud is enabled for the Root management group in this illustration. Your environment might include additional management groups nested beneath the Root management group. Enabling Defender for Cloud for a management group provides monitoring across resources that are contained in multiple Azure subscriptions.  

For more information about configuring management groups and enabling Defender for Cloud, see: 
- [Organize subscriptions into management groups and assign roles to users](/azure/defender-for-cloud/management-groups-roles) 
- [Enable Defender for Cloud on all subscriptions in a management group](/azure/defender-for-cloud/onboard-management-group) 

Defender for Cloud is an eXtended detection and response (XDR) solution that automatically collects, correlates, and analyzes signal, threat, and alert data from across your environment. Defender for Cloud is intended to be used together with Microsoft 365 Defender to provide a greater breadth of correlated protection of your environment.  

Image

In the illustration: 
- Microsoft 365 Defender provides threat protection for the services of Microsoft 365, your SaaS apps that are integrated with Azure Active Directory (Azure AD), and your on-premises Active Directory and Active Directory Federated Services servers.  
- Microsoft Defender for Cloud provides threat protection for the Azure subscriptions managed within a management group.
 
## Training for administrators
The following training modules help provide your team with the skills that are necessary to implement the layers of protection required for Zero Trust. 


|Training:   |[Azure Fundamentals: Describe Azure architecture and services](/training/paths/azure-fundamentals-describe-azure-architecture-services/)   |
|---------|---------|
|Image     | <p> Azure Fundamentals: Describe Azure architecture and services </p> <p>The Microsoft Azure Fundamentals training is composed of three learning paths: Microsoft Azure Fundamentals: Describe cloud concepts, Describe Azure architecture and services, and Describe Azure management and governance. Microsoft Azure Fundamentals: Azure architecture and services is the second learning path in the Microsoft Azure Fundamentals course. This learning path explores Microsoft Azure, its architecture, and some of the most commonly used services and resources.</p> |

## Technical illustrations 
You can download the illustrations used in this series of articles. Use the Visio file provided to modify the illustrations for your own use. 

Image

[PDF](https://download.microsoft.com/download/f/d/b/fdb6ab0c-34bb-4cb8-84e6-5de8f13298da/m365-zero-trust-deployment-plan.pdf) | [Visio](https://download.microsoft.com/download/f/d/b/fdb6ab0c-34bb-4cb8-84e6-5de8f13298da/m365-zero-trust-deployment-plan.vsdx)

