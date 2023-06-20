---
title: Embedding Zero Trust security into your developer workflow
description: Learn how to develop using Zero Trust principles so that you can innovate quickly and securely.
ms.service: identity
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
ms.date: 11/11/2022
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to develop using Zero Trust principles so that I can innovate quickly and securely.
---
# Embedding Zero Trust security into your developer workflow

As a developer, you need to feel confident and secure to move at speed. The need for security starts as soon as you clone your code. In this article, you'll learn how to [develop using Zero Trust principles](overview.md) so that you can innovate quickly and securely. The [Zero Trust security strategy](../zero-trust-overview.md) and approach for designing and implementing applications comprises these principles:

- **Verify explicitly**. Always authenticate and authorize based on all available data points.
- **Use least privilege access.** Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection.
- **Assume breach.** Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses.

Embedding security into your workflow helps you to:

- Pinpoint security vulnerabilities more quickly.
- Provide more secure developer tooling.
- Create connections to improve collaboration between security and development teams.

## Power innovation and secure your workflow as you create code

Microsoft's unified solution, illustrated in the following diagram, bridges across DevOps and SecOps teams to help you accelerate and secure code-to-cloud development.

:::image type="complex" source="../media/develop/embed-zero-trust-dev-workflow/diagram-code-to-cloud-dev-solution-inline.png" alt-text="Diagram shows the technologies that comprise the unified code-to-cloud development solution." lightbox="../media/develop/embed-zero-trust-dev-workflow/diagram-code-to-cloud-dev-solution-expanded.png":::
   Diagram title: Microsoft provides a unified solution. Diagram subtitle: to help you accelerate and secure code-to-cloud development. Listed technologies: Visual Studio Code, GitHub Codespaces, Visual Studio, Microsoft DevBox, GitHub Advanced Security, Azure Pipelines, GitHub Actions, Azure AD, Azure.
:::image-end:::

Our solution to safeguard DevOps relies on two main components: providing developers with tooling to power innovation and securing the developer workflow as developers create code. Watch the [Accelerate and secure your code to cloud development](https://mybuild.microsoft.com/sessions/84ff7d8d-64da-4a5e-9c84-92f7b6387225) session from [Microsoft Build 2022](https://mybuild.microsoft.com/) to learn how these components can secure your development environment.

Implement the following best practices that work together in Azure and GitHub to secure your development solution.

- Because security starts when developers clone code, [enable DevSecOps with Azure and GitHub](/devops/devsecops/enable-devsecops-azure-github) to bridge across DevOps and SecOps teams and secure your development environments.
- Provide flexible and powerful developer tools for any developer, language, and stack with [Visual Studio](/visualstudio/) and [Visual Studio Code](https://code.visualstudio.com/docs).
- Simplify new developer onboarding and third-party collaboration with an entire development lifecycle tool in the cloud using [GitHub Codespaces](https://docs.github.com/codespaces) and [Microsoft Dev Box](/azure/dev-box/).
- Include built-in intellectual property protection for code that you no longer disperse into multiple locations. Help your teams collaborate, develop, automate, and deploy code wherever they want with [GitHub Actions](https://docs.github.com/actions) and [Azure Pipelines](/azure/devops/pipelines/security/overview).
- Get security guidance and continuous security feedback within the developer workflow with code scanning, secret scanning, and dependency review using [GitHub Advanced Security](https://docs.github.com/get-started/learning-about-github/about-github-advanced-security).
- Instill zero-trust security throughout your organization using [identity management services](/azure/active-directory/develop/workload-identity-federation) in Azure Active Directory (Azure AD).

## Fit Zero Trust security into your development lifecycle

From pre-commit to commit through deploy then operate and monitor, you need security solutions in place throughout all of your development lifecycle stages.

### Pre-commit stage

- Threat modeling
- IDE security plug-in
- Pre-commit hooks
- Secure coding standards
- Peer review

Eighty-five percent of code defects appear during the development pre-commitment phase, mostly due to human error. Focus on security before you commit your code by writing your code in Visual Studio Code, Visual Studio, or GitHub Codespaces to identify vulnerabilities and secure code. Use peer reviews to encourage secure coding practices.

### Commit (CI) stage

- Static code analysis
- Security unit tests
- Dependency management
- Credential scanning

During the commit stage, use extensive security methods to review your code (including static code analysis) and scan your code as you check it into your source control. Use credential scanning (also known as secret scanning or token scanning) to expose credentials that you may have inadvertently introduced into the codebase. Catch insecure dependencies before you introduce them to your environment with dependency review.

### Deploy (CD) stage

- Infrastructure as code (IaC) scanning
- Dynamic security scanning
- Cloud configuration checks
- Security acceptance tests

During the deploy stage, look at the overall health of your codebase and perform high-level security scanning to identify risks. Perform cloud configuration checks, infrastructures code checks, and security acceptance tests to ensure alignment with organizational security goals.

### Operate and monitor stage

- Continuous monitoring
- Threat intelligence
- Blameless postmortems

During the operate and monitor phase, use continuous monitoring and threat intelligence to mitigate overall dependency vulnerabilities that you may inherit over time. Perform postmortems to take away lessons learned and continue iterating through your DevOps cycle.

## Implement dependency, code, and secret scanning

To make securing code easier for developers, use native and automated capabilities to provide continuous feedback with continuous security features throughout your development lifecycle. Provide overall security to developers and communities with GitHub Advanced Security dependency scanning, code scanning, and secret scanning.

### Dependency scanning

- Integrated review of dependencies
- Alerts and security updates

Get risk levels of dependencies and automated fixes to vulnerable dependencies in your codebase with continuous [dependency scanning](https://docs.github.com/code-security/supply-chain-security/understanding-your-software-supply-chain/about-dependency-review). As a continuous process, it nudges your developers in the right direction in a friendly and non-obtrusive way.

### Code scanning

- Extensible framework for code scanning
- Integrated within the developer workflow
- Backed by industry leading CodeQL engine

Implement [code scanning](https://docs.github.com/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/about-code-scanning) as you generate code with no other steps to run at separate locations. Ease fixes early in your development lifecycle by viewing scanning results in your familiar GitHub user experience.

### Secret scanning

- Scan for leaked secrets in public and private repos
- Partnership with 40+ providers
- Push protection
  - Move from remediation to prevention
  - Check for high-confidence secrets
  - Enable protection with one click

Scan your code for hardcoded credentials and tokens with [secret scanning](https://docs.github.com/code-security/secret-scanning/about-secret-scanning). Push protection scans for secrets and tokens before you push to your codebase. Check for high-confidence secrets as developers push code, blocking the push when GitHub identifies a secret.

## Manage and secure workload identities

- Lifecycle management
- Access governance
- Secure adaptive access

Get visibility into the activity of your [workload identities](/azure/active-directory/develop/workload-identities-overview) and enable periodic cleanup. Determine who owns workload identities and how you keep this information up to date across organization changes. Track when you have last used workload identities, when you last issued tokens and when tokens expire.

To mitigate the potential for leaked secrets and credentials, periodically conduct access reviews. Require users to review their workload identities and remove unnecessary access privileges. Have users report overprivileged and underutilized access privileges. Discuss how you'll protect workload identities from breach. Enable conditional access to ensure that access is originating from expected resources.

## Secure identities with GitHub OIDC and Azure AD Workload Identity Federation

To further secure your organization, use [GitHub OpenID Connect](https://docs.github.com/actions/deployment/security-hardening-your-deployments/about-security-hardening-with-openid-connect) (OIDC) with Azure AD [Workload Identity Federation](/azure/active-directory/develop/workload-identity-federation) and minimize the need to store and access secrets. Securely manage Azure server principal secrets and other long-lived cloud credentials resources to minimize service downtime due to expired credentials. Integrate with developer platforms, like GitHub Actions, to securely build your apps.

Our recommended Workload Identity Federation workflow, illustrated in the following diagram, comprises six steps.

:::image type="content" source="../media/develop/embed-zero-trust-dev-workflow/diagram-workload-identity-federation-inline.png" alt-text="Diagram illustrates the six Workload Identity Federation workflow steps that are described below." lightbox="../media/develop/embed-zero-trust-dev-workflow/diagram-workload-identity-federation-expanded.png":::

1. Set up trust in Azure AD and request a token.
1. Configure the GitHub workflow to allow actions to get the token.
1. GitHub workflow sends a request to Azure ID.
1. Azure AD validates the trust on the application and fetches the keys to validate the token.
1. Azure AD accesses and issues the token.
1. The deploy action uses the Azure AD access token to deploy to resources in Azure.

Watch April Edwards, Senior Cloud Advocate and DevOps Practice Lead, demo the Workload Identity Federation workflow. The demonstration begins at the 19:14 mark in the [Accelerate and secure your code to cloud development](https://mybuild.microsoft.com/en-US/sessions/84ff7d8d-64da-4a5e-9c84-92f7b6387225?source=sessions) Microsoft Build 2022 session that is [also available on YouTube](https://www.youtube.com/watch?v=1fMdA3pSBaY&t=1154s) (embedded below).

> [!VIDEO https://www.youtube.com/embed/1fMdA3pSBaY]

## Next steps

- Sign up for [Azure Developer CLI](/azure/developer/azure-developer-cli/overview), an open-source tool that accelerates the time it takes to get started on Azure.
- Configure Azure to trust GitHub's OIDC as a federated identity. OpenID Connect (OIDC) allows your GitHub Actions workflows to [access resources in Azure](https://docs.github.com/actions/deployment/security-hardening-your-deployments/configuring-openid-connect-in-azure) without needing to store the Azure credentials as long-lived GitHub secrets.
- Implement Zero Trust principles as described in memorandum 22-09 (in support of US executive order 14028, Improving the Nation's Cyber Security) by using Azure Active Directory (Azure AD) as a [centralized identity management system](/azure/active-directory/standards/memo-22-09-meet-identity-requirements).
- [Accelerate and secure your code with Azure DevOps](/events/resources/build-2022/accelerate-secure-devops) with tools that give developers the fastest and most secure code to cloud experience.
- [Securing the developer environment](secure-dev-environment-zero-trust.md) helps you to implement Zero Trust principles in your development environments with best practices for least privilege, branch security, and trusting tools, extensions, and integrations.
- [Securing DevOps environments for Zero Trust](secure-devops-environments-zero-trust.md) describes best practices for securing your DevOps environments for preventing hackers from compromising developer boxes, infecting release pipelines with malicious scripts, and gaining access to production data via test environments.
- [Customizing tokens](zero-trust-token-customization.md) describes the information that you can receive in Azure AD tokens and how to customize tokens to improve flexibility and control while increasing application zero trust security with least privilege.
- [Configuring group claims and app roles in tokens](configure-tokens-group-claims-app-roles.md) shows you how to configure your apps with app role definitions and assign security groups to app roles to improve flexibility and control while increasing application zero trust security with least privilege.
