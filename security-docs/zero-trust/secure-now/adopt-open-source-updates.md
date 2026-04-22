---
title: Adopt updates for open-source software (OSS) components - Microsoft Zero Trust
description: Harden your open-source supply chain by centralizing ingestion, scanning dependencies and containers, generating SBOMs, and protecting AI workloads.
ms.date: 04/21/2026
ms.service: security
ms.subservice: zero-trust
ms.topic: concept-article
ms.collection:
  - highpri
  - zerotrust
ai-usage: ai-assisted
---

# Adopt updates for open-source software (OSS) components

AI is compressing the time from public open-source CVE disclosure to exploitation, so the security update or patch window is now days. Most apps also depend on far more open source than teams realize (especially transitive dependencies), and public registries should be treated as untrusted inputs given dependency-confusion and typosquatting risks.

Expect leaked credentials to be abused quickly, so scan and update images, IaC modules, and build tools the same way you do libraries. Since many incidents compromise CI/CD, harden the pipeline and prioritize fixes by what's deployed and reachable—not just the pure Common Vulnerability Scoring System (CVSS) score. The following are the top actions to block the biggest attack paths first.

## Centralize open-source ingestion

Centralize open-source ingestion through a governed feed so every package is cached, scanned, and retained under your control.

- Use **Azure Artifacts** feeds with upstream sources as the single ingestion point for open source packages. For more information, see [What are upstream sources](/azure/devops/artifacts/concepts/upstream-sources) and [Azure Artifacts best practices](/azure/devops/artifacts/concepts/best-practices).
- Reference a single feed per repository in configuration files (for example, `nuget.config`, `.npmrc`, and `settings.xml`). For NuGet, include a `<clear />` element so higher-level configurations cannot reintroduce public sources.
- Block externally sourced versions by default. For more information, see [Safeguard against malicious public packages](/azure/devops/artifacts/concepts/upstream-behavior).
- Order upstreams intentionally. Place internally modified or hardened upstreams ahead of public registries so hardened copies are preferred over public ones.
- Apply retention policies to feeds to remove old, unpatched package versions automatically. Promote released versions to an immutable view so they are protected from cleanup. For more information, see [Azure Artifacts best practices](/azure/devops/artifacts/concepts/best-practices).

## Turn on dependency scanning and automated updates

Turn on dependency scanning and automated updates for every repository.

- For GitHub repositories, enable dependency scanning. For more information, see [Securing your supply chain](https://docs.github.com/code-security/supply-chain-security) and [About GitHub Advanced Security](https://docs.github.com/get-started/learning-about-github/about-github-advanced-security).
- For Azure repositories (Azure DevOps), enable dependency scanning. For more information, see [Configure GitHub Advanced Security for Azure DevOps](/azure/devops/repos/security/configure-github-advanced-security-features).
- Turn on Dependabot version updates and alerts on GitHub repositories. For more information, see [About Dependabot version updates](https://docs.github.com/code-security/dependabot/dependabot-version-updates/about-dependabot-version-updates) and [Dependabot supported ecosystems and repositories](https://docs.github.com/code-security/dependabot/working-with-dependabot/dependabot-options-reference).
- Enable Copilot Autofix for code scanning. For more information, see [About Copilot Autofix for code scanning](https://docs.github.com/code-security/concepts/code-scanning/copilot-autofix-for-code-scanning).
- Block pull-request merges on new high- or critical-severity dependency findings. For more information, see [Configure GitHub Advanced Security for Azure DevOps](/azure/devops/repos/security/configure-github-advanced-security-features).
- Aggregate findings across repositories by connecting your GitHub and Azure DevOps organizations to DevOps security in **Microsoft Defender for Cloud**. For more information, see [Overview of Microsoft Defender for Cloud DevOps security](/azure/defender-for-cloud/defender-for-devops-introduction), [Connect Azure DevOps environments to Defender for Cloud](/azure/defender-for-cloud/quickstart-onboard-devops), and [Quick Start: Connect your GitHub Environment to Microsoft Defender for Cloud](/azure/defender-for-cloud/quickstart-onboard-github).

## Generate a Software Bill of Materials (SBOM)

Generate a Software Bill of Materials (SBOM) on every build so you can answer the question "where is CVE-X in our estate?" in minutes.

- Generate a Software Package Data Exchange (SPDX)-compliant SBOM on every build using the open-source Microsoft SBOM tool, referenced from Microsoft documentation or Defender for Cloud. Ship the SBOM as a build artifact alongside the binary. For more information, see [microsoft/sbom-tool on GitHub](https://github.com/microsoft/sbom-tool) and [Defender for Cloud CLI Reference](/azure/defender-for-cloud/defender-cli-syntax).
- Enforce SBOM generation in a central pipeline template. For more information, see [Use YAML templates in pipelines for reusable and secure processes](/azure/devops/pipelines/process/templates).
- Measure SBOM compliance (percentage of production builds that produce an SBOM automatically) as a program-level metric.

## Scan containers and IaC

Scan containers and IaC both in the pipelines and Container Registries.

- Scan IaC templates (Terraform, Bicep, ARM, CloudFormation, Kubernetes manifests, Helm charts, and Docker files) in the pipeline using the Microsoft Security DevOps Azure DevOps extension. For more information, see [Configure the Microsoft Security DevOps Azure DevOps extension](/azure/defender-for-cloud/azure-devops-extension).
- Scan container images in the pipeline and at the registry. The Microsoft Security DevOps extension includes container scanning for pipeline use; **Defender for Containers** scans images in Azure Container Registry and protects running workloads. For more information, see [Overview of Microsoft Defender for Containers](/azure/defender-for-cloud/defender-for-containers-introduction).
- Enable pull-request annotations for IaC and code-scanning findings so issues are commented on the pull-request diff, with the ability to block merge at a configured severity. For more information, see [Enable pull request annotations](/azure/defender-for-cloud/enable-pull-request-annotations).
- Enable container image mapping. When you connect Azure DevOps to Defender for Cloud, container images are mapped back to the pipeline and repository that produced them. For more information, see [Connect your Azure DevOps organizations](/azure/defender-for-cloud/quickstart-onboard-devops).

## Discover and protect AI deployments

Use AI Security Posture Management (AI-SPM) in Defender for Cloud to inventory all deployed AI models and services (for example, Azure OpenAI, Copilot Studio, AWS Bedrock, or GCP Vertex AI) automatically, generate an AI Bill of Materials, analyze attack paths targeting AI workloads, and detect threats such as prompt injection and data leakage. For more information, see [Overview - AI security posture management](/azure/defender-for-cloud/ai-security-posture).

## Accelerate with AI-powered agents

The Threat Intelligence Briefing Agent in Microsoft Defender generates tailored threat intelligence briefings based on real-time threat actor activity, including emerging supply-chain and CI/CD attack campaigns relevant to your environment, with actionable recommendations and MITRE ATT&CK framework mapping. For more information, see [Microsoft Security Copilot Threat Intelligence Briefing Agent](/copilot/security/threat-intel-briefing-agent).

## Next steps

- [Stay current on Microsoft software](stay-current-microsoft-software.md)
- [Scan and secure your source code](scan-secure-source-code.md)
- [Minimize internet-facing exposure](minimize-internet-exposure.md)
- [Implement baseline security measures](baseline-security-measures.md)
