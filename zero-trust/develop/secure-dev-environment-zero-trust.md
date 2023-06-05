---
title: Securing the developer environment for Zero Trust
description: Learn how to secure your developer environment with best practices for branch security and trusting tools, extensions, and integrations so that you can implement Zero Trust principles.
ms.service: identity
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
ms.date: 11/11/2022
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to secure my development environment and learn best practices for branch security and trusting tools, extensions, and integrations so that I can implement Zero Trust principles.
---
# Securing the developer environment for Zero Trust

This article will help you, as a developer, to secure your development environment so that you can implement [Zero Trust principles](../zero-trust-overview.md) (verify explicitly, use least privilege access, assume breach). It features content from our [Securing Enterprise DevOps Environments](https://aka.ms/SecureDevEnvironmentsEbook) eBook and highlights best practices for branch security and trusting tools, extensions, and integrations.

Developer velocity relies on your ability to work how and where you want to maximize  business outcomes. You want powerful, customizable machines with root or administrator access. However, developer demands can run contrary to compliance regulations and the need to audit and control private employee environment access and storage.

Unmanaged machines that connect to the organization network challenge security teams, procurement, and the governance board. The best-case scenario of providing developers with default and hardened employee environments creates disdain on both sides. When employees connect from anywhere, vulnerable Wi-Fi networks are an open door for cyberattack. Hardware theft and loss are major concerns.

Vulnerabilities extend to development environment integrations. Development tools that feature rich extensibility may have unmaintained integrations in their marketplaces. Malicious extensions can endanger developer tools and cause company-wide breaches.

In the diagram below, notice how the developer environment connects to the DevOps tools environment to affect Git branches. It widens the environment surface through connection to third-party open-source packages and application extensions. Extensions present attack vectors in dependency and extension application vulnerabilities.

:::image type="content" source="../media/develop/secure-devops-environments/diagram-developer-environment-overview-inline.png" alt-text="Diagram illustrates developer environments and security threats as described in above-linked eBook and summarized in related articles linked herein." lightbox="../media/develop/secure-devops-environments/diagram-developer-environment-overview-expanded.png":::

Giving DevOps team members flexibility and control while preventing malicious attacks is a fundamental challenge for security offices. DevOps can control the developer environment with a cloud environment (see [Trusted launch for Azure VMs](/azure/virtual-machines/trusted-launch) and [GitHub Enterprise Cloud Docs](https://docs.github.com/enterprise-cloud@latest/admin)) and secure the developer environment with containers (see [GitHub Codespaces Documentation](https://docs.github.com/codespaces)).

In addition, developers can implement these Zero Trust measures to help secure the developer environment:

- Configure least privilege.
- Limit who can change and approve code with branch security.
- Adopt only trusted tools, extensions, and integrations.

## Best practices for least privilege

Developers often believe that they can catch malware, phishing, and breaches in their environments. Large developer environment threat surfaces make it unrealistic for developers to maintain omnipresent system knowledge. When an organization detects a breach after an attack compromises a developer environment that has administrator access to all systems, precious remediation time may have already passed.

To remediate potential access opportunities that cause hackers to target the software developer role, consider the following Zero Trust least privilege [security best practices for apps](https://docs.github.com/developers/github-marketplace/creating-apps-for-github-marketplace/security-best-practices-for-apps).

- **Implement least privilege and just-in-time access for DevOps.** Make sure that team members maintain only minimal access to environments for the shortest required time. Put policies in place to cover administrator access rights on main devices, DevOps tools, release pipelines, code repositories, environments, secret stores, and databases. For DevOps teams, the base requirement is a [connection to the organization identity store](https://docs.github.com/actions/deployment/security-hardening-your-deployments/configuring-openid-connect-in-azure). Use identity federation for integrating with SaaS environments to avoid duplication of identities on third party platforms and to reduce exposure risk.
- **Don't use personal access tokens for source code access.** Secure practices for DevOps teams include access to SaaS-based DevOps tools, code repositories (via SSH, HTTPS, or personal access token). For SaaS-based environment access, have clear instructions for how access principles dictate who can download (clone) systems code repos and from which devices (local, cloud, and container). For example, OneDrive can block or limit [unmanaged device access](/sharepoint/control-access-from-unmanaged-devices).
- **Standardize and synchronize GitHub Enterprise Managed User (EMU) user accounts with corporate identities.** With [Enterprise Managed Users](https://docs.github.com/enterprise-cloud@latest/admin/identity-and-access-management/using-enterprise-managed-users-for-iam/about-enterprise-managed-users), you can control the user accounts of your enterprise members through your identity provider (IdP). In your organization identity store, explicitly define GitHub usernames, emails, and display names. Users then easily identify collaborators even when they've never met face-to-face.
- **For the three ways a developer can connect to a SaaS environment (HTTPS with an identity, personal access token, connecting with SSH key), make connections with the organization identity store.** With GitHub (except for GitHub EMU accounts), your identity is and always will be your public identity. Controlled [access via SSO](https://docs.github.com/rest/overview/other-authentication-methods) requires connection with the organization identity store.
- **Use an SSH certificate authority (CA) to provide signed SSH certificates for members to securely access resources with Git.** An SSH certificate is a mechanism for one SSH key to sign another SSH key. [GitHub Enterprise Cloud](https://docs.github.com/enterprise-cloud@latest/admin) supports SSH certificates to give organizations more control over how members access repositories. Admins can upload their SSH CA public key and issue certificates for members to use for Git authentication. Certificates can only access repositories that belong to the organization. Admins can require members to use certificates when accessing their repositories.
- **Use a Git credential manager to harden access to your code.** Tools like Visual Studio (VS) have built-in [identity support](/visualstudio/subscriptions/use-connected-identities). VS Code will defer to a [Git credential manager](https://docs.github.com/get-started/getting-started-with-git/caching-your-github-credentials-in-git).

## Best practices for branch security

When hackers gain access to the code repository, they can study system security and modify code without teams noticing. To prevent unauthorized code repository access, implement a [branching strategy](/azure/devops/repos/git/branch-policies) to establish control over code changes (see example illustrated in the following diagram).

:::image type="content" source="../media/develop/secure-devops-environments/diagram-branching-strategy-inline.png" alt-text="Diagram illustrates an example branching strategy that protects the main repository." lightbox="../media/develop/secure-devops-environments/diagram-branching-strategy-expanded.png":::

To remediate potential repository access opportunities, consider the following branch security best practices.

- **Protect branches with code reviews to give DevOps teams control over code changes and auditing advances.** The branching strategy in the preceding diagram articulates a controlled flow of changes that delivers a clear chain of command and blueprint for [addressing code changes](https://docs.github.com/organizations/organizing-members-into-teams/managing-code-review-settings-for-your-team). Of the different approaches for the branching strategy, one commonality is that protected branches serve as the source for new releases to production.
- **Have administrators of Git repositories control approval authorizations.** The control mechanism of branching strategies is in the [approval workflow](https://docs.github.com/enterprise-cloud@latest/actions/managing-workflow-runs/approving-workflow-runs-from-public-forks). Protected branches require validations, reviews, and approvals before accepting changes. One option is to create a branch protection rule to enforce workflows. For example, require an approval review or status check pass for all pull requests merged into the protected branch. [Branch policies](https://docs.github.com/rest/deployments/branch-policies) help teams protect important branches of development. Policies enforce your team's code quality and change management standards.

## Best practices for trusting tools, extensions, and integrations

Extensibility in integrated developer environments (IDE) is so productive that it's essentially a mandated feature. You rely on the ability to apply and curate extensions within the marketplace of a specific IDE to design your optimal work environment.

To remediate secure IDEs, consider the following tool, extension, and integration best practices.

- **Ensure that you only integrate tools from both trusted marketplaces and publishers.** For example, the [VS Code marketplace](https://marketplace.visualstudio.com/VSCode) has thousands of extensions to make your life easier. However, when your teams adopt new tools or extensions, the most important aspect can be verifying a publisher's trustworthiness.
- **Set up secure practices to control extension use to limit the attack surface of developer environments.** Most IDE extensions require approving certain privileges to function, often as a file with read permissions on the system to analyze code. Extensions require connections to cloud environments to function (common in metric tools). Approving extra functionalities on top of the IDE opens up organizations to more threats.
- **On developer machines, track the number and maturity of used extensions to understand the potential attack surface.** Incorporate only VS Code marketplace extensions from [verified publishers](https://code.visualstudio.com/api/working-with-extensions/publishing-extension). When you're installing third-party application extensions with VS Code, regularly check extensions that you're running with the command line, code `--list-extensions --show-versions`. Have a good understanding of extensible components that you're running in your developer environment.

## Next steps

- [Embedding Zero Trust security into your developer workflow](embed-zero-trust-dev-workflow.md) helps you to innovate quickly and securely.
- [Securing the DevOps platform environment](secure-devops-platform-environment-zero-trust.md) helps you to implement Zero Trust principles in your DevOps platform environment and highlights best practices for secret and certificate management.
- [Securing DevOps environments for Zero Trust](secure-devops-environments-zero-trust.md) describes best practices for securing your DevOps environments with a Zero Trust approach for preventing hackers from compromising developer boxes, infecting release pipelines with malicious scripts, and gaining access to production data via test environments.
- Implement Zero Trust principles as described in memorandum 22-09 (in support of US executive order 14028, Improving the Nation's Cyber Security) by using Azure Active Directory (Azure AD) as a [centralized identity management system](/azure/active-directory/standards/memo-22-09-meet-identity-requirements).
- [Accelerate and secure your code with Azure DevOps](/events/resources/build-2022/accelerate-secure-devops) with tools that give developers the fastest and most secure code to cloud experience.
- Configure Azure to trust GitHub's OIDC as a federated identity. OpenID Connect (OIDC) allows your GitHub Actions workflows to [access resources in Azure](https://docs.github.com/actions/deployment/security-hardening-your-deployments/configuring-openid-connect-in-azure)without needing to store the Azure credentials as long-lived GitHub secrets.
