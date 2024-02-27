---
title: What is Zero Trust?
description: Understand the Zero Trust security model, learn about the principles, and apply the Zero Trust architecture using Microsoft 365 and Microsoft Azure services.  
ms.date: 02/26/2024
ms.service: security
author: mjcaparas
ms.author: macapara
ms.topic: conceptual
ms.collection: 
  - highpri
  - zerotrust
---

# What is Zero Trust?

<!---
:::image type="icon" source="./media/icon-introduction-medium.png":::
--->

Zero Trust is a security strategy. It is not a product or a service, but an approach in designing and implementing the following set of security principles.

| Principle | Description |
| --- | --- |
| Verify explicitly | Always authenticate and authorize based on all available data points. |
| Use least privilege access | Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection. |
| Assume breach | Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses. |

This is the core of **Zero Trust**. Instead of believing everything behind the corporate firewall is safe, the Zero Trust model assumes breach and verifies each request as though it originated from an uncontrolled network. Regardless of where the request originates or what resource it accesses, the Zero Trust model teaches us to "never trust, always verify."

Zero Trust is designed to adapt to the complexities of the modern environment that embraces the mobile workforce and protects user accounts, devices, applications, and data wherever they are located.

A Zero Trust approach should extend throughout the entire digital estate and serve as an integrated security philosophy and end-to-end strategy.

Different organizational requirements, existing technology implementations, and security stages all affect how a Zero Trust security model implementation is planned and executed. Using our experience in helping customers to secure their organizations, as well as in implementing our own Zero Trust model, Microsoft has developed guidance to assess your readiness and help you build a plan to get to Zero Trust.

With Zero Trust, you move away from a trust-by-default perspective to a trust-by-exception one. An integrated capability to automatically manage those exceptions and alerts is important so you can more easily find and detect threats, respond to them, and prevent or block undesired events across your organization.

## Zero Trust and the US Executive Order 14028 on Cybersecurity

[US executive order 14028, Improving the Nation's Cyber Security](https://www.whitehouse.gov/briefing-room/presidential-actions/2021/05/12/executive-order-on-improving-the-nations-cybersecurity), directs federal agencies on advancing security measures that drastically reduce the risk of successful cyberattacks against the federal government's digital infrastructure. On January 26, 2022, the [Office of Management and Budget (OMB)](https://www.whitehouse.gov/omb/) released the federal Zero Trust strategy in [memorandum 22-09](https://www.whitehouse.gov/wp-content/uploads/2022/01/M-22-09.pdf), in support of EO 14028. 

<!---

## Zero Trust for Microsoft 365

Microsoft 365 is built intentionally with many security and information protection capabilities to help you build Zero Trust into your environment. Many of the capabilities can be extended to protect access to other SaaS apps your organization uses and the data within these apps.

See these key resources to get started:

- [Zero Trust deployment plan with Microsoft 365](/microsoft-365/security/microsoft-365-zero-trust)
- [The Microsoft Zero Trust security model setup guide](https://go.microsoft.com/fwlink/?linkid=2222968)
- [Advanced deployment guide for Zero Trust with Microsoft 365 (requires sign-in)](https://go.microsoft.com/fwlink/?linkid=2224820) in the Microsoft 365 admin center

## Zero Trust for Microsoft Azure

These articles help you apply the principles of Zero Trust to your workloads and services in Microsoft Azure based on a multi-disciplinary approach to applying the Zero Trust principles.

- [Azure IaaS](azure-infrastructure-overview.md)
- [Azure Virtual Desktop](azure-infrastructure-avd.md)
- [Azure Virtual WAN](azure-virtual-wan.md)
- [IaaS applications in Amazon Web Services](secure-iaas-apps.md)
- [Microsoft Sentinel and Microsoft Defender XDR](/security/operations/siem-xdr-overview)

--->

## Next steps

Use additional Zero Trust content based on a documentation set or roles in your organization.

### Documentation set

Follow this table for the best Zero Trust documentation sets for your needs.

| Documentation set | Helps you... | Roles |
| --- | --- | --- |
| [Adoption framework](adopt/zero-trust-adoption-overview.md) for phase and step guidance for key business solutions and outcomes | Apply Zero Trust protections from the C-suite to the IT implementation. | Security architects, IT teams, and project managers |
| [Deployment for technology pillars](deploy/overview.md) for conceptual information and deployment objectives | Apply Zero Trust protections aligned with typical IT technology areas. | IT teams and security staff |
| [Zero Trust for small businesses](guidance-smb-partner.md) | Apply Zero Trust principles to small business customers. | Customers and partners working with Microsoft 365 for business |
| [Zero Trust Rapid Modernization Plan (RaMP)](zero-trust-ramp-overview.md) for project management guidance and checklists for easy wins | Quickly implement key layers of Zero Trust protection. | Security architects and IT implementers |
| [Zero Trust deployment plan with Microsoft 365](/microsoft-365/security/microsoft-365-zero-trust?bc=%2fsecurity%2fzero-trust%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fzero-trust%2ftoc.json) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to your Microsoft 365 tenant. | IT teams and security staff |
| [Zero Trust for Copilot for Microsoft 365](zero-trust-microsoft-365-copilot.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Copilot for Microsoft 365. | IT teams and security staff |
| [Zero Trust for Azure services](azure-infrastructure-overview.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Azure workloads and services. | IT teams and security staff |
| [Partner integration with Zero Trust](integrate/overview.md) for design guidance for technology areas and specializations | Apply Zero Trust protections to partner Microsoft cloud solutions. | Partner developers, IT teams, and security staff |
| [Develop using Zero Trust principles](develop/overview.md) for application development design guidance and best practices | Apply Zero Trust protections to your application. | Application developers |

### Your role

Follow this table for the best documentation sets for the roles in your organization.

| Role | Documentation set | Helps you... |
| --- | --- | --- |
| Security architect <br><br> IT project manager <br><br> IT implementer | [Adoption framework](adopt/zero-trust-adoption-overview.md) for phase and step guidance for key business solutions and outcomes| Apply Zero Trust protections from the C-suite to the IT implementation. |
| Member of an IT or security team | [Deployment for technology pillars](deploy/overview.md) for conceptual information and deployment objectives | Apply Zero Trust protections aligned with typical IT technology areas. |
| Customer or partner for Microsoft 365 for business | [Zero Trust for small businesses](guidance-smb-partner.md) | Apply Zero Trust principles to small business customers.  |
| Security architect <br><br> IT implementer | [Zero Trust Rapid Modernization Plan (RaMP)](zero-trust-ramp-overview.md) for project management guidance and checklists for easy wins | Quickly implement key layers of Zero Trust protection. |
| Member of an IT or security team for Microsoft 365 | [Zero Trust deployment plan with Microsoft 365](/microsoft-365/security/microsoft-365-zero-trust?bc=%2fsecurity%2fzero-trust%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fzero-trust%2ftoc.json) for stepped and detailed design and deployment guidance for Microsoft 365 | Apply Zero Trust protections to your Microsoft 365 tenant. |
| Member of an IT or security team for Microsoft Copilots | [Zero Trust for Copilot for Microsoft 365](zero-trust-microsoft-365-copilot.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Copilot for Microsoft 365. |
| Member of an IT or security team for Azure services | [Zero Trust for Azure services](azure-infrastructure-overview.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Azure workloads and services. |
| Partner developer or member of an IT or security team | [Partner integration with Zero Trust](integrate/overview.md) for design guidance for technology areas and specializations | Apply Zero Trust protections to partner Microsoft cloud solutions. |
| Application developer | [Develop using Zero Trust principles](develop/overview.md) for application development design guidance and best practices | Apply Zero Trust protections to your application. |

<!---

### Current section

On this site you can find:

- [Adoption framework](adopt/zero-trust-adoption-overview.md)
- [Concepts and deployment objectives](deploy/overview.md)
- [Zero Trust for small businesses](guidance-smb-partner.md)
- [Rapid Modernization Plan (RaMP) guidance](zero-trust-ramp-overview.md)
- [Microsoft 365 deployment plans](/microsoft-365/security/microsoft-365-zero-trust?bc=%2fsecurity%2fzero-trust%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fzero-trust%2ftoc.json)
- [Microsoft Azure deployment plans](azure-infrastructure-overview.md)
- [Integration guidance for ISVs](integrate/overview.md)
- [Developer guidance](develop/overview.md)

--->


## Recommended training

|Training  | [Introduction to Zero Trust](/training/modules/zero-trust-introduction) |
|---------|---------|
|:::image type="icon" source="./media/introduction-to-zero-trust.svg" border="false"::: | Use this module to understand the Zero Trust approach and how it strengthens the security infrastructure within your organization. |
> [!div class="nextstepaction"]
> [Start >](/training/modules/zero-trust-introduction)

|Training  | [Introduction to Zero Trust and best practice frameworks](/training/modules/introduction-zero-trust-best-practice-frameworks/) |
|---------|---------|
|:::image type="icon" source="./media/introduction-zero-trust-best-practice-frameworks.svg" border="false"::: | Use this module to learn about best practices that cybersecurity architects use and some key best practice frameworks for Microsoft cybersecurity capabilities. You also learn about the concept of Zero Trust, and how to get started with Zero Trust in your organization. |
> [!div class="nextstepaction"]
> [Start >](/training/modules/introduction-zero-trust-best-practice-frameworks/)


## Related links

- [Zero Trust Overview](https://www.youtube.com/watch?v=KlEKAzMQEOw&list=PLtVMyW0H7aiOQwZSsn2d-tg2z729ce1BZ&index=13)-This video provides information about:

    - Zero Trust definition
    - Zero Trust principles
    - Zero Trust core concepts
    - Rapid modernization plan (RaMP) quick wins

- [Zero Trust - The Open Group](https://www.youtube.com/watch?v=x0xlTVyX968&list=PLtVMyW0H7aiOQwZSsn2d-tg2z729ce1BZ&index=12)-This video provides a perspective on Zero Trust from a standards organization.
