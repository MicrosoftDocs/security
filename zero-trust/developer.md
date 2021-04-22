# Zero Trust for the Microsoft Identity Platform developer

## Summary

As today's contemporary landscape of security models increasingly adapt the principals of Zero Trust, developers are often left wondering their place in role and responsibility in this space. This document aims to provide a set of guidance and a checklist for developers who integrate their applications and services with the Microsoft Identity platform for Authentication, Authorization and access to popular APIs like [MS Graph](http://aka.ms/graph) and [Azure REST API](https://docs.microsoft.com/en-us/rest/api/azure/). We hope that developers will utilize the advice and guidance provided here to ensure that their integrated applications and services hold true to the principals of Zero Trust. The aim of this document is to help developers building, integrating and configuration apps achieve the following objectives:

- Ensures their application _abides by principles of Zero Trust._ This objective helps apps being inherently secure.
- Ensure that their application _works well and is manageable in environments that implement ZT principles._ This helps the app being compatible with security features that may be used in the environment(s) my app will run in.

Microsoft's [Zero Trust business plan's](https://www.microsoft.com/en-ca/security/business/zero-trust) essential audience is an IT pro. So, this guide aims to keep the development aspects of the advisories and checklists separate from an IT pro and a platform (like Azure AD).

## Background

A developer, by habit, might choose to focus more on the integration and business aspects of their applications than end-to-end security. This approach is often acceptable for the most part as in today's cloud platform world, where the Identity and Access providers like the Microsoft Identity platform provide most of the necessary means for developers to achieve security.

A developer following [Microsoft's prescriptive guidance](http://aka.ms/identityplatform) provided at the resources listed below will usually end integrating their apps using modern protocols for authentication and making good use the provided tools, like the portal, development tools, SDKs, and the established integration patterns for the most part.

- [Microsoft identity platform documentation](https://docs.microsoft.com/en-us/azure/active-directory/develop/)
- [Authentication flows and application scenarios](https://docs.microsoft.com/en-us/azure/active-directory/develop/authentication-flows-app-scenarios)
- [Microsoft identity platform code samples](https://docs.microsoft.com/en-us/azure/active-directory/develop/sample-v2-code)
- [Microsoft identity platform best practices and recommendations](https://docs.microsoft.com/en-us/azure/active-directory/develop/identity-platform-integration-checklist)

Following Microsoft's guidance will essentially ensure that the app integration integrations is safe and secure for the most part. The tooling and SDKs have been developed and made available to the developers with an aim to offload most of the security aspects to the Microsoft Identity platform and developers are encouraged to use and follow the provided resources.

## Why should developers care?

With apps now being expected to follow and implement aspects of identity proofing, controlled access to data or even limit data access based on security parameters, the challenges of app development exposes aspects of security, developers in the classic sense never had to deal with earlier.

While we advise developers to offload most aspects to the Microsoft Identity Platform (IdP), there still remains a bit that the developers are expected to also undertake at their end. The complete security posture is achieved by utilizing the combination of features provided by the IdP and developers following a set of guided recommendations.

Every aspect of zero trust cannot be evaluated and validated by the app developers alone and a full compliance requires developers to work with the IT pros. Even if not directly, the developers do carry the responsibility of building and integrating apps in a manner where an IT pro can use tools at their disposal to carry out steps to further secure the applications.

One great way for developers to look at this paradigm is how they, together with IT admins, can quickly respond to defeat attacks and compromises and reduce damage to business. The guidance provided here helps developers develop and integrate applications in a manner that will help you quickly attend to these actions by bad actors.

To start with, any established culture of implicit trust must give way to that of explicit verification to achieve Zero Trust.

## Zero Trust summarized

Instead of assuming everything behind the corporate firewall is safe, the Zero Trust model assumes breach and verifies each request as though it originates from an open network. Regardless of where the request originates or what resource it accesses, Zero Trust teaches us to &quot;never trust, always verify.&quot; Every access request is fully authenticated, authorized, and encrypted before granting access. Micro segmentation and least privileged access principles are applied to minimize lateral movement. Rich intelligence and analytics are utilized to detect and respond to anomalies in real time.

![](RackMultipart20210422-4-1lh88p4_html_99bc73dd2b9cf451.jpg)

A simplified diagram provided of Zero Trust security with a security policy enforcement engine at its core providing real-time policy evaluation. The engine delivers protection by analyzing signals and applying organization policy and threat intelligence. It ensures identities are verified and authenticated, and devices are safe, before granting access to data, apps, infrastructure, and networks. In addition, visibility and analytics, along with automation, are applied continuously and comprehensively.

With [features](https://azure.microsoft.com/en-us/services/active-directory/#features) like Single Sign-on, Conditional Access with MFA, Device registration and management, Identity Protection and a full set of developer tools and SDKs, coupled with a rich set of additional services provided under the [Microsoft Intelligent Security](https://www.microsoft.com/en-ca/security/business) umbrella available out of the box, Microsoft provides all that a business will ever need to achieve full Zero Trust posture for their applications, users and devices.

## Application Types

The guide will use the [application types as classified by the Microsoft Identity platform](https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-app-types) and thus will keep the developers already involved with the platform in a familiar territory.

Most of the steps and guidance applies to all types of applications and thus would not be called out as such. But at times, we would discuss any particular steps for the following types of applications as applicable.

1. **Web applications** – These are usually web sites that users sign-in and interact with.
2. **Web APIs** – APIs that expose operations and data and does not directly interacts with users. They are almost exclusively called by other applications.
3. **Desktop applications** – Applications that are used on a desktop, Windows machine. Examples are those built with frameworks like WPF and WinForms.
4. **Mobile applications** – Applications that are developed for mobile devices, like for iOS and Android.
5. **Daemon &amp; Services** - TODO

We have divided the guidance provided under the three principals of Zero Trust.

## Verify Explicitly

_Always authenticate and authorize based on all available data points, including user identity, location, device health, service or workload, data classification, and anomalies._

To meet the aforementioned objectives in a single application would be a very tall order if not outright unfair to expect from the developers. Today, this requires integration with an Identity and Access provider that provides these services out of the box. Thus, developers start with learning how to best integrate with Identity providers whose offerings best meet these objectives. The Microsoft Identity platform (Azure AD) is an Identity Provider (IdP) that is fully capable to meet these needs and more.

To start with, it provides support for modern protocols (OpenID Connect, OAuth and SAML) that developers can use for authentication and Single sign-on. Additionally, it also provides authentication services for on-prem apps via App Proxy, Secure Hybrid Access and Windows Integrated Authentication.

While integrating their applications and services, we advise the developers follow and adopt the following guidance to make their integrations hold true to this tenet of Zero Trust principles.

- Prepare applications to authenticate using all available sources.
  - Most of this is taken care by the IdPs as long as the application has used one of the available [authentication protocols](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-v2-protocols) to integrate their app. Once single sign-on (SSO) is achieved using the provided protocols, any need for holding credentials in applications is removed, vastly improving the security posture of an application. The identity provider becomes the security perimeter instead.
  - We strongly advise developers use standard SDKs to integrate their applications with the Microsoft identity platform.
    - [MSALs](https://docs.microsoft.com/en-us/azure/active-directory/develop/reference-v2-libraries) SDKs are provided by Microsoft to sign-in users and get Access Tokens (AT) for APIs.
    - Or developers should use any of the [Certified OpenID Connect Implementations](https://openid.net/developers/certified/)
    - Prefer to use more recent protocols like OpenID Connect and OAuth 2.0 over older ones like SAML. The OpenID Connect and OAuth 2.0 continue to receive new innovations and are continuously evolving to address new paradigms, opportunities and challenges in the identity and security space.
    - New and evolving features like Conditional Access Auth Context (CAAC), Continuous Access Evaluation (CAE) follow the [Individual Claims Requests](https://openid.net/specs/openid-connect-core-1_0.html#IndividualClaimsRequests) which will not work for apps using SAML.
- Use the [correct authentication flow by app type](https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-app-types) for authentication.
  - The flows for web applications that can hold a secret ([Confidential clients](https://docs.microsoft.com/en-us/azure/active-directory/develop/msal-client-applications)) are considered more secure than [Public clients](https://docs.microsoft.com/en-us/azure/active-directory/develop/msal-client-applications). Web applications should always aim to use the confidential client flows.
  - Consider avoiding weaker flows like [implicit grant flow](https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-implicit-grant-flow).
- Prepare for additional claim requests (CA, CCAE and CAE).
  - Use the combination of right SDKs and flows to ensure that your app is accessible to the right users in the most restrictive of environments. These controls ensure that a user access the app from a situation specified by security, like from a managed device, location and is capable of redirection the user back to the IdP if additional authentication methods (like MFA) and actions (password change) need to be carried out.
- Mobile apps
  - Rely on [brokers](https://developer.microsoft.com/en-us/identity/blogs/microsoft-authentication-libraries-for-android-ios-and-macos-are-now-generally-available/) to conduct authentication when available on the device.
  - Consider supporting Intune [App protection policies](https://docs.microsoft.com/en-us/mem/intune/apps/app-protection-policy) in your app to ensure that an organization's data remains safe and contained.
  - Follow instructions provided in [Support single sign-on and app protection policies in mobile apps you develop](https://docs.microsoft.com/en-us/azure/active-directory/develop/mobile-sso-support-overview) to build the most secure and manageable experience in your mobile applications.
  - If using the MSAL library is not possible, consider using the [system web browser](https://docs.microsoft.com/en-us/azure/active-directory/develop/mobile-sso-support-overview#use-the-system-web-browser) for a secure and great SSO experience.
- If integrating a Web API
  - [Validate tokens](https://github.com/AzureAD/azure-activedirectory-identitymodel-extensions-for-dotnet/wiki/ValidatingTokens) using an [established standard library.](https://github.com/AzureAD/azure-activedirectory-identitymodel-extensions-for-dotnet/blob/dev/README.md) Not only would their abstractions make this process smooth for you, they will also handle key rotations for your app.
  - Check for the correct [scopes (scp) and roles (roles)](https://docs.microsoft.com/en-us/azure/active-directory/develop/scenario-protected-web-api-verification-scope-app-roles) or both as applicable.
  - Check for the right audience (aud).
    - During Azure AD registration, an AppID URI can be defined or made available to you.
    - Your API should only accept tokens for your app or app ID URI, see [aud](https://docs.microsoft.com/en-us/azure/active-directory/develop/access-tokens) claim.
    - Please do not accept tokens issued to popular APIs like [_https://graph.microsoft.com_](https://graph.microsoft.com/) as proof of authentication.
  - Consider [extending token validation](https://github.com/Azure-Samples/active-directory-dotnet-webapi-manual-jwt-validation/blob/master/README.md) to:
    - Filter Apps that are allowed to call your API.
    - Filter [Tenants](https://github.com/Azure-Samples/active-directory-aspnetcore-webapp-openidconnect-v2/blob/master/2-WebApp-graph-user/2-3-Multi-Tenant/README.md) where a token can be obtained by your API.
  - Expose granular permissions.
    - If your API exposes a lot of operations, consider providing granular set of scopes to avoid exposing all operations to each client. Usually APIs have just a single scope, named like _user\_impersonation_ or _access\_as\_user_ which is insufficient to lay down a proper permission set if your API surface is large.
    - See [this example](https://docs.microsoft.com/en-us/graph/api/resources/users?view=graph-rest-1.0#authorization) in Graph on how to design leveled permission sets.
- If you have [Microsoft Dynamics 365 Fraud Protection with Azure Active Directory B2C](https://docs.microsoft.com/en-us/azure/active-directory-b2c/partner-dynamics-365-fraud-protection), it helps you assess if the risk of attempts to create new accounts and attempts to login to client's ecosystem are fraudulent. Microsoft DFP assessment can be used by the customer to block or challenge suspicious attempts to create new fake accounts or to compromise existing accounts.
- Consider enabling explicit access to users and applications in your tenant. By default, apps can sign in all users (including guest users) in a tenant.
  - Use the &quot;[User assignment Required](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/assign-user-or-group-access-portal)&quot; flag to ensure that only a set of users are able to sign-in to the application.
- Avoid using built-in accounts that have access to resources. They might be shared. Let IT admins drive access from outside.
  - If the app is a daemon or server side that authenticates as itself (App only AuthN), avoid hardcoding authentication parameters in the app. Let it be driven by config, so it can be replaced without redeploying in case of a breach
- Do not let the users remain signed-in beyond Drive applications' session timeouts from the IDPs' granted tokens expiry.
  - Several popular frameworks, ASP.NET for example, allow you to set session/cookie timeouts from Azure AD's ID token's expiry time. Following the IDPs token expiry time will ensure that your user's sessions are not longer than IDPs.
- Learn to distinguish different types of users (homed, guest) if needed.
  - Your application can be made aware of different types of users and
- In apps and APIs that are signing-in users
  - Have code that can check and optionally log the signing-in user's identity and user's attributes like designation, home tenant (if applicable), sign-in method, user type, (guest, homed)
  - Check for [app roles assigned](https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-add-app-roles-in-azure-ad-apps) to users and apps.
- Handle errors gracefully
  - When relying on the IdP for authentication, not all authentication scenarios will be under the control of the developer. For example, if a user is deemed risky, the IdP will refuse to sign the user in. The app developer should develop code so that any existing sessions and cached tokens are removed till the user successfully authenticates.
- Check redirect URLs used in your app registration for ownership and to avoid domain takeovers.
  - The URLs should be of domains you know and own.
  - Remove unnecessary and unused URLs.

Proof of possession and Token binding – TODO

## Use least privileged access

_Limit user access with just-in-time and just-enough-access (JIT/JEA), risk-based adaptive polices, and data protection to help secure both data and productivity._

Today, the most popular mechanism to expose data is through [APIs protected by the Identity Platform](https://docs.microsoft.com/en-us/azure/active-directory/develop/scenario-protected-web-api-overview). Most developers will access their own organization's or their customers' data using popular Microsoft APIs like [Microsoft Graph](http://aka.ms/graph) or the [Azure REST API](https://docs.microsoft.com/en-us/rest/api/azure/).

This section will thus be heavily focused towards developers accessing Microsoft's popular APIs or exposing their own.

- Evaluate Graph permissions that your app needs carefully to ensure least privileged access.
  - Too often developers request for higher privilege permissions to avoid the effort to carefully work through the large number of permissions that Graph provides to help with just the right number of permissions to get done.
  - Graph is often an important point of attack that is used to access an organization's data. Keeping apps that read and write data using Graph to least privileged set of permissions cannot be emphasized enough.
- Do not let your app end up with multiple high-privilege permissions for APIs in general.
  - Consider breaking apps according to responsibility if feasible.
- Avoid using the same app registration for multiple apps.
  - Unless tightly coupled, apps that sign-in users and those that expose data and operations via API should have separate app registrations. This allows permissions, like those for Graph and any credentials (like secrets and certificates) for a higher privileged API at a distance from users directly signing-in and interacting with apps.
  - Prefer to use separate app registrations for web apps and APIs.
  - This also helps ensure that if the web API has a higher set of permissions, then the client app does inherit those.
- Use [app roles](https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-add-app-roles-in-azure-ad-apps) to drive authorization in your apps, especially for administrative and high-privilege functions. You can even use [PIM managed groups](https://docs.microsoft.com/en-us/azure/active-directory/privileged-identity-management/groups-features) to enable JIT access to these app roles.
- For Azure APIs, ensure the users and roles are in roles just right for the actions they need to perform.
  - Use [Azure Policy](https://docs.microsoft.com/en-us/azure/governance/policy/overview) to enforce organizational standards and to assess compliance at-scale.
  - When developing your own APIs, take time to divide the functionality and data access into sections that can be controlled via scopes and app roles. It's usually a bad idea to just have one app role (app permission) and scope for an API for its clients.

## Assume Breach

_Minimize blast radius for breaches and prevent lateral movement by segmenting access by network, user, devices, and app awareness. Verify all sessions are encrypted end to end. Use analytics to get visibility, drive threat detection, and improve defenses._

The aim here is that the application should be integrated and deployed in a manner where detection and remediation can be carried out without downtime or affecting legitimate users.

We would thus list out some guidelines, which when followed helps to detect and bring control after a breach/compromise.

- Remove all secrets from code and configuration.
  - Place them in [Key vault](https://docs.microsoft.com/en-us/azure/key-vault/general/basic-concepts) and access them via a [Managed Identity](https://docs.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/overview). This makes the code resilient to handle secret rotations if a compromise occurs. The IT admins can remove/rotate secrets and certificates without taking the application down or affecting legitimate users.
- Use SSL/TLS (Https) for all endpoints used and accessed in your app.
  - Token grants from Azure AD rely on secure communications provided by https to ensure that tokens stay within the browser and cannot be sniffed on the network.
- Prefer certificates over client secrets.
  - Certificates can be revoked if compromised.
  - Use secrets with set expiry time period (1 year, 2 years) and avoid never expires. Once leaked, a leaked secret usage is hard to track.
- Build [resilience in your application](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/resilience-app-development-overview)
  - Secure token caching connection strings with encryption.
  - Do not pass security artefacts like tokens around on non-secure channels.
  - Understand and act on exceptions and service responses from IdP.
- Do not aim for very long or very short token lifetimes. Let the IdP decide that policy.
  - Very short sessions degrade user experience and does not necessarily increase the security posture.
- Keep data behind APIs and segregate them so that least privileged access principals can be applied.
  - For example, segregate data access for users and applications like [Microsoft Graph does](https://docs.microsoft.com/en-us/graph/permissions-reference) it.
  - This helps to keep the data loss limited to the compromised user.
- Ensure app and service principal owners are always defined and maintained for your apps registered in your tenant.
  - Avoid orphaned apps, i.e. apps and [service principals](https://docs.microsoft.com/en-us/azure/active-directory/develop/app-objects-and-service-principals) that have no owners assigned. Locating app owners should not be a time-consuming process.
- Enable your code for [Continuous Access Evaluation (CAE)](https://docs.microsoft.com/en-us/azure/active-directory/develop/app-resilience-continuous-access-evaluation) events and challenges. This allows CAE supporting APIs like MS Graph to reject tokens for users whose tokens have been invalidated (user left, or user marked as risky)

- Have a solid and tested backup and restore strategy. Prepare to revert data and state to an earlier stage.
  - Backup and restore app and its data regularly.
- Log detailed telemetry of your authentication and authorization layers of your app for best analytics. This information will be valuable in analyzing, detecting and controlling comprised access or data loss.
  - [Tokens](https://docs.microsoft.com/en-us/azure/active-directory/develop/id-tokens) issued to users and applications will have claims like _oid_, _upn_, _tid_, _sub_, _preferred\_username_, _aud_, _idp_/_iss_, _appid_/_azp_ which should be logged into your logging and telemetry. For SaaS multi-tenant applications, it also provides a detailed view to the distribution of the [multi-tenant apps](https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-convert-app-to-be-multi-tenant) across Azure AD tenants.
  - Additionally, also log actions specific to the app, device info (if available), environmental conditions (see [optional claims](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-optional-claims) like IP address (_ipaddr_))
- If developing a SaaS application that will be provisioned into customer tenants, consider integrating using the [multi-tenant](https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-convert-app-to-be-multi-tenant) pattern. Among other benefits, this pattern enhances your security posture by:
  - Credentials remain with the SaaS developer (ISV), thus removing scope of abuse in a tenant.
  - It helps provide unique identification of an app for CA policy, reporting and QoS
  - App can be identified and isolated during attacks much more quickly.