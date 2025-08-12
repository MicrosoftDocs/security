---
title: Secure DevOps environments for Zero Trust
description: Learn best practices to secure DevOps environments and prevent compromise of developer boxes, release pipelines, and production data.
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
ms.date: 02/24/2025
ms.custom: template-concept
ms.service: zero-trust
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to learn best practices for securing my DevOps environments so that I can prevent bad actors from compromising developer boxes, infecting release pipelines with malicious scripts, and gaining access to production data via test environments.
---
# Secure DevOps environments for Zero Trust

Securing DevOps environments is no longer a choice for developers. Bad actors are shifting left so you must implement [Zero Trust principles](../zero-trust-overview.md) that include verify explicitly, use least privilege access, and assume breach in DevOps environments.

This article describes best practices for securing your DevOps environments with a Zero Trust approach for preventing bad actors from compromising developer boxes, infecting release pipelines with malicious scripts, and gaining access to production data via test environments.

Our [Securing Enterprise DevOps Environments](https://aka.ms/SecureDevEnvironmentsEbook) eBook features the following visualization of the developer, DevOps platform, and application environments along with the potential security threats for each.

:::image type="content" source="../media/develop/secure-devops-environments/diagram-enterprise-devops-overview-inline.png" alt-text="Diagram illustrates DevOps environments and security threats." lightbox="../media/develop/secure-devops-environments/diagram-enterprise-devops-overview-expanded.png":::

Notice in the previous diagram how connections between environments and to external integrations expand the threat landscape. These connections can increase opportunities for bad actors to compromise the system.

Bad actors stretch across enterprises to compromise DevOps environments, gain access, and unlock new dangers. Attacks go beyond the typical breadth of cybersecurity breaches to inject malicious code, assume powerful developer identities, and steal production code.

As companies transition to ubiquitous, work-from-anywhere scenarios, they must strengthen device security. Cybersecurity offices might lack consistent understanding of where and how developers secure and build code. Bad actors take advantage of these weaknesses with remote connection hacks and developer identity thefts.

DevOps tools are key entry points for bad actors, from pipeline automation to code validation and code repositories. If bad actors infect code before it reaches production systems, in most cases, it can pass through cybersecurity checkpoints. To prevent compromise, ensure that your development teams are engaged with peer reviews, security checks with IDE security plugins, secure coding standards, and branch review.

Cybersecurity teams aim to prevent bad actors from sieging production environments. However, environments now include supply chain tools and products. Open source tool breach can heighten global cybersecurity risks.

Learn more about developer-specific articles with the following **DevSecOps** articles in the [Developer guidance](overview.md) section of the [Zero Trust Guidance Center](../index.yml):

- [Secure the DevOps platform environment](secure-devops-platform-environment-zero-trust.md) helps you to implement Zero Trust principles in your DevOps platform environment and highlights best practices for secret and certificate management.
- [Secure the developer environment](secure-dev-environment-zero-trust.md) helps you to implement Zero Trust principles in your development environments with best practices for least privilege, branch security, and trusting tools, extensions, and integrations.
- [Embed Zero Trust security into your developer workflow](embed-zero-trust-dev-workflow.md) helps you to innovate quickly and securely.

## Next steps

- [Accelerate and secure your code with Azure DevOps](/events/resources/build-2022/accelerate-secure-devops) with tools that give developers the fastest and most secure code to cloud experience.
- Sign up for [Azure Developer CLI](/azure/developer/azure-developer-cli/overview), an open-source tool that accelerates the time it takes to get started on Azure.
- Configure Azure to trust GitHub's OIDC as a federated identity. OpenID Connect (OIDC) allows your GitHub Actions workflows to [access resources in Azure](https://docs.github.com/actions/deployment/security-hardening-your-deployments/configuring-openid-connect-in-azure)without needing to store the Azure credentials as long-lived GitHub secrets.
- The [DevOps resource center](/devops/what-is-devops) helps you with DevOps practices, Agile methods, Git version control, DevOps at Microsoft, and how to assess your organization's DevOps progress.
- Learn how the [Microsoft DevSecOps solution](https://azure.microsoft.com/solutions/devsecops/#overview) integrates security into every aspect of the software delivery lifecycle to enable DevSecOps, or secure DevOps, for apps on the cloud (and anywhere) with Azure and GitHub.
