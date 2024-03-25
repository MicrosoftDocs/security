---
title: Zero Trust Rapid Modernization Plan
description: An overview of the Zero Trust Rapid Modernization Plan (RaMP) to quickly modernize your security and IT infrastructure to comply with Zero Trust principles.
ms.date: 01/08/2024
ms.service: security
ms.author: dansimp
author: dansimp
manager: dansimp
ms.topic: conceptual
ms.collection:
  - zerotrust-ramp
---

# Zero Trust Rapid Modernization Plan

<!---

Writers notes:

For updates to product names, please also update the appropriate figures.

To update figures that are not screen shots, your options are:

- Locate the source Visio file in internal storage.
- Use the published Visio file in the Microsoft Download Center (see the "Technical publications" section of this article).
- For figures that are published in Scalable Vector Graphics (SVG) format, save the SVG file from the article web page, insert into Visio, modify, and then save it as a new version of the SVG file.

For new articles in this content set, please:

- Add a link in the zero-trust-ramp-overview.md to the new article.
- Add a link to the Zero Trust Guidance Center page (index.yml).

--->

As an alternative to [deployment guidance](./deploy/overview.md) that provides detailed configuration steps for each of the technology pillars being protected by Zero Trust principles, Rapid Modernization Plan (RaMP) guidance is based on initiatives and gives you a set of deployment paths to more quickly implement key layers of protection.

RaMP guidance takes a project management and checklist approach:

- By providing a suggested mapping of key stakeholders, implementers, and their accountabilities, you can more quickly organize an internal project and define the tasks and owners to drive them to conclusion.
- By providing a checklist of deployment objectives and implementation steps, you can see the bigger picture of infrastructure requirements and track your progress.

## RaMP initiatives for Zero Trust

To rapidly adopt Zero Trust in your organization, RaMP offers technical deployment guidance organized in these initiatives.

| Initiative | Steps |
|:-------|:-----|
| **Top priority** | Critical security modernization initiatives: |
| ![User Access and Productivity](./media/zero-trust-ramp-overview/user-access-icon.png) <br> [User access and productivity](user-access-productivity-overview.md) | <ol><li>[Explicitly validate trust for all access requests](user-access-productivity-validate-trust.md)<br><ul><li>[Identities](user-access-productivity-validate-trust.md#identities)</li><li>[Endpoints (devices)](user-access-productivity-validate-trust.md#endpoints)</li><li>[Apps](user-access-productivity-validate-trust.md#apps)</li><li>[Network](user-access-productivity-validate-trust.md#network)</li></ul></li> |
| ![Data, compliance, and governance](./media/zero-trust-ramp-overview/data-compliance-governance-icon.png) <br> [Data, compliance, and governance](data-compliance-governance-overview.md) | <ol start="2"><li>[Ransomware recovery readiness](data-compliance-gov-ransomware-recovery-readiness.md)<br></li><li>[Data](data-compliance-gov-data.md)<br></ol> |
| Modernize security operations  | <ol start="4"><li>Streamline response</li><li>Unify visibility</li><li>Reduce manual effort</li></li></ol>|
| **As needed** | Additional initiatives based on Operational Technology (OT) or IoT usage, on-premises and cloud adoption, and security for in-house app development: |
| OT and Industrial IoT | <ul><li>Discover</li><li>Protect</li><li>Monitor</li></ul> |
| Datacenter & DevOps Security | <ul><li>Security Hygiene</li><li>Reduce Legacy Risk</li><li>DevOps Integration</li><li>Microsegmentation</li></ul> |

Here is the overall architecture for Zero Trust.

:::image type="content" source="./media/zero-trust-ramp-overview/zero-trust-architecture.svg" alt-text="The overall architecture for Zero Trust" lightbox="./media/zero-trust-ramp-overview/zero-trust-architecture.svg":::

The RaMP initiatives for Zero Trust address all of the elements of this architecture. As you step through the initiatives, we'll show which parts are being covered.

## Next step

Begin your Zero Trust RaMP deployment journey with [User access and productivity](user-access-productivity-overview.md).

## Additional Zero Trust documentation

Use additional Zero Trust content based on a documentation set or the roles in your organization.

### Documentation set

Follow this table for the best Zero Trust documentation sets for your needs.

| Documentation set | Helps you... | Roles |
| --- | --- | --- |
| [Adoption framework](adopt/zero-trust-adoption-overview.md) for phase and step guidance for key business solutions and outcomes | Apply Zero Trust protections from the C-suite to the IT implementation. | Security architects, IT teams, and project managers |
| [Concepts and deployment objectives](deploy/overview.md) for general deployment guidance for technology areas | Apply Zero Trust protections aligned with technology areas. | IT teams and security staff |
| [Zero Trust for small businesses](guidance-smb-partner.md) | Apply Zero Trust principles to small business customers. | Customers and partners working with Microsoft 365 for business |
| [Zero Trust deployment plan with Microsoft 365](/microsoft-365/security/microsoft-365-zero-trust?bc=%2fsecurity%2fzero-trust%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fzero-trust%2ftoc.json) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to your Microsoft 365 tenant. | IT teams and security staff |
| [Zero Trust for Copilot for Microsoft 365](zero-trust-microsoft-365-copilot.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Copilot for Microsoft 365. | IT teams and security staff |
| [Zero Trust for Azure services](azure-infrastructure-overview.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Azure workloads and services. | IT teams and security staff |
| [Partner integration with Zero Trust](integrate/overview.md) for design guidance for technology areas and specializations | Apply Zero Trust protections to partner Microsoft cloud solutions. | Partner developers, IT teams, and security staff |
| [Develop using Zero Trust principles](develop/overview.md) for application development design guidance and best practices | Apply Zero Trust protections to your application. | Application developers |

### Your role

Follow this table for the best documentation sets for your role in your organization.

| Role | Documentation set | Helps you... |
| --- | --- | --- |
| Security architect <br><br> IT project manager <br><br> IT implementer | [Adoption framework](adopt/zero-trust-adoption-overview.md) for phase and step guidance for key business solutions and outcomes| Apply Zero Trust protections from the C-suite to the IT implementation. |
| Member of an IT or security team | [Concepts and deployment objectives](deploy/overview.md) for general deployment guidance for technology areas | Apply Zero Trust protections aligned with technology areas. |
| Customer or partner for Microsoft 365 for business | [Zero Trust for small businesses](guidance-smb-partner.md) | Apply Zero Trust principles to small business customers.  |
| Member of an IT or security team for Microsoft 365 | [Zero Trust deployment plan with Microsoft 365](/microsoft-365/security/microsoft-365-zero-trust?bc=%2fsecurity%2fzero-trust%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fzero-trust%2ftoc.json) for stepped and detailed design and deployment guidance for Microsoft 365 | Apply Zero Trust protections to your Microsoft 365 tenant. |
| Member of an IT or security team for Microsoft Copilots | [Zero Trust for Copilot for Microsoft 365](zero-trust-microsoft-365-copilot.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Copilot for Microsoft 365. |
| Member of an IT or security team for Azure services | [Zero Trust for Azure services](azure-infrastructure-overview.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Azure workloads and services. |
| Partner developer or member of an IT or security team | [Partner integration with Zero Trust](integrate/overview.md) for design guidance for technology areas and specializations | Apply Zero Trust protections to partner Microsoft cloud solutions. |
| Application developer | [Develop using Zero Trust principles](develop/overview.md) for application development design guidance and best practices | Apply Zero Trust protections to your application. |
