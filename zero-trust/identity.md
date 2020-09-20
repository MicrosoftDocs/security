---
title: Securing identity with Zero Trust
description: Identities, representing people, services, or IoT devices, are the common dominator across today’s many networks, endpoints, and applications. In the Zero Trust security model, they function as a powerful, flexible, and granular way to control access to data. 
ms.date: 09/01/2020
ms.service: security
author: garycentric
ms.author: v-gmoor
ms.topic: conceptual
---

# Securing identity with Zero Trust

:::image type="content" source="./media/identity/icon-fingerprint-large.png" alt-text="Fingerprint icon." border="false":::

**Background**

Cloud applications and the mobile workforce have redefined the security perimeter. Employees are bringing their own devices and working remotely. Data is being accessed outside the corporate network and shared with external collaborators such as partners and vendors. Corporate applications and data are moving from on-premises to hybrid and cloud environments. Organizations can no longer rely on traditional network controls for security. Controls need to move to where the data is: on devices, inside apps, and with partners.

Identities, representing people, services, or IoT devices, are the common dominator across today's many [networks](./networks.md), [endpoints](./endpoints.md), and [applications](./applications.md). In the Zero Trust security model, they function as a powerful, flexible, and granular way to control access to [data](./data.md).

**Before an identity attempts to access a resource, organizations must:**

-   Verify the identity with strong authentication.

-   Ensure access is compliant and typical for that identity.

-   Follows least privilege access principles.

Once the identity has been verified, we can control that identity's access to resources based on organization policies, on-going risk analysis, and other tools.

## Identity Zero Trust deployment objectives


<div class="alert.is-info"><b>Before</b> most organizations <b>start the Zero Trust journey</b>, their approach to identity is problematic in that the on-premises identity provider is in use, no SSO is present between cloud and on-premises apps, and <a href="./visibility-automation-orchestration.md">visibility</a> into identity risk is very limited.</div>

When implementing an end-to-end Zero Trust framework for identity, we recommend you focus first on these _initial_ deployment objectives:

:::row:::
   :::column:::
:::image type="content" source="./media/identity/image3.png" alt-text="List icon with one checkmark." border="false":::
   :::column-end:::
   :::column span="3":::
1. Cloud identity federates with on-premises identity systems.

2. Conditional Access policies gate access and provide remediation activities.

3. Analytics improve visibility.
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="4":::

After these are completed, focus on these _additional_ deployment objectives:

   :::column-end:::
:::row-end:::
:::row:::
   :::column::: 
:::image type="content" source="./media/identity/image5.png" alt-text="List icon with two checkmarks." border="false":::
   :::column-end:::
   :::column span="3":::
4.  Identities and access privileges are managed with identity governance.

5. User, device, location, and behavior is analyzed in real time to determine risk and deliver ongoing protection.

6. Threat signals from other security solutions are integrated.
   :::column-end:::
:::row-end:::

## Products covered in this guide

**Microsoft Azure**

[Azure Active Directory](https://azure.microsoft.com/services/active-directory/)

[Azure Advanced Threat Protection](https://azure.microsoft.com/features/azure-advanced-threat-protection/)

**Microsoft 365**

[Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager)
(includes Microsoft Intune)

[Microsoft Defender Advanced Threat Protection](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp)

[SharePoint Online](https://www.microsoft.com/microsoft-365/sharepoint/collaboration)

[Exchange Online](https://www.microsoft.com/microsoft-365/exchange/email)


## Identity Zero Trust deployment guide

This guide will walk you through the steps required to manage identities following the principles of a Zero Trust security framework.


:::row:::
   :::column:::
:::image type="content" source="./media/identity/icon-checklist-one-checkmark-large.png" alt-text="Checklist icon with one checkmarks." border="false":::
   :::column-end:::
   :::column span="3":::
## Initial deployment objectives
   :::column-end:::
:::row-end:::

### Cloud identity federates with on-premises identity systems

Azure Active Directory (AD) enables strong authentication, a point of integration for endpoint security, and the core of your user-centric policies to guarantee least-privileged access. Azure AD's Conditional Access capabilities are the policy decision point for access to resources based on user identity, environment, device health, and risk—verified explicitly at the point of access. We will show how you can implement a Zero Trust identity strategy with Azure AD.

:::row:::
   :::column span="2":::
Connect all of your users to Azure AD and federate with on-premises identity systems.
   :::column-end:::
   :::column:::
:::image type="content" source="./media/identity/circled-arrow-right.png" alt-text="Arrow in a circle pointing right." border="false":::
   :::column-end:::
   :::column span="2":::
Establish your Identity Foundation with Azure AD.
   :::column-end:::
   :::column:::
:::image type="content" source="./media/identity/circled-arrow-right.png" alt-text="Arrow in a circle pointing right." border="false":::
   :::column-end:::
   :::column span="2":::
Integrate all your applications with Azure AD.
   :::column-end:::
   :::column:::
:::image type="content" source="./media/identity/circled-arrow-right.png" alt-text="Arrow in a circle pointing right." border="false":::
   :::column-end:::
   :::column span="2":::
Verify explicitly with strong authentication.
   :::column-end:::
:::row-end:::



### Connect all of your users to Azure AD and federate with on-premises identity systems

Maintaining a healthy pipeline of your employees' identities and the necessary security artifacts (groups for authorization and endpoints for extra access policy controls) puts you in the best place to use consistent identities and controls in the cloud. 

Follow these steps:

1.  [Choose an authentication option](https://aka.ms/auth-options). Azure AD provides you the best brute force, DDoS, and password spray protection, but make the decision that's right for your organization and your compliance needs.

2.  Only bring the identities you absolutely need. For example, use going to the cloud as an opportunity to leave behind service accounts that only make sense on-premises. Leave on-premises privileged roles behind.

3.  If your enterprise has more than 100,000 users, groups, and devices combined [build a high performance sync box](https://aka.ms/aadconnectperf) that will keep your life cycle up to date.


### Establish your Identity Foundation with Azure AD

A Zero Trust strategy requires verifying explicitly, using least-privileged access principles, and assuming breach. Azure AD can act as the policy decision point to enforce your access policies based on insights on the user, endpoint, target resource, and environment.

Take this step:

 - Put Azure AD in the path of every access request. This connects every user and every app or resource through one identity control plane and provides Azure AD with the signal to make the best possible decisions about the authentication/authorization risk. In addition, single sign-on and consistent policy guardrails provide a better user experience and contribute to productivity gains.

### Integrate all your applications with Azure AD

Single sign-on prevents users from leaving copies of their credentials in various apps and helps avoid users get used to surrendering their credentials due to excessive prompting.

Also make sure you do not have multiple IAM engines in your environment. Not only does this diminish the amount of signal that Azure AD sees, allowing bad actors to live in the seams between the two IAM engines, it can also lead to poor user experience and your business partners becoming the first doubters of your Zero Trust strategy.

Follow these steps:

1.  [Integrate modern enterprise applications](https://docs.microsoft.com/azure/active-directory/manage-apps/plan-sso-deployment) that speak OAuth2.0 or SAML.

2.  For Kerberos and form-based auth applications, [integrate them using the Azure AD Application Proxy](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-deployment-plan).

3.  If you publish your legacy applications using application delivery networks/controllers, use Azure AD to [integrate](https://docs.microsoft.com/azure/active-directory/manage-apps/secure-hybrid-access) with most of the major ones (such as Citrix, Akamai, and F5).

4.  To help discover and migrate your apps off of ADFS and existing/older IAM engines, review [resources and tools](https://docs.microsoft.com/azure/active-directory/manage-apps/migration-resources).

5.  [Power push identities into your various cloud applications](https://docs.microsoft.com/azure/active-directory/app-provisioning/plan-auto-user-provisioning). This gives you a tighter identity lifecycle integration within those apps.

> [!TIP]
> [Learn about implementing an end-to-end Zero Trust strategy for applications](https://aka.ms/ZTApplications).

### Verify explicitly with strong authentication

Follow these steps:

1.  [Roll out Azure AD MFA (P1)](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted). This is a foundational piece of reducing user session risk. As users appear on new devices and from new locations, being able to respond to an MFA challenge is one of the most direct ways that your users can teach us that these are familiar devices/locations as they move around the world (without having administrators parse individual signals).

2.  [Block legacy authentication](https://docs.microsoft.com/azure/active-directory/conditional-access/block-legacy-authentication). One of the most common attack vectors for malicious actors is to use stolen/replayed credentials against legacy protocols, such as SMTP, that cannot do modern security challenges.


### Conditional Access policies gate access and provide remediation activities

Azure AD Conditional Access (CA) analyzes signals such as user, device, and location to automate decisions and enforce organizational access policies for resource. You can use CA policies to apply access controls like multi-factor authentication (MFA). CA policies allow you to prompt users for MFA when needed for security and stay out of users' way when not needed.

:::image type="content" source="./media/identity/conditional-access-policies-diagram.png" alt-text="Diagram of Conditional Access policies in Zero Trust." border="false":::

Microsoft provides standard conditional policies called [security defaults](https://docs.microsoft.com/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) that ensure a basic level of security. However, your organization may need more flexibility than security defaults offer. You can use Conditional Access to customize security defaults with more granularity and to configure new policies that meet your requirements.

Planning your Conditional Access policies in advance and having a set of active and fallback policies is a foundational pillar of your Access Policy enforcement in a Zero Trust deployment. Take the time to configure your trusted IP locations in your environment. Even if you do not use them in a Conditional Access policy, configuring these IPs informs the risk of Identity Protection mentioned above.

Take this step:

 - Check out our [deployment guidance](https://docs.microsoft.com/azure/active-directory/conditional-access/plan-conditional-access) and [best practices](https://aka.ms/resilientaad) for resilient Conditional Access policies.

### Register devices with Azure AD to restrict access from vulnerable and compromised devices

Follow these steps:

1.  [Enable Azure AD Hybrid Join](https://docs.microsoft.com/azure/active-directory/devices/concept-azure-ad-join-hybrid) or [Azure AD Join](https://docs.microsoft.com/azure/active-directory/devices/concept-azure-ad-join-hybrid). If you are managing the user's laptop/computer, bring that information into Azure AD and use it to help make better decisions. For example, you may choose to allow rich client access to data (clients that have offline copies on the computer) if you know the user is coming from a machine that your organization controls and manages. If you do not bring this in, you will likely choose to block access from rich clients, which may result in your users working around your security or using shadow IT.

2.  Enable the [Intune](https://docs.microsoft.com/mem/intune/remote-actions/device-management) service within Microsoft Endpoint Manager (EMS) for managing your users' mobile devices and [enroll devices](https://docs.microsoft.com/mem/intune/enrollment/device-enrollment). The same can be said about user mobile devices as about laptops: The more you know about them (patch level, jailbroken, rooted, etc.), the more you are able to trust or mistrust them and provide a rationale for why you block/allow access.

> [!TIP]
> [Learn about implementing an end-to-end Zero Trust strategy for endpoints](https://aka.ms/ZTEndpoints)

### Analytics improve visibility

As you build your estate in Azure AD with authentication, authorization, and provisioning, it's important to have strong operational insights into what is happening in the directory.

### Configure your logging and reporting to improve visibility

Take this step:

 - [Plan an Azure AD reporting and monitoring deployment](https://docs.microsoft.com/azure/active-directory/reports-monitoring/plan-monitoring-and-reporting) to be able to persist and analyze logs from Azure AD, either in Azure or using a SIEM system of choice.

:::row:::
   :::column:::
:::image type="content" source="./media/identity/icon-checklist-two-checkmarks-large.png" alt-text="Checklist icon with two checkmarks." border="false":::
   :::column-end:::
   :::column span="3":::
## Additional deployment objectives
   :::column-end:::
:::row-end:::

### Identities and access privileges are managed with identity governance

Once you've accomplished your initial three objectives, you can focus on additional objectives such as more robust identity governance.

:::row:::
   :::column:::
Secure privileged access with Privileged Identity Management.
   :::column-end:::
   :::column:::
:::image type="content" source="./media/identity/circled-arrow-right.png" alt-text="Arrow in a circle pointing right." border="false":::
   :::column-end:::
   :::column:::
Restrict user content to applications.
   :::column-end:::
   :::column:::
:::image type="content" source="./media/identity/circled-arrow-right.png" alt-text="Arrow in a circle pointing right." border="false":::
   :::column-end:::
   :::column:::
Manage entitlement.
   :::column-end:::
   :::column:::
:::image type="content" source="./media/identity/circled-arrow-right.png" alt-text="Arrow in a circle pointing right." border="false":::
   :::column-end:::
   :::column:::
User passwordless authentication to reduce the risk of phishing and password attacks.
   :::column-end:::
:::row-end:::


### Secure privileged access with Privileged Identity Management

Control the endpoints, conditions, and credentials that users use to access privileged operations/roles.

Follow these steps:

1.  [Take control of your privileged identities](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-admin-roles-secure). Keep in mind that in a digitally-transformed organization, privileged access is not only administrative access, but also application owner or developer access that can change the way your mission-critical apps run and handle data.

2.  [Use Privileged Identity Management to secure privileged identities](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-deployment-plan).

### Restrict user consent to applications

User consent to applications is a very common way for modern applications to get access to organizational resources, but there are some best practices to keep in mind.

Follow these steps:

1.  [Restrict user consent and manage consent requests](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-consent-requests) to ensure that no unnecessary exposure occurs of your organization's data to apps.

2.  [Review prior/existing consent in your organization](https://docs.microsoft.com/microsoft-365/security/office-365-security/detect-and-remediate-illicit-consent-grants?view=o365-worldwide&preserve-view=true) for any excessive or malicious consent.

For more on tools to protect against tactics to access sensitive information, see "Strengthen protection against cyber threats and rogue apps" in our [guide to implementing an identity Zero Trust strategy](https://aka.ms/ZTIdentity).


### Manage entitlement

With applications centrally authenticating and driven from Azure AD, you can now streamline your access request, approval, and recertification process to make sure that the right people have the right access and that you have a trail of why users in your organization have the access they have.

Follow these steps:

1.  Use Entitlement Management to [create access packages](https://docs.microsoft.com/azure/active-directory/governance/entitlement-management-access-package-create) that users can request as they join different teams/projects and that assigns them access to the associated resources (such as applications, SharePoint sites, group memberships).

2.  If deploying Entitlement Management is not possible for your organization at this time, at least enable self-service paradigms in your organization by deploying [self-service group management](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-self-service-management) and [self-service application access](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-self-service-access).

### Use passwordless authentication to reduce the risk of phishing and password attacks

With Azure AD supporting FIDO 2.0 and passwordless phone sign-in, you can move the needle on the credentials that your users (especially sensitive/privileged users) are employing day-to-day. These credentials are strong authentication factors that can mitigate risk as well.

Take this step:

 - [Start rolling out passwordless credentials](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-deployment) in your organization.


## User, device, location, and behavior is analyzed in real time to determine risk and deliver ongoing protection

Real-time analysis is critical for determining risk and protection.

:::row:::
   :::column:::
Deploy Azure AD Password Protection.
   :::column-end:::
   :::column:::
:::image type="content" source="./media/identity/circled-arrow-right.png" alt-text="Arrow in a circle pointing right." border="false":::
   :::column-end:::
   :::column:::
Enable Identity Protection.
   :::column-end:::
   :::column:::
:::image type="content" source="./media/identity/circled-arrow-right.png" alt-text="Arrow in a circle pointing right." border="false":::
   :::column-end:::
   :::column:::
Enable Microsoft Cloud App Security integration with Identity Protection.
   :::column-end:::
   :::column:::
:::image type="content" source="./media/identity/circled-arrow-right.png" alt-text="Arrow in a circle pointing right." border="false":::
   :::column-end:::
   :::column:::
Enable Conditional Access integration with Microsoft Cloud App Security.
   :::column-end:::
:::row-end:::


### Deploy Azure AD Password Protection

While enabling other methods to verify users explicitly, don't ignore weak passwords, password spray, and breach replay attacks. And [classic complex password policies do not prevent the most prevalent password attacks](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/your-pa-word-doesn-t-matter/ba-p/731984).

Take this step:

 - Enable Azure AD Password Protection for your users [in the cloud](https://docs.microsoft.com/azure/active-directory/authentication/concept-password-ban-bad) and [on-premises](https://docs.microsoft.com/azure/active-directory/authentication/howto-password-ban-bad-on-premises-deploy).

### Enable Identity Protection

Get more granular session/user risk signal with Identity Protection. You'll be able to investigate risk and confirm compromise or dismiss the signal, which will help the engine better understand what risk looks like in your environment.

Take this step:

 - [Enable Identity Protection](https://docs.microsoft.com/azure/active-directory/identity-protection/overview-identity-protection).

### Enable Microsoft Cloud App Security integration with Identity Protection

Microsoft Cloud App Security (MCAS) monitors user behavior inside SaaS and modern applications. This informs Azure AD about what happened to the user after they authenticated and received a token. If the user pattern starts to look suspicious (e.g., a user starts to download gigabytes of data from OneDrive or starts to send spam emails in Exchange Online), then a signal can be fed to Azure AD notifying it that the user seems to be compromised or high risk. On the next access request from this user, Azure AD can correctly take action to verify the user or block them.

Take this step:

 - [Enable MCAS monitoring](https://docs.microsoft.com/cloud-app-security/azip-integration) to enrich the Identity Protection signal.

### Enable Conditional Access integration with Microsoft Cloud App Security

Using signals emitted after authentication and with MCAS proxying requests to applications, you will be able to monitor sessions going to SaaS applications and enforce restrictions.

Follow these steps:

1.  [Enable Conditional Access integration](https://docs.microsoft.com/cloud-app-security/proxy-intro-aad).

2.  [Extend Conditional Access to on-premises apps](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-integrate-with-microsoft-cloud-application-security).

### Enable restricted session for use in access decisions

When a user's risk is low, but they are signing in from an unknown endpoint, you may want to allow them access to critical resources, but not allow them to do things that leave your organization in a noncompliant state. Now you can configure Exchange Online and SharePoint Online to offer the user a restricted session that allows them to read emails or view files, but not download them and save them on an untrusted device.

Take this step:

 - Enable limited access to [SharePoint Online](https://aka.ms/spolimitedaccessdocs) and [Exchange Online](https://aka.ms/owalimitedaccess)


## Integrate threat signals from other security solutions to improve detection, protection, and response

Finally, other security solutions can be integrated for greater effectiveness.

### Integrate Azure Advanced Threat Protection with Microsoft Cloud App Security

Integration with Azure Advanced Threat Protection (Azure ATP) enables Azure AD to know that a user is indulging in risky behavior while accessing on-premises, non-modern resources (like File Shares). This can then be factored into overall user risk to block further access in the cloud.

Follow these steps:

1.  [Enable Azure ATP integration](https://docs.microsoft.com/cloud-app-security/aatp-integration) with Microsoft Cloud App Security to bring on-premises signals into the risk signal we know about the user.

2.  Check the [combined Investigation Priority score](https://techcommunity.microsoft.com/t5/enterprise-mobility-security/introducing-investigation-priority-built-on-user-and-entity/ba-p/360853) for each user at risk to give a holistic view of which ones your SOC should focus on.

### Enable Microsoft Defender Advanced Threat Protection

Microsoft Defender Advanced Threat Protection (Defender ATP) allows you to attest to the health of Windows machines and determine whether they are undergoing a compromise. You can then feed that information into mitigating risk at runtime. Whereas Domain Join gives you a sense of control, Defender ATP allows you to react to a malware attack at near real time by detecting patterns where multiple user devices are hitting untrustworthy sites, and to react by raising their device/user risk at runtime.

Take this step:

 - [Configure Conditional Access in Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-conditional-access).

## Conclusion

Identity is central to a successful Zero Trust strategy. For further information or help with implementation, please contact your Customer Success team or continue to read through the other chapters of this guide, which span all Zero Trust pillars.

<!--
**The Zero Trust deployment guide series**

| <img src="./media/identity/image11.emf" style="width:0.34215in;height:0.34215in" /> | <img src="./media/identity/image12.png" style="width:0.20833in;height:0.26316in" /> | <img src="./media/identity/image13.png" style="width:0.28564in;height:0.23809in" /> | <img src="./media/identity/image14.emf" style="width:0.26496in;height:0.26496in" /> | <img src="./media/identity/image15.png" style="width:0.26189in;height:0.22618in" /> | <img src="./media/identity/image17.png" style="width:0.2375in;height:0.26181in" /> | <img src="./media/identity/image18.png" style="width:0.24653in;height:0.24653in" /> | <img src="./media/identity/image19.png" style="width:0.27908in;height:0.27908in" /> |
|-----------------------------------------------------------------------------|-----------------------------------------------------------------------------|-----------------------------------------------------------------------------|-----------------------------------------------------------------------------|-----------------------------------------------------------------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| [Introduction](https://aka.ms/ZTDeploymentGuideIntroduction)                | [Identity](https://aka.ms/ZTIdentity)                                       | [Endpoints](https://aka.ms/ZTEndpoints)                                     | [Applications](https://aka.ms/ZTApplications)                               | [Data](https://aka.ms/ZTData)                                               | [Network](https://aka.ms/ZTNetwork)                                        | [Infrastructure](https://aka.ms/ZTInfrastructure)                           | [Visibility, Automation, Orchestration](https://aka.ms/ZTCrossPillars)      |
-->
