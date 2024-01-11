---
title: Securing identity with Zero Trust
description: Identities, representing people, services, or IoT devices, are the common dominator across today’s many networks, endpoints, and applications. In the Zero Trust security model, they function as a powerful, flexible, and granular way to control access to data. 
ms.date: 10/19/2023
ms.service: security
author: mjcaparas
ms.author: mjcapara
ms.topic: conceptual
ms.collection:
  - zerotrust-pillar
---

# Securing identity with Zero Trust

:::image type="icon" source="../media/icon-identity-medium.png":::

**Background** 

Cloud applications and the mobile workforce have redefined the security perimeter. Employees are bringing their own devices and working remotely. Data is being accessed outside the corporate network and shared with external collaborators such as partners and vendors. Corporate applications and data are moving from on-premises to hybrid and cloud environments. Organizations can no longer rely on traditional network controls for security. Controls need to move to where the data is: on devices, inside apps, and with partners.

Identities, representing people, services, or IoT devices, are the common dominator across today's many [networks](https://aka.ms/ZTNetwork), [endpoints](https://aka.ms/ZTDevices), and [applications](https://aka.ms/ZTApplications). In the Zero Trust security model, they function as a powerful, flexible, and granular way to control access to [data](https://aka.ms/ZTData).

**Before an identity attempts to access a resource, organizations must:**

-   Verify the identity with strong authentication.

-   Ensure access is compliant and typical for that identity.

-   Follows least privilege access principles.

Once the identity has been verified, we can control that identity's access to resources based on organization policies, on-going risk analysis, and other tools.

## Identity Zero Trust deployment objectives

<div class="alert">
   <p><b>Before</b> most organizations <b>start the Zero Trust journey</b>, their approach to identity is problematic in that the on-premises identity provider is in use, no SSO is present between cloud and on-premises apps, and <a href="https://aka.ms/ZTCrossPillars">visibility</a> into identity risk is very limited.</p>
</div>


<table border="0">
   <tr>
      <td colspan="2">
         <p>When implementing an end-to-end Zero Trust framework for identity, we recommend you focus first on these <b>initial deployment objectives</b>:</p>
	  </td>
   </tr>
   <tr>
      <td>
		 <p><img src="../media/icon-initial-deployment-small.png" alt="List icon with one checkmark."></p>
      </td>
      <td>
	     <p><b>I.</b> <a href="#i-cloud-identity-federates-with-on-premises-identity-systems">Cloud identity federates with on-premises identity systems.</a></p>
         <p><b>II.</b> <a href="#ii-conditional-access-policies-gate-access-and-provide-remediation-activities">Conditional Access policies gate access and provide remediation activities.</a></p>
	     <p><b>III.</b> <a href="#iii-analytics-improve-visibility">Analytics improve visibility.</a></p>
      </td>
   </tr>
   <tr>
      <td colspan="2">
         <p>After these are completed, focus on these <b>additional deployment objectives</b>:</p>
      </td>
   </tr>
   <tr>
      <td>
		 <p><img src="../media/icon-additional-deployment-small.png" alt="List icon with two checkmarks."></p>
      </td>
      <td>
         <p><b>IV.</b> <a href="#iv-identities-and-access-privileges-are-managed-with-identity-governance">Identities and access privileges are managed with identity governance.</a></p>
         <p><b>V.</b> <a href="#v-user-device-location-and-behavior-is-analyzed-in-real-time-to-determine-risk-and-deliver-ongoing-protection">User, device, location, and behavior is analyzed in real time to determine risk and deliver ongoing protection.</a></p>
         <p><b>VI.</b> <a href="#vi-integrate-threat-signals-from-other-security-solutions-to-improve-detection-protection-and-response">Integrate threat signals from other security solutions to improve detection, protection, and response.</a></p>
      </td>
   </tr>
</table>

## Identity Zero Trust deployment guide

This guide will walk you through the steps required to manage identities following the principles of a Zero Trust security framework.


<br/><br/>
<!-- H2 heading, "Initial deployment objectives" -->
[!INCLUDE [H2 heading, Initial deployment objectives](../includes/deployment-objectives-initial.md)]



### I. Cloud identity federates with on-premises identity systems

Microsoft Entra ID enables strong authentication, a point of integration for endpoint security, and the core of your user-centric policies to guarantee least-privileged access. Microsoft Entra Conditional Access capabilities are the policy decision point for access to resources based on user identity, environment, device health, and risk—verified explicitly at the point of access. We will show how you can implement a Zero Trust identity strategy with Microsoft Entra ID.

:::image type="content" source="../media/diagram-steps-box-identity-1.png" alt-text="Diagram of the steps within phase 1 of the initial deployment objectives." border="true":::


<a name='connect-all-of-your-users-to-azure-ad-and-federate-with-on-premises-identity-systems'></a>

#### Connect all of your users to Microsoft Entra ID and federate with on-premises identity systems

Maintaining a healthy pipeline of your employees' identities and the necessary security artifacts (groups for authorization and endpoints for extra access policy controls) puts you in the best place to use consistent identities and controls in the cloud. 

Follow these steps:

1.  [Choose an authentication option](https://aka.ms/auth-options). Microsoft Entra ID provides you the best brute force, DDoS, and password spray protection, but make the decision that's right for your organization and your compliance needs.

2.  Only bring the identities you absolutely need. For example, use going to the cloud as an opportunity to leave behind service accounts that only make sense on-premises. Leave on-premises privileged roles behind.

3.  If your enterprise has more than 100,000 users, groups, and devices combined [build a high performance sync box](https://aka.ms/aadconnectperf) that will keep your life cycle up to date.


<a name='establish-your-identity-foundation-with-azure-ad'></a>

#### Establish your Identity Foundation with Microsoft Entra ID

A Zero Trust strategy requires verifying explicitly, using least-privileged access principles, and assuming breach. Microsoft Entra ID can act as the policy decision point to enforce your access policies based on insights on the user, endpoint, target resource, and environment.

Take this step:

 - Put Microsoft Entra ID in the path of every access request. This connects every user and every app or resource through one identity control plane and provides Microsoft Entra ID with the signal to make the best possible decisions about the authentication/authorization risk. In addition, single sign-on and consistent policy guardrails provide a better user experience and contribute to productivity gains.

<a name='integrate-all-your-applications-with-azure-ad'></a>

#### Integrate all your applications with Microsoft Entra ID

Single sign-on prevents users from leaving copies of their credentials in various apps and helps avoid users get used to surrendering their credentials due to excessive prompting.

Also make sure you do not have multiple IAM engines in your environment. Not only does this diminish the amount of signal that Microsoft Entra ID sees, allowing bad actors to live in the seams between the two IAM engines, it can also lead to poor user experience and your business partners becoming the first doubters of your Zero Trust strategy.

Follow these steps:

1.  [Integrate modern enterprise applications](/azure/active-directory/manage-apps/plan-sso-deployment) that speak OAuth2.0 or SAML.

2.  For Kerberos and form-based auth applications, [integrate them using the Microsoft Entra application proxy](/azure/active-directory/manage-apps/application-proxy-deployment-plan).

3.  If you publish your legacy applications using application delivery networks/controllers, use Microsoft Entra ID to [integrate](/azure/active-directory/manage-apps/secure-hybrid-access) with most of the major ones (such as Citrix, Akamai, and F5).

4.  To help discover and migrate your apps off of ADFS and existing/older IAM engines, review [resources and tools](/azure/active-directory/manage-apps/migration-resources).

5.  [Power push identities into your various cloud applications](/azure/active-directory/app-provisioning/plan-auto-user-provisioning). This gives you a tighter identity lifecycle integration within those apps.

> [!TIP]
> [Learn about implementing an end-to-end Zero Trust strategy for applications](https://aka.ms/ZTApplications).


#### Verify explicitly with strong authentication

Follow these steps:

1.  [Roll out Microsoft Entra multifactor authentication (P1)](/azure/active-directory/authentication/howto-mfa-getstarted). This is a foundational piece of reducing user session risk. As users appear on new devices and from new locations, being able to respond to an MFA challenge is one of the most direct ways that your users can teach us that these are familiar devices/locations as they move around the world (without having administrators parse individual signals).

2.  [Block legacy authentication](/azure/active-directory/conditional-access/block-legacy-authentication). One of the most common attack vectors for malicious actors is to use stolen/replayed credentials against legacy protocols, such as SMTP, that cannot do modern security challenges.


### II. Conditional Access policies gate access and provide remediation activities

Microsoft Entra Conditional Access (CA) analyzes signals such as user, device, and location to automate decisions and enforce organizational access policies for resource. You can use CA policies to apply access controls like multifactor authentication (MFA). CA policies allow you to prompt users for MFA when needed for security and stay out of users' way when not needed.

:::image type="content" source="../media/diagram-conditional-access-policies.png" alt-text="Diagram of Conditional Access policies in Zero Trust." border="false":::

Microsoft provides standard conditional policies called [security defaults](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) that ensure a basic level of security. However, your organization may need more flexibility than security defaults offer. You can use Conditional Access to customize security defaults with more granularity and to configure new policies that meet your requirements.

Planning your Conditional Access policies in advance and having a set of active and fallback policies is a foundational pillar of your Access Policy enforcement in a Zero Trust deployment. Take the time to configure your trusted IP locations in your environment. Even if you do not use them in a Conditional Access policy, configuring these IPs informs the risk of Identity Protection mentioned above.

Take this step:

 - Check out our [deployment guidance](/azure/active-directory/conditional-access/plan-conditional-access) and [best practices](https://aka.ms/resilientaad) for resilient Conditional Access policies.

<a name='register-devices-with-azure-ad-to-restrict-access-from-vulnerable-and-compromised-devices'></a>

#### Register devices with Microsoft Entra ID to restrict access from vulnerable and compromised devices

Follow these steps:

1.  [Enable Microsoft Entra hybrid join](/azure/active-directory/devices/concept-azure-ad-join-hybrid) or [Microsoft Entra join](/azure/active-directory/devices/concept-azure-ad-join-hybrid). If you are managing the user's laptop/computer, bring that information into Microsoft Entra ID and use it to help make better decisions. For example, you may choose to allow rich client access to data (clients that have offline copies on the computer) if you know the user is coming from a machine that your organization controls and manages. If you do not bring this in, you will likely choose to block access from rich clients, which may result in your users working around your security or using shadow IT.

2.  Enable the [Intune](/mem/intune/remote-actions/device-management) service within Microsoft Endpoint Manager (EMS) for managing your users' mobile devices and [enroll devices](/mem/intune/enrollment/device-enrollment). The same can be said about user mobile devices as about laptops: The more you know about them (patch level, jailbroken, rooted, etc.), the more you are able to trust or mistrust them and provide a rationale for why you block/allow access.

> [!TIP]
> [Learn about implementing an end-to-end Zero Trust strategy for endpoints](https://aka.ms/ZTEndpoints)


### III. Analytics improve visibility

As you build your estate in Microsoft Entra ID with authentication, authorization, and provisioning, it's important to have strong operational insights into what is happening in the directory.


#### Configure your logging and reporting to improve visibility

Take this step:

 - [Plan a Microsoft Entra reporting and monitoring deployment](/azure/active-directory/reports-monitoring/plan-monitoring-and-reporting) to be able to persist and analyze logs from Microsoft Entra ID, either in Azure or using a SIEM system of choice.


<br/><br/>
<!-- H2 heading, "Additional deployment objectives" -->
[!INCLUDE [H2 heading, Additional deployment objectives](../includes/deployment-objectives-additional.md)]



### IV. Identities and access privileges are managed with identity governance

Once you've accomplished your initial three objectives, you can focus on additional objectives such as more robust identity governance.

:::image type="content" source="../media/diagram-steps-box-identity-4.png" alt-text="Diagram of the steps within phase 4 of the additional deployment objectives." border="true":::


#### Secure privileged access with Privileged Identity Management

Control the endpoints, conditions, and credentials that users use to access privileged operations/roles.

Follow these steps:

1.  [Take control of your privileged identities](/azure/active-directory/users-groups-roles/directory-admin-roles-secure). Keep in mind that in a digitally-transformed organization, privileged access is not only administrative access, but also application owner or developer access that can change the way your mission-critical apps run and handle data.

2.  [Use Privileged Identity Management to secure privileged identities](/azure/active-directory/privileged-identity-management/pim-deployment-plan).


#### Restrict user consent to applications

User consent to applications is a very common way for modern applications to get access to organizational resources, but there are some best practices to keep in mind.

Follow these steps:

1.  [Restrict user consent and manage consent requests](/azure/active-directory/manage-apps/manage-consent-requests) to ensure that no unnecessary exposure occurs of your organization's data to apps.

2.  [Review prior/existing consent in your organization](/microsoft-365/security/office-365-security/detect-and-remediate-illicit-consent-grants?view=o365-worldwide&preserve-view=true) for any excessive or malicious consent.

For more on tools to protect against tactics to access sensitive information, see "Strengthen protection against cyber threats and rogue apps" in our [guide to implementing an identity Zero Trust strategy](https://aka.ms/ZTIdentity).


#### Manage entitlement

With applications centrally authenticating and driven from Microsoft Entra ID, you can now streamline your access request, approval, and recertification process to make sure that the right people have the right access and that you have a trail of why users in your organization have the access they have.

Follow these steps:

1.  Use Entitlement Management to [create access packages](/azure/active-directory/governance/entitlement-management-access-package-create) that users can request as they join different teams/projects and that assigns them access to the associated resources (such as applications, SharePoint sites, group memberships).

2.  If deploying Entitlement Management is not possible for your organization at this time, at least enable self-service paradigms in your organization by deploying [self-service group management](/azure/active-directory/users-groups-roles/groups-self-service-management) and [self-service application access](/azure/active-directory/manage-apps/manage-self-service-access).

#### Use passwordless authentication to reduce the risk of phishing and password attacks

With Microsoft Entra ID supporting FIDO 2.0 and passwordless phone sign-in, you can move the needle on the credentials that your users (especially sensitive/privileged users) are employing day-to-day. These credentials are strong authentication factors that can mitigate risk as well.

Take this step:

 - [Start rolling out passwordless credentials](/azure/active-directory/authentication/howto-authentication-passwordless-deployment) in your organization.


### V. User, device, location, and behavior is analyzed in real time to determine risk and deliver ongoing protection

Real-time analysis is critical for determining risk and protection.

:::image type="content" source="../media/diagram-steps-box-identity-5.png" alt-text="Diagram of the steps within phase 5 of the additional deployment objectives." border="true":::

<a name='deploy-azure-ad-password-protection'></a>

#### Deploy Microsoft Entra Password Protection

While enabling other methods to verify users explicitly, don't ignore weak passwords, password spray, and breach replay attacks. And [classic complex password policies do not prevent the most prevalent password attacks](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/your-pa-word-doesn-t-matter/ba-p/731984).

Take this step:

 - Enable Microsoft Entra Password Protection for your users [in the cloud](/azure/active-directory/authentication/concept-password-ban-bad) and [on-premises](/azure/active-directory/authentication/howto-password-ban-bad-on-premises-deploy).

#### Enable Identity Protection

Get more granular session/user risk signal with Identity Protection. You'll be able to investigate risk and confirm compromise or dismiss the signal, which will help the engine better understand what risk looks like in your environment.

Take this step:

- [Enable Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection).

#### Enable Microsoft Defender for Cloud Apps integration with Identity Protection

Microsoft Defender for Cloud Apps monitors user behavior inside SaaS and modern applications. This informs Microsoft Entra ID about what happened to the user after they authenticated and received a token. If the user pattern starts to look suspicious (e.g., a user starts to download gigabytes of data from OneDrive or starts to send spam emails in Exchange Online), then a signal can be fed to Microsoft Entra ID notifying it that the user seems to be compromised or high risk. On the next access request from this user, Microsoft Entra ID can correctly take action to verify the user or block them.

Take this step:

- [Enable Defender for Cloud Apps monitoring](/cloud-app-security/azip-integration) to enrich the Identity Protection signal.

#### Enable Conditional Access integration with Microsoft Defender for Cloud Apps

Using signals emitted after authentication and with Defender for Cloud Apps proxying requests to applications, you will be able to monitor sessions going to SaaS applications and enforce restrictions.

Follow these steps:

1.  [Enable Conditional Access integration](/cloud-app-security/proxy-intro-aad).

2.  [Extend Conditional Access to on-premises apps](/azure/active-directory/manage-apps/application-proxy-integrate-with-microsoft-cloud-application-security).

#### Enable restricted session for use in access decisions

When a user's risk is low, but they are signing in from an unknown endpoint, you may want to allow them access to critical resources, but not allow them to do things that leave your organization in a noncompliant state. Now you can configure Exchange Online and SharePoint Online to offer the user a restricted session that allows them to read emails or view files, but not download them and save them on an untrusted device.

Take this step:

 - Enable limited access to [SharePoint Online](https://aka.ms/spolimitedaccessdocs) and [Exchange Online](https://aka.ms/owalimitedaccess)


### VI. Integrate threat signals from other security solutions to improve detection, protection, and response

Finally, other security solutions can be integrated for greater effectiveness.

#### Integrate Microsoft Defender for Identity with Microsoft Defender for Cloud Apps

Integration with Microsoft Defender for Identity enables Microsoft Entra ID to know that a user is indulging in risky behavior while accessing on-premises, non-modern resources (like File Shares). This can then be factored into overall user risk to block further access in the cloud.

Follow these steps:

1. [Enable Microsoft Defender for Identity](/cloud-app-security/aatp-integration) with Microsoft Defender for Cloud Apps to bring on-premises signals into the risk signal we know about the user.

2. Check the [combined Investigation Priority score](https://techcommunity.microsoft.com/t5/enterprise-mobility-security/introducing-investigation-priority-built-on-user-and-entity/ba-p/360853) for each user at risk to give a holistic view of which ones your SOC should focus on.

#### Enable Microsoft Defender for Endpoint

Microsoft Defender for Endpoint allows you to attest to the health of Windows machines and determine whether they are undergoing a compromise. You can then feed that information into mitigating risk at runtime. Whereas Domain Join gives you a sense of control, Defender for Endpoint allows you to react to a malware attack at near real time by detecting patterns where multiple user devices are hitting untrustworthy sites, and to react by raising their device/user risk at runtime.

Take this step:

 - [Configure Conditional Access in Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/configure-conditional-access).

## Securing Identity in accordance with Executive Order 14028 on Cybersecurity & OMB Memorandum 22-09

The [Executive Order 14028 on Improving the Nations Cyber Security](https://www.whitehouse.gov/briefing-room/presidential-actions/2021/05/12/executive-order-on-improving-the-nations-cybersecurity) & [OMB Memorandum 22-09](https://www.whitehouse.gov/wp-content/uploads/2022/01/M-22-09.pdf) includes specific actions on Zero Trust. Identity actions include employing centralized identity management systems, use of strong phishing-resistant MFA, and incorporating at least one device-level signal in authorization decision(s). For detailed guidance on implemening these actions with Microsoft Entra ID see [Meet identity requirements of memorandum 22-09 with Microsoft Entra ID](/azure/active-directory/standards/memo-22-09-meet-identity-requirements).

## Products covered in this guide

**Microsoft Azure**

[Microsoft Entra ID](https://azure.microsoft.com/services/active-directory/)

[Microsoft Defender for Identity](https://www.microsoft.com/security/business/threat-protection/endpoint-defender)

**Microsoft 365**

[Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager)
(includes Microsoft Intune)

[Microsoft Defender for Endpoint](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp)

[SharePoint Online](https://www.microsoft.com/microsoft-365/sharepoint/collaboration)

[Exchange Online](https://www.microsoft.com/microsoft-365/exchange/email)

## Conclusion

Identity is central to a successful Zero Trust strategy. For further information or help with implementation, please contact your Customer Success team or continue to read through the other chapters of this guide, which span all Zero Trust pillars.


<br/><br/>
<!-- Include the nav bar. -->
[!INCLUDE [navbar, bottom](../includes/navbar-bottom.md)]
