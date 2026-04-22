---
title: Scan and secure your source code
description: Connect your repositories, pipelines, registries, and runtime workloads to Microsoft Defender for Cloud to secure your development lifecycle from code to cloud.
ms.date: 04/21/2026
ms.service: security
ms.subservice: zero-trust
ms.topic: concept-article
ms.collection:
  - highpri
  - zerotrust
ai-usage: ai-assisted
---

# Scan and secure your source code

Secure your development lifecycle from code to cloud by connecting your source code repositories, CI/CD pipelines, container registries, and runtime workloads to DevOps security in **Microsoft Defender for Cloud**. This gives your security and engineering teams a single view to catch risks early, focus on what's actually exploitable in production, and fix issues without blocking developers.

## Connect, scan, and trace from code to cloud

- **Connect your repositories and pipelines**—Onboard your GitHub, Azure DevOps, and GitLab environments into Defender for Cloud to get unified visibility across code repositories, pipelines, Infrastructure as Code (IaC) templates, and container images in one place.
- **Scan code and infrastructure before it ships**—Enable agentless code and IaC scanning to catch misconfigurations and vulnerabilities at the pull request stage. For tighter control, add the Defender for Cloud CLI directly into your CI/CD pipelines to enforce scanning as part of every build.
- **Trace vulnerabilities from code to running workload**—Use code-to-cloud contextualization to map findings back through build artifacts, registries, and runtime environments. This lets you prioritize the vulnerabilities that are actually reachable in production rather than chasing every finding.
- **Lock down your container supply chain**—Scan container images at build time, enforce policy-based gating to block vulnerable images from deploying, and correlate build-time findings with runtime behavior to catch threats that emerge after deployment. For more information, see [Enable gated deployment in Defender for Containers](/azure/defender-for-cloud/enablement-guide-runtime-gated).

## Operate, route, and protect runtime

- **Audit your DevOps posture**—Review your CI/CD pipelines, repository configurations, and service connections for unsecure settings, excessive permissions, and weak access controls. Use the DevOps posture management recommendations to systematically harden your development infrastructure.
- **Route fixes to the right developers**—Turn on pull request annotations so developers see security findings directly in their workflow. Use ownership mapping and workflow automation to assign remediation to the teams that own the code, integrated with the tools they already use.
- **Bring GitHub Advanced Security findings into Defender**—If you're using GitHub Advanced Security, connect it to Defender for Cloud to surface code scanning, secret detection, and dependency findings alongside your cloud posture and runtime risk, giving your security operations center (SOC) full visibility from commit to production.
- **Reduce supply chain risk from developer machines**—Use **GitHub Codespaces** or **Microsoft Dev Box** to provide pre-hardened, isolated cloud development environments with scoped repository access, encrypted secrets management, and full audit logging. Enforce endpoint protection and Conditional Access policies on developer accounts. For more information, see:
  - [Security in GitHub Codespaces](https://docs.github.com/codespaces/reference/security-in-github-codespaces)
  - [What is Microsoft Dev Box?](/azure/dev-box/overview-what-is-microsoft-dev-box)
- **Detect threats in running Kubernetes workloads**—Go beyond scan-time vulnerability detection by enabling **Microsoft Defender for Containers** runtime protection. A lightweight sensor deployed to Kubernetes nodes—such as Azure Kubernetes Service (AKS), Amazon Elastic Kubernetes Service (EKS), Google Kubernetes Engine (GKE), and Arc-enabled clusters—monitors for malicious activity including cryptocurrency mining, lateral movement, and drifted binaries with real-time alerts mapped to the MITRE ATT&CK framework. For more information, see [Container protection in Defender for Cloud](/azure/defender-for-cloud/defender-for-containers-introduction).

## Secrets and pipeline hardening

- Enable secret scanning and push protection at the organization level, with auto-enable for new repositories.
  - For GitHub: Enable **GitHub Secret Protection**. For more information, see [About secret scanning](https://docs.github.com/code-security/secret-scanning/introduction/about-secret-scanning).
  - For Azure DevOps: Enable Secret Protection in **GitHub Advanced Security for Azure DevOps**. For more information, see [Configure GitHub Advanced Security for Azure DevOps](/azure/devops/repos/security/configure-github-advanced-security-features).
- Harden the build pipeline with centrally managed templates, least-privilege identities, and OpenID Connect (OIDC)-based authentication to the cloud.
  - Use centrally managed pipeline templates to inject required scanners, Software Bill of Materials (SBOM) generation, signing, and compliance gates across all pipelines. For more information, see [Use YAML templates in pipelines for reusable and secure processes](/azure/devops/pipelines/security/templates).
  - Require two-reviewer pull-request approval and code signing in the central template before a release artifact is produced.
  - Replace long-lived credentials with workload identity federation (OIDC) for pipeline-to-cloud authentication. For more information, see [Workload identity federation concepts](/entra/workload-id/workload-identity-federation).
  - Use a dedicated service identity for the Defender for Cloud DevOps connector scoped to least privilege. For more information, see [Connect Azure DevOps environments to Defender for Cloud](/azure/defender-for-cloud/quickstart-onboard-devops).
  - Harden self-hosted build agents. Restrict outbound network access to only the Advanced Security and Defender endpoints required and ensure the CodeQL bundle is present. For more information, see [Configure GitHub Advanced Security for Azure DevOps](/azure/devops/repos/security/configure-github-advanced-security-features).

## AI-powered code review and exposure correlation

- **AI-powered code review**—You can assign **GitHub Copilot** as a PR reviewer to catch security issues using both AI and CodeQL. GitHub Copilot has completed more than 60 million reviews. For more information, see [Using GitHub Copilot code review](https://docs.github.com/copilot/using-github-copilot/code-review/using-copilot-code-review).
- Correlate code findings to cloud exposure using Defender for Cloud so you can fix what is actually reachable first.
- Connect your source-control organizations to Defender for Cloud and enable **Defender Cloud Security Posture Management (CSPM)**. For more information, see:
  - [Overview of Defender for Cloud](/azure/defender-for-cloud/defender-for-cloud-introduction)
  - [Identify and remediate attack paths](/azure/defender-for-cloud/how-to-manage-attack-path)
- Track organization-wide vulnerability exposure in **Microsoft Security Exposure Management**, which aggregates signal from Defender products to produce an end-to-end exposure score and prioritized remediation. See [What is Microsoft Security Exposure Management?](/security-exposure-management/microsoft-security-exposure-management).

## Accelerate with AI-powered agents

- The **Threat Hunting Agent** in Microsoft Defender enables analysts to investigate suspicious activity across code, pipelines, and runtime workloads using natural language queries, translating them into Kusto Query Language (KQL) and surfacing contextual insights without requiring manual query composition. For more information, see [Microsoft Security Copilot Threat Hunting Agent in advanced hunting](/defender-xdr/advanced-hunting-security-copilot-threat-hunting-agent).

## Next steps

- [Stay current on Microsoft software](stay-current-microsoft-software.md)
- [Adopt updates for open-source software (OSS) components](adopt-open-source-updates.md)
- [Minimize internet-facing exposure](minimize-internet-exposure.md)
- [Implement baseline security measures](baseline-security-measures.md)
- [Secure Now overview](secure-now-overview.md)
