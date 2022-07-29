---
title: Step 1. Explicitly validate trust for all access requests
description: Explicitly validate trust for all access requests 
ms.service: security
ms.author: josephd
author: JoeDavies-MSFT
manager: dansimp
ms.topic: conceptual
---

# Checklist — Explicitly validate trust for all access requests

This Rapid Modernization Plan (RaMP) checklist helps you establish a security perimeter for cloud applications and mobile devices that uses identity as the control plane and explicitly validates trust for user accounts and devices before allowing access, for both public and private networks.

To be productive, your employees (users) must be able to use:

- Their account credentials to verify their identity.
- Their endpoint (device), such as a PC, tablet, or phone.
- The applications you have provided them to do their jobs.
- A network over which traffic flows between devices and applications, whether they are on premises or in the cloud.

Each one of these elements are the targets of attackers and must be protected with the "never trust, always verify" central principle of Zero Trust.

This checklist includes using Zero Trust to explicitly validate trust for all access requests for:

- [Identities](#identities)
- [Endpoints (devices)](#endpoints)
- [Apps](#apps)
- [Network](#network)

After completing this work, you will have built out this part of the Zero Trust architecture.

:::image type="content" source="./media/user-access-productivity-overview/user-access-productivity-validate-trust-users-devices-apps-network.png" alt-text="The identities, endpoints, apps, and network sections of the Zero Trust architecture" lightbox="./media/user-access-productivity-overview/user-access-productivity-validate-trust-users-devices-apps-network.png":::

## Identities

Verify and secure each identity with strong authentication across your entire digital estate with Azure Active Directory (Azure AD), a complete identity and access management solution with integrated security that connects 425 million people to their apps, devices, and data each month.

### Program and project member accountabilities

This table describes the overall protection of your user accounts in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Owner | Accountability |
|:-------|:-------|:-----|
|  CISO, CIO, or Director of Identity Security | | Executive sponsorship |
| Program lead from Identity Security or Identity Architect | | Drive results and cross-team collaboration |
| | Security Architect  | Advise on configuration and standards |
| | Identity Security or an Identity Architect | Implement configuration changes |
| | Identity Admin | Update standards and policy documents |
| | Security Governance or Identity Admin | Monitor to ensure compliance |
| | User Education Team | Ensure guidance for users reflects policy updates |


### Deployment objectives

Meet these deployment objectives to protect your privileged identities with Zero Trust.

| Done | Deployment objective | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. Deploy secured privileged access to protect administrative user accounts.  | IT implementer | [Securing privileged access for hybrid and cloud deployments in Azure AD](/azure/active-directory/roles/security-planning) |
| <input type="checkbox" /> | 2. Deploy Azure AD Privileged Identity Management (PIM) for a time-bound, just-in-time approval process for the use of privileged user accounts. | IT implementer | [Plan a Privileged Identity Management deployment](/azure/active-directory/authentication/howto-mfa-getstarted) |

Meet these deployment objectives to protect your user identities with Zero Trust.

| Done | Deployment objective | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. Enable self-service password reset (SSPR), which gives you credential reset capabilities | IT implementer | [Plan an Azure AD self-service password reset deployment](/azure/active-directory/authentication/howto-sspr-deployment) |
| <input type="checkbox" /> | 2. Enable Multi-Factor Authentication (MFA) and select appropriate methods for MFA | IT implementer | [Plan an Azure AD Multi-Factor Authentication deployment](/azure/active-directory/authentication/howto-mfa-getstarted) |
| <input type="checkbox" /> | 3. Enable combined User Registration for your directory to allow users to register for SSPR and MFA in one step | IT implementer | [Enable combined security information registration in Azure AD](/azure/active-directory/authentication/howto-registration-mfa-sspr-combined) |
| <input type="checkbox" /> | 4. Configure a Conditional Access policy to require MFA registration. | IT implementer | [How To: Configure the Azure AD Multi-Factor Authentication registration policy](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy) |
| <input type="checkbox" /> | 5. Enable user and sign-in risk-based policies to protect user access to resources. | IT implementer | [How To: Configure and enable risk policies](/azure/active-directory/identity-protection/howto-identity-protection-configure-risk-policies) |
| <input type="checkbox" /> | 6. Detect and block known weak passwords and their variants and block additional weak terms specific to your organization. | IT implementer | [Eliminate bad passwords using Azure AD Password Protection](/azure/active-directory/authentication/concept-password-ban-bad) |
| <input type="checkbox" /> | 7. Deploy Microsoft Defender for Identity and review and mitigate any open alerts (in parallel with your security operations).| Security operations team  | [Microsoft Defender for Identity](/defender-for-identity/what-is#whats-next)  |
| <input type="checkbox" /> | 8. Deploy passwordless credentials. | IT implementer | [Plan a passwordless authentication deployment in Azure AD](/azure/active-directory/authentication/howto-authentication-passwordless-deployment) |

You have now built out the **Identities** section of the Zero Trust architecture.

:::image type="content" source="./media/user-access-productivity-overview/user-access-productivity-validate-trust-identities.png" alt-text="The Identities section of the Zero Trust architecture" lightbox="./media/user-access-productivity-overview/user-access-productivity-validate-trust-identities.png":::

## Endpoints

Ensure compliance and health status before granting access to your endpoints (devices) and gain visibility into how they are accessing the network. 

### Program and project member accountabilities

This table describes the overall protection of your endpoints in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Owner | Accountability |
|:-------|:-------|:-----|
| CISO, CIO, or Director of Identity Security | | Executive sponsorship |
| Program lead from Identity Security or an Identity Architect | | Drive results and cross-team collaboration |
| | Security Architect  | Advise on configuration and standards |
| | Identity Security or an Infrastructure Security Architect | Implement configuration changes |
| | Mobile device management (MDM) Admin | Update standards and policy documents |
| | Security Governance or MDM Admin | Monitor to ensure compliance |
| | User Education Team | Ensure guidance for users reflects policy updates |

### Deployment objectives

Meet these deployment objectives to protect your endpoints (devices) with Zero Trust.

| Done | Deployment objective | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | 1. Register devices with Azure AD. | MDM Admin | [Device identities](/azure/active-directory/devices/overview) |
| <input type="checkbox" /> | 2. Enroll devices and create configuration profiles. | MDM Admin | [Device management overview](/mem/intune/fundamentals/what-is-device-management) |
| <input type="checkbox" /> | 3. Connect Defender for Endpoint to Intune (in parallel with your security operations). | Identity Security Admin | [Configure Microsoft Defender for Endpoint in Intune](/mem/intune/protect/advanced-threat-protection-configure) |
| <input type="checkbox" /> | 4. Monitor device compliance and risk for Conditional Access. | Identity Security Admin | [Use compliance policies to set rules for devices you manage with Intune](/mem/intune/protect/device-compliance-get-started) |
| <input type="checkbox" /> | 5. Implement Microsoft Information Protection and integrate with Conditional Access policies. | Identity Security Admin | [Use sensitivity labels to protect content](/microsoft-365/compliance/sensitivity-labels-teams-groups-sites) |

You have now built out the **Endpoints** section of the Zero Trust architecture.

:::image type="content" source="./media/user-access-productivity-overview/user-access-productivity-validate-trust-endpoints.png" alt-text="The Endpoints section of the Zero Trust architecture" lightbox="./media/user-access-productivity-overview/user-access-productivity-validate-trust-endpoints.png":::

## Apps

Because apps are used by malicious users to infiltrate your organization, you need to ensure that your apps are using services, such as Azure AD and Intune, that provide Zero Trust protection or are hardened against attack.

### Program and project member accountabilities

This table describes a Zero Trust implementation for apps in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Owner | Accountability |
|:-------|:-------|:-----|
|  CISO, CIO, or Director of Application Security | | Executive sponsorship |
| Program lead from Apps Management| | Drive results and cross-team collaboration |
| | Identity Architect  | Advise on Azure AD configuration for apps <br> Update authentication standards for on-premises apps |
| | Developer Architect  | Advise on configuration and standards for in-house on-premises and cloud apps |
| | Network Architect | Implement VPN configuration changes |
| | Cloud Network Architect | Deploy Azure AD Application Proxy |
| | Security Governance | Monitor to ensure compliance |

### Deployment objectives

Meet these deployment objectives to ensure Zero Trust protection for your SaaS, PaaS, and on-premises apps.

| Done | Type of app or app usage | Deployment objectives | Owner | Documentation |
|:-------|:-------|:-----|:-----|:-----|
| <input type="checkbox" /> | SaaS and PaaS apps that are part of your Microsoft cloud subscriptions | Use Azure AD app registration and certification and app consent policies. <br>  Use Azure AD Conditional Access policies and Intune MAM and Application Protection Policies (APP) policies to allow app usage. | Identity Architect | [Application management in Azure AD](/azure/active-directory/manage-apps/what-is-application-management)  |
| <input type="checkbox" /> | Apps in your Microsoft cloud subscriptions that are OAuth-enabled and access Microsoft 365 data through the Graph APIs | Use the app governance add-on to Defender for Cloud Apps for app behavior visibility, governance with policy enforcement, and detection and remediation of app-based attacks. | Security Engineer | [Overview](/defender-cloud-apps/app-governance-manage-app-governance) |
| <input type="checkbox" /> | SaaS and PaaS apps that are **NOT** part of your Microsoft cloud subscriptions | Ensure that they are using Azure AD for authentication. This means that all sign-ins to the app are subject to user and device security requirements such as multifactor authentication and meeting defined requirements for device compliance. | Apps Architect | [Integrating all your apps with Azure AD](/azure/active-directory/fundamentals/five-steps-to-full-application-integration-with-azure-ad) |
| <input type="checkbox" /> | On-premises users accessing on-premises applications, which includes applications running on both on-premises and IaaS-based servers | Ensure that your apps support modern authentication protocols such as OAuth/OIDC and SAML. Contact your application vendor for updates to protect user sign-in. | Identity Architect | See your vendor documentation |
| <input type="checkbox" /> | Remote users accessing on-premises applications through a VPN connection | Configure your VPN appliance so that it uses Azure AD as its identity provider | Network Architect | See your vendor documentation |
| <input type="checkbox" /> | Remote users accessing on-premises **web** applications through a VPN connection | Publish the applications through Azure AD Application Proxy. Remote users only need to access the individual published application, which is routed to the on-premises web server through an application proxy connector. <br><br> Connections take advantage of strong Azure AD authentication and limits users and their devices to accessing a single application at a time. In contrast, the scope of a typical remote access VPN is all locations, protocols, and ports of the entire on-premises network. | Cloud Network Architect | [Remote access to on-premises applications through Azure AD Application Proxy](/azure/active-directory/app-proxy/application-proxy) |


After completing these deployment objectives, you will have built out the **Apps** section of the Zero Trust architecture.

:::image type="content" source="./media/user-access-productivity-overview/user-access-productivity-validate-trust-apps.png" alt-text="The Apps section of the Zero Trust architecture" lightbox="./media/user-access-productivity-overview/user-access-productivity-validate-trust-apps.png":::


## Network

The Zero Trust model assumes breach and verifies each request as though it originated from an uncontrolled network. Although this is a common practice for public networks, it also applies to your organization’s internal networks which are generally firewalled from the public Internet.

To adhere to Zero Trust, your organization must address security vulnerabilities on both public and private networks, whether on-premises or in the cloud, and ensure that you verify explicitly, use least privilege access, and assume breach. Devices, users, and apps are not to be inherently trusted because they are on your private networks.

### Program and project member accountabilities

This table describes a Zero Trust implementation for public and private networks in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Owner | Accountability |
|:-------|:-------|:-----|
|  CISO, CIO, or Director of Network Security | | Executive sponsorship |
| Program lead from Networking Leadership| | Drive results and cross-team collaboration |
| | Security Architect  | Advise on encryption and access policy configuration and standards |
| | Network Architect  | Advise on traffic filtering and network architecture changes |
| | Network Engineers | Design segmentation configuration changes |
| | Network Implementers | Change networking equipment configuration and update configuration documents |
| | Networking Governance | Monitor to ensure compliance |

### Deployment objectives

Meet these deployment objectives to ensure Zero Trust protection for your public and private networks, for both on-premises and cloud-based traffic. These objectives can be done in parallel.

| Done | Deployment objective | Owner | Documentation |
|:-------|:-------|:-----|:-----|
| <input type="checkbox" /> | Require encryption for all traffic connections, including between IaaS components and between on-premises users and apps. | Security Architect | [Azure IaaS components](/azure/vpn-gateway/vpn-gateway-ipsecikepolicy-rm-powershell) <br><br> [IPsec for on-premises Windows devices](/windows/security/threat-protection/windows-firewall/securing-end-to-end-ipsec-connections-by-using-ikev2) |
| <input type="checkbox" /> | Limit access to critical data and applications by policy (user or device identity) or traffic filtering. | Security Architect or Network Architect| [Access policies for Cloud App Security Conditional Access App Control](/cloud-app-security/proxy-intro-aad) <br><br> [Windows Firewall for Windows devices](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security) |
| <input type="checkbox" /> | Deploy on-premises network segmentation with ingress and egress traffic controls with micro-perimeters and micro-segmentation. | Network Architect or Network Engineer | See your on-premises network and edge devices documentation. |
| <input type="checkbox" /> | Use real-time threat detection for on-premises traffic. | SecOps Analysts | [Windows threat protection](/windows/security/threat-protection/) <br><br> [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint) |
| <input type="checkbox" /> | Deploy cloud network segmentation with ingress and egress traffic controls with micro-perimeters and micro-segmentation. | Network Architect or Network Engineer | [Implement network segmentation patterns on Azure](/azure/architecture/framework/security/design-network-segmentation) |
| <input type="checkbox" /> | Use real-time threat detection for cloud traffic. | Network Architect or Network Engineer | [Azure Firewall threat intelligence-based filtering](/azure/firewall/threat-intel) <br><br> [Azure Firewall Premium network intrusion detection and prevention system (IDPS)](/azure/firewall/premium-features#idps) |


After completing these deployment objectives, you will have built out the **Network** section of the Zero Trust architecture.

:::image type="content" source="./media/user-access-productivity-overview/user-access-productivity-validate-trust-network.png" alt-text="The Network section of the Zero Trust architecture" lightbox="./media/user-access-productivity-overview/user-access-productivity-validate-trust-network.png":::

## Next step

Continue the user access and productivity initiative with [Data, Compliance, and Governance](data-compliance-governance-overview.md).

