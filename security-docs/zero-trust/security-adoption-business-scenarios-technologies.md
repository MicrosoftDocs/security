---
title: Align business outcomes and scenarios with Microsoft technologies
description: Learn how business security outcomes are enabled with Microsoft security technologies.
ms.date: 05/24/2026
ms.service: security
ms.subservice: zero-trust
author: rayne-wiselman
ms.author: raynew
ms.topic: concept-article
#customer intent: As a business leader or security adopter, I want to understand how Microsoft security technologies interact with each other as we adopt and modernize security
---

# Enable business scenarios with Microsoft technologies

This article shows how [business scenarios](security-adoption-business-scenarios-overview.md) are implemented with Microsoft technologies. 

We capture the business outcome for each scenario, the disciplines responsible for delivering the outcomes, and the Microsoft technologies that enable it.


## Minimize business damage

### Outcome

Minimize business damage by detecting, investigating, and responding to security incidents quickly and consistently across the enterprise.


### Primary discipline

Security operations (SecOps). [Learn more](security-adoption-discipline-security-operations.md).

### Primary technologies

Primary technologies for this business solution are Microsoft Defender XDR services, and Microsoft Sentinel.

#### Microsoft Defender 

Defender and other security services align under the Defender portal. Defender XDR is the unifying threat detection and response layer for SecOps. It brings together signals, alerts, and response actions from a range of Defender technologies, enabling coordinated detection, investigation, and response across the digital estate.

:::image type="content" source="./media/security-adoption-defender-map.png" alt-text="Illustration of how Microsoft Defender aligns to the business scenario." lightbox="./media/security-adoption-defender-map.png":::

#### Microsoft Sentinel 

Microsoft Sentinel is a primary enabler for this business scenario. 

- It provides centralized visibility across your entire digital estate, enabling rapid detection and response to threats before they cause significant damage.
- Automated playbooks and SOAR capabilities accelerate incident response, reducing mean time to remediation.
- Microsoft Sentinel is the primary technology to enable a unified and effective security operations discipline that provides comprehensive threat detection, investigation, and response capabilities across technology pillars.

:::image type="content" source="./media/security-adoption-sentinel-map.png" alt-text="Illustration of how Microsoft Sentinel aligns to the business scenario." lightbox="./media/security-adoption-sentinel-map.png":::


Review the business scenario [Minimizing business damage from security incidents](security-adoption-scenario-minimize-impact.md).

## Enable secure work from anywhere

### Outcome

Enable productivity while enforcing Zero Trust access decisions based on identity, device health, risk, and data sensitivity.

### Primary discipline

Access and identities. [Learn more](security-adoption-discipline-identity-access.md).

### Primary technologies

Primary technologies for this business solution are Microsoft Entra and Microsoft Intune.

#### Microsoft Entra

Microsoft Entra technologies are a primary enabler for this business scenario. It provides the identities necessary to secure remote access from anywhere. Technologies like Microsoft Entra Private Access allow you to replace legacy VPNs and Microsoft Entra Conditional Access is the policy engine to enforce compliance with Zero Trust policy.

:::image type="content" source="./media/security-adoption-entra-map.png" alt-text="Illustration of how Microsoft Entra aligns to the business scenario." lightbox="./media/security-adoption-entra-map.png":::

#### Microsoft Intune

Microsoft Intune technologies are a primary enabler for this business scenario. It provides cloud-based unified endpoint management across multiple operating systems, cloud, on-premises, mobile, desktop, and virtualized endpoints. Intune provides the device compliance foundation for Zero Trust access: MFA + compliant device + risk evaluation when paired with Microsoft Entra Conditional Access. Only secure devices can reach SaaS, apps, and data.

:::image type="content" source="./media/security-adoption-intune-map.png" alt-text="Illustration of how Microsoft Intune aligns to the business scenario." lightbox="./media/security-adoption-intune-map.png":::


Review the business scenario [Enabling people to do their job securely](security-adoption-scenario-remote-work.md).

## Continuously improve posture and compliance

### Outcome

Reduce exposure and improve compliance by providing clear visibility into attack paths, misconfigurations, and vulnerabilities across the digital estate.

### Primary discipline

- Posture management: Continuous visibility, risk assessment, prioritization, and improvement tracking. [Learn more](security-adoption-discipline-posture.md).
- Development security: Effective identification and remediation of vulnerabilities across the development lifecycle. [Learn more](security-adoption-discipline-development.md).
- Data security: Protect sensitive and personal data. [Learn more](security-adoption-discipline-data.md).

### Primary technologies

Primary technologies for this business solution are Microsoft Security Exposure Management, GitHub Advanced Security, and Microsoft Priva.

#### Microsoft Security Exposure Management

Microsoft Security Exposure Management is a primary enabler for this business scenario. It provides a unified view of your security posture, enabling you to identify attack paths, prioritize vulnerabilities based on business impact, and track security improvements over time.

:::image type="content" source="./media/security-adoption-security-exposure-map.png" alt-text="Graphic shows how Microsoft Security Exposure Management aligns to the business scenario." lightbox="./media/security-adoption-security-exposure-map.png":::

#### GitHub Advanced Security

Security posture isn't only about deployed assets—it's also shaped by how software is built. Shifting security earlier in the development lifecycle reduces downstream exposure, lowers remediation cost, and improves overall risk posture.

GitHub Advanced Security is a primary enabler for this business scenario. It shifts security left by integrating security scanning directly into the development workflow, enabling developers to identify and fix vulnerabilities before code reaches production. 
It improves security posture by:

- Preventing vulnerabilities from entering production environments.
- Reducing exposure that would otherwise appear later in posture tools.
- Supporting compliance by enforcing consistent security standards in code.
- Lowering remediation cost and risk compared to post‑deployment fixes.

:::image type="content" source="./media/security-adoption-github-map.png" alt-text="Illustration of how GitHub advanced security aligns to the business scenario." lightbox="./media/security-adoption-github-map.png":::

#### Microsoft Priva

Microsoft Priva is a primary enabler for this business scenario. It helps organizations discover personal data across their environment, automate privacy risk assessments, and demonstrate compliance with privacy regulations such as GDPR, CCPA, and other data protection requirements.


Review the business scenario [Continuously improving security posture and compliance](security-adoption-scenario-improve-posture.md).


## Protect critical assets

### Outcome

Identify where sensitive data resides and applying appropriate protection controls throughout its lifecycle.


### Primary discipline

Data security: Provide comprehensive data governance, protection, and compliance. [Learn more](security-adoption-discipline-data.md)



### Primary technologies

Primary technologies for this business solution are Microsoft Purview, and Microsoft Entra for privileged access.

#### Microsoft Purview

Microsoft Purview is a primary enabler for this business scenario. It provides comprehensive data discovery, classification, and protection capabilities that help organizations identify where sensitive data resides and apply appropriate protection controls throughout its lifecycle.

:::image type="content" source="./media/security-adoption-purview-map.png" alt-text="Graphic shows how Microsoft Purview aligns to the business scenario." lightbox="./media/security-adoption-purview-map.png":::

#### Microsoft Entra

Microsoft Entra partners with Purview to provide the identity control plane for this business scenario, ensuring that access to sensitive data is governed, verified, and continuously monitored. It enforces least-privilege access and secures privileged roles that can access or modify critical assets.


Review the business scenario [Identifying and protecting critical business assets](security-adoption-scenario-secure-assets.md).

## Rapidly and securely adopt AI

### Outcome

Enable teams to innovate with AI quickly while protecting data, code, and intellectual property.


### Primary discipline

Data security: Control data used by and produced through AI. Include discovery, classification, sensitivity labels, DLP, and governance for AI interactions. Enable teams to innovate with AI quickly while protecting data, code, and intellectual property.

### Primary technologies

Primary technologies for this business solution are Microsoft Purview, and GitHub Advanced Security.

#### Microsoft Purview

Microsoft Purview is a primary enabler for this business scenario. It provides comprehensive data discovery, classification, and protection capabilities that help organizations identify where sensitive data resides and apply appropriate protection controls throughout its lifecycle.


Review the business scenario [Rapidly and securely adopt AI](security-adoption-scenario-secure-ai.md).

## Next steps

- [Select a business scenario](security-adoption-business-scenarios-overview.md) to get started.
- Review implementation instructions for:

    - [I want to minimize business damage](security-adoption-scenario-minimize-impact.md).
    - [I want people to do their job from anywhere](security-adoption-scenario-remote-work.md).
    - [I want to continuously improve security posture](security-adoption-scenario-improve-posture.md).
    - [I want to protect critical assets](security-adoption-scenario-secure-assets.md).
    - [I want to secure privileged access](security-adoption-scenario-privileged-access.md).
    - [I want to security adoption AI](security-adoption-scenario-secure-ai.md).