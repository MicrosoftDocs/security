---
title: How do I apply Zero Trust principles to Azure services?
description: An overview of the set of articles that describe how to apply Zero Trust principles to Microsoft Azure services.
ms.date: 05/06/2025    
ms.service: security
ms.subservice: zero-trust
ms.topic: overview
ms.collection: 
  - msftsolution-azureiaas
  - msftsolution-overview
  - zerotrust-solution
  - zerotrust-azure
---

<!---

Writers note:

For updates to product names, please also update the appropriate figures.

To update figures that are not screen shots, your options are:

- Locate the source Visio file in internal storage (ask your publishing contacts about the Illustration-locations.docx document) (highly recommended).
- Use a published Visio file in the Microsoft Download Center (see the https://learn.microsoft.com/security/zero-trust/zero-trust-tech-illus article for all the downloads).
- For figures that are published in Scalable Vector Graphics (SVG) format, save the SVG file from the article web page, insert into Visio, modify, and then save it as a new version of the SVG file (last resort).

For updates to figures that are included in download files (see the https://learn.microsoft.com/security/zero-trust/zero-trust-tech-illus article for all the downloads), please: 

- Update the corresponding files (Visio, PowerPoint, PDF) as needed.
- Publish the Visio and PDF files in the Microsoft Download Center and update the refresh date (such as March 2024) for the download in this article and the https://learn.microsoft.com/security/zero-trust/zero-trust-tech-illus article.

For new articles in this content set, please:

- Add cross-links in the "Next steps" section FROM all the other articles in this content set TO the new article.
- Add a link to the Zero Trust Guidance Center page (index.yml).
- Update the "Content architecture" figure in the apply-zero-trust-azure-services-overview.md article as needed.

--->

# Overview – Apply Zero Trust principles to Azure services

**Summary:** To apply Zero Trust principles to Azure services, you need to determine the set of infrastructure components required to support your desired workload, and then apply Zero Trust principles to those components.

This series of articles helps you apply the [principles of Zero Trust](zero-trust-overview.md) to your services in Microsoft Azure using a multi-disciplinary methodology. Zero Trust is a security strategy. It is not a product or a service, but an approach in designing and implementing the following set of security principles:

- Verify explicitly
- Use least privileged access
- Assume breach

Implementing the Zero Trust “never trust, always verify” approach requires changes to cloud infrastructure, deployment strategy, and implementation.

These articles show you how to apply Zero Trust approach to these new or already deployed Azure services:

- [Azure IaaS overview](azure-infrastructure-overview.md)
  - [Azure storage](azure-infrastructure-storage.md)
  - [Virtual machines](azure-infrastructure-virtual-machines.md)
  - [Spoke virtual networks](azure-infrastructure-iaas.md)
  - [Spoke virtual networks with Azure PaaS services](azure-infrastructure-paas.md)
  - [Hub virtual networks](azure-infrastructure-networking.md)
- [Azure Virtual Desktop](azure-infrastructure-avd.md)
- [Azure Virtual WAN](azure-virtual-wan.md)
- [IaaS applications in Amazon Web Services](secure-iaas-apps.md)
- [Microsoft Sentinel and Microsoft Defender XDR](/security/operations/siem-xdr-overview)

## Content architecture

Here is the content architecture for this set of articles that contain the set of platform and workload articles to apply Zero Trust principles to Azure services.

:::image type="content" source="media/apply-zero-trust-azure-services-overview/content-architecture.svg" alt-text="The stack diagram for the set of articles that describe how you apply Zero Trust to Azure services, starting at the bottom of the stack and moving up to the desired workload." lightbox="media/apply-zero-trust-azure-services-overview/content-architecture.svg":::

You apply the guidance in the articles in a stack from the bottom up.

| Workload | Platform set of articles (from the bottom up) |
| --- | --- |
| IaaS apps in Amazon Web Services (AWS) | <ul><li> Cloud identity infrastructure </li><li> Microsoft Sentinel and Microsoft Defender XDR </li></ul> |
| Spoke VNet with Azure IaaS services | <ul><li> Cloud identity infrastructure </li><li> Microsoft Sentinel and Microsoft Defender XDR </li><li> Hub VNets (traditional) OR Azure Virtual WAN (Microsoft-managed) </li><li> Storage </li></ul> |
| Azure Virtual Desktop or virtual machines | <ul><li> Cloud identity infrastructure </li><li> Microsoft Sentinel and Microsoft Defender XDR </li><li> Hub VNets (traditional) OR Azure Virtual WAN (Microsoft-managed) </li><li> Storage </li><li> Spoke VNet with Azure IaaS services </li></ul>  |

It’s important to note that the guidance in this series of articles is more specific for this type of architecture than the guidance provided in the [Cloud Adoption Framework](/azure/cloud-adoption-framework/get-started/index) and [Azure landing zone](/azure/cloud-adoption-framework/ready/landing-zone/index) architectures. If you have applied the guidance in either of these resources, be sure to also review this series of articles for additional recommendations.  

## Additional articles for Azure services

Take a look at these additional articles for applying Zero Trust principles to Azure services:

- For Azure IaaS:
  - [Azure storage](azure-infrastructure-storage.md)
  - [Virtual machines](azure-infrastructure-virtual-machines.md)
  - [Spoke virtual networks](azure-infrastructure-iaas.md)
  - [Hub virtual networks](azure-infrastructure-networking.md)
- [Azure Virtual Desktop](azure-infrastructure-avd.md)
- [Azure Virtual WAN](azure-virtual-wan.md)
- [IaaS applications in Amazon Web Services](secure-iaas-apps.md)
- [Protect Azure resources from cyberattacks](azure-protect-resources-cyberattacks.md)
- [Microsoft Sentinel and Microsoft Defender XDR](/security/operations/siem-xdr-overview)

See these additional articles for applying Zero Trust principles to Azure networking:

- [Encrypt your network traffic](azure-networking-encryption.md)
- [Segment your network traffic](azure-networking-segmentation.md)
- [Gain visibility into your network traffic](azure-networking-visibility.md)
- [Discontinue legacy network security technology](azure-networking-legacy.md)

## References

Refer to the links below to learn about the various services and technologies mentioned in this article.

- [What is Azure - Microsoft Cloud Services](https://azure.microsoft.com/resources/cloud-computing-dictionary/what-is-azure/)
- [Introduction to Azure security](/azure/security/fundamentals/overview)
- [Zero Trust implementation guidance](zero-trust-overview.md)
- [Overview of the Microsoft cloud security benchmark](/security/benchmark/azure/overview)
- [Security baselines for Azure overview](/security/benchmark/azure/security-baselines-overview)
- [Building the first layer of defense with Azure security services](/azure/architecture/solution-ideas/articles/azure-security-build-first-layer-defense)
- [Microsoft Cybersecurity Reference Architectures](/security/cybersecurity-reference-architecture/mcra)

## Additional Zero Trust documentation

Use additional Zero Trust content based on a documentation set or the roles in your organization.

### Documentation set

Follow this table for the best Zero Trust documentation sets for your needs.

| Documentation set | Helps you... | Roles |
| --- | --- | --- |
| [Adoption framework](adopt/zero-trust-adoption-overview.md) for phase and step guidance for key business solutions and outcomes | Apply Zero Trust protections from the C-suite to the IT implementation. | Security architects, IT teams, and project managers |
|[Assessment and progress tracking resource](zero-trust-assessment-progress-tracking-resources.md) |Assess your infrastructure's readiness and track your progress. |Security architects, IT teams, and project managers|
|[Zero Trust partner kit](zero-trust-partner-kit.md) |Co-branded tracking resources, workshop, and architecture illustrations |Partners and security architects |
| [Concepts and deployment objectives](deploy/overview.md) for general deployment guidance for technology areas | Apply Zero Trust protections aligned with technology areas. | IT teams and security staff |
| [Zero Trust for small businesses](guidance-smb-partner.md) | Apply Zero Trust principles to small business customers. | Customers and partners working with Microsoft 365 for business |
| [Zero Trust deployment plan with Microsoft 365](/microsoft-365/security/microsoft-365-zero-trust?bc=%2fsecurity%2fzero-trust%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fzero-trust%2ftoc.json) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to your Microsoft 365 tenant. | IT teams and security staff |
| [Zero Trust for Microsoft Copilots](./copilots/apply-zero-trust-copilots-overview.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Microsoft Copilots. | IT teams and security staff |
| [Partner integration with Zero Trust](integrate/overview.md) for design guidance for technology areas and specializations | Apply Zero Trust protections to partner Microsoft cloud solutions. | Partner developers, IT teams, and security staff |
| [Develop using Zero Trust principles](develop/overview.md) for application development design guidance and best practices | Apply Zero Trust protections to your application. | Application developers |

