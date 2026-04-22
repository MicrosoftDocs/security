---
title: Implement baseline security measures
description: Apply Microsoft's foundational controls across identity, devices, data, network, and servers to measurably reduce exposure across every tenant.
ms.date: 04/21/2026
ms.service: security
ms.subservice: zero-trust
ms.topic: concept-article
ms.collection:
  - highpri
  - zerotrust
ai-usage: ai-assisted
---

# Implement baseline security measures

Microsoft has defined and operationalized a set of foundational controls that measurably reduce exposure at scale—and most intrusions still map back to organizations simply not enabling them. Use **Microsoft Baseline Security Mode (BSM)** to apply these defaults across Microsoft 365 apps and Microsoft Entra, with impact simulation before enforcement. Then, run the **Zero Trust Assessment** to produce an evidence-backed, scored gap list across identity, devices, data, and network so you can prioritize the highest-value fixes first and start burning down risk now. Threat actors aren't waiting for your next planning cycle.

The goal is coverage, not perfection: get every tenant onto a defensible baseline across identity, device, data, network, and servers, rather than bespoke excellence in one pillar while the others stay unmanaged. Protecting the few accounts that hold privileged roles pays back faster than any other control; compromise of a single Global Administrator is tenant-ending. Turn on diagnostic settings for Entra, Intune, and Azure Firewall and ship them to a workspace you actually query: logs you don't ship, you can't investigate.

## Take these steps

1. **Enable Baseline Security Mode.** BSM is available to all Microsoft 365 customers, so confirm if you're already running it. If not, turn it on today. See [Baseline security mode settings](https://admin.cloud.microsoft/).
1. **Run the Zero Trust Assessment, and work through the gap list.** Get an automated assessment of your tenant's posture across identity, data, devices, and network. Every check is scored by risk level, user impact, and implementation cost, so start where risk reduction is high and cost is low, then work outward. Manually checking these controls is slow and error-prone; this is the automation. For more information, see:

   - [What is the Zero Trust Assessment?](../assessment/overview.md)
   - [Get started with the Zero Trust Assessment](../assessment/get-started.md)

   The three pillar-indexes the assessment runs against are:

   - [Configure Microsoft Entra for increased security](/entra/fundamentals/configure-security?toc=%2Fsecurity%2Fzero-trust%2Fassessment%2Ftoc.json&bc=%2Fsecurity%2Fzero-trust%2Fassessment%2Ftoc.json)—Entra-side index.
   - [Configure Microsoft Intune for increased security](/intune/device-security/ref-zero-trust-security?toc=%2Fsecurity%2Fzero-trust%2Fassessment%2Ftoc.json&bc=%2Fsecurity%2Fzero-trust%2Fassessment%2Ftoc.json)—Intune-side index.
   - [Configure Microsoft Purview for increased security](/purview/configure-security)—Microsoft Purview-side index.
1. **Deploy Intune security baselines for endpoints.** Apply Microsoft's recommended configurations for Windows, Microsoft Edge, Defender for Endpoint, and Windows 365. These baselines reflect settings validated by Microsoft security teams and report compliance directly in Intune. Intune enrollment is also the prerequisite for the most effective identity control available—Conditional Access that requires a compliant, managed device—so treat devices as identities and plan enrollment accordingly. For more information, see [Use security baselines to help secure Windows devices you manage with Microsoft Intune](/mem/intune/protect/security-baselines).
1. **Apply Azure security baselines for cloud services.** Use **Microsoft Defender for Cloud's** regulatory compliance dashboard to measure your Azure, AWS, and GCP workloads against the **Microsoft Cloud Security Benchmark (MCSB)**. For more information, see:

   - [Introduction to the Microsoft cloud security benchmark](/security/benchmark/azure/introduction)
   - [Microsoft cloud security benchmark in Defender for Cloud](/azure/defender-for-cloud/concept-regulatory-compliance)
1. **Enforce Conditional Access baselines or Security Defaults, not both.** New or small tenants should keep Security Defaults on. Tenants on Microsoft Entra ID P1/P2 should disable Security Defaults and deploy the Microsoft-managed Conditional Access templates to enforce multifactor authentication (MFA), block legacy authentication, and require compliant devices—the most impactful identity controls with minimal configuration.
1. **Harden your servers at the OS layer.** Apply **OSConfig** security baselines to Windows Server 2025 (`MemberServer`, `WorkgroupMember`, `DomainController` scenarios, plus SecuredCore and Microsoft Defender Antivirus), and apply Azure Policy guest configuration baselines to Windows Server 2022/2019/2016/2012, Linux, CIS Linux, and Docker hosts. Both are audit-and-remediate and surface findings in Defender for Cloud's "Vulnerabilities in security configuration on your machines should be remediated" recommendation. For more information, see:

   - [OSConfig overview](/windows-server/security/osconfig/osconfig-overview)
   - [Deploy Windows Server 2025 security baselines locally with OSConfig](/windows-server/security/osconfig/osconfig-how-to-configure-security-baselines)
   - [Windows security baseline](/azure/governance/policy/samples/guest-configuration-baseline-windows)

## Track posture with built-in scoring surfaces

Once the controls are in place, track posture over time using the built-in scoring surfaces. Don't rebuild them:

- **Microsoft Secure Score**—Tenant-wide posture across identity, data, devices, apps, and infrastructure in the Microsoft Defender portal.
- **Identity Security Initiative**—Provides posture and recommendations across Microsoft Entra, Active Directory, software as a service (SaaS) applications, and non-Microsoft identity providers, and appears in Microsoft Security Exposure Management, Microsoft Secure Score, and the Entra Admin Center. (Requires Defender for Identity and Defender for Cloud Apps.)
- **Microsoft Cloud Security Benchmark in Defender for Cloud**—Posture for Azure, AWS, and GCP workloads, measured against MCSB. Its latest version, currently in preview, adds an AI Security domain covering more than 420 controls across more than 65 services.
- **Zero Trust Assessment report**—Point-in-time evidence across Entra, Intune, and Microsoft Purview, with per-check risk, user-impact, and implementation-cost.

## Accelerate with AI-powered agents

- The **Conditional Access Optimization Agent** in Microsoft Entra is an AI-driven capability that continuously monitors Conditional Access policies to identify coverage gaps, policy conflicts, and optimization opportunities, recommending refinements that strengthen Zero Trust access controls without disrupting user productivity. For more information, see [Microsoft Entra Conditional Access Optimization Agent](/entra/security-copilot/conditional-access-agent-optimization).
- The **Policy Configuration Agent** in Microsoft Intune is an AI-powered capability that interprets regulatory frameworks, compliance baselines, and uploaded policy documents such as Security Technical Implementation Guides (STIGs), Center for Internet Security (CIS) benchmarks, and National Institute of Standards and Technology (NIST) guidelines, and translates them into actionable Intune settings catalog policies, reducing manual configuration effort and policy drift. For more information, see [Policy Configuration Agent in Microsoft Intune](/intune/copilot/agents/policy-configuration-agent).
- The **Change Review Agent** in Microsoft Intune is an AI-driven capability that evaluates Multi-Admin Approval requests for PowerShell scripts by performing risk-based analysis using signals from Microsoft Defender, Microsoft Entra ID, and Intune, providing contextual insights that help administrators make informed approve-or-deny decisions. For more information, see [Change Review Agent overview](/intune/copilot/agents/change-review-agent).

## Next steps

- [Stay current on Microsoft software](stay-current-microsoft-software.md)
- [Scan and secure your source code](scan-secure-source-code.md)
- [Adopt updates for open-source software (OSS) components](adopt-open-source-updates.md)
- [Minimize internet-facing exposure](minimize-internet-exposure.md)
- [Secure Now overview](secure-now-overview.md)
