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

The [Microsoft Zero Trust Workshop](https://microsoft.github.io/zerotrustassessment/docs/intro) provides a guidance tool for organizations on a security journey. The Workshop helps you to develop  an actionable and orderly Zero Trust security strategy and deployment plan across your IT landscape. 

## Why use the Workshop?

Implementing security based on Zero Trust principles can be overwhelming. Often organizations struggle to know where to start, what to enable first, or how to measure  existing posture or progress. The Workshop helps you to understand and identify:

- Microsoft's Zero Trust approach to security.
- The state of your current security posture.
- An actionable implementation roadmap based on real assessment data. 
- Alignment with Microsoft security solutions. Recommendations and implementation best pracitces are practical, and tied to Microsoft tools and services.
- Progress tracking, with an interactive and continuous improvement plan. 


## What's in the Workshop?

The Zero Trust Workshop focuses on a couple of components.

- **Assessment tool**:  [Learn more](assessment/overview.md).
- [**Zero Trust Assessment tool**](assessment/overview.md): An assessment tool (PowerShell module) that you run in your environment to assess and improve your security posture and baseline.
    - The tool provides the technical backbone of the workshop.
    - It ensures that workshop findings and outcomes are based on real data and analysis. - - The assessment:
        - Collects configuration data from your tenant.
        - Checks your environment configuration against a broad range of Zero Trust best practices.
        - Produces scores, gaps, and recommendations for each Zero Trust pillar and Microsoft Secure Future Initiative (SFI) pillar.
        - The tool requires read-only permissions for a tenant configuration.
- [**Workshop tool**](https://microsoft.github.io/zerotrustassessment/docs/videos/IntroductionToZT): A single-page app that helps you to document your Zero Trust progress, and develop an actionable roadmap for your journey. Get a [quick video introduction] to the Workshop.
_ **Workshop guidance**: Workshop articles provide written guidance for facilitators and Workshop participants. They focus on the Zero Trust pillars:
    - [**Identity**](workshop-zero-trust-identity.md), the primary Zero Trust control plane protecting users, admins, service accounts, and workload identities.
    - [**Devices**](workshop-zero-trust-devices.md), ensuring that all endpoints access corporate resources and healthy, compliant, and monitored.
    - [**Data**](workshop-zero-trust-data.md), protecting sensitive information, including documents, emails, databases, structured and unstructured data.
    - [**Networking**](workshop-zero-trust-networking.md), related to infrastructure, protecting network traffic, segmentation boundaries, and connectivity.
    - [**Infrastructure**](workshop-zero-trust-infrastructure.md), protecting multicloud and hybrid resources, including compute and storage.
    - [**SecOps**](workshop-zero-trust-security-operations.md), providing threat protection, detection, and response across the business.
    - [**AI**](workshop-zero-trust-ai-security.md), focusing on security for AI models and datasets


## How is the Workshop run?

The Workshop can be run as follows:

- By Microsoft or a partner for an expert-led engagement.
- In self-service mode, using Microsoft workshop guidance accompanied by the assessment tool.
- 
## How is a Workshop structured?

Typically a Workshop focuses on four phases, with repeating cycles per pillar.

When run as a [formal engagement](https://microsoft.github.io/zerotrustassessment/docs/workshop-guidance/delivery-guide#engagement-model) the Workshop runs as follows:


**Phase** | **Details** | **Outcome**
--- | --- | ---
**Phase 1 - Kickoff/Orientation**: Initial scoping call to introduce Zero Trust principles and Microsoft Zero Trust architecture, clarify scope, context and goals, and understand assessment logistics and prerequisites. | Workshop engagement is clear to all stakeholders.<br/><br/>Logistics are in place.
**Phase 2 - Assessment (optional)**: [Run the Zero Trust assessment tool](/security/zero-trust/assessment/get-started) to capture current baseline posture.<br/><br/>Walk through assessment findings. | Findings are clearly understood and gaps are identified.
**Phase 3 - Roadmap**: Define a with a customized and concrete deployment plan based on a baseline adoption roadmap. | Customer has a tailed adoption roadmap for Zero Trust security. 
**Phase 4 Closeout**: Gather feedback and identify additional technology pillar workshops. 

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

## How is the Workshop maintained?

The Workshop is maintained and regularly updated by Microsoft on GitHub as a community-style resource. It's provided "as-is" with best effort, and isn't formally supported via Microsoft support. For questions on the preview Zero Trust Assessment tool, [raise an issue on the assessment github page](https://github.com/microsoft/zerotrustassessment/issues).

## Next steps

Begin the [SecOps workshop](https://zerotrust.microsoft.com/).