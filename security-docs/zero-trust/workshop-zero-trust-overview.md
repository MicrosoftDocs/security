---
title: Microsoft Zero Trust Workshop
description: Learn about the Microsoft Zero Trust Workshop
ms.date: 05/24/2026
ms.service: security
author: rayne-wiselman
ms.author: raynew
ms.subservice: zero-trust
ms.topic: conceptual

#customer intent: As a security implementer, I want to understand how the Zero Trust implementation workshops can help me to deploy security controls that align with Zero Trust principles and security best practices.
---

# The Microsoft Zero Trust Workshop

The [Microsoft Zero Trust Workshop](https://microsoft.github.io/zerotrustassessment/docs/intro) provides a guidance tool for organizations on their Zero Trust security journey. It's intended to help you develop an actionable and orderly strategy for implementing a secure Zero Trust security posture across your IT landscape. The workshop aids in understanding and identifying:

- Microsoft's Zero Trust approach to security.
- The state of your current security posture.
- An actionable roadmap for implementing Zero Trust security.
- Security best practices and implementation steps.

## Why use the Workshop?

- Implementing security based on Zero Trust principles can be overwhelming. Often organizations struggle to know where to start, what to enable first, or how to measure their existing posture or progress. The Workshop helps you to:
- Assess your current Zero Trust posture. It turns strategy into actionable steps based on real assessment data.
- Keep progress on track and build an interactive and continuous improvement plan for security. 
- Align with Microsoft security solutions. Recommendations and implementation steps are practical, and tied to Microsoft tools and services.

## What's in the Workshop?

The Zero Trust workshop provides:

- A single-page app that helps you to document your current Zero Trust progress, and develop an actionable roadmap for your Zero Trust journey. Get a [quick video introduction](https://microsoft.github.io/zerotrustassessment/docs/videos/IntroductionToZT) to the Workshop.
- An assessment tool (provided as a PowerShell module) to assess and improve your security posture and baseline. [Learn more](assessment/overview.md).

## How is the Workshop run?

The Workshop can be run as follows:

- By Microsoft or a partner for a more formal expert-led engagement.
- In self-service mode, using Microsoft workshop guidance accompanied by a posture assessment.

When run as a formal engagement there are two parts to the workshop: 

- For the first part we assess your environment with programmatic checks to help identify gaps and areas for improvement. 
- The second part of the engagement helps you to identify security projects and initiatives for security modernization and implementation. [Get detailed information about the engagement model](https://microsoft.github.io/zerotrustassessment/docs/workshop-guidance/delivery-guide#engagement-model).
- 
## How is a Workshop structured?

Typically a Workshop focuses on four phases, with repeating cycles per pillar.

**Phase** | **Details** | **Outcome**
--- | --- | ---
**Phase 1 - Kickoff/Orientation**: Introduce Zero Trust principles and Microsoft Zero Trust architecture.<br/><br/> Clarify context and goals.<br/><br/>Understand assessment logistics and prerequisites.<br/><br/>Validate stakeholders. | Workshop engagement is understood by all stakeholders.<br/><br/>Logistics are in place.
**Phase 2 - Assessment**: [Run the Zero Trust assessment tool](/security/zero-trust/assessment/get-started) to assess current state of the Identity and Device pillars.<br/><br/>Evaluate the state of the other pillars manually. The Workshop Excel workbook helps you to assess your current security state using the workbook as a checklist/guide. Walk through each pillar sheet, and use the implementation controls/recommendations to assess your current state, identify gaps, estimate maturity levels, and identify recommendations. | Findings are clearly understood and gaps are identified.
**Phase 2 - Pillar workshops**: Run a workshop for each pillar in accordance with your requirements. Each pillar workshop provides a comprehensive guidance that focuses on implementation tasks for securing each pillar in accordance with security best practices from Microsoft and from external standards such as the NIST CyberSecurity Framework (CSF). | A tailored adoption roadmap for evolving and improving Zero Trust security for specific pillars.

Learn more about [Workshop delivery](https://microsoft.github.io/zerotrustassessment/docs/workshop-guidance/delivery-guide).




## Who's the Workshop intended for?

The Workshop is intended for a variety of stakeholders. Attendance at pillar workshops is recommended for CISOs and IT Directors where possible.

- **Zero Trust/security strategy owners**: People responsible for the organizational security strategy, such as the CISO, security architects, and IT managers leading cloud and modernization initiatives.
- **Pillar owners**: Zero Trust focuses on a number of cross-organizational pillars. Pillar owners should participate, including:
    - Identity - IAM teams, SecOps team, Devices/Endpoint team, ID governance team, enterprise app developers.
    - Devices - Mobile device management architect/admin, security architect/ops, conditional access admin, governance and risk team.
    - Data - Information protection architect, Compliance officer/admin, platform admins focused on data security (Exchange, Sharepoint etc.)
    - Infrastructure, Apps - Infrastructure security teams, SecOps team, Endpoint security team, Compliance/policy team, app development team, network admin team.
    - Networking - IAM team, network ops team, SecOps team, devices/endpoints team, app/workload stakeholders.
    - SecOps - Security team decision makers, security team specialists (security architect, analyst, engineer, SIEM admin etc.)
    - DevOps: Developer leads/engineers.
- **Decision makers/Budget stakeholders**: With focus on the roadmap strategy - CTO, CIO, business app owners.
- **Risk program owners**: Enterprise risk managers, governance and compliance leaders, data protection officers, specific business risk owners.
- **Cross-functional staff**: People who operate systems across the business - infrastructure/network owners, cloud engineers, security engineers, helpdesk leads.


## How is the Workshop structured?

The Workshop has a number of components:

**Component** | **Goal**
--- | ---
[**Zero Trust Assessment tool**](assessment/overview.md). | The assessment tool provides the technical backbone of the workshop. It ensures that workshop findings and outcomes are based on real data and analysis. It:<br/><br/>Collects configuration data from your tenant.<br/>Checks your environment configuration against a broad range of Zero Trust best practices.<br/>Produces scores, gaps, and recommendations for each Zero Trust pillar and Microsoft Secure Future Initiative (SFI) pillar.<br/><br/> The Zero Trust assessment tool is currently available for the assessment of identity, devices, network, and data posture.<br/><br/> The tool requires read-only permissions for a tenant configuration. 
**Workshop session guides** | The guides provide written guidance for facilitators and structured learning for Workshop participants. They focus on the Zero Trust pillars:<br/><br/>[Identity](workshop-zero-trust-identity.md), the primary Zero Trust control plane protecting users, admins, service accounts, and workload identities.<br/><br/>[Devices](workshop-zero-trust-devices.md), ensuring that all endpoints access corporate resources and healthy, compliant, and monitored.<br/><br/>Data, protecting sensitive information, including documents, emails, databases, structured and unstructured data.<br/><br/>[Infrastructure](workshop-zero-trust-infrastructure.md), protecting multicloud and hybrid resources, including compute and storage.<br/><br/>[Networking](workshop-zero-trust-networking.md), related to infrastructure, protecting network traffic, segmentation boundaries, and connectivity.<br/><br/>[AI](workshop-zero-trust-ai-security.md), focusing on security for AI models and datasets.<br/><br/>[SecOps](workshop-zero-trust-security-operations.md), providing threat protection, detection, and response across the business.



## How is the Workshop maintained?

The Workshop is maintained and regularly updated by Microsoft on GitHub as a community-style resource. It's provided "as-is" with best effort, and isn't formally supported via Microsoft support. For questions on the preview Zero Trust Assessment tool, [raise an issue on the assessment github page](https://github.com/microsoft/zerotrustassessment/issues).

## Next steps

Begin the [SecOps workshop](https://zerotrust.microsoft.com/).