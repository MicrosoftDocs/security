---
title: Rapidly modernize your security infrastructure
description: Key initiatives to rapidly secure your environment

ms.service: security
ms.subservice: 
ms.topic: how-to
ms.date: 12/15/2020

ms.author: joflore
author: MicrosoftGuyJFlo
manager: daveba
ms.reviewer: mas
---
# Security rapid modernization plan

This rapid modernization plan (RAMP) will help you quickly adopt Microsoft's recommended [privileged access strategy](privileged-access-strategy.md).

This roadmap builds on the technical controls established in the [privileged access deployment](howto-azure-managed-workstation.md) guidance. Complete those steps and then use the steps in this RAMP to configure the controls for your organization.  

![Privileged access RAMP summary](./media/security-rapid-modernization-plan/privileged-access-ramp-summary.png)

> [!NOTE]
> Many of these steps will have a green/brownfield dynamic as organizations often have security risks in the way they are already deployed or configured accounts. 
> This roadmap prioritizes stopping the accumulation of new security risks first, and then later cleans up the remaining items that have already accumulated.

As you progress through the roadmap, you can utilize Microsoft Secure Score to track and compare many items in the journey with others in similar organizations over time. Learn more about Microsoft Secure Score in the article [Secure score overview](https://docs.microsoft.com/security/mtp/microsoft-secure-score).

Each item in this RAMP is structured as an initiative that will be tracked and managed using a format that builds on the objectives and key results (OKR) methodology. Each item includes what (objective), why, who, how, and how to measure (key results). Some items require changes to processes and people's knoweldge/skills, while others are simpler technology changes. Many of these initiatives will include members outside of the traditional IT Department that should be included in the decision making and implementation of these changes to ensure they are successfully integrated in your organization. 

It is critical to work together as an organization, create partnerships, and educate people who traditionally were not part of this process. It is critical to create and maintain buy-in across the organization, without it many projects fail.

## Separate and manage privileged accounts

### Emergency access accounts

- **What**: Ensure that you are not accidentally locked out of your Azure Active Directory (Azure AD) organization in an emergency situation. 
- **Why**: Emergency access accounts rarely used and highly damaging to the organization if compromised, but their availability to the organization is also critically important for the few scenarios when they are required. Ensure you have a plan for continuity of access that accommodates both expected and unexpected events. 
- **Who**: This initiative is typically led by [Identity and Key Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) and/or [Security Architecture](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-architecture).
   - **Sponsorship:** This initiative is typically sponsored by CISO, CIO, or Director of Identity
   - **Execution:** This initiative is a collaborative effort involving
     - [Policy and standards](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-policy-standards) team document clear requirements and standards
     - [Identity and Key Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) or [Central IT Operations](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/central-it) to implement any changes
     - [Security Compliance management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-compliance-management) monitors to ensure compliance
- **How**: Follow the guidance in [Manage emergency access accounts in Azure AD](https://docs.microsoft.com/azure/active-directory/roles/security-emergency-access).
- **Measure key results:**
   - **Established** Emergency access process has been designed based on Microsoft guidance that meets organizational needs
   - **Maintained** Emergency access has been reviewed and tested within the past 90 days

### Enable Azure AD Privileged Identity Management

- **What**: Use Azure AD Privileged Identity Management (PIM) in your Azure AD production environment to discover and secure privileged accounts
- **Why**: Privileged Identity Management provides time-based and approval-based role activation to mitigate the risks of excessive, unnecessary, or misused access permissions.
- **Who**: This initiative is typically led by [Identity and Key Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) and/or [Security Architecture](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-architecture).
   - **Sponsorship:** This initiative is typically sponsored by CISO, CIO, or Director of Identity
   - **Execution:** This initiative is a collaborative effort involving
     - [Policy and standards](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-policy-standards) team document clear requirements and standards (based on this guidance)
     - [Identity and Key Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) or [Central IT Operations](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/central-it) to implement any changes
     - [Security Compliance management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-compliance-management) monitors to ensure compliance
- **How**: Deploy and Configure Azure AD Privileged Identity Management using the guidance in the article, [Deploy Azure AD Privileged Identity Management (PIM)](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-deployment-plan).
- **Measure key results**: 100% of applicable privileged access roles are using Azure AD PIM

### Identify and categorize privileged accounts (Azure AD)

- **What**: Identify all roles and groups with high business impact that will require privileged security level (immediately or over time). Additional specialized roles will be identified in later stages. 
- **Why**: This step is required to identify and minimize the number of people that require separate accounts and privileged access protection
- **Who**: This initiative is typically led by [Identity and Key Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) and/or [Security Architecture](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-architecture).
   - **Sponsorship:** This initiative is typically sponsored by CISO, CIO, or Director of Identity
   - **Execution:** This initiative is a collaborative effort involving
     - [Policy and standards](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-policy-standards) team document clear requirements and standards (based on this guidance)
     - [Identity and Key Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) or [Central IT Operations](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/central-it) to implement any changes
     - [Security Compliance management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-compliance-management) monitors to ensure compliance
- **How**: After turning on Azure AD Privileged Identity Management, view the users who are in the following Azure AD roles:
  - Global administrator
  - Privileged role administrator
  - Exchange administrator
  - SharePoint administrator
  
  For a complete list of administrator roles, see [Administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/roles/permissions-reference).

   > Remove any accounts that are no longer needed in those roles. Then, categorize the remaining accounts that are assigned to admin roles:
   >
   > - Assigned to administrative users, but also used for non-administrative productivity purposes, like reading and responding to email.
   > - Assigned to administrative users and used for administrative purposes only
   > - Shared across multiple users
   > - For break-glass emergency access scenarios
   > - For automated scripts
   > - For external users

If you don't have Azure AD Privileged Identity Management in your organization, you can use the PowerShell API. Also start with the Global Administrator role, because a Global Administrator has the same permissions across all cloud services for which your organization has subscribed. These permissions are granted no matter where they were assigned: in the Microsoft 365 admin center, the Azure portal, or by the Azure AD module for Microsoft PowerShell.
- **Measure key results:** Review and Identification of privileged access roles has been completed within the past 90 days

### Separate accounts (On-premises AD accounts)

- **What**: Secure on-premises privileged administrative accounts, if not already done. This stage includes:
   - Creating separate admin accounts for users who need to conduct on-premises administrative tasks
   - Deploying Privileged Access Workstations for Active Directory administrators
   - Creating unique local admin passwords for workstations and servers

- **Why**: Hardening the accounts used for administrative tasks. The administrator accounts should have mail disabled and no personal Microsoft accounts should be allowed.

- **Who**: This initiative is typically led by [Identity and Key Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) and/or [Security Architecture](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-architecture).
   - **Sponsorship:** This initiative is typically sponsored by CISO, CIO, or Director of Identity
   - **Execution:** This initiative is a collaborative effort involving
     - [Policy and standards](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-policy-standards) team document clear requirements and standards (based on this guidance)
     - [Identity and Key Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) or [Central IT Operations](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/central-it) to implement any changes
     - [Security Compliance management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-compliance-management) monitors to ensure compliance

- **How**: All personnel that are authorized to possess administrative privileges must have separate accounts for administrative functions that are distinct from user accounts. **Do not share these accounts between users.**
   - *Standard user accounts* - Granted standard user privileges for standard user tasks, such as email, web browsing, and using line-of-business applications. These accounts are not granted administrative privileges.
   - *Administrative accounts* - Separate accounts created for personnel who are assigned the appropriate administrative privileges. 
- **Measure key results:** 100% of on-premises privileged users have separate dedicated accounts

### Microsoft Defender for Identity

- **What**: Microsoft Defender for Identity combines on-premises signals with cloud insights to monitor, protect, and investigate events in a simplified format enabling your security teams to detect advanced attacks against your identity infrastructure with the ability to:
    - Monitor users, entity behavior, and activities with learning-based analytics
    - Protect user identities and credentials stored in Active Directory
    - Identify and investigate suspicious user activities and advanced attacks throughout the kill chain
    - Provide clear incident information on a simple timeline for fast triage 

- **Why**: Modern attackers may stay undetected for long periods of time. Many threats are hard to find without a cohesive picture of your entire identity environment.

- **Who**: This initiative is typically led by [Identity and Key Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) and/or [Security Architecture](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-architecture).
   - **Sponsorship:** This initiative is typically sponsored by CISO, CIO, or Director of Identity
   - **Execution:** This initiative is a collaborative effort involving
     - [Policy and standards](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-policy-standards) team document clear requirements and standards (based on this guidance)
     - [Identity and Key Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) or [Central IT Operations](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/central-it) to implement any changes
     - [Security Compliance management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-compliance-management) monitors to ensure compliance

- **How**: Deploy and enable [Microsoft Defender for Identity](https://docs.microsoft.com/defender-for-identity/what-is#whats-next) and review any open alerts.
- **Measure key results**: All open alerts reviewed and mitigated by the appropriate teams.

## Improve credential management experience

### Implement and document self-service password reset and combined security information registration

- **What**: Enable and configure self-service password reset (SSPR) in your organization and enable the combined security information registration experience.
- **Why**: Users are able to reset their own passwords once they have registered. The combined security information registration experience provides a better user experience allowing registration for Azure AD Multi-Factor Authentication and self-service password reset. These tools when used together contribute to lower helpdesk costs and more satisfied users.
- **Who**: This initiative is typically led by [Identity and Key Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) and/or [Security Architecture](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-architecture).
   - **Sponsorship:** This initiative is typically sponsored by CISO, CIO, or Director of Identity
   - **Execution:** This initiative is a collaborative effort involving
     - [Policy and standards](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-policy-standards) team document clear requirements and standards (based on this guidance)
     - [Identity and Key Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) or [Central IT Operations](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/central-it) to implement any changes
     - [Security Compliance management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-compliance-management) monitors to ensure compliance
     - [Central IT Operations](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/central-it) Helpdesk processes have been updated and personnel has been trained on them
- **How**: To enable and deploy SSPR, see the article [Plan an Azure Active Directory self-service password reset deployment](https://docs.microsoft.com/azure/active-directory/authentication/howto-sspr-deployment).
- **Measure key results**: Self-service password reset is fully configured and available to the organization

### Protect admin accounts - Enable and require MFA / Passwordless for Azure AD privileged users

- **What**: Require all privileged accounts in Azure AD to use strong multi-factor authentication
- **Why**: To protect access to data and services in Microsoft 365.
- **Who**: This initiative is typically led by [Identity and Key Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) and/or [Security Architecture](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-architecture).
   - **Sponsorship:** This initiative is typically sponsored by CISO, CIO, or Director of Identity
   - **Execution:** This initiative is a collaborative effort involving
     - [Policy and standards](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-policy-standards) team document clear requirements and standards (based on this guidance)
     - [Identity and Key Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) or [Central IT Operations](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/central-it) to implement any changes
     - [Security Compliance management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-compliance-management) monitors to ensure compliance
     - [Central IT Operations](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/central-it) Helpdesk processes have been updated and personnel has been trained on them
     - [Central IT Operations](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/central-it) Service owner processes have been updated and personnel has been trained on them
- **How**: Turn on Azure AD Multi-Factor Authentication (MFA) and register all other highly privileged single-user non-federated admin accounts. Require multi-factor authentication at sign-in for all individual users who are permanently assigned to one or more of the Azure AD admin roles like:

   - Global administrator
   - Privileged Role administrator
   - Exchange administrator
   - SharePoint administrator

   Require administrators to use passwordless sign-in methods such as FIDO2 security keys or Windows Hello for Business in conjunction with unique, long, complex passwords. Enforce this change with an organizational policy document.

Follow the guidance in the following articles, [Plan an Azure AD Multi-Factor Authentication deployment](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted) and 
[Plan a passwordless authentication deployment in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-deployment).
- **Measure key results**: 100% of privileged users are using passwordless authentication or a strong form of multi-factor authentication for all logons. See [Privileged Access Accounts](privileged-access-accounts.md) for description of multi-factor authentication

### Block legacy authentication protocols for privileged user accounts

- **What**: Block legacy authentication protocol use for privileged user accounts.

- **Why**: Organizations should block these legacy authentication protocols because multi-factor authentication cannot be enforced against them. Leaving legacy authentication protocols enabled can create an entry point for attackers. Some legacy applications may rely on these protocols and organizations have the option to create specific exceptions for certain accounts. These exceptions should be tracked and additional monitoring controls implemented.

- **Who**: This initiative is typically led by [Identity and Key Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) and/or [Security Architecture](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-architecture).
   - **Sponsorship:** This initiative is typically sponsored by CISO, CIO, or Director of Identity
   - **Execution:** This initiative is a collaborative effort involving
     - [Policy and standards](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-policy-standards): establish clear requirements
     - [Identity and Key Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) or Central IT Operations [Central IT Operations](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/central-it) to implement the policy
     - [Security Compliance management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-compliance-management) monitors to ensure compliance
- **How**: To block legacy authentication protocols in your organization, follow the guidance in the article [How to: Block legacy authentication to Azure AD with Conditional Access](https://docs.microsoft.com/azure/active-directory/conditional-access/block-legacy-authentication).
- **Measure key results**: 
   - **Legacy protocols blocked:** All legacy protocols are blocked for all users, with only authorized exceptions
   - **Exceptions** are reviewed every 90 days and expire permanently within one year. Application owners must fix all exceptions within one year of first exception approval 

### Application consent process

- **What**: Disable end-user consent to Azure AD applications. 
> [!NOTE]
> This change will require centralizing the decision-making process with your organization's security and identity administration teams.
- **Why**: Users can inadvertently create organizational risk by providing consent for an app that can maliciously access organizational data. 
- **Who**: This initiative is typically led by [Identity and Key Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) and/or [Security Architecture](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-architecture).
   - **Sponsorship:** This initiative is typically sponsored by CISO, CIO, or Director of Identity
   - **Execution:** This initiative is a collaborative effort involving
     - [Policy and standards](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-policy-standards) team document clear requirements and standards (based on this guidance)
     - [Identity and Key Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) or [Central IT Operations](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/central-it) to implement any changes
     - [Security Compliance management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-compliance-management) monitors to ensure compliance
     - [Central IT Operations](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/central-it) Helpdesk processes have been updated and personnel has been trained on them
     - [Central IT Operations](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/central-it) Service owner processes have been updated and personnel has been trained on them
- **How**: Establish a centralized consent process to maintain centralized visibility and control of the applications that have access to data by following the guidance in the article, [Managing consent to applications and evaluating consent requests](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-consent-requests).
- **Measure key results**: End users are not able to consent to Azure AD application access

### Clean up account and sign-in risks

- **What**: Enable Azure AD Identity Protection and cleanup any risks that it finds.
- **Why**: Risky user and sign-in behavior can be a source of attacks against your organization.
- **Who**: This initiative is typically led by [Identity and Key Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) and/or [Security Architecture](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-architecture).
   - **Sponsorship:** This initiative is typically sponsored by CISO, CIO, or Director of Identity
   - **Execution:** This initiative is a collaborative effort involving
     - [Policy and standards](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-policy-standards) team document clear requirements and standards (based on this guidance)
     - [Identity and Key Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) or [Central IT Operations](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/central-it) to implement any changes
     - [Security Compliance management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-compliance-management) monitors to ensure compliance
     - [Central IT Operations](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/central-it) Helpdesk processes have been updated for related support calls and personnel has been trained on them
- **How**: Create a process that monitors and manages user and sign-in risk. Decide if you will automate remediation, using Azure AD Multi-Factor Authentication and SSPR, or block and require administrator intervention.Follow the guidance in the article [How To: Configure and enable risk policies](https://docs.microsoft.com/azure/active-directory/identity-protection/howto-identity-protection-configure-risk-policies).
- **Measure key results**: The organization has zero unaddressed user and sign-in risks. 
> [!NOTE]
> Conditional Access policies are required to block accrual of new sign-in risks. See the Conditional access section of [Privileged Access Deployment](howto-azure-managed-workstation.md#azure-active-directory-configuration)

## Admin workstations initial deployment

- **What**: Privileged accounts such as Global Administrators  have dedicated workstations to perform administrative tasks from.
- **Why**: Devices where privileged administration tasks are completed are a target of attackers. Securing not only the account but these assets are critical in reducing your attack surface area. This separation limits their exposure to common attacks directed at productivity-related tasks like email and web browsing.
- **Who**: This initiative is typically led by [Identity and Key Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) and/or [Security Architecture](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-architecture).
   - **Sponsorship:** This initiative is typically sponsored by CISO, CIO, or Director of Identity
   - **Execution:** This initiative is a collaborative effort involving
     - [Policy and standards](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-policy-standards) team document clear requirements and standards (based on this guidance)
     - [Identity and Key Management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) or [Central IT Operations](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/central-it) to implement any changes
     - [Security Compliance management](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/cloud-security-compliance-management) monitors to ensure compliance
     - [Central IT Operations](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/central-it) Helpdesk processes have been updated and personnel has been trained on them
     - [Central IT Operations](https://docs.microsoft.com/azure/cloud-adoption-framework/organize/central-it) Service owner processes have been updated and personnel has been trained on them
- **How**: Initial deployment should be to the Enterprise level as described in the article [Privileged Access Deployment](howto-azure-managed-workstation.md)
- **Measure key results**: Every privileged account has a dedicated workstation to perform sensitive tasks from.
> [!NOTE]
> This step rapidly establishes a security baseline and must be increased to specialized and privileged levels as soon as possible.  

## Next steps

- [Securing privileged access overview](overview.md)
- [Privileged access strategy](privileged-access-strategy.md)
- [Measuring success](privileged-access-success-criteria.md)
- [Security levels](privileged-access-security-levels.md)
- [Privileged access accounts](privileged-access-accounts.md)
- [Intermediaries](privileged-access-intermediaries.md)
- [Interfaces](privileged-access-interfaces.md)
- [Privileged access devices](concept-azure-managed-workstation.md)
- [Enterprise access model](privileged-access-access-model.md)
