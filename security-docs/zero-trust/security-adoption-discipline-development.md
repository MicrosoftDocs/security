---
title: Establish a Development Security discipline
description: Use the Microsoft security adoption model to modernize and secure development processes and functions, based on Zero Trust principles.
ms.date: 05/24/2026
ms.service: security
ms.subservice: zero-trust
author: rayne-wiselman
ms.author: raynew
ms.topic: conceptual

#customer intent: As a business leader or security adopter, I want to understand how I can use the Microsoft security adoption model to modernize and secure dev functions and processes across the business.
---

# Establish a Development Security discipline


This article helps security and technology teams establish and modernize a Development Security discipline. This discipline helps security, engineering, and technology teams ensure that software is designed, built, integrated, and deployed securely—without slowing innovation.

[Security disciplines](security-adoption-discipline-overview.md) are groupings of related security work that help organizations consistently deliver security outcomes across the entire technology estate. Within the security adoption model, disciplines help provide a bridge between [business scenarios](security-adoption-business-scenarios-overview.md) and [technical implementation](implement-overview.md), ensuring that security investments translate into real measurable outcomes as part of the [security adoption model](security-adoption-model.md).



## Why this discipline?

Software is deeply interconnected with identities, data, infrastructure, and business processes. When development security is weak or inconsistent, each software release can introduce new vulnerabilities that attackers exploit to gain access to broader organizational assets.

Without an effective Development Security discipline, organizations commonly experience:

- Increased risk from software vulnerabilities introduced during development.
- Application compromise that enables lateral movement across identities and data.
- Disruption of business operations and revenue.
- Exposure or abuse of customer and regulated data.
- Accumulation of technical debt that increases long‑term risk and remediation cost.

A strong development security discipline ensures that each release reduces risk, rather than compounding it.

## Mission and outcomes


The Development Security discipline reduces organizational risk by ensuring that all software, whether developed internally or by partners, is designed, built, integrated, and deployed in alignment with security standards, without slowing delivery or innovation.

Organizations that mature this discipline achieve:

- Security built into development processes rather than added late.
- Earlier identification and remediation of design and implementation flaws.
- More predictable, secure release cycles.
- Reduced rework, emergency fixes, and operational disruption.
- Lower accumulation of technical and security debt over time.

Development Security ensures that security posture improves continuously with each release, rather than being periodically reset.


### Changes in team work

It's important that a Development Security discipline meets developers and product teams where they are, focusing n integrating security into existing development workflows, rather than introducing late-stage controls, friction-heavy review processes, or even skipping security in development processes.

This approach is often described as **shifting left**, introducing security thinking earlier in ideation, design, and implementation, when issues are easier and less costly to fix. Shifting left does not mean saying no earlier in the process. Instead, it introduces security-informed discussion early to improve product decisions and ensure solutions meet security and business requirements.

Key principles include:

- **Early integration**: Consider security during ideation and design, not just testing
- **Developer alignment**: Meet development and product teams where they already work
- **Small, incremental change**: Prefer automation and low-friction improvements
- **Continuous improvement**: Treat security as an ongoing discipline, not a milestone

Over time, consistent integration reduces fire drills and accelerates delivery rather than slowing it.


## How to apply this discipline

To apply the Development Security discipline effectively, focus on establishing a consistent approach to building and maintaining secure applications and services across the organization:

1. **Define a secure development strategy aligned to business risk**  
  Establish a clear approach for how applications and services are designed, built, and maintained to reduce the risk of compromise and protect critical business functionality.
1. **Embed security into development and engineering processes**  
  Ensure security practices are integrated into planning, design, development, and deployment activities rather than applied after the fact.
1. **Establish standardized secure development practices**  
  Provide clear guidance to ensure that secure coding, testing, and release practices are applied consistently across teams and projects.
1. **Align development security with critical assets and business scenarios**  
  Prioritize protections for applications and services that support high-value assets and key business operations.
1. **Continuously improve based on risk, vulnerabilities, and feedback**  
  Use insights from vulnerabilities, incidents, and testing results to strengthen development practices and reduce risk over time.



## Manage change


Modern development security is typically implemented through a DevSecOps approach that combines agile delivery with essential governance and quality practices before release.

Rather than choosing between speed and security, DevSecOps focuses on securing key aspects of the development lifecycle to mitigate urgent risk while not impeding rapid release cycles:

**Secure the design** – Use proven security design patterns and validate designs through threat modeling.
**Secure the code** – Follow secure coding practices and validate software and dependencies.
**Secure the pipeline** – Validate the pipeline process and protect CI/CD systems from compromise and unauthorized change. Ensure traceability of changes to the pipeline and the software going through the pipeline.
**Secure operations** – Ensure deployed workloads follow configuration, patching, and operational best practices.

Teams can improve outcomes by continuously refining collaboration between development, security, and operations, balancing functional delivery goals with reliability and risk reduction.

:::image type="content" source="./media/security-adoption-discipline-dev-overview.png" alt-text="DevSecOps strategy that combines traditional development practices with Agile techniques." lightbox="./media/security-adoption-discipline-dev-overview.png":::

This continuous incremental improvement should be applied to both work production (software code produced in the lifecycle) as well as the maturing of the development lifecycle itself.


## Define a DevSecOps process

Development Security is commonly implemented through a DevSecOps operating model that evolves over time rather than appearing fully formed. DevSecOps brings development, security, and operations together to achieve better outcomes through continuous improvement.

Most organizations progress through these stages:

Development (Dev) – The first production release focuses on delivering a minimally viable product (MVP) that meets core business requirements.
DevOps – After initial release, teams focus on rapid iteration, operational stability, and governance through continuous delivery.
DevSecOps – As collaboration matures, development, security, and operations work together to continuously refine processes and balance speed, risk, and reliability.


:::image type="content" source="./media/security-adoption-discipline-dev-agile.png" alt-text="DevSecOps strategy that combines traditional quality controls and agile development." lightbox="./media/security-adoption-discipline-dev-agile.png":::

This progression allows organizations to improve security outcomes without sacrificing agility or innovation.


### Establish a secure MVP baseline
 
A key step in this model is defining what constitutes a minimum viable product (MVP) from development, security, and operations perspectives. Establishing this shared baseline creates clarity across teams and enables consistent improvement over time.

**Component** | **Details**
--- | ---
**Dev(elopment)** | Ensure that the software meets the minimum business and functional requirements.
**Sec(urity)** | Ensure that software meets the minimum security and compliance requirements.
**Op(eration)s** | Ensure that software meets the minimum quality, reliability, and operational readiness requirements.

MVP requirements vary by organization and industry and are influenced by risk appetite, regulatory exposure, and business criticality. These requirements often evolve as the organization, threat landscape, and delivery models change.


### Continuous software improvement

After the initial production release, workloads move into continuous improvement cycles. In this phase, development, security, and operations refine both the software and the delivery process.
Security efforts focus on:

- **Integrate security natively** into development workflows, using the same tools and prioritization models as other engineering work
- **Rapidly identify, prioritize and fix security bugs** as part of standard release cycles.
- 
This approach aligns with Microsoft Secure Future Initiative (SFI) learnings such as pr[**Paved Paths**](https://devblogs.microsoft.com/engineering-at-microsoft/building-paved-paths-the-journey-to-platform-engineering/), where secure practices are built into platforms and processes rather than enforced externally.

Over time, this continuous learning helps teams refine requirements, streamline collaboration, and better balance delivery speed, security, and reliability.


## Discipline roles and collaborators

The Dev Security discipline is typically run by teams doing app and product development. 

Primary roles in this discipline typically include:

- Technology delivery and product managers
- Software developers (including AI development)
- Software security engineers
- DevOps and platform engineers
- Testing and quality engineering roles
- Supply chain and dependency security roles

Key collaborators include:

- Business and technical leadership – Provide sponsorship and prioritization
- Architecture roles – Guide secure design and integration decisions
- Security Strategy, Integration, and Governance discipline roles– Provide policy, education, and oversight
- Infrastructure and platform teams – Enable secure development environments
- Security Operations (SecOps) – Monitor and respond when applications are attacked

## Alignment with other disciplines

Development Security is tightly integrated with other SAF disciplines:

- Access and Identities – Protects developer, workload, and service identities.
- Infrastructure Security – Secures platforms running applications and pipelines.
- Data Security – Ensures sensitive data is protected throughout the software lifecycle.
- SecOps– Detects and responds to application-level attacks.
- Security Strategy, Integration, and Governance – Aligns development practices to enterprise risk priorities.

Together, these disciplines ensure software security supports broader business and security outcomes.

## Alignment with technology pillars 

Executing the strategy for the development security discipline requires security controls across multiple technology pillars.

:::image type="content" source="./media/security-adoption-discipline-dev-pillars.png" alt-text="Development Security - mapping to technology pillars." lightbox="./media/security-adoption-discipline-dev-pillars.png":::

Alignment with technology pillars includes:


- **Identities**: Protects developer and workload identities and credentials.
- **Endpoints**: Secures developer workstations and build systems.
- **Infrastructure**: Protects platforms hosting code, pipelines, and workloads.
- **Apps**: Provides a primary focus for development security practices.
- **Data**: Protects data used, generated, and stored by applications.
- **Network**: Designs software to operate securely on untrusted networks.
- **AI**: Secures AI components and models used in modern applications.

This breadth ensures the discipline addresses real-world attack paths.

## What's next?

Additional development security strategy guidance is in the [Development security strategy](security-adoption-discipline-development-security.md).

### Take a workshop

Microsoft Unified offers expert-led workshops to help organizations modernize their Dev security discipline. These workshops include:

- **Architecture and strategy workshops** - The *Security Adoption Framework (SAF) - Architecture Design Session: Infrastructure and Development Security workshop* focuses on accelerating development security modernization and integration with infrastructure security. This workshop is available as a less than four-hour discussion focused on key learnings and best practices.
- **Technology adoption workshops**: Microsoft Unified has workshops to help organizations learn about, plan, implement, and optimize the use of Microsoft Development Security Technology as illustrated in this diagram.

:::image type="content" source="./media/security-adoption-discipline-dev-technical.png" alt-text="Development Technology Adoption Workshops" lightbox="./media/security-adoption-discipline-dev-technical.png":::



### Review the Microsoft Security Development Lifecycle 

The Microsoft Continuous Security Development Lifecycle provides a methodology to securely develop software. The Security Development Lifecycle (SDL) is the approach Microsoft uses to integrate security into DevOps processes (sometimes called a DevSecOps approach). The SAF development security guidance helps you adapt the SDL approach and practices to your organization.  

You can apply the practices described in the SDL approach to all types of software development and all platforms, from classic waterfall through to modern DevOps approaches. This generally applicable software security approach works across any type of software and platform. 

For more information, see [Microsoft Security Development Lifecycle (SDL)](https://www.microsoft.com/securityengineering/sdl/).

Effective development security requires following a security development lifecycle (SDL) like the [Microsoft Security Development Lifecycle (SDL)](https://www.microsoft.com/securityengineering/sdl/)


## Next steps

[Learn about](security-adoption-discipline-development-security.md) the shift from DevOps to DevSecOps.