---
title: Step 1. Explicitly validate trust for all access requests
description: Explicitly validate trust for all access requests 
ms.service: security
ms.author: josephd
author: JoeDavies-MSFT
manager: dansimp
ms.topic: conceptual
---

# Step 1. Explicitly validate trust for all access requests

Your first step is to establish an identity security perimeter for cloud applications and mobile devices that uses identity as the control plane and explicitly validates trust for user accounts and devices before allowing access.

This includes using Zero Trust to explicitly validate trust for all access requests for:

- [User Accounts](#user-accounts)

  Require Passwordless or multi-factor authentication (MFA) for all users and measure risk with threat intelligence and behavior analytics.

- [Devices](#devices)

  Require device integrity and health compliance for access.

- [Apps](#apps)

  Enable Azure Active Directory (Azure AD) for all SaaS apps and VPN authentication and publish legacy on-premises and IaaS-based Web services with Azure AD Application Proxy.

- [Network](#network)

  Apply additional traffic filtering and segmentation to private networks to protect business critical data and applications.


After completing this step, you will have built out this part of the Zero Trust architecture.

![The identities and devices sections of the Zero Trust architecture](./media/user-access-productivity-overview/user-access-productivity-validate-trust-users-and-devices.png)

## User accounts

Verify and secure each identity with strong authentication across your entire digital estate with Azure Active Directory (Azure AD), a complete identity and access management solution with integrated security that connects 425 Million people to their apps, devices, and data each month.

### Program and project member accountabilities

This table describes the overall protection of your user accounts in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Owner | Accountability |
|:-------|:-------|:-----|
|  CISO, CIO, or Director of Identity Security | | Executive sponsorship |
| Program lead from Identity Security and/or an Identity Architect | | Drive results and cross-team collaboration |
| | Security Architect  | Advise on configuration and standards |
| | Identity Security and/or an Identity Architect | Implement configuration changes |
| | Identity Admin | Update standards and policy documents |
| | Security Governance and/or Identity Admin | Monitor to ensure compliance |
| | User Education | Ensure guidance for users reflects policy updates |


### Deployment objectives

Meet these deployment objectives to protect your accounts with Zero Trust.

| Done | Deployment objective | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. Self-service password reset (SSPR) has been enabled, which gives you credential reset capabilities | IT implementer | [Plan an Azure Active Directory self-service password reset deployment](https://docs.microsoft.com/azure/active-directory/authentication/howto-sspr-deployment) |
| <input type="checkbox" /> | 2. Multi-Factor Authentication (MFA) has been enabled and appropriate methods for MFA have been selected | IT implementer | [Plan an Azure Active Directory Multi-Factor Authentication deployment](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted) |
| <input type="checkbox" /> | 3. Combined User Registration has been enabled for your directory, allows users to register for SSPR and MFA in one step | IT implementer | [Enable combined security information registration in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/authentication/howto-registration-mfa-sspr-combined) |
| <input type="checkbox" /> | 4. Configure a Conditional Access policy to require MFA registration. | IT implementer | [How To: Configure the Azure AD Multi-Factor Authentication registration policy](https://docs.microsoft.com/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy) |
| <input type="checkbox" /> | 5. Enable user and sign-in risk-based policies to protect user access to resources. | IT implementer | [How To: Configure and enable risk policies](https://docs.microsoft.com/azure/active-directory/identity-protection/howto-identity-protection-configure-risk-policies) |
| <input type="checkbox" /> | 6. Detect and block known weak passwords and their variants, and block additional weak terms specific to your organization. | IT implementer | [Eliminate bad passwords using Azure Active Directory Password Protection](https://docs.microsoft.com/azure/active-directory/authentication/concept-password-ban-bad) |
| <input type="checkbox" /> | 7. Microsoft Defender for Identity | IT implementer | Deploy and enable [Microsoft Defender for Identity](https://docs.microsoft.com/defender-for-identity/what-is#whats-next). Review and mitigate any open alerts. |
| <input type="checkbox" /> | 8. Passwordless credential deployment | IT implementer | [Plan a passwordless authentication deployment in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-deployment) |

You have now built out the **identities** section of the Zero Trust architecture.

![The identities section of the Zero Trust architecture](./media/user-access-productivity-overview/user-access-productivity-validate-trust-users.png)

## Devices

Ensure compliance and health status before granting access to your devices (endpoints) and gain visibility into how they are accessing the network. 

### Program and project member accountabilities

This table describes the overall protection of your devices in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Owner | Accountability |
|:-------|:-------|:-----|
| CISO, CIO, or Director of Identity Security | | Executive sponsorship |
| Program lead from Identity Security and/or an Identity Architect | | Drive results and cross-team collaboration |
| | Security Architect  | Advise on configuration and standards |
| | Identity Security and/or an Infrastructure Security | Implement configuration changes |
| | MDM Admin | Update standards and policy documents |
| | Security Governance and/or MDM Admin | Monitor to ensure compliance |
| | User Education | Ensure guidance for users reflects policy updates |


### Deployment objectives

Meet these deployment objectives to protect your devices with Zero Trust.

| Done | Deployment objective | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. Register devices with Azure AD |  | [Device identities](https://docs.microsoft.com//azure/active-directory/devices/overview) |
| <input type="checkbox" /> | 2. Enroll devices into management and configure configuration profiles |  | [Device management overview](https://docs.microsoft.com/mem/intune/fundamentals/what-is-device-management) |
| <input type="checkbox" /> | 3. Connect Defender for Endpoint to Intune |  | [Configure Microsoft Defender for Endpoint in Intune](https://docs.microsoft.com/mem/intune/protect/advanced-threat-protection-configure) |
| <input type="checkbox" /> | 4. Monitor device compliance/risk as a signal for Conditional Access |  | [Use compliance policies to set rules for devices you manage with Intune](https://docs.microsoft.com/mem/intune/protect/device-compliance-get-started) |
| <input type="checkbox" /> | 5. Implement Microsoft Information Protection and integrate with Conditional Access polciies |  | link |

You have now built out the **devices** section of the Zero Trust architecture.

![The devices section of the Zero Trust architecture](./media/user-access-productivity-overview/user-access-productivity-validate-trust-devices.png)


## Apps

From Mark's Ignite deck:

SaaS apps:

Ensure all your SaaS apps are using Azure AD for authentication.

Improve access security across your estate by using the Azure AD authentication security you configured in step 1, starting with your SaaS applications.

On-premises applications

Update and modernize authentication security for applications that don’t directly support modern protocols like OAuth/OIDC and SAML by modernizing and then going beyond VPN authentication in a two-step process

Improve VPN Security - By connecting your VPN appliance to Azure AD authentication, VPN sessions benefit from the added security of explicit validation of user account/session and device trustworthiness. 
Publish Applications – Move applications off of VPN by publishing existing on-premises (and IaaS) applications through Azure AD App proxy, enabling you to take advantages of strong Azure AD authentication from step 1, improve user experience, and limit accounts to accessing a single application at a time (instead of a VPN that typically provides access to all ports/protocols of the whole network).


### Program and project member accountabilities

This table describes a Zero Trust implementation for apps in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Owner | Accountability |
|:-------|:-------|:-----|
|  CISO, CIO, or Director of Identity Security | | Executive sponsorship |
| Program lead from SecOps Leadership| | Drive results and cross-team collaboration |
| | Security Architect  | Advise on configuration and standards |
| | SecOps Analysts | Implement configuration changes |
| | SecOps Analysts | Update standards and policy documents |
| | Security Governance | Monitor to ensure compliance |

### Deployment objectives

From App protection section of cloud security model for SaaS and PaaS apps:

Acquisition

1. 	Verify registration and certificate.
2. 	Register app in tenant.
3. 	Restrict user consent operations with an app consent policy.

Deployment

1. Azure AD Conditional Access policies: Add app to the list of allowed apps.
2. Intune: Add app to MAM and APP policies.
3. Try the app for 30 days in a test tenant.
4. Sign-off for the app in your production tenant.
5. First 60 days in production tenant. 

Run state

1. Monitor Azure AD identity Protection alerts for compromised credentials.
2. Update Conditional Access and Intune policies as needed.

Meet these deployment objectives to ensure Zero Trust protection for your SaaS and PaaS apps that use Azure AD.

| Done | Deployment objective | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1.  | |  |
| <input type="checkbox" /> | 2.  | |  |
| <input type="checkbox" /> | 3.  | |  |
| <input type="checkbox" /> | 4.  | |  |
| <input type="checkbox" /> | 5.  | |  |
| <input type="checkbox" /> | 6.  | |  |
| <input type="checkbox" /> | 7.  | |  |
| <input type="checkbox" /> | 8.  | |  |

Update and modernize authentication security for applications that don’t directly support modern protocols like OAuth/OIDC and SAML by modernizing and then going beyond VPN authentication in a two-step process

Improve VPN Security - By connecting your VPN appliance to Azure AD authentication, VPN sessions benefit from the added security of explicit validation of user account/session and device trustworthiness. 
Publish Applications – Move applications off of VPN by publishing existing on-premises (and IaaS) applications through Azure AD App proxy, enabling you to take advantages of strong Azure AD authentication from step 1, improve user experience, and limit accounts to accessing a single application at a time (instead of a VPN that typically provides access to all ports/protocols of the whole network).

Meet these deployment objectives to ensure Zero Trust protection for your on-premises apps.

| Done | Deployment objective | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1.  | |  |
| <input type="checkbox" /> | 2.  | |  |
| <input type="checkbox" /> | 3.  | |  |
| <input type="checkbox" /> | 4.  | |  |
| <input type="checkbox" /> | 5.  | |  |
| <input type="checkbox" /> | 6.  | |  |
| <input type="checkbox" /> | 7.  | |  |
| <input type="checkbox" /> | 8.  | |  |


After completing these deployment objectives, you will have built out the **apps** section of the Zero Trust architecture.

![The apps section of the Zero Trust architecture](./media/user-access-productivity-overview/user-access-productivity-validate-trust-apps.png)


## Network

From Mark's Ignite deck:

Ensure devices and users are not trusted just because they are on an internal network. Encrypt all internal communications, limit access by policy, and employ microsegmentation and real-time threat detection.

Enable good user experience over both public and private network. Apply additional traffic filtering and segmentation to private networks to protect business critical data and applications. 

Establish basic traffic filtering and segmentation to isolate business-critical or highly vulnerable resources

Microsegmentation – this group of users can access from these devices. Networking: physical, virtual; what traffic is allowed to flow. / Additional identity and network restrictions (dynamic trust-based and/or static rules)

### Program and project member accountabilities

This table describes a Zero Trust implementation for public and on-premises networks in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Owner | Accountability |
|:-------|:-------|:-----|
|  CISO, CIO, or Director of Identity Security | | Executive sponsorship |
| Program lead from SecOps Leadership| | Drive results and cross-team collaboration |
| | Security Architect  | Advise on configuration and standards |
| | SecOps Analysts | Implement configuration changes |
| | SecOps Analysts | Update standards and policy documents |
| | Security Governance | Monitor to ensure compliance |

### Deployment objectives

Meet these deployment objectives to ensure Zero Trust protection for your on-premises network and cloud-based traffic.

| Done | Deployment objective | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1.  | |  |
| <input type="checkbox" /> | 2.  | |  |
| <input type="checkbox" /> | 3.  | |  |
| <input type="checkbox" /> | 4.  | |  |
| <input type="checkbox" /> | 5.  | |  |
| <input type="checkbox" /> | 6.  | |  |
| <input type="checkbox" /> | 7.  | |  |
| <input type="checkbox" /> | 8.  | |  |

From the Zero Trust stack diagram:

SaaS and PaaS
Deploy cloud native filtering and protection for known threats

IaaS with Azure AD DS
Deploy cloud network segmentation with fully distributed ingress/egress cloud micro-perimeters and deeper micro-segmentation
Use Azure DDoS Protection Standard for ML-based threat protection and filtering with context-based signals

Across SaaS/PaaS/IaaS
Deploy on-premises network segmentation with many ingress/egress cloud micro-perimeters and some micro-segmentation
Require encryption for all traffic connections, between IaaS components, and between on-premises users and apps (including over ExpressRoute, if used)

After completing these deployment objectives, you will have built out the **network** section of the Zero Trust architecture.

## Next step

Continue the user access and productivity initiative with [Data, Compliance, and Governance](data-compliance-governance-overview.md).

