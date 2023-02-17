---
title: Apply Zero Trust principles to Azure Virtual Desktop
description: Learn how to secure an Azure Virtual Desktop deployment with Zero Trust principles. 
ms.date: 02/17/2023
ms.service: security
author: JoeDavies-TechWriter
ms.author: v-joedavies
ms.topic: conceptual
ms.collection: 
  - msftsolution-azurepaas
  - msftsolution-scenario
  - zerotrust-solution
---

# Apply Zero Trust principles to an Azure Virtual Desktop deployment

This article provides steps to apply the [principles of Zero Trust](zero-trust-overview.md#guiding-principles-of-zero-trust) to an Azure Virtual Desktop deployment in the following ways:

| Zero Trust principle | Definition | Met by |
| --- | --- | --- |
| Verify explicitly |Always authenticate and authorize based on all available data points. | Verify the identities and endpoints of Azure Virtual Desktop users and secure access to session hosts. |
| Use least privileged access |  Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection. | <ul><li> Confine access to session hosts and their data. </li><li> Storage: Protect data in all three modes: data at rest, data in transit, data in use. </li><li> Virtual networks (VNets): Specify allowed network traffic flows between hub and spoke VNets with Azure Firewall. </li><li> Virtual machines: Use Role Based Access Control (RBAC). </li></ul>  |
| Assume breach | Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses. | <ul><li> Isolate the components of an Azure Virtual Desktop deployment. </li><li> Storage: Use Defender for Storage for automated threat detection and protection. </li><li> VNets: Prevent traffic flows between workloads with Azure Firewall. </li><li> Virtual machines: Use double encryption for end-to-end encryption, enable encryption at host, secure maintenance for virtual machines, and Microsoft Defender for Servers for threat detection. </li><li> 	Azure Virtual Desktop: Use Azure Virtual Desktop security, governance, management, and monitoring features to improve defenses and collect session host analytics. </li></ul>
 |

For more information about how to apply the principles of Zero Trust across an Azure IaaS environment, see the [Apply Zero Trust principles to Azure infrastructure overview](azure-infrastructure-overview.md).

## Reference architecture

In this article, we'll use the following reference architecture for Hub and Spoke to demonstrate a commonly deployed environment and how to apply the principles of Zero Trust for Azure Virtual Desktop with users’ access over the Internet. [Azure Virtual WAN](/azure/virtual-wan/virtual-wan-about) architecture is also supported in addition to private access over a managed network with [RDP Shortpath for Azure Virtual Desktop](/azure/virtual-desktop/rdp-shortpath?tabs=managed-networks).

:::image type="content" source="media/avd/ref-arch-avd.png" alt-text="Diagram of the reference architecture for Azure Virtual Desktop." lightbox="media/avd/ref-arch-avd.png":::

The Azure environment for Azure Virtual Desktop includes:

| Component | Description |
| --- | --- |
| A | Azure Storage Services for Azure Virtual Desktop user profiles. |
| B | A connectivity hub VNet. |
| C | A spoke VNet with Azure Virtual Desktop session host virtual machine-based workloads. |
| D | An Azure Virtual Desktop Control Plane. |
| E | An Azure Virtual Desktop Management Plane. |
| F | Dependent PaaS services including Azure Active Directory (Azure AD), Microsoft Defender for Cloud, role-based access control (RBAC), and Azure Monitor. |
| G | Azure Compute Gallery. |

Users or admins that access the Azure environment can originate from the internet, office locations, or on-premises datacenters.

This reference architecture aligns to the architecture described in the [Enterprise-scale landing zone for Azure Virtual Desktop](/azure/cloud-adoption-framework/scenarios/wvd/enterprise-scale-landing-zone) Cloud Adoption Framework.

## Logical architecture

In this diagram, the Azure infrastructure for an Azure Virtual Desktop deployment is contained within one Azure AD tenant.

:::image type="content" source="media/avd/logical-arch-avd.png" alt-text="Diagram of the components of Azure Virtual Desktop in an Azure AD tenant." lightbox="media/avd/logical-arch-avd.png":::

The elements of the logical architecture are:

- Azure subscription for your Azure Virtual Desktop

  You can distribute the resources in more than one subscription, where each subscription may hold different roles, such as network subscription, or security subscription. This is described in [Cloud Adoption Framework and Azure Landing Zone](/azure/cloud-adoption-framework/scenarios/wvd/enterprise-scale-landing-zone). The different subscriptions may also hold different environments, such as production, development, and tests environments. It depends on how you want to separate your environment and the number of resources you will have in each. One or more subscriptions can be managed together using a Management Group. This will give you the ability to apply permissions with RBAC and Azure policies to a group of subscriptions instead of setting up each subscription individually.

- Azure Virtual Desktop resource group

  A separate resource group for a Key Vault and service objects are isolated with an Azure Virtual Desktop resource group.

- Storage resource group

  Resources provided by the Azure Files service private endpoints and data sets are isolated with a storage resource group.

- Session host virtual machines resource group

  The virtual machines for their session hosts and an Application Security Group are isolated with a dedicated resource group.

- Spoke VNet resource group

  The spoke VNet resources and a Network Security Group are isolated within a dedicated resource group, which can then be managed by networking specialists in your organization.

## What’s in this article?

This article walks through the steps to apply the principles of Zero Trust across the Azure Virtual Desktop reference architecture.

| Step | Task | Zero Trust principle(s) applied |
| --- | --- | --- |
| 1 | Secure your identities with Zero Trust. | Verify explicitly |
| 2 | Secure your endpoints with Zero Trust. | Verify explicitly |
| 3 | Apply Zero Trust principles to Azure Virtual Desktop storage resources. | Verify explicitly <br> Use least privileged access <br> Assume breach |
| 4 | Apply Zero Trust principles to hub and spoke Azure Virtual Desktop VNets. |  Verify explicitly <br> Use least privileged access <br> Assume breach |
| 5 | Apply Zero Trust principles to Azure Virtual Desktop session host. | Verify explicitly <br> Use least privileged access <br> Assume breach |
| 6 | Deploy security, governance, and compliance to Azure Virtual Desktop. | Assume breach |
| 7 | Deploy secure management and monitoring to Azure Virtual Desktop. | Assume breach |

## Step 1. Secure your identities with Zero Trust

To apply Zero Trust principles to the identities used in Azure Virtual Desktop:

- Azure Virtual Desktop supports different types of [identities](/azure/virtual-desktop/prerequisites#supported-identity-scenarios). Use the information in [Securing identity with Zero Trust](/security/zero-trust/deploy/identity) to ensure that your chosen identity types adhere to Zero Trust principles.
- Create a dedicated user account with least privileges that you will need to join session hosts to an Azure AD DS or AD DS domain during session host [deployment](/azure/virtual-desktop/prerequisites#deployment-parameters).

## Step 2. Secure your endpoints with Zero Trust

Endpoints are the devices through which users access the Azure Virtual Desktop environment and session host virtual machines. Use the instructions in the [Endpoint integration overview](/security/zero-trust/integrate/endpoints) and use Microsoft Defender for Endpoint and Microsoft Endpoint Manager to ensure that your endpoints adhere to your security and compliance requirements.

## Step 3. Apply Zero Trust principles to Azure Virtual Desktop storage resources

Implement the steps in [Apply Zero Trust principles to Storage in Azure](azure-infrastructure-storage.md) for the storage resources being used in your Azure Virtual Desktop deployment. These steps ensure that you:

- Secure your Azure Virtual Desktop data at rest, in transit, and in use.
- Verify users and control access to storage data with the least privileges.
- Implement private endpoints for storage accounts.
- Logically separate critical data with network controls. Such as separate storage accounts for different host pools and other purposes such as with MSIX app attach file shares.
- Use Defender for Storage for automated threat protection.

>[!Note]
>In some designs, [Azure NetApp files](/azure/virtual-desktop/create-fslogix-profile-container) is the storage service of choice for FSLogix profiles for Azure Virtual Desktop via an SMB share. Azure NetApp Files provides built-in security features that include [delegated subnets](/azure/azure-netapp-files/azure-netapp-files-delegate-subnet) and [security benchmarks](/security/benchmark/azure/baselines/azure-netapp-files-security-baseline?toc=%2Fazure%2Fazure-netapp-files%2FTOC.json).
>

## Step 4. Apply Zero Trust principles to hub and spoke Azure Virtual Desktop VNets

A hub VNet is a central point of connectivity for multiple spoke virtual networks. Implement the steps in [Apply Zero Trust principles to a hub virtual network in Azure](azure-infrastructure-networking.md) for the hub VNet being used to filter outbound traffic from your session hosts.

A spoke VNet isolates the Azure Virtual Desktop workload and contains the session host virtual machines. Implement the steps in [Apply Zero Trust principles to spoke virtual network in Azure](azure-infrastructure-iaas.md) for the spoke VNet that contain the session host/virtual machines.

Isolate different host pools on separate VNets using [NSG](/azure/virtual-network/network-security-groups-overview) with the required URL necessary for Azure Virtual Desktop. Azure Firewall or a network virtual appliance (NVA) firewall can be used to control and restrict outbound traffic for Azure Virtual Desktop session hosts.

Use the instructions [here](/azure/firewall/protect-azure-virtual-desktop?tabs=azure) for Azure Firewall to protect session hosts. Force the traffic through the firewall with [User-Defined Routes (UDRs)](/azure/virtual-network/virtual-networks-udr-overview#user-defined) linked to the host pool subnet. Review the full list of required [Azure Virtual Desktop URLs](/azure/virtual-desktop/safe-url-list?tabs=azure) to configure your firewall. Azure Firewall provides an Azure Virtual Desktop [FQDN Tag](/azure/firewall/fqdn-tags#current-fqdn-tags) to simplify this configuration.

## Step 5. Apply Zero Trust principles to Azure Virtual Desktop session hosts

Session hosts are virtual machines that run inside a spoke VNet. Implement the steps in [Apply Zero Trust principles to virtual machines in Azure](azure-infrastructure-virtual-machines.md) for the virtual machines being created for your session hosts.

[Host pools](/azure/virtual-desktop/environment-setup#host-pools) should have separated organizational units (OUs) if managed by [group policies](/windows-server/remote/remote-desktop-services/clients/rdp-files?context=%2Fazure%2Fvirtual-desktop%2Fcontext%2Fcontext) on [Active Directory Domain Services (AD DS)](/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview).

Microsoft Defender for Endpoint is an enterprise endpoint security platform designed to help enterprise networks prevent, detect, investigate, and respond to advanced threats. You can use Microsoft Defender for Endpoint for session hosts. for more information, see [virtual desktop infrastructure (VDI) devices](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-vdi).

## Step 6. Deploy security, governance, and compliance to Azure Virtual Desktop

Azure Virtual Desktop has built-in advanced security features to protect session hosts. However, see the following articles to improve the security defenses of your Azure Virtual Desktop environment and session hosts:

- [Azure Virtual Desktop security best practices](/azure/virtual-desktop/security-guide)
- [Azure security baseline for Azure Virtual Desktop](/security/benchmark/azure/baselines/azure-virtual-desktop-security-baseline?context=%2Fazure%2Fvirtual-desktop%2Fcontext%2Fcontext)

In addition, see the key design considerations and recommendations for [security, governance, and compliance](/azure/cloud-adoption-framework/scenarios/wvd/eslz-security-governance-and-compliance) in Azure Virtual Desktop landing zones in accordance with Microsoft's Cloud Adoption Framework.

## Step 7. Deploy secure management and monitoring to Azure Virtual Desktop

Management and continuous monitoring are important to ensure that your Azure Virtual Desktop environment is not engaging in malicious behavior. Use [Azure Virtual Desktop Insights](/azure/virtual-desktop/insights) to log data and report diagnostic and usage data.

See these additional articles:

- Review recommendations from [Azure Advisor for Azure Virtual Desktop](/azure/virtual-desktop/azure-advisor-recommendations).
- Use [Microsoft Intune](/azure/virtual-desktop/management#microsoft-intune) for granular policy management or [group policy management](/windows-server/remote/remote-desktop-services/rds-vdi-recommendations).
- Review and set [RDP Properties](/azure/virtual-desktop/rdp-properties) for granular settings on a host pool level.

## Recommended training

### Secure an Azure Virtual Desktop deployment

|Training  |[Secure an Azure Virtual Desktop deployment](/training/modules/m365-wvd-security/)|
|---------|---------|
|:::image type="icon" source="media/secure-avd-deployment.svg" border="false"::: | Learn about the Microsoft security capabilities that help keep your applications and data secure in your Microsoft Azure Virtual Desktop deployment. |
> [!div class="nextstepaction"]
> [Start >](/training/modules/m365-wvd-security/)

### Protect your Azure Virtual Desktop deployment by using Azure

|Training  |[Protect your Azure Virtual Desktop deployment by using Azure](/training/modules/protect-virtual-desktop-deployment-azure-firewall/)|
|---------|---------|
|:::image type="icon" source="media/protect-virtual-desktop-deployment-azure-firewall.svg" border="false"::: | Deploy Azure Firewall, route all network traffic through Azure Firewall, and configure rules. Route the outbound network traffic from the Azure Virtual Desktop host pool to the service through Azure Firewall. |
> [!div class="nextstepaction"]
> [Start >](/training/modules/protect-virtual-desktop-deployment-azure-firewall/)

### Manage access and security for Azure Virtual Desktop

|Training  |[Manage access and security for Azure Virtual Desktop](/training/paths/manage-access-security/)|
|---------|---------|
|:::image type="icon" source="media/manage-access-and-security.svg" border="false"::: | Learn how to plan and implement Azure roles for Azure Virtual Desktop and implement Conditional Access policies for remote connections. This learning path aligns with exam AZ-140: Configuring and Operating Microsoft Azure Virtual Desktop. |
> [!div class="nextstepaction"]
> [Start >](/training/paths/manage-access-security/)

### Design for user identities and profiles

|Training  |[Design for user identities and profiles](/training/modules/design-user-identities-profiles/)|
|---------|---------|
|:::image type="icon" source="media/3-design-for-user-identities-and-profiles.svg" border="false"::: | Your users require access to those applications both on-premises and in the cloud. You use the Remote Desktop client for Windows Desktop to access Windows apps and desktops remotely from a different Windows device. |
> [!div class="nextstepaction"]
> [Start >](/training/modules/design-user-identities-profiles/)

For more training on security in Azure, see these resources in the Microsoft catalog:<br> 
[Security in Azure](/training/browse/?subjects=security&products=azure)

## Next Steps

See these additional articles for applying Zero Trust principles to Azure IaaS:

- [Apply Zero Trust principles to Azure infrastructure overview](azure-infrastructure-overview.md)
- [Apply Zero Trust principles to Azure storage](azure-infrastructure-storage.md)
- [Apply Zero Trust principles to virtual machines](azure-infrastructure-virtual-machines.md)
- [Apply Zero Trust principles to a spoke virtual network in Azure](azure-infrastructure-iaas.md)
- [Apply Zero Trust principles to a hub virtual network in Azure](azure-infrastructure-networking.md)

## References

Refer to the links below to learn about the various services and technologies mentioned in this article.

- [What is Azure - Microsoft Cloud Services](https://azure.microsoft.com/resources/cloud-computing-dictionary/what-is-azure/)
- [Azure Infrastructure as a Service (IaaS)](https://azure.microsoft.com/resources/cloud-computing-dictionary/what-is-azure/azure-iaas/)
- [Virtual Machines (VMs) for Linux and Windows](https://azure.microsoft.com/products/virtual-machines/)
- [Introduction to Azure Storage - Cloud storage on Azure](/azure/storage/common/storage-introduction)
- [Azure Virtual Network](/azure/virtual-network/virtual-networks-overview)
- [Introduction to Azure security](/azure/security/fundamentals/overview)
- [Zero Trust implementation guidance](/security/zero-trust/zero-trust-overview)
- [Overview of the Microsoft cloud security benchmark](/security/benchmark/azure/overview)
- [Security baselines for Azure overview](/security/benchmark/azure/security-baselines-overview)
- [Building the first layer of defense with Azure security services - Azure Architecture Center](/azure/architecture/solution-ideas/articles/azure-security-build-first-layer-defense)
- [Microsoft Cybersecurity Reference Architectures - Security documentation](/security/cybersecurity-reference-architecture/mcra)
