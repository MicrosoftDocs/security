---
title: Securing the DevOps platform environment for Zero Trust
description: Learn best practices for secret and certificate management so that DevOps team members can secure their DevOps platform environments.
ms.service: identity
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
ms.date: 11/11/2022
ms.custom: template-concept
# Customer intent: As a DevOps team member, I want learn best practices for secret and certificate management so that I can secure my DevOps platform environments.
---
# Securing the DevOps platform environment for Zero Trust

This article will help you, as a DevOps team member, to implement the [Zero Trust principle](../zero-trust-overview.md) of least privilege and secure the DevOps platform environment. It features content from our [Securing Enterprise DevOps Environments](https://aka.ms/SecureDevEnvironmentsEbook) eBook and highlights best practices for secret and certificate management.

Modern enterprises rely on DevOps platforms for deployment, including pipelines and production environments that developers require to be productive. In the past, application security methods didn't consider the increased attack surface that present day pipelines and production environments expose. As hackers shift left and target upstream tools, you need innovative approaches to secure your DevOps platform environments.

In the diagram below, notice that the DevOps platform environment connects to the application environment and to [continuous integration and continuous delivery](/azure/devops/pipelines/get-started/key-pipelines-concepts) (CI/CD) pipeline extensions.

:::image type="content" source="../media/develop/secure-devops-environments/diagram-devops-platform-environment-overview-inline.png" alt-text="Diagram illustrates DevOps platform environments and security threats as described in above-linked eBook and summarized in related articles linked herein." lightbox="../media/develop/secure-devops-environments/diagram-devops-platform-environment-overview-expanded.png":::

CICD pipeline extensions present hackers with opportunities to engage in privilege escalations from the application environment. Extensions and integrations increase attack surface vulnerabilities. It's critical to defend against malware intrusion threats.

## How and why attackers target pipelines

Pipelines and production environments may be independent of standard application security practices and processes. They typically require high-level access credentials that can provide deep and meaningful access to attackers.

While attackers find new ways to compromise systems, the most common attack vectors for pipelines include:

- Extracting runtime variables and argument injection.
- Scripts that retrieve service principles or credentials from pipelines.
- Misconfigured personal access tokens that allow anyone with the key to access the DevOps platform environment.
- Vulnerabilities and misconfigurations in third-party integrated tools that require access to the code (often read-only, but sometimes write access). Integrated tools can include test frameworks, static application security testing (SAST), and dynamic application security testing (DAST).

## Best practices for secret and certificate management

Avoiding a catastrophic breach can be as simple as effective secret management. The diagram below illustrates an example of effective secret, password, access token, and certificate management.

:::image type="content" source="../media/develop/secure-devops-environments/diagram-secret-management-example-inline.png" alt-text="Diagram illustrates secret and certificate management as described below." lightbox="../media/develop/secure-devops-environments/diagram-secret-management-example-expanded.png":::

As shown in the above diagram, the developer starts a build for a customer request. GitHub then starts a runner with a Vault App Role's role ID and secret ID. The Trusted Entity periodically requests a new secret ID from the Vault and gets the GitHub Secret secret ID from GitHub. The Vault uses the GitHub Secrets role ID and secret ID to sign in and get code-signing assets. The Runner customizes and code-signs the mobile app.

The following best practices will help you to build a secure setup that minimizes secret and parameter exposure.

- **Provide secure storage for secrets and certificates at each application lifecycle stage.** Always develop as if it's an open-source project. Ensure that teams are storing secrets in key vaults rather than in the code or on team environments. Use the [Azure Key Vault](/azure/key-vault/general/basic-concepts) cloud service for securely storing and accessing secrets.
- **Configure Azure to trust GitHub's OIDC as a federated identity.** OpenID Connect (OIDC) allows your GitHub Actions workflows to [access resources in Azure](https://docs.github.com/actions/deployment/security-hardening-your-deployments/configuring-openid-connect-in-azure) without needing to store the Azure credentials as long-lived GitHub secrets.

## More best practices for DevOps environment security

To help defend against security incidents, below are more best practices to fortify your DevOps platform environments. Find a detailed discussion of these recommendations in our [Securing Enterprise DevOps Environments](https://aka.ms/SecureDevEnvironmentsEbook) eBook.

- **Equip every DevOps platform environment with audit trails.** [Review audit logs to track](https://docs.github.com/enterprise-cloud@latest/organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/reviewing-the-audit-log-for-your-organization) who gained access, what change occurred, and the date/time for any active system. Specifically include DevOps platforms with CI/CD pipelines that flow into production. Audit trails for DevOps tools provide robust ways to remediate threats quicker, find and alert on suspicious activities to possible breaches or vulnerabilities, and find potential data or privilege misuse. Ensure granular control and audit trails are available across each environment.
- **Secure the software supply chain.** With every library you bring into your codebase, you expand the software supply chain and inherit dependencies from each open-source project or tool. With caution, remove unnecessary libraries and open-source components to reduce the attack surface of your software supply chain.
- **Automate Infrastructure-as-Code (IaC) template scans.** With [IaC environments](/azure/cloud-adoption-framework/ready/considerations/infrastructure-as-code), it's easy to scan for misconfigurations, compliance audits, and policies issues. Implementing compliance checks and access controls raises the security posture of your entire infrastructure. Verify the security of third-party tool integrations that fulfill automation system requirements.
- **Automate approval workflows.** For any approval workflow to push code into production, certain automatic or manual checks must confirm security, business value, status, and quality of each request. These checks function as a gate between development and production to prevent denial-of-service attacks and hackers injecting code into production environments without flagging or triggering an alert.
- **Allow only verified DevOps tool integrations.** As in developer environments, DevOps tools come with extensions and integrations to make the DevOps team efficient and secure. Confirm that verified integrations require the least privilege possible to execute their work. Implement least privilege access when possible and ensure the right level of read/write permissions. Learn how to [disable or limit GitHub Actions for your organization.](https://docs.github.com/organizations/managing-organization-settings/disabling-or-limiting-github-actions-for-your-organization)

## Next steps

- [Securing the developer environment](secure-dev-environment-zero-trust.md) helps you to implement Zero Trust principles in your development environments with best practices for least privilege, branch security, and trusting tools, extensions, and integrations.
- [Embedding Zero Trust security into your developer workflow](embed-zero-trust-dev-workflow.md) helps you to innovate quickly and securely.
- [Securing DevOps environments for Zero Trust](secure-devops-environments-zero-trust.md) describes best practices for securing your DevOps environments with a Zero Trust approach for preventing hackers from compromising developer boxes, infecting release pipelines with malicious scripts, and gaining access to production data via test environments.
- Implement Zero Trust principles as described in memorandum 22-09 (in support of US executive order 14028, Improving the Nation's Cyber Security) by using Azure Active Directory (Azure AD) as a [centralized identity management system](/azure/active-directory/standards/memo-22-09-meet-identity-requirements).
- [Accelerate and secure your code with Azure DevOps](/events/resources/build-2022/accelerate-secure-devops) with tools that give developers the fastest and most secure code to cloud experience.
