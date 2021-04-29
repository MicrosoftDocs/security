---
title: Identity and Access Management in Azure | Microsoft Docs
description: Manage access based on identity authentication and authorization 
author: MarkSimos
ms.author: josephd
ms.date: 04/20/2021
ms.topic: article
ms.prod: m365-security
---

# Identity and access management

In cloud-based architecture, identity provides the basis of a large percentage of security assurances. While legacy IT infrastructure often heavily relied on firewalls and network security solutions at the internet egress points for protection against outside threats, these controls are less effective in cloud architectures with shared services being accessed across cloud provider networks or the internet.

It is challenging or impossible to write concise firewall rules when you don’t control the networks where these services are hosted, different cloud resources spin up and down dynamically, cloud customers may share common infrastructure, and employees and users expect to be able to access data and services from anywhere. To enable all these capabilities, you must manage access based on identity authentication and authorization controls in the cloud services to protect data and resources and to decide which requests should be permitted.

Additionally, using a cloud-based identity solution like Azure Active Directory (Azure AD) offers additional security features that legacy identity services cannot because they can apply threat intelligence from their visibility into a large volume of access requests and threats across many customers.

## A single enterprise directory

**Best practice:** Establish a single enterprise directory for managing identities of full-time employees and enterprise resources.

A single authoritative source for identities increases clarity and consistency for all roles in IT and Security. This reduces security risk from human errors and automation failures resulting from complexity. By having a single authoritative source, teams that need to make changes to the directory can do so in one place and have confidence that their change will take effect everywhere.

For Azure, designate a single Azure AD tenant as the authoritative source for your organization's accounts.

For more information, see [What is hybrid identity?](https://docs.microsoft.com/azure/active-directory/hybrid/whatis-hybrid-identity).
 

## Synchronized identity systems

**Best practice:** Synchronize your cloud identity with your existing identity systems.

Consistency of identities across cloud and on-premises will reduce human errors and resulting security risk. Teams managing resources in both environments need a consistent authoritative source to achieve security assurances.

For Azure, synchronize Azure AD with your existing authoritative on premises Active Directory Domain Services (AD DS) using [What is hybrid identity?](https://docs.microsoft.com/azure/active-directory/hybrid/whatis-hybrid-identity).

This is also required for an Office 365 migration, so it is often already done before Azure migration and development projects begin. 

Note that administrator accounts should be excepted from synchronization as described in [Don’t synchronize on-premises admin accounts to cloud identity providers](/azure/architecture/security/identity#dont-synchronize-on-premises-admin-accounts-to-cloud-identity-providers) and 
[Critical impact account dependencies](/azure/architecture/security/critical-impact-accounts#critical-impact-admin-dependencies--accountworkstation).

## Cloud provider identity source for third parties

**Best practice:** Use cloud identity services to host non-employee accounts such as vendors, partners, and customers, rather than rather than including them in your on-premises directory.

This reduces risk by granting the appropriate level of access to external entities instead of the full default permissions given to full-time employees. This least privilege approach and clear clearly differentiation of external accounts from company staff makes it easier to prevent and detect attacks coming in from these vectors. Additionally, management of these identities is done by the external also increases productivity by parties, reducing effort required by company HR and IT teams.

For example, these capabilities natively integrate into the same Azure AD identity and permission model used by Azure and Office 365:

- [Azure AD](https://docs.microsoft.com/azure/active-directory/) for employees and enterprise resources.
- [Azure AD B2B](https://docs.microsoft.com/azure/active-directory/b2b/) for business partners.
- [Azure AD B2C](https://docs.microsoft.com/azure/active-directory-b2c/) customers or citizens.

For more information, see the [Azure AD federation compatibility list](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-compatibility).

## Passwordless or multi-factor authentication for administrative accounts

**Best practice:** All users should be converted to use passwordless authentication or multi-factor authentication (MFA) over time. 

The details of this recommendation are in the administration section [Passwordless Or multi-factor authentication for admins](/azure/architecture/security/critical-impact-accounts#passwordless-or-multi-factor-authentication-for-admins) 

The same recommendation applies to all users but should be applied first and strongest to accounts with administrative privileges.

You can also reduce use of passwords by applications using [Managed Identities](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview) to grant access to resources in Azure.

## Block legacy authentication

**Best practice:** Disable insecure legacy protocols for internet-facing services.

Legacy authentication methods are among the top attack vectors for cloud-hosted services. Created before multifactor-authentication existed, legacy protocols don’t support additional factors beyond passwords and are therefore prime targets for password spraying, dictionary, or brute force attacks. As an example, nearly 100% of all password spray attacks against Office 365 customers use legacy protocols. Additionally, these older protocols frequently lack other attack countermeasures, such as account lockouts or back-off timers. Services running on Microsoft’s cloud that block legacy protocols have observed a 66% reduction in successful account compromises.

For Azure and other Azure AD-based accounts, configure [Conditional Access to block legacy protocols](https://docs.microsoft.com/azure/active-directory/conditional-access/block-legacy-authentication).

Disabling legacy authentication can be difficult, as some users may not want to move to new client software that supports modern authentication methods. However, moving away from legacy authentication can be done gradually. Start by using metrics and logging from your authentication provider to determine the how many users still authenticate with old clients. Next, disable any down-level protocols that aren’t in use, and set up Conditional Access for all users who aren’t using legacy protocols. Finally, give plenty of notice and guidance to users on how to upgrade before blocking legacy authentication for all users on all services at a protocol level.

## No on-premises admin accounts in cloud identity providers

**Best practice:** Don’t synchronize accounts with the highest privilege access to on-premises resources as you synchronize your enterprise identity systems with cloud directories.

This mitigates the risk of an adversary pivoting to full control of on-premises assets following a successful compromise of a cloud account. This helps contain the scope of an incident from growing significantly.

For Azure, don’t synchronize accounts to Azure AD that have high privileges in your existing AD DS. This is blocked by default in the default Azure AD Connect configuration, so you only need to confirm you haven’t customized this configuration.

This is related to the [critical impact account dependencies](/azure/architecture/security/critical-impact-accounts#critical-impact-admin-dependencies--accountworkstation) guidance in the administration section that mitigates the inverse risk of pivoting from on-premises to cloud assets.

## Modern password protection

**Best practice:** Provide modern and effective protections for accounts that cannot go passwordless ([Passwordless Or multi-factor authentication for admins](/azure/architecture/security/critical-impact-accounts#passwordless-or-multi-factor-authentication-for-admins)).

Legacy identity providers mostly checked to make sure passwords had a good mix of character types and minimum length, but we have learned that these controls in practice led to passwords with less entropy that could be cracked easier:

- **Microsoft** - <https://www.microsoft.com/research/publication/password-guidance/>

- **NIST** - https://pages.nist.gov/800-63-3/sp800-63b.html

Identity solutions today need to be able to respond to types of attacks that didn't even exist one or two decades ago such as password sprays, breach replays (also called *“credential stuffing*”) that test username/password pairs from other sites’ breaches, and phishing man-in-the-middle attacks. Cloud identity providers are uniquely positioned to offer protection against these attacks. Since they handle such large volumes of sign-ons, they can apply better anomaly detection and use a variety of data sources to both proactively notify companies if their users’ passwords have been found in other breaches, as well as validate that any given sign in appears legitimate and is not coming from an unexpected or known-malicious host.

Additionally, synchronizing passwords to the cloud to support these checks also add resiliency during some attacks. Customers affected by (Not)Petya attacks were able to continue business operations when password hashes were synchronized to Azure AD (vs. near zero communications and IT services for customers affected organizations that had not synchronized passwords).

For Azure, enable modern protections in Azure AD with these steps:

1.  [Configure Azure AD Connect to synchronize password hashes](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

2.  Choose whether to automatically remediate these issues or manually remediate
    them based on a report:

    a.  **Automatic Enforcement -** Automatically remediate high risk passwords with Conditional Access [leveraging Azure AD Identity Protection risk assessments](https://docs.microsoft.com/azure/active-directory/identity-protection/overview)

    b.  **Report & Manually Remediate -** View reports and manually remediate
        accounts

       -   **Azure AD reporting** - Risk events are part of Azure AD's security reports. For more information, see the [users at risk security report](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-user-at-risk) and the [risky sign-ins security report](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-risky-sign-ins).

       -   **Azure AD Identity Protection** - Risk events are also part of the reporting capabilities of [Azure Active Directory Identity Protection](https://docs.microsoft.com/azure/active-directory/active-directory-identityprotection).

Use the [Identity Protection risk events API](https://docs.microsoft.com/graph/api/resources/identityprotection-root) to gain programmatic access to security detections using Microsoft Graph.

## Cross-platform credential management

**Best practice:** Use a single identity provider for authenticating all platforms (Windows, Linux, and others) and cloud services.

A single identity provider for all enterprise assets will simplify management and security, minimizing the risk of oversights or human mistakes. Deploying multiple identity solutions (or an incomplete solution) can result in unenforceable password policies, passwords not reset after a breach, proliferation of passwords (often stored insecurely), and former employees retaining passwords after termination.

For example, Azure AD can be used to authenticate:

- Windows
- [Linux](https://docs.microsoft.com/azure/virtual-machines/linux/login-using-aad)
- Azure
- Office 365
- [Amazon Web Services (AWS)](https://docs.microsoft.com/azure/active-directory/saas-apps/amazon-web-service-tutorial)
- [Google Services](https://docs.microsoft.com/azure/active-directory/saas-apps/google-apps-tutorial)
- Remote access to [legacy on-premises applications](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy)
- Third-party [SaaS providers](https://docs.microsoft.com/azure/active-directory/saas-apps/tutorial-list)

## Conditional Access for users with Zero Trust

**Best practice:** Authentication for all users should include measurement and enforcement of key security attributes to support a Zero Trust strategy. 

The details of this recommendation are in the administration section [Enforce conditional access for ADMINS (Zero Trust)](/azure/architecture/security/critical-impact-accounts#enforce-conditional-access-for-admins---zero-trust). The same recommendation applies to all users, but should be applied first to accounts with administrative privileges.

You can also reduce use of passwords by applications using [Managed Identities](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview) to grant access to resources in Azure.

## Simulate attacks

**Best practice:** Regularly simulate attacks against your users to educate and empower them.

People are a critical part of your defense, so ensure they have the knowledge and skills to avoid and resist attacks will reduce your overall organizational
risk.

You can use [Attack Simulator in Microsoft Defender for Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/attack-simulator) or any number of third-party offerings.

## Next step

Review identity and device access [capabilities](identity-capabilities.md).

## See also

For additional security guidance from Microsoft, see [Microsoft security documentation](https://docs.microsoft.com/security/).
