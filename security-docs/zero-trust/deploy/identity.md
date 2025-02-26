---
title: Identity, the first pillar of a Zero Trust security architecture
description: Identities, representing people, services, or devices, are the common denominator across today’s many networks, endpoints, and applications. In the Zero Trust security model, they function as a powerful, flexible, and granular way to control access to data. 
ms.service: security

ms.topic: conceptual
ms.date: 08/01/2024

ms.author: joflore
author: MicrosoftGuyJFlo
manager: amycolannino
ms.collection:
  - zerotrust-pillar
---
# Securing identity with Zero Trust

:::image type="icon" source="../media/icon-identity-medium.png":::

Before most organizations start a Zero Trust journey, their approach to identity might be fragmented with various identity providers, a lack of single sign-on (SSO) between cloud and on-premises apps, and limited [visibility](/security/zero-trust/deploy/visibility-automation-orchestration) into identity risk.

Cloud applications and mobile workers require a new way of thinking when it comes to security. Many employees bring their own devices and work in a hybrid manner. Data is regularly accessed outside the traditional corporate network perimeter and shared with external collaborators like partners and vendors. Traditional corporate applications and data are moving from on-premises to hybrid and cloud environments. 

Traditional network controls for security aren't enough anymore.

Identities represent the people, services, or devices, across [networks](/security/zero-trust/deploy/networks), [endpoints](/security/zero-trust/deploy/endpoints), and [applications](/security/zero-trust/deploy/applications). In the Zero Trust security model, they function as a powerful, flexible, and granular means to control access to resources.

**Before an identity attempts to access a resource, organizations must:**

- Verify the identity with strong authentication.
- Ensure access is compliant and typical for that identity.
- Follow least privilege access principles.

Once the identity is verified, we can control access to resources based on organization policies, ongoing risk analysis, and other tools.

## Identity Zero Trust deployment objectives

When implementing an end-to-end Zero Trust framework for identity, we recommend you focus first on these initial deployment objectives:

- [Cloud identity federates with on-premises identity systems](#i-cloud-identity-federates-with-on-premises-identity-systems).
- [Conditional Access policies gate access and provide remediation activities](#ii-conditional-access-policies-gate-access-and-provide-remediation-activities).
- [Analytics improve visibility](#iii-analytics-improve-visibility).

After the previous areas are addressed, focus on these deployment objectives:

- [Identities and access privileges are managed with identity governance](#iv-identities-and-access-privileges-are-managed-with-identity-governance).
- [User, device, location, and behavior is analyzed in real time](#v-user-device-location-and-behavior-are-analyzed-in-real-time-to-determine-risk-and-deliver-ongoing-protection).
- [Integrate threat signals from other security solutions](#vi-integrate-threat-signals-from-other-security-solutions-to-improve-detection-protection-and-response).

### I. Cloud identity federates with on-premises identity systems

Microsoft Entra ID enables strong authentication, a point of integration for endpoint security, and the core of your user-centric policies to guarantee least-privileged access. Microsoft Entra Conditional Access is the policy engine used to make decisions for access to resources based on user identity, environment, device health, and risk verified explicitly at the time of access. You can implement a Zero Trust identity strategy with Microsoft Entra ID.

:::image type="content" source="../media/diagram-steps-box-identity-1.png" alt-text="Diagram of the steps within phase 1 of the initial deployment objectives." border="true":::

#### Connect all of your users to Microsoft Entra ID and federate with on-premises identity systems

Maintaining a healthy pipeline of your employees' identities and the necessary security artifacts including groups for authorization and endpoints for access policy controls puts you in the best place to use consistent identities and controls in the cloud. 

Follow these steps:

1. [Choose an authentication option](/entra/identity/hybrid/connect/choose-ad-authn). Microsoft Entra ID provides you the best brute force, DDoS, and password spray protection, but make the decision that's right for your organization and your compliance needs.
1. Only bring the identities you absolutely need. Use going to the cloud as an opportunity to leave behind service accounts that only make sense on-premises. Leave on-premises privileged roles on-premises.
1. Ensure you meet the [hardware requirements for Microsoft Entra Connect Sync](/entra/identity/hybrid/connect/how-to-connect-install-prerequisites#hardware-requirements-for-microsoft-entra-connect) based on your organization's size.

#### Establish your Identity Foundation with Microsoft Entra ID

A Zero Trust strategy requires verifying explicitly, using least-privileged access principles, and assuming breach. Microsoft Entra ID can act as the policy decision point to enforce your access policies based on insights on the user, endpoint, target resource, and environment.

Put Microsoft Entra ID in the path of every access request. This process connects every user, app, and resource through a common identity control plane and provides Microsoft Entra ID with the signals to make the best possible decisions about the authentication/authorization risk. In addition, single sign-on (SSO) and consistent policy guardrails provide a better user experience and contribute to productivity gains.

#### Integrate all your applications with Microsoft Entra ID

Single sign-on prevents users from leaving copies of their credentials in various apps and helps avoid phishing attacks or MFA fatigue due to excessive prompting.

Make sure you don't have multiple identity and access management (IAM) solutions in your environment. This duplication diminishes signals that Microsoft Entra ID sees, allows bad actors to live in the shadows between the two IAM engines, and leads to poor user experience. This complexity might lead to your business partners becoming doubters of your Zero Trust strategy.

Follow these steps:

1. [Integrate modern enterprise applications](/entra/identity/enterprise-apps/plan-sso-deployment) that speak OAuth2.0 or SAML.
1. For Kerberos and form-based auth applications, [integrate them using the Microsoft Entra application proxy](/entra/identity/app-proxy/conceptual-deployment-plan).
1. If you publish your legacy applications using application delivery networks/controllers, use Microsoft Entra ID to [integrate](/entra/identity/enterprise-apps/secure-hybrid-access) with most of the major ones (such as Citrix, Akamai, and F5).
1. To help discover and migrate your apps off of ADFS and existing/older IAM engines, review [Resources for migrating applications to Microsoft Entra ID](/entra/identity/enterprise-apps/migration-resources).
1. [Automate user provisioning](/entra/identity/app-provisioning/plan-auto-user-provisioning).

> [!TIP]
> [Learn more about implementing an end-to-end Zero Trust strategy for applications](/security/zero-trust/deploy/applications).

#### Verify explicitly with strong authentication

Follow these steps:

1. [Roll out Microsoft Entra multifactor authentication](/entra/identity/authentication/howto-mfa-getstarted). This effort is a foundational piece of reducing user session risk. As users appear on new devices and from new locations, being able to respond to an MFA challenge is one of the most direct ways that your users can teach us that these are familiar devices/locations as they move around the world (without having administrators parse individual signals).
1. [Block legacy authentication](/entra/identity/conditional-access/block-legacy-authentication). One of the most common attack vectors for malicious actors is to use stolen/replayed credentials against legacy protocols, such as SMTP, that can't do modern security challenges.

### II. Conditional Access policies gate access and provide remediation activities

Microsoft Entra Conditional Access analyzes signals such as user, device, and location to automate decisions and enforce organizational access policies for resource. You can use Conditional Access policies to apply access controls like multifactor authentication (MFA). Conditional Access policies allow you to prompt users for MFA when needed for security and stay out of users' way when not needed.

:::image type="content" source="../media/diagram-conditional-access-policies.png" alt-text="Diagram of Conditional Access policies in Zero Trust." border="false":::

Microsoft provides standard conditional policies called [security defaults](/entra/fundamentals/security-defaults) that ensure a basic level of security. However, your organization might need more flexibility than security defaults offer. You can use Conditional Access to customize security defaults with more granularity and to configure new policies that meet your requirements.

Planning your Conditional Access policies in advance and having a set of active and fallback policies is a foundational pillar of your Access Policy enforcement in a Zero Trust deployment. Take the time to [configure known network locations](/entra/identity/conditional-access/concept-assignment-network#how-are-these-locations-defined) in your environment. Even if you don't use these network locations in a Conditional Access policy, configuring these IPs informs the risk of Microsoft Entra ID Protection.

Take this step:

- Check out our [deployment guidance](/entra/identity/conditional-access/plan-conditional-access) and [best practices](/entra/architecture/resilience-overview) for resilient Conditional Access policies.

#### Register devices with Microsoft Entra ID to restrict access from vulnerable and compromised devices

Follow these steps:

1. [Enable Microsoft Entra hybrid join](/entra/identity/devices/concept-hybrid-join) or [Microsoft Entra join](/entra/identity/devices/concept-directory-join). If you're managing the user's laptop/computer, bring that information into Microsoft Entra ID and use it to help make better decisions. For example, allowing rich clients, that have offline copies on the computer, access to data if you know the user is coming from a machine that your organization controls and manages.
1. Enable the [Intune](/mem/intune/remote-actions/device-management) service within Microsoft Endpoint Manager (EMS) for managing your users' mobile devices and [enroll devices](/mem/intune/fundamentals/deployment-guide-enrollment). The same can be said about user mobile devices as about laptops: The more you know about them (patch level, jailbroken, rooted, etc.), the more you can provide a rationale for why you block/allow access.

> [!TIP]
> [Learn about implementing an end-to-end Zero Trust strategy for endpoints](/security/zero-trust/deploy/endpoints).

### III. Analytics improve visibility

As you build your estate in Microsoft Entra ID with authentication, authorization, and provisioning, it's important to have strong operational insights into what is happening in the directory.

#### Configure logging and reporting to improve visibility

Take this step:

- [Plan a Microsoft Entra reporting and monitoring deployment](/entra/identity/monitoring-health/plan-monitoring-and-reporting) to be able to persist and analyze logs from Microsoft Entra ID, either in Azure or using a SIEM system of choice.

### IV. Identities and access privileges are managed with identity governance

Once you accomplish your initial objectives, focus on other objectives such as more robust identity governance.

:::image type="content" source="../media/diagram-steps-box-identity-4.png" alt-text="Diagram of the steps within phase 4 of the additional deployment objectives." border="true":::

#### Secure privileged access with Privileged Identity Management

Control the endpoints, conditions, and credentials that users use to access privileged operations/roles.

Follow these steps:

1. [Take control of your privileged identities](/entra/identity/role-based-access-control/security-planning). Privileged access isn't only administrative access, but also application or developer access that can change the way your mission-critical apps run and handle data.
1. [Use Privileged Identity Management to secure privileged identities](/entra/id-governance/privileged-identity-management/pim-deployment-plan).

#### Restrict user consent to applications

User consent to applications is a common way for modern applications to get access to organizational resources, but there are some best practices to keep in mind.

Follow these steps:

1. [Restrict user consent and manage consent requests](/entra/identity/enterprise-apps/manage-consent-requests) to ensure that no unnecessary exposure occurs of your organization's data to apps.
1. [Review prior/existing consent in your organization](/defender-office-365/detect-and-remediate-illicit-consent-grants) for any excessive or malicious consent.

For more on tools to protect against tactics to access sensitive information, see "Strengthen protection against cyber threats and rogue apps" in our [guide to implementing an identity Zero Trust strategy](/security/zero-trust/deploy/applications#v-strengthen-protection-against-cyber-threats-and-rogue-apps).

#### Manage entitlement

With applications centrally authenticating and driven from Microsoft Entra ID, you can streamline your access request, approval, and recertification process to make sure that the right people have the right access and that you have a trail of why users in your organization have the access they have.

Follow these steps:

1. Use Entitlement Management to [create access packages](/entra/id-governance/entitlement-management-access-package-create) that users can request as they join different teams/projects and that assigns them access to the associated resources (such as applications, SharePoint sites, group memberships).
1. If deploying Entitlement Management isn't possible for your organization at this time, at least enable self-service paradigms in your organization by deploying [self-service group management](/entra/identity/users/groups-self-service-management) and [self-service application access](/entra/identity/enterprise-apps/manage-self-service-access).

#### Use passwordless authentication to reduce the risk of phishing and password attacks

With Microsoft Entra ID supporting FIDO 2.0 and passwordless phone sign-in, you can move the needle on the credentials that your users (especially sensitive/privileged users) are employing day-to-day. These credentials are strong authentication factors that can mitigate risk as well.

Take this step:

- [Start rolling out passwordless credentials](/entra/identity/authentication/howto-authentication-passwordless-deployment) in your organization.

### V. User, device, location, and behavior are analyzed in real time to determine risk and deliver ongoing protection

Real-time analysis is critical for determining risk and protection.

:::image type="content" source="../media/diagram-steps-box-identity-5.png" alt-text="Diagram of the steps within phase 5 of the additional deployment objectives." border="true":::

#### Deploy Microsoft Entra Password Protection

While enabling other methods to verify users explicitly, don't ignore weak passwords, password spray, and breach replay attacks. And [classic complex password policies don't prevent the most prevalent password attacks](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/your-pa-word-doesn-t-matter/ba-p/731984).

Take this step:

- Enable Microsoft Entra Password Protection for your users [in the cloud](/entra/identity/authentication/concept-password-ban-bad) and [on-premises](/entra/identity/authentication/howto-password-ban-bad-on-premises-deploy).

#### Enable Microsoft Entra ID Protection

Get more granular session/user risk signal with Microsoft Entra ID Protection. You can enable risk investigation and remediation options based on your organization's evolving security needs.

Take this step:

- [Enable Microsoft Entra ID Protection](/entra/id-protection/overview-identity-protection).

#### Enable Microsoft Defender for Cloud Apps integration with Microsoft Entra ID Protection

Microsoft Defender for Cloud Apps monitors user behavior inside SaaS and modern applications. This signal informs Microsoft Entra ID about what happened to the user after they authenticated and received a token. If the user pattern starts to look suspicious, then a signal can feed to Microsoft Entra ID Protection and Conditional Access notifying it that the user seems to be compromised or high risk. On the next access request from this user, Microsoft Entra ID can correctly take action to verify the user or block them.

Take this step:

- [Enable Defender for Cloud Apps monitoring](/defender-cloud-apps/azip-integration) to enrich the Microsoft Entra ID Protection signal.

#### Enable Conditional Access integration with Microsoft Defender for Cloud Apps

Using signals emitted after authentication and with Defender for Cloud Apps proxying requests to applications, you'll be able to monitor sessions going to SaaS applications and enforce restrictions.

Follow these steps:

1. [Enable Conditional Access integration](/defender-cloud-apps/proxy-intro-aad).

1. [Extend Conditional Access to on-premises apps](/entra/identity/app-proxy/application-proxy-integrate-with-microsoft-cloud-application-security).

#### Enable restricted session for use in access decisions

When a user's risk is low, but they're signing in from an unknown endpoint, you might want to allow access to resources, but not allow them to do things that expose your organization to risky actions. You can configure Exchange Online and SharePoint Online to offer the user a restricted session that allows them to read emails or view files, but not download them and save them on an untrusted device.

Take this step:

- Enable limited access to [SharePoint Online](/sharepoint/control-access-from-unmanaged-devices) and [Exchange Online](https://aka.ms/owalimitedaccess).

### VI. Integrate threat signals from other security solutions to improve detection, protection, and response

Finally, other security solutions can be integrated for greater effectiveness.

#### Integrate Microsoft Defender for Identity with Microsoft Defender for Cloud Apps

Integration with Microsoft Defender for Identity enables Microsoft Entra ID to know that a user is indulging in risky behavior while accessing on-premises, nonmodern resources (like file shares). This signal can be factored into overall risk, possibly blocking further access in the cloud.

Follow these steps:

1. [Enable Microsoft Defender for Identity](/defender-xdr/microsoft-365-security-center-mdi) with Microsoft Defender for Cloud Apps to bring on-premises signals into the risk signal we know about the user.
1. Check the [combined Investigation Priority score](https://techcommunity.microsoft.com/t5/enterprise-mobility-security/introducing-investigation-priority-built-on-user-and-entity/ba-p/360853) for each user at risk to give a holistic view of which ones your SOC should focus on.

#### Enable Microsoft Defender for Endpoint

Microsoft Defender for Endpoint allows you to attest to the health of Windows machines and determine whether they're undergoing a compromise. You can then feed that information into mitigating risk at runtime. Whereas Domain Join gives you a sense of control, Defender for Endpoint allows you to react to a malware attack at near real time by detecting patterns where multiple user devices are hitting untrustworthy sites, and to react by raising their device/user risk at runtime.

Take this step:

- [Configure Conditional Access in Microsoft Defender for Endpoint](/defender-endpoint/configure-conditional-access).

## Securing Identity in accordance with Executive Order 14028 on Cybersecurity & OMB Memorandum 22-09

Executive Order 14028 on Improving the Nations Cyber Security & OMB Memorandum 22-09 include specific actions on Zero Trust. Identity actions include employing centralized identity management systems, use of strong phishing-resistant MFA, and incorporating at least one device-level signal in authorization decisions. For detailed guidance on implementing these actions with Microsoft Entra ID, see [Meet identity requirements of memorandum 22-09 with Microsoft Entra ID](/entra/standards/memo-22-09-meet-identity-requirements).

## Products covered in this guide

- [Microsoft Entra ID](https://azure.microsoft.com/services/active-directory/)
- [Microsoft Defender for Identity](https://www.microsoft.com/security/business/threat-protection/endpoint-defender)
- [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager)
(includes Microsoft Intune)
- [Microsoft Defender for Endpoint](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp)
- [SharePoint Online](https://www.microsoft.com/microsoft-365/sharepoint/collaboration)
- [Exchange Online](https://www.microsoft.com/microsoft-365/exchange/email)

## Conclusion

Identity is central to a successful Zero Trust strategy. For further information or help with implementation, contact your Customer Success team or continue to read through the other chapters of this guide, which span all Zero Trust pillars.

<br/><br/>
<!-- Include the nav bar. -->
[!INCLUDE [navbar, bottom](../includes/navbar-bottom.md)]
