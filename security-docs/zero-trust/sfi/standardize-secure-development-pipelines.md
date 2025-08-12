---
title: Standardize secure development pipelines – Zero Trust
description: Standardize secure development pipelines is part of the protect engineering systems  pillar of the Secure Future Initiative (SFI), focusing on developing governed pipeline templates for implementing centrally managed production pipelines.
ms.date: 08/05/2025
ms.service: security
author: brendacarter
ms.author: bcarter
ms.subservice: zero-trust
ms.topic: conceptual
ms.collection: 
  - highpri
  - zerotrust
  - sfi-zerotrust
---

# Standardize secure development pipelines (Secure Future Initiative)

**Pillar name: Protect engineering systems**<br>  
**Pattern name: Standardize secure development pipelines**

## Context and problem

CI/CD pipelines are the backbone of modern software delivery. But when left unmanaged, they can also become a blind spot.

For many organizations using tools like Azure DevOps (AzDO), development teams enjoy the flexibility to build and deploy software in ways that fit their unique workflows. But over time, that flexibility can lead to fragmentation. Customers may find that different teams within the same organization implement CI/CD pipelines inconsistently using different security checks, compliance validations, and automation logic. This inconsistency increases the risk of gaps in security, slows down onboarding for new team members, and makes it harder to enforce enterprise-wide standards for responding quickly to emerging threats.

This lack of standardization can make it difficult to:

- Enforce company-wide security or regulatory policies
- Generate Software Bills of Materials (SBOMs) as required by Executive Order 14028
- Apply updates uniformly across thousands of pipelines

The result is a patchwork of practices that slows security adoption, increases compliance risk, and creates unnecessary overhead for engineering teams.

## Solution

To address this challenge at scale, Microsoft developed governed pipeline templates as part of the Secure Future Initiative (SFI). These centrally managed Azure DevOps YAML templates and GitHub actions encode standardized logic, security controls, and compliance requirements—enabling teams to move faster without compromising trust.

Governed pipeline templates serve as secure-by-default blueprints that teams can extend to meet local needs while maintaining a core set of features and enforcement. This approach balances centralized control with developer autonomy.

The templates support a range of workflows, including:

- Pull request (PR) validation
- Official builds
- Release automation
- Services spanning web applications, desktop applications, microservices, and ML models

Microsoft completed the rollout of governed pipeline templates in two quarters. Today, 92% of Microsoft’s commercial cloud production pipelines are centrally managed.

## Guidance

Organizations can adopt a similar pattern using the following actionable practices:

|Use case|Recommended action |Resource |
|---|---|---|
| Leverage built-in tools   | <ul><li>Identify which security, compliance, and productivity tools should be built into every pipeline</li><li>Use regulatory needs and SDL policy as a starting point</li></ul> | <ul><li><a href="/azure/defender-for-cloud/defender-for-devops-introduction">Defender for Cloud DevOps security</a></li><li><a href="/azure/defender-for-cloud/azure-devops-extension">Azure DevOps extension</a></li></ul> |
| Create a common template  | <ul><li>Build a reusable “extends” YAML template that defines required logic and stages</li><li>Limit overrides to prevent accidental policy removal</li></ul> | <ul><li><a href="/azure/devops/pipelines/process/templates">Azure Pipelines</a></li><li><a href="/azure/devops/pipelines/process/templates">Use YAML templates in pipelines for reusable and secure processes</a></li></ul> |
| Support local extensions    | Allow teams to create spoke templates that add local functionality without modifying the core set of features | [Configure the Microsoft Security DevOps Azure DevOps extension](/azure/defender-for-cloud/azure-devops-extension) |
| Automate evidence generation   | Include SBOMs, test results, security scans, and compliance artifacts in the build process | [ACR - Manage OCI artifacts](/azure/container-registry/container-registry-manage-artifact)  |

## Outcomes

### Benefits

- Speedy onboarding for new teams, who can adopt secure pipelines out of the box
- Reduce the risk of misconfigurations, inconsistent enforcement, or human error
- Increase compliance coverage, including SBOMs and regulatory gates
- Improve visibility into pipeline usage, health, and policy compliance
- Support scalable innovation through continuously evolving central templates
- Simplify support, as the pipeline tooling is maintained and optimized by a dedicated team—freeing engineers to focus on product development

### Trade-offs

- Standardizing pipelines requires significant coordination, change management, and upfront investment
- Teams must migrate custom logic into spoke templates, which can reveal tightly coupled or outdated pipeline designs
- Not every edge case is supported, requiring a balance between flexibility and security—but the long-term gains outweigh initial challenges

## Key success factors

Organizations can track success using the following indicators:

- Percentage of active pipelines using governed templates
- SBOM generation coverage across production builds
- Number of pipelines passing vs. failing compliance gates
- Time to apply new policy or security updates across all pipelines
- Number of support tickets or bugs related to pipeline inconsistency or misconfiguration

## Summary

**Learn how Microsoft is transforming development pipelines into security-first systems, ready for whatever comes next.**
