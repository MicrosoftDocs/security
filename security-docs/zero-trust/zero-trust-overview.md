---
title: What is Zero Trust?
description: Understand the Zero Trust security model, learn about the principles, and apply the Zero Trust architecture using Microsoft 365 and Microsoft Azure services.  
ms.date: 02/21/2025
ms.service: security
author: brendacarter
ms.author: bcarter
ms.topic: conceptual
ms.collection: 
  - highpri
  - zerotrust
---

# What is Zero Trust?

Zero Trust is a security strategy. It isn't a product or a service, but an approach in designing and implementing the following set of security principles.

|Principle|Description|
|---|---|
|Verify explicitly|Always authenticate and authorize based on all available data points.|
|Use least privilege access|Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection.|
|Assume breach|Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses.|

These principles are the core of **Zero Trust**. Instead of believing everything behind the corporate firewall is safe, the Zero Trust model assumes breach and verifies each request as though it originated from an uncontrolled network. Regardless of where the request originates or what resource it accesses, the Zero Trust model teaches us to "never trust, always verify."

Zero Trust is designed to adapt to the complexities of the modern environment that embraces the mobile workforce. Zero Trust protects user accounts, devices, applications, and data wherever they're located.

A Zero Trust approach should extend throughout the entire organization and serve as an integrated security philosophy and end-to-end strategy.

Different organizational requirements, existing technology implementations, and security stages all affect how a Zero Trust security model implementation is planned and executed. Our guidance helps you assess your readiness for Zero Trust, and helps you build a plan to get to Zero Trust. Our guidance is based on our experience helping customers secure their organizations, and by implementing our own Zero Trust model for ourselves.

With Zero Trust, you move away from a trust-by-default perspective to a trust-by-exception one. An integrated capability to automatically manage those exceptions and alerts is important. You can more easily detect threats, respond to threats, and prevent or block undesired events across your organization.



## Zero Trust and the US Executive Order 14028 on Cybersecurity

US executive order 14028, Improving the Nation's Cyber Security, directs federal agencies on advancing security measures that drastically reduce the risk of successful cyberattacks against the federal government's digital infrastructure. On January 26, 2022, the Office of Management and Budget (OMB) released the federal Zero Trust strategy in [memorandum 22-09](https://bidenwhitehouse.archives.gov/wp-content/uploads/2022/01/M-22-09.pdf), in support of Executive Order 14028. Microsoft provides guidance to help organizations meet these requirements — [Meet identity requirements of memorandum 22-09 with Microsoft Entra ID](/entra/standards/memo-22-09-meet-identity-requirements).


## Documentation set

Follow this table for the best Zero Trust documentation sets for your needs.

|Documentation set|Helps you...|Roles|
|---|---|---|
|[Adoption framework](adopt/zero-trust-adoption-overview.md) for phase and step guidance for key business solutions and outcomes|Apply Zero Trust protections from the C-suite to the IT implementation.|Security architects, IT teams, and project managers|
|[Assessment and progress tracking resource](/zero-trust-assessment-progress-tracking-resources) |Assess your infrastructure's readiness and track your progress. |Security architects, IT teams, and project managers|
|[Zero Trust partner kit](/zero-trust-partner-kit) |Co-branded tracking resources, workshop, and architecture illustrations |Partners and security architects |
|[Deployment for technology pillars](deploy/overview.md) for conceptual information and deployment objectives|Apply Zero Trust protections aligned with typical IT technology areas.|IT teams and security staff|
|[Zero Trust for small businesses](guidance-smb-partner.md)|Apply Zero Trust principles to small business customers.|Customers and partners working with Microsoft 365 for business|
|[Zero Trust for Microsoft Copilots](copilots/apply-zero-trust-copilots-overview.md) for stepped and detailed design and deployment guidance|Apply Zero Trust protections to Microsoft Copilots.|IT teams and security staff|
|[Zero Trust deployment plan with Microsoft 365](/microsoft-365/security/microsoft-365-zero-trust?bc=%2fsecurity%2fzero-trust%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fzero-trust%2ftoc.json) for stepped and detailed design and deployment guidance|Apply Zero Trust protections to your Microsoft 365 organization.|IT teams and security staff|
|[Incident response with XDR and integrated SIEM](siem-xdr-overview.md)|Set XDR tools and integrate these with Microsoft Sentinel|IT teams and security staff|
|[Zero Trust for Azure services](azure-infrastructure-overview.md) for stepped and detailed design and deployment guidance|Apply Zero Trust protections to Azure workloads and services.|IT teams and security staff|
|[Partner integration with Zero Trust](integrate/overview.md) for design guidance for technology areas and specializations|Apply Zero Trust protections to partner Microsoft cloud solutions.|Partner developers, IT teams, and security staff|
|[Develop using Zero Trust principles](develop/overview.md) for application development design guidance and best practices|Apply Zero Trust protections to your application.|Application developers|
|US Governemnt guidance for [CISA](/security/zero-trust/cisa-zero-trust-maturity-model-intro), [DoD](/security/zero-trust/dod-zero-trust-strategy-intro), and the [Memorandum for Zero Trust architecture](/entra/standards/memo-22-09-meet-identity-requirements) |Prescriptive recommendatinos for US Government requirements |IT Architects and IT teams|


## Recommended training

|Training|[Introduction to Zero Trust](/training/modules/zero-trust-introduction)|
|---|---|
|:::image type="icon" source="media/introduction-to-zero-trust.svg" border="false":::|Use this module to understand the Zero Trust approach and how it strengthens the security infrastructure within your organization.|

> [!div class="nextstepaction"]
> [Start >](/training/modules/zero-trust-introduction)

|Training|[Introduction to Zero Trust and best practice frameworks](/training/modules/introduction-zero-trust-best-practice-frameworks/)|
|---|---|
|:::image type="icon" source="media/introduction-zero-trust-best-practice-frameworks.svg" border="false":::|Use this module to learn about best practices that cybersecurity architects use and some key best practice frameworks for Microsoft cybersecurity capabilities. You also learn about the concept of Zero Trust, and how to get started with Zero Trust in your organization.|

> [!div class="nextstepaction"]
> [Start >](/training/modules/introduction-zero-trust-best-practice-frameworks/)

## Next steps

Learn about the [Microsoft Zero Trust adoption framework](/adopt/zero-trust-adoption-overview).

<!---
### Your role

Follow this table for the best documentation sets for the roles in your organization.

|Role|Documentation set|Helps you...|
|---|---|---|
|Security architect <br/><br/> IT project manager <br/><br/> IT implementer|[Adoption framework](adopt/zero-trust-adoption-overview.md) for phase and step guidance for key business solutions and outcomes|Apply Zero Trust protections from the C-suite to the IT implementation.|
|Member of an IT or security team|[Deployment for technology pillars](deploy/overview.md) for conceptual information and deployment objectives|Apply Zero Trust protections aligned with typical IT technology areas.|
|Customer or partner for Microsoft 365 for business|[Zero Trust for small businesses](guidance-smb-partner.md)|Apply Zero Trust principles to small business customers.|
|Security architect <br/><br/> IT implementer|[Zero Trust Rapid Modernization Plan (RaMP)](zero-trust-ramp-overview.md) for project management guidance and checklists for easy wins|Quickly implement key layers of Zero Trust protection.|
|Member of an IT or security team for Microsoft 365|[Zero Trust deployment plan with Microsoft 365](/microsoft-365/security/microsoft-365-zero-trust?bc=%2fsecurity%2fzero-trust%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fzero-trust%2ftoc.json) for stepped and detailed design and deployment guidance for Microsoft 365|Apply Zero Trust protections to your Microsoft 365 organization.|
|Member of an IT or security team for Microsoft Copilots|[Zero Trust for Microsoft Copilots](copilots/apply-zero-trust-copilots-overview.md) for stepped and detailed design and deployment guidance|Apply Zero Trust protections to Microsoft Copilots.|
|Member of an IT or security team for Azure services|[Zero Trust for Azure services](azure-infrastructure-overview.md) for stepped and detailed design and deployment guidance|Apply Zero Trust protections to Azure workloads and services.|
|Partner developer or member of an IT or security team|[Partner integration with Zero Trust](integrate/overview.md) for design guidance for technology areas and specializations|Apply Zero Trust protections to partner Microsoft cloud solutions.|
|Application developer|[Develop using Zero Trust principles](develop/overview.md) for application development design guidance and best practices|Apply Zero Trust protections to your application.|

---> 

Related links:

- [Zero Trust Overview](https://www.youtube.com/watch?v=KlEKAzMQEOw&list=PLtVMyW0H7aiOQwZSsn2d-tg2z729ce1BZ&index=13): This video provides information about:
    - Zero Trust definition
    - Zero Trust principles
    - Zero Trust core concepts


- [Zero Trust - The Open Group](https://www.youtube.com/watch?v=x0xlTVyX968&list=PLtVMyW0H7aiOQwZSsn2d-tg2z729ce1BZ&index=12): This video provides a perspective on Zero Trust from a standards organization.
