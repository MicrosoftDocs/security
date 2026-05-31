---
title: Adopt secure development planning imperatives
description: Modernize and secure development processes and functions using key imperatives.
ms.date: 05/24/2026
ms.service: security
ms.subservice: zero-trust
author: rayne-wiselman
ms.author: raynew
ms.topic: conceptual

#customer intent: As a business leader or security adopter, I want to understand the key imperatives for modernizing and securing dev functions and processes across the business.
---

# Adopt secure development planning imperatives

This article defines the key imperatives for integrating security into development practices as part of the [Development Security discipline](security-adoption-discipline-development.md).


Modern organizations rely on rapid software development to deliver innovation, meet business requirements, maintain competitive advantage, and respond to changing business needs. While DevOps enables this agility, it also introduces new security risks as code, infrastructure, and deployment processes evolve more quickly.

To securely adopt DevOps practices, organizations must integrate security into development strategy, workflows, and delivery processes, and adopt DevSecOps practices that secure application delivery across the lifecycle.

## Outcomes

Adopting the planning imperatives in this article enables organizations to:

- Reduce the introduction of security weaknesses into production workloads.
- Improve consistency of production readiness decisions.
- Reduce friction between development, security, and operations.
- Improve resilience of applications and delivery infrastructure.
- Sustain innovation velocity while managing security and operational risk.

## Recognize the scope of development security

Development security applies to more than application code. Organizations should define security requirements and activities across all components involved in designing, building, deploying, and operating workloads.

Organizations must account for security risks across:

- Application logic and services
- Infrastructure automation/Infrastructure‑as‑code (IaC) deployments
- Build and release pipelines
- Deployment configurations and operational scripting
- Developer environments and service identities
- Third-party dependencies and supply chain components

Recognizing this full scope helps organizations define security requirements that reflect how modern workloads are delivered, rather than limiting security to application code review late in the lifecycle.

## Account for key risks

Organizations should explicitly include the following risks when defining requirements:

**Risk area** | **Example impact**
--- | ---
Application design flaws | Unauthorized access, data exposure, persistent logic flaws.
Pipeline compromise | Injection of malicious code into build artifacts.
Developer environment compromise | Theft of credentials or elevation of privileges.
DevOps tooling misuse | Unauthorized changes via automation or integrations.
Supply chain vulnerabilities | Introduction of malicious or vulnerable dependencies.

These risks directly inform the planning imperatives defined in this article and must be addressed through design, process, and governance decisions.

These risks affect both application workloads and the infrastructure used to build and operate them.


## Integrate security into strategy/lifecycle

Security must be incorporated into development strategy, not applied as a post-release control.

Organizations must define security requirements alongside functional requirements and align them with:

- Development strategy
- Architectural planning
- Delivery workflows
- Operational support models

Security outcomes are shared responsibilities owned by engineering and operations roles, supported by security specialists.

Security enables innovation, it isn't a gate applied after delivery.

Organizations must adopt a continuous Secure Development Lifecycle (SDL) approach that includes:



- Defining security requirements early in design.
- Aligning security requirements with architecture and implementation.
- Integrating security with infrastructure automation.
- Performing continuous security validation.
- Tracking security findings.
- Prioritizing remediation.
- Applying security findings to release readiness decisions so that security issues are treated as production blockers when necessary.

Security must be continuously evaluated and improved as application architectures, risks, and delivery models evolve.

## Define minimum production viability criteria

Workloads must meet minimum viability criteria before production release. These criteria define whether a workload is safe, compliant, and operationally ready for production use across three dimensions:

- **Development (dev)**:  Development stakeholders define minimum functional requirements necessary to meet business needs and customer/user value.
- **Security (sec)**: Security stakeholders define minimum requirements necessary to meet regulatory obligations, sustain organizational security posture, and support detection and response of active threats.
- **Operations (ops)**: Operations stakeholders define minimum performance, quality, and supportability requirements necessary for the workload to operate reliably in production environments.

Production viability criteria:

- Ensure workloads are safe to deploy and operate in production environments.
- Act as release decision inputs and must be enforced consistently across development workflows.

Production viability criteria evolve based on changes to:

- Application delivery models.
- Threat conditions.
- Organizational risk tolerance.
- Compliance requirements.


## Integrate security into development workflows

Security must be embedded directly into development and delivery processes. Organizations should:

- Define security requirements within development workflows.
- Integrate security activities into:
    - Design processes
    - Build pipelines
    - Deployment workflows (CI/CD)
- Implement security validation mechanisms such as:
    - Code scanning
    - Dependency validation
    - Configuration checks


Security findings must be treated the same as production defects and incorporated into release decisions.

Security validation should occur continuously through the delivery, not only at release checkpoints.


## Balance and harmonize requirements

Organizations must define how development, security, and operational requirements are balanced in software delivery decisions. Production workloads must meet requirements across:

- Business functionality.
- Security resilience.
- Speed of innovation.
- Operational reliability and performance.

Organizations must define shared delivery objectives and performance metrics that:

- Align to shared performance and delivery objectives across development, security, and operations.
- Avoid domination by a single domain.
- Prioritize outcomes based on:
    - Organizational risk tolerance.
    - Regulatory obligations.
    - Business accountability.

The balance must adapt as threat conditions evolve, delivery models change, and organizational priorities shift.


## Establish shared accountability

Effective DevSecOps requires shared ownership across development, security, and operations teams with a view to:

- Aligning ownership of production viability criteria.
- Aligning delivery objectives across disciplines.
- Reducing silos and unhealthy friction that creates security gaps, delivery delays, and operational instability.


## Apply policy-driven security guardrails

Policy-driven guardrails should enforce controls without introducing excessive friction. Guardrails should include:

- Identity and access requirements.
- Configuration and compliance standards.
- Deployment and release controls. 

Guardrails should be:

- Integrated into platform foundations (for example landing zones).
- Embedded into development/deployment workflows.
- Enforced automatically when possible.

This approach ensures security requirements are consistently applied while maintaining delivery velocity.

For a balanced approach to security and speed of innovation, review adoption using [policy-driven guardrails](/azure/cloud-adoption-framework/ready/enterprise-scale/dine-guidance).

## Sustain and improve

Security doesn't remain effective as a static set of controls and must evolve over time.

Organizations must continuously evaluate and update development security practices in response to changes in:

- Threat conditions and attacker behavior.
- Application architectures and delivery models.
- Regulatory obligations.
- Organizational risk tolerance.
- Production viability criteria.
- Development delivery processes.
- Security governance practices.

Security practices must evolve alongside the systems they protect.

### Alignment techniques

Teams must align to: 

- **Define common goals**: Development, security, and operations leaders should collaboratively define delivery objectives and performance metrics for workload delivery, to support consistent release planning.
- **Prevent single‑domain decision dominance**: Delivery decisions should account for development, security, and operational requirements to avoid imbalances that might negatively impact workload reliability, compliance, or business functionality.
- **Prioritize continuous improvement over static release criteria**: Development security practices should be iteratively refined over time as application delivery models, threat conditions, and organizational priorities evolve.
- **Establish shared delivery context across stakeholder roles**: Development, security, and operations teams should maintain a shared understanding of:
    - Business urgency and delivery timelines
    - Relevant threat conditions and risk exposure
    - Operational availability and supportability requirements
- **Monitor delivery friction introduced by security requirements**: Security requirements may introduce delivery friction. Leaders should evaluate whether this friction contributes to risk reduction (for example, by enabling earlier identification of vulnerabilities) or unnecessarily delays workload delivery without materially improving production resilience.
- **Incorporate development security into planning and resource allocation**: Security requirements for application workloads should be incorporated into development planning and resource allocation alongside functionality and operational support requirements.
- **Define shared delivery performance objectives**: Performance and success metrics for application workloads should reflect development, security, and operational delivery outcomes.



## Align workflows with security requirements

Security must be operationalized through development workflows. Organizations must define and align workflows for:

- Architectural design activities.
- Build and deployment processes.
- Issue tracking and remediation workflows.

Security findings must be:

- Prioritized and tracked.
- Managed alongside production defects.
- Incorporated into release readiness decisions.

Workflow alignment ensures that security requirements are consistently enforced throughout delivery.


## Next steps

[Learn about](develop/overview.md) development using Zero Trust principles
