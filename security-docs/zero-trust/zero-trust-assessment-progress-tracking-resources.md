---
title: Zero Trust Readiness and Progress Assessment
description: Discover Zero Trust assessment tools and progress tracking resources to evaluate your security posture and streamline your Zero Trust implementation journey.
ms.date: 01/23/2025
ms.service: security
author: MicrosoftGuyJFlo
ms.author: joflore
ms.subservice: zero-trust
ms.topic: conceptual
ms.collection: zerotrust
---
# Zero Trust assessment and progress tracking resources

[Zero Trust](zero-trust-overview.md) is a security model that assumes breach and verifies each request as though it originated from an uncontrolled network. Regardless of where the request came from or what resource it accessed, the Zero Trust model teaches us to "never trust, always verify."

Before implementing a Zero Trust security model, start by assessing your current security posture. The assessment tools in this article help you:

- Discover where you are on your Zero Trust journey
- Identify which security controls are already in place
- Pinpoint gaps and areas for improvement
- Create a prioritized roadmap for implementing Zero Trust principles

After completing an assessment, use the progress tracking resources to monitor your adoption of Zero Trust architecture.

## Zero Trust assessment tools

Choose the assessment tool that best fits your needs and technical environment.

### Automated Zero Trust Assessment (Recommended)

The automated Zero Trust Assessment is an open-source PowerShell tool that tests hundreds of security configuration items across your Microsoft 365 and Azure environments against Microsoft's best practices. Get immediate, actionable results with detailed recommendations.

**Best for:** IT implementers who want comprehensive, automated analysis of their environment.

[Get started with the Zero Trust Assessment](assessment/overview.md)

:::image type="content" source="assessment/media/results-overview.png" alt-text="Screenshot of a sample run of the Zero Trust Assessment showing results for an example company called Contoso.":::

### Zero Trust Assessment Strategy Workshop

Download the Zero Trust Assessment strategy workshop Excel workbook to manually assess your environment and track your improvement roadmap. This structured workbook guides you through each Zero Trust pillar with clear evaluation criteria.

**Best for:** Organizations that prefer offline assessment tools or need customizable tracking worksheets.

[Download the workshop (Excel)](https://aka.ms/ztworkshop)

:::image type="content" source="./media/zero-trust-assessment-strategy-workshop.png" alt-text="Screenshot of the Zero Trust roadmap for identities." lightbox="./media/zero-trust-assessment-strategy-workshop.png":::

### Interactive Security Posture Assessment

The Microsoft Zero Trust Security Posture Assessment is an interactive online tool that evaluates your Zero Trust maturity level across all security pillars. Complete a guided questionnaire to receive a customized maturity score and recommendations.

**Best for:** Security architects and project leads who want to evaluate organizational readiness and build executive buy-in.

[Take the Security Posture Assessment](https://www.microsoft.com/security/business/zero-trust/maturity-model-assessment-tool)

:::image type="content" source="./media/adoption-guide/zero-trust-posture-assessment-example.png" alt-text="Screenshot of assessment questions for identities." lightbox="./media/adoption-guide/zero-trust-posture-assessment-example.png":::

## Progress tracking for adoption scenarios

After assessing your Zero Trust readiness, use these resources to track progress through the [Zero Trust adoption framework](adopt/zero-trust-adoption-overview.md) business scenarios.

### Adoption framework business scenarios

- [Rapidly modernize your security posture](adopt/rapidly-modernize-security-posture.md)
- [Secure remote and hybrid work](./adopt/secure-remote-hybrid-work.md)
- [Identify and protect sensitive business data](adopt/identify-protect-sensitive-business-data.md)
- [Prevent or reduce business damage from a breach](adopt/prevent-reduce-business-damage-breach.md)
- [Meet regulatory and compliance requirements](adopt/meet-regulatory-compliance-requirements.md)

### Available tracking resources

| Resource | Format | Best for | Download |
|----------|--------|----------|----------|
| **In-product dashboard** | Microsoft Defender portal | Real-time security metrics and recommendations | [View dashboard](https://security.microsoft.com/exposure-initiative?initiativeId=zero_trust&viewid=overview) |
| **Implementation tracker** | Excel workbook | IT teams tracking detailed tasks and ownership | [Download workbook](https://download.microsoft.com/download/d/0/3/d030e1d6-ea3d-45a1-9672-938e1b01db0d/zero-trust-business-scenario-objectives-tracking-workbook.xlsx) |
| **Executive presentation** | PowerPoint | Business leaders tracking high-level progress | [Download presentation](https://download.microsoft.com/download/a/b/5/ab51ac2a-e9de-4c8f-8323-6bc7c2f78c1f/ZeroTrust-Adoption-Resources.pptx) |
| **Strategy blueprint** | Visio/PDF | Project leads visualizing implementation stages | [Visio](https://download.microsoft.com/download/c/c/5/cc56e1ff-a13e-49d8-8703-16453dce0370/zero-trust-phase-grid-tracker-microsoft.vsdx) \| [PDF](https://download.microsoft.com/download/c/c/5/cc56e1ff-a13e-49d8-8703-16453dce0370/zero-trust-phase-grid-tracker-microsoft.pdf) |

## Recommended training

|Training|[Introduction to Zero Trust](/training/modules/zero-trust-introduction)|
|---|---|
|:::image type="icon" source="media/introduction-to-zero-trust.svg" border="false":::|Use this module to understand the Zero Trust approach and how it strengthens the security infrastructure within your organization.|

> [!div class="nextstepaction"]
> [Start >](/training/modules/zero-trust-introduction)

|Training|[Introduction to Zero Trust and best practice frameworks](/training/modules/introduction-zero-trust-best-practice-frameworks/)|
|---|---|
|:::image type="icon" source="./media/introduction-zero-trust-best-practice-frameworks.svg" border="false":::|Use this module to learn about best practices that cybersecurity architects use and some key best practice frameworks for Microsoft cybersecurity capabilities. You also learn about the concept of Zero Trust, and how to get started with Zero Trust in your organization.|

> [!div class="nextstepaction"]
> [Start >](/training/modules/introduction-zero-trust-best-practice-frameworks/)

## Other Zero Trust resources

Use other Zero Trust content based on a documentation set or the roles in your organization.

### Documentation set

Follow this table for the best Zero Trust documentation set for your needs.

|Documentation set|Helps you...|Roles|
|---|---|---|
|[Adoption framework](adopt/zero-trust-adoption-overview.md) for phase and step guidance for key business solutions and outcomes|Apply Zero Trust protections from the C-suite to the IT implementation.|Security architects, IT teams, and project managers|
|[Concepts and deployment objectives](deploy/overview.md) for general deployment guidance for technology areas|Apply Zero Trust protections aligned with technology areas.|IT teams and security staff|
|[Zero Trust for small businesses](guidance-smb-partner.md)|Apply Zero Trust principles to small business customers.|Customers and partners working with Microsoft 365 for business|
|[Zero Trust Rapid Modernization Plan (RaMP)](zero-trust-ramp-overview.md) for project management guidance and checklists for easy wins|Quickly implement key layers of Zero Trust protection.|Security architects and IT implementers|
|[Zero Trust deployment plan with Microsoft 365](/microsoft-365/security/microsoft-365-zero-trust?bc=%2fsecurity%2fzero-trust%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fzero-trust%2ftoc.json) for stepped and detailed design and deployment guidance|Apply Zero Trust protections to your Microsoft 365 organization.|IT teams and security staff|
|[Zero Trust for Microsoft Copilots](./copilots/apply-zero-trust-copilots-overview.md) for stepped and detailed design and deployment guidance|Apply Zero Trust protections to Microsoft Copilots.|IT teams and security staff|
|[Zero Trust for Azure services](azure-infrastructure-overview.md) for stepped and detailed design and deployment guidance|Apply Zero Trust protections to Azure workloads and services.|IT teams and security staff|
|[Partner integration with Zero Trust](integrate/overview.md) for design guidance for technology areas and specializations|Apply Zero Trust protections to partner Microsoft cloud solutions.|Partner developers, IT teams, and security staff|
|[Develop using Zero Trust principles](develop/overview.md) for application development design guidance and best practices|Apply Zero Trust protections to your application.|Application developers|

### Your role

Follow this table for the best documentation sets for your role in your organization.

|Role|Documentation set|Helps you...|
|---|---|---|
|Security architect <br><br> IT project manager <br><br> IT implementer|[Adoption framework](adopt/zero-trust-adoption-overview.md) for phase and step guidance for key business solutions and outcomes|Apply Zero Trust protections from the C-suite to the IT implementation.|
|Member of an IT or security team|[Concepts and deployment objectives](deploy/overview.md) for general deployment guidance for technology areas|Apply Zero Trust protections aligned with technology areas.|
|Customer or partner for Microsoft 365 for business|[Zero Trust for small businesses](guidance-smb-partner.md)|Apply Zero Trust principles to small business customers.|
|Security architect <br><br> IT implementer|[Zero Trust Rapid Modernization Plan (RaMP)](zero-trust-ramp-overview.md) for project management guidance and checklists for easy wins|Quickly implement key layers of Zero Trust protection.|
|Member of an IT or security team for Microsoft 365|[Zero Trust deployment plan with Microsoft 365](/microsoft-365/security/microsoft-365-zero-trust?bc=%2fsecurity%2fzero-trust%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fzero-trust%2ftoc.json) for stepped and detailed design and deployment guidance for Microsoft 365|Apply Zero Trust protections to your Microsoft 365 organization.|
|Member of an IT or security team for Microsoft Copilots|[Zero Trust for Microsoft Copilots](./copilots/apply-zero-trust-copilots-overview.md) for stepped and detailed design and deployment guidance|Apply Zero Trust protections to Microsoft Copilots.|
|Member of an IT or security team for Azure services|[Zero Trust for Azure services](azure-infrastructure-overview.md) for stepped and detailed design and deployment guidance|Apply Zero Trust protections to Azure workloads and services.|
|Partner developer or member of an IT or security team|[Partner integration with Zero Trust](integrate/overview.md) for design guidance for technology areas and specializations|Apply Zero Trust protections to partner Microsoft cloud solutions.|
|Application developer|[Develop using Zero Trust principles](develop/overview.md) for application development design guidance and best practices|Apply Zero Trust protections to your application.|
