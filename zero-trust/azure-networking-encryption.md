---
title: Apply Zero Trust principles to encrypting Azure-based network communication
description: How to apply Zero Trust principles to encrypting Azure-based network communication.  
ms.date: 03/18/2024
ms.service: security
author: brsteph
ms.author: bstephenson
ms.topic: conceptual
ms.collection: 
  - msftsolution-azureiaas
  - msftsolution-scenario
  - zerotrust-solution
  - zerotrust-azure
---

# Apply Zero Trust principles to encrypting Azure-based network communication

<!---

Writers notes:

For updates to product names, please also update the appropriate figures.

To update figures that are not screen shots, your options are:

- Locate the source Visio file in internal storage.
- Use the published Visio file in the Microsoft Download Center (see the "Technical publications" section of this article).
- For figures that are published in Scalable Vector Graphics (SVG) format, save the SVG file from the article web page, insert into Visio, modify, and then save it as a new version of the SVG file.

For any updates to figures, please update the corresponding posters as needed (see the "Technical publications" section of this article) and republish the Visio and PDF files in the Microsoft Download Center.

For new articles in this content set, please:

- Add cross-links in the "Next Steps" section FROM all the other articles in this content set TO the new article.
- Add a link to the Zero Trust Guidance Center page (index.yml).
- Update the "Content architecture" figure in the apply-zero-trust-azure-services-overview.md article as needed.

--->

This article provides guidance to applying the [principles of Zero Trust](zero-trust-overview.md) for encrypting network communication to, from, and across Azure environments in the following ways. 

| Zero Trust principle | Definition | Met by |
| --- | --- | --- |
| Verify explicitly | Always authenticate and authorize based on all available data points. | Using Conditional Access policies for your Azure VPN Gateway connections and Secure Shell (SSH) and Remote Desktop Protocol (RDP) for your user-to-virtual machine connections. |
| Use least privileged access | Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection. | Configuring your Microsoft Enterprise Edge (MSEE) devices to use static CAK for Azure ExpressRoute with direct ports and using managed identity to authenticate ExpressRoute circuit resources. |
| Assume breach | Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses. | Protecting network traffic with encryption methods and protocols that provide confidentiality, integrity, and authenticity of your data in transit. <br><br> Using Azure Monitor to provide ExpressRoute network performance metrics and alerts. <br><br> Using Azure Bastion to manage individual sessions from the Bastion service and delete or force a disconnect.|

<!---
This article is a part of a series of articles that demonstrate how to apply the principles of Zero Trust for Azure networking.
--->

The levels of encryption for network traffic are:

- Network layer encryption

  - Secure and verify communication from the Internet or your on-premises network to Azure VNets and virtual machines

   - Secure and verify communication within and across Azure VNets
 
- Application layer encryption

  - Protection for Azure Web Applications

- Protection for workloads running on Azure virtual machines


## Reference architecture

The following diagram shows the reference architecture for this Zero Trust guidance for encrypted communication between users and admins on-premises or on the Internet and components in the Azure environment for the steps described in this article.

>> add

:::image type="content" source="media/hub/azure-infra-hub-architecture-1.svg" alt-text="The reference architecture for the components of a hub virtual network with Zero Trust principles applied." lightbox="media/hub/azure-infra-hub-architecture-1.svg":::
 
In the diagram, the numbers correspond to the steps in the following sections.

## What's in this article?

Zero Trust principles are applied across the reference architecture, from users and admins on the Internet or your on-premises network to and within the Azure cloud. The following table describes the recommendations for ensuring the encryption of network traffic across this architecture.

| Step | Task | Zero Trust principle(s) applied |
| --- | --- | --- |
| 1 | Implement network layer encryption. | Verify explicitly <br> Use least privileged access <br> Assume breach |
| 2 | Secure and verify communication from an on-premises network to Azure VNets. | Verify explicitly <br> Assume breach |
| 3 | Secure and verify communication within and across Azure VNets. | Assume breach |
| 4 | Implement application layer encryption. | Verify explicitly <br> Assume breach |
| 5 | Use Azure Bastion to protect Azure virtual machines. | Assume breach |

## Step 1: Implement network layer encryption


## Step 2: Secure and verify communication from an on-premises network to Azure VNets


## Step 3: Secure and verify communication within and across Azure VNets


## Step 4: Implement encryption at the application layer


## Step 5: Use Azure Bastion to protect Azure virtual machines

[Azure Bastion](/azure/bastion/bastion-overview) is a managed PaaS service that allows you securely connect to your virtual machines over a TLS connection. This connectivity can be established from the Azure portal or through a native client to the private IP address on the virtual machine. Advantages of using Bastion include: 

- Azure virtual machines don't need a public IP address. Connections are over TCP port 443 for HTTPS and can traverse most firewalls.
- Virtual machines are protected against port scanning.
- The Azure Bastion platform is constantly updated and protected against zero-day exploits.

With Bastion, you can control the RDP and SSH connectivity to your virtual machine from a single point of entry. You can manage individual sessions from the Bastion service in the Azure portal. You can also delete or force a disconnect of an on-going remote session if you suspect a user isn't supposed to be connecting to that machine.

To protect your Azure virtual machine, deploy [Azure Bastion](/azure/bastion/tutorial-create-host-portal) and begin using RDP and SSH to connect to your virtual machines with their private IP addresses.


## Recommended training

- [Connect your on-premises network to Azure with VPN Gateway](/training/modules/connect-on-premises-network-with-vpn-gateway/)
- [Connect your on-premises network to the Microsoft global network by using ExpressRoute](https://learn.microsoft.com/en-us/training/modules/connect-on-premises-network-with-expressroute/)
- [Introduction to Azure Front Door](https://learn.microsoft.com/en-us/training/modules/intro-to-azure-front-door/)
- [Configure Azure Application Gateway](https://learn.microsoft.com/en-us/training/modules/configure-azure-application-gateway/)
- [Introduction to Azure Bastion](https://learn.microsoft.com/en-us/training/modules/intro-to-azure-bastion/)


- [Configure Azure Policy](/training/modules/configure-azure-policy/)
- [Design and implement network security](/training/modules/design-implement-network-security-monitoring/)
- [Configure Azure Firewall](/training/modules/configure-azure-firewall/)
- [Configure VPN Gateway](/training/modules/configure-vpn-gateway/)
- [Introduction to Azure DDoS Protection](/training/modules/introduction-azure-ddos-protection/)
- [Resolve security threats with Microsoft Defender for Cloud](/training/modules/resolve-threats-with-azure-security-center/)

For more training on security in Azure, see these resources in the Microsoft catalog:<br> 
[Security in Azure | Microsoft Learn](/training/browse/?subjects=security&products=azure)

## Next Steps

See these additional articles for applying Zero Trust principles to Azure:

- [Azure IaaS overview](azure-infrastructure-overview.md)
  - [Azure storage](azure-infrastructure-storage.md)
  - [Virtual machines](azure-infrastructure-virtual-machines.md)
  - [Spoke virtual networks](azure-infrastructure-iaas.md)
  - [Spoke virtual networks with Azure PaaS services](azure-infrastructure-paas.md)
- [Azure Virtual Desktop](azure-infrastructure-avd.md)
- [Azure Virtual WAN](azure-virtual-wan.md)
- [IaaS applications in Amazon Web Services](secure-iaas-apps.md)
- [Microsoft Sentinel and Microsoft Defender XDR](/security/operations/siem-xdr-overview)

## Technical illustrations

This poster provides a single-page, at-a-glance view of the components of Azure IaaS as reference and logical architectures, along with the steps to ensure that these components have the "never trust, always verify" principles of the Zero Trust model applied.

| Item | Description |
|:-----|:-----|
|[![Thumbnail figure for the Apply Zero Trust to Azure IaaS infrastructure poster.](media/tech-illus/apply-zero-trust-to-Azure-IaaS-infra-poster-thumb.png)](https://download.microsoft.com/download/d/8/b/d8b38a95-803c-4956-88e6-c0de68f7f8e9/apply-zero-trust-to-Azure-IaaS-infra-poster.pdf) <br/> [PDF](https://download.microsoft.com/download/d/8/b/d8b38a95-803c-4956-88e6-c0de68f7f8e9/apply-zero-trust-to-Azure-IaaS-infra-poster.pdf) \| [Visio](https://download.microsoft.com/download/d/8/b/d8b38a95-803c-4956-88e6-c0de68f7f8e9/apply-zero-trust-to-Azure-IaaS-infra-poster.vsdx) <br/> Updated February 2023 | Use this illustration together with this article: [Apply Zero Trust principles to Azure IaaS overview](azure-infrastructure-overview.md) <br/><br/>**Related solution guides** <br/> <ul><li>[Azure Storage services](azure-infrastructure-storage.md)</li><li>[Virtual machines](azure-infrastructure-virtual-machines.md)</li><li>[Spoke VNets](azure-infrastructure-iaas.md)</li></ul>|


This poster provides the reference and logical architectures and the detailed configurations of the separate components of Zero Trust for Azure IaaS. Use the pages of this poster for separate IT departments or specialties or, with the Microsoft Visio version of the file, customize the diagrams for your infrastructure.

| Item | Description |
|:-----|:-----|
|[![Thumbnail figure for the Diagrams for applying Zero Trust to Azure IaaS infrastructure poster.](media/tech-illus/apply-zero-trust-to-Azure-IaaS-infra-diagrams-thumb.png)](https://download.microsoft.com/download/c/e/a/ceac5996-7cbf-4184-aed8-16dffcad3795/apply-zero-trust-to-Azure-IaaS-infra-diagrams.pdf) <br/> [PDF](https://download.microsoft.com/download/c/e/a/ceac5996-7cbf-4184-aed8-16dffcad3795/apply-zero-trust-to-Azure-IaaS-infra-diagrams.pdf) \| [Visio](https://download.microsoft.com/download/c/e/a/ceac5996-7cbf-4184-aed8-16dffcad3795/apply-zero-trust-to-Azure-IaaS-infra-diagrams.vsdx) <br/> Updated February 2023 | Use these diagrams together with the articles starting here: [Apply Zero Trust principles to Azure IaaS overview](azure-infrastructure-overview.md) <br/><br/>**Related solution guides** <br/> <ul><li>[Azure Storage services](azure-infrastructure-storage.md)</li><li>[Virtual machines](azure-infrastructure-virtual-machines.md)</li><li>[Spoke VNets](azure-infrastructure-iaas.md)</li></ul>|

For additional technical illustrations, click [here](zero-trust-tech-illus.md).

## References

Refer to these links to learn about the various services and technologies mentioned in this article.

- [Azure Virtual Networks](/azure/virtual-network/virtual-networks-overview)

- [What is Azure Firewall?](/azure/firewall/overview)

- [About Azure VPN Gateway](/azure/vpn-gateway/vpn-gateway-about-vpngateways)

- [Azure DDoS Protection Overview](/azure/ddos-protection/ddos-protection-overview)

- [Introduction to Azure security](/azure/security/fundamentals/overview)

- [Zero Trust implementation guidance](zero-trust-overview.md)

- [Overview of the Microsoft cloud security benchmark](/security/benchmark/azure/overview)

- [Security baselines for Azure overview](/security/benchmark/azure/security-baselines-overview)

- [Building the first layer of defense with Azure security services](/azure/architecture/solution-ideas/articles/azure-security-build-first-layer-defense)

- [Microsoft Cybersecurity Reference Architectures](/security/cybersecurity-reference-architecture/mcra)
