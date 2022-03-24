---
title: Compromised and malicious applications
description: Learn how to investigate if one or more applications in a customer tenant are compromised.
keywords: compromise, malicious, applications, investigation, attack, microsoft threat protection, microsoft 365, search, query, telemetry, security events, antivirus, firewall, incident response, playbook, guidance, Microsoft 365 Defender
search.product: DART
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords: 
  - NOCSH
ms.author: dansimp
author: RatulaC
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: 
  - M365-security-compliance
  - m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
---

# Compromised and malicious applications

This article provides guidance on identifying and investigating malicious attacks on one or more applications in a customer tenant that are compromised. The step-by-step instructions will help you take the required remedial action to protect information and minimize further risks.

- **Prerequisites:** Covers the specific requirements you need to complete before starting the investigation. For example, logging that should be turned on, roles and permissions required, among others.
- **Workflow:** Shows the logical flow that you should follow to perform this investigation.
- **Investigation steps:** Includes a detailed step-by-step guidance for this specific investigation.
- **Recovery steps:** Contains high-level steps on how to recover/mitigate from a malicious attack on compromised applications.
- **References:** Contains additional reading and reference materials.

## Prerequisites

Before starting the investigation, make sure you have detailed information on the applications that you suspect to be compromised by the malicious attack.

- To leverage Identity protection signals, the tenant must be licensed for Azure Active Directory (Azure AD) Premium P2.
  - Understanding of the [Identity Protection risk concepts](/azure/active-directory/identity-protection/concept-identity-protection-risks)
  - Understanding of the [Identity protection investigation concepts](/azure/active-directory/identity-protection/howto-identity-protection-investigate-risk)

- Ability to use Graph Explorer and be familiar (to some extend) with the Microsoft Graph API.

- An account with the following directory roles:
  - Global administrator
  - Security administrator

- Familiarize yourself with the [application auditing concepts](/azure/active-directory/fundamentals/security-operations-applications) (part of https://aka.ms/AzureADSecOps).

- Make sure application owners have the set of ALL Enterprise apps in your tenant. Review the concepts [here](/azure/active-directory/manage-apps/overview-assign-app-owners) and [here](/azure/active-directory/manage-apps/assign-app-owners).

- Familiarize yourself with the concepts of the [App Consent grant investigation](/security/compass/incident-response-playbook-app-consent) (part of https://aka.ms/IRPlaybooks).

- Make sure you understand the following Azure AD permissions: 
  - [Risky permissions](/security/compass/incident-response-playbook-app-consent#classifying-risky-permissions)
  - [Consent model and the Admin consent workflow](/azure/active-directory/manage-apps/configure-admin-consent-workflow)

### Required tools

For an effective investigation, install the following PowerShell module and the toolkit on your investigation machine:

- [Azure AD Incident Response PowerShell Module](https://github.com/AzureAD/Azure-AD-Incident-Response-PowerShell-Module)
- [Azure AD Toolkit](https://github.com/microsoft/AzureADToolkit)

## Workflow

[Add screenshot of the Visio diagram]

## Investigation steps

For this investigation, it is assumed that you either have a indication for a potential application compromise in the form of a user report, Azure AD sign-in logs example, or Identity protection detection. Make sure to complete and enable all required prerequisite steps.

This playbook is created with the intention that not all Microsoft customers and their investigation teams will have the full Microsoft 365 E5 or Azure AD Premium P2 license suite available or configured in the tenant that is being investigated. We will however highlight additional automation capabilities when appropriate.

### Determine application type

It is important to determine the type of application (multi or single tenant) early in the investigation phase to get the correct information needed to reach out to the application owner. For more information, see [Tenancy in Azure Active Directory](/azure/active-directory/develop/single-and-multi-tenant-apps).

#### Multi-tenant applications

For Multi-tenant applications, the application is hosted and managed by a third party. Identify the process needed to reach out and report issues to the application owner.

#### Single-tenant applications

Find the contact details of the application owner within your organization. You can find it under the **Owners** tab on the **Enterprise Applications** section, or your organization may have a database that has this information.

### Check Identity Protection - risky workload identities

This feature is in preview at the time of writing this playbook and licensing requirements will apply to its usage. Risky workload identities can be the trigger to investigate a Service Principal, but also be used to further investigate into other triggers you may have identified. You can check the **Risk State** of a Service Principal using the **Identity Protection - risky workload identities** tab, or you can use Graph API.

### Check for unusual sign-in behavior

The first step of the investigation is to look for evidence of unusual authentications patterns in the usage of the Service Principal. Within the Azure portal, Azure Monitor, Azure Sentinel, or the Security Information and Event Management (SEIM) system of your organization's choice, look for the following in the **Service principal sign-ins** section:

- Location - is the Service Principal authenticating from locations\IP addresses that you would not expect?
- Failures - are there a large number of authentication failures for the Service Principal?
- Timestamps - are there successful authentications that are occurring at times that you would not expect?
- Frequency - is there an increased frequency of authentications for the Service Principal?

### Check the target resource

Within Service principal sign-ins, also check the **Resource** that the Service Principal was accessing during the authentication. Is it an expected resource? It is important to have input from the application owner as they will be familiar with which resources the Service Principal should be accessing.

### Check for abnormal credential changes

- All the required information can be found in the Audit logs.
- Filter for **Category** by **Application Management**, and **Activity** by **Update Application – Certificates and secrets management**.
- Check to see if there was an unauthorized change to credentials on the account.
- Also check whether there are more credentials than warranted, assigned to the service principal.
- Finally, when checking for credentials, check both the application and associated service principal objects.

### Search for anomalous app configuration changes

- Check Audit logs (filter **Activity** by **Update Application** or **Update Service Principal**).
- Confirm whether the connection strings are consistent and whether has the sign-out URL has been modified.
- Confirm whether the domains in the URL are in-line with those registered.
- Determine whether anyone has added an unauthorized redirect URL.
- Confirm ownership of the redirect URI that you own to ensure it did not expire and was claimed by an adversary.

### Check for suspicious application roles

- This can also be investigated using the Audit logs. Filter **Activity** by **Add app role assignment to service principal**.
- Confirm whether the assigned roles have high privilege.
- Confirm whether those privileges are necessary.

### Check for unverified commercial apps

- Check whether commercial gallery (published and verified versions) applications are being used.

### Check UAL for phishing indications 

Typically, when attackers use malicious or compromised applications as a means of persistence or to exfiltrate data, a phishing campaign is involved. Based on the findings from the previous steps, you should review the identities of:

- Application Owners
- Consent Admins

Review the identities for indications of phishing attacks in the last 24 hours. Increase this time span if needed to 7, 14, and 30 days if there are no immediate indications. For a detailed phishing investigation playbook, see the [Phishing Investigation Playbook](incident-response-playbook-phishing.md).

### Search for malicious application consents 

To get an application added to a tenant, attackers spoof users or admins to consent to applications. To know more about the signs of an attack, see the [Application Consent Grant Investigation Playbook](incident-response-playbook-app-consent.md#finding-signs-of-an-attack). 

### Check application consent for the flagged application

- Check Audit logs. To see all consent grants for that application, filter **Activity** by **Consent to application**. Follow the steps described [here](incident-response-playbook-app-consent.md#finding-signs-of-an-attack).
  An example using Graph API:
  
```HTTP
GET https://graph.microsoft.com/v1.0/auditLogs/auditLogs/directoryAudits?&$filter=activityDateTime le 2022-01-24
```

- Determine if there was suspicious end-user consent to the application.
- Check Audit logs to find whether the permissions granted are too broad (tenant-wide or admin-consented).
- Check whether the permissions were granted by user identities that should not have the ability to do this, or whether the actions were performed at strange dates and times.
- Dismiss/Confirm Risk: Once you determine whether the application was compromised, call the API to dismiss the risk or confirm compromised per the above guidance.

## Recovery steps

### Remediate Service Principals

1. List all credentials assigned to the **Risky Service Principal**. The best way to do this is to perform a Microsoft Graph call using GET ~/application/{id} where id passed is the application object ID.

    - Parse the output for credentials. The output may contain passwordCredentials or keyCredentials. Record the keyIds for all. 

      ```
      "keyCredentials": [],
           "parentalControlSettings": {
               "countriesBlockedForMinors": [],
               "legalAgeGroupRule": "Allow"
           },
           "passwordCredentials": [
               {
                   "customKeyIdentifier": null,
                   "displayName": "Test",
                   "endDateTime": "2021-12-16T19:19:36.997Z",
                   "hint": "7~-",
                   "keyId": "9f92041c-46b9-4ebc-95fd-e45745734bef",
                   "secretText": null,
                   "startDateTime": "2021-06-16T18:19:36.997Z"
               }
           ],
      ```

2. Add a new (x509) certificate credential to the application object using the application addKey API.

   ```
   POST ~/applications/{id}/addKey
   ```

3. Immediately remove all old credentials. For each old password credential, remove it by using:

   ```
   POST ~/applications/{id}/removePassword
   ```

   For each old key credential, remove it by using:

   ```
   POST ~/applications/{id}/removeKey
   ```

4. Remediate all Service Principals associated with the application. Follow this if your tenant hosts/registers a multi-tenant application, and/or registers multiple service principals associated to the application. Perform similar steps to what is listed above:

- GET ~/servicePrincipals/{id}
- Find passwordCredentials and keyCredentials in the response, record all old keyIds
- Remove all old password and key credentials. Use:
  
  ```
  POST ~/servicePrincipals/{id}/removePassword and POST ~/servicePrincipals/{id}/removeKey for this, respectively.
  ```

### Remediate affected Service Principal resources

Remediate KeyVault secrets that the Service Principal has access to by rotating them, in the following priority:

- Secrets directly exposed with GetSecret calls.
- The rest of the secrets in exposed KeyVaults.
- The rest of the secrets across exposed subscriptions.

For more information, see [Interactively removing and rolling over the certificates and secrets of a Service Principal or Application](https://github.com/microsoft/azureadtoolkit#interactively-removing-and-rolling-over-the-certificates-and-secrets-of-a-service-principal-or-application).

For Azure AD SecOps guidance on applications, see [Azure Active Directory security operations guide for Applications](/azure/active-directory/fundamentals/security-operations-applications).

In order of priority, this scenario would be:

- Update Graph PowerShell cmdlets (Add/Remove ApplicationKey + ApplicationPassword) doc to include examples for credential roll-over.
- Add custom cmdlets to Graph PowerShell that simplifies this scenario.

### Disable or delete malicious applications

An application can either be disabled or deleted. To disable the application, under **Enabled for users to sign in**, move the toggle to **No**.

[image] 

You can delete the application, either temporarily or permanently, in the portal or through the Graph API. When you soft delete, the application can be recovered up to 30 days after deletion.

```
DELETE /applications/{id}
```

To permanently delete the application, use this Graph API call:

```
DELETE /directory/deletedItems/{id}
```

If you disable or if you soft delete the application, set up monitoring in Azure AD Audit logs to learn if the state changes back to enabled or recovered.

**Logging for enabled:**

- **Service** - Core Directory
- **Activity Type** - Update Service Principle
- **Category** - Application Management
- **Initiated by (actor)** - UPN of actor
- **Targets** - App ID and Display Name
- **Modified Properties** - Property Name = account enabled, new value = true

**Logging for recovered:**

- **Service** - Core Directory
- **Activity Type** - Add Service Principle
- **Category** - Application Management
- **Initiated by (actor)** - UPN of actor
- **Targets** - App ID and Display Name
- **Modified Properties** - Property name = account enabled, new value = true

### Implement Identity Protection for workload identities

When risk detection indicates unusual sign-in properties or patterns, as well as unusual addition of credentials to an OAuth App, that may be an indicator of compromise. The detection baselines sign-in behavior between 2 and 60 days, and fires if one or more of the following unfamiliar properties occur during a subsequent sign-in:

- IP address / ASN
- Target resource
- User agent
- Hosting/non-hosting IP change
- IP country
- Credential type

When this detection is fired, the account is marked as high risk because this can indicate account takeover for the subject application. Note that the legitimate changes to an application’s configuration will sometimes trigger this detection. 

For more information, see [Securing workload identities with Identity Protection](/azure/active-directory/identity-protection/concept-workload-identity-risk).

These alerts appear in the Identity Protection portal and can be exported into SIEM tools through the [Identity Protection APIs](/graph/api/resources/identityprotection-overview?view=graph-rest-beta&preserve-view=true).

[image]

### Conditional Access for risky workload identities

Conditional Access allows you to block access for specific accounts that you designate when Identity Protection marks them as “at risk.” Note that the enforcement through Conditional Access is currently limited to single-tenant applications only.

[image]

- AuthN strengths - when one elevates into Cloud Admin role -> require FIDO only.
- Move the identified SPs to an AU, restrict access to this AU, and then cycle the credentials.

For more information, see [Conditional Access for workload identities](/azure/active-directory/conditional-access/workload-identity).

## Additional incident response playbooks

Examine guidance for identifying and investigating these additional types of attacks:

- [Phishing](incident-response-playbook-phishing.md)
- [Password spray](incident-response-playbook-password-spray.md)
- [App consent](incident-response-playbook-app-consent.md)
- [Microsoft DART ransomware approach and best practices](incident-response-playbook-dart-ransomware-approach.md)

## Incident response resources

- [Overview](incident-response-overview.md) for Microsoft security products and resources for new-to-role and experienced analysts
- [Planning](incident-response-planning.md) for your Security Operations Center (SOC)
- [Process](incident-response-process.md) for incident response process recommendations and best practices
- [Microsoft 365 Defender](/microsoft-365/security/defender/incidents-overview) incident response
- [Microsoft Defender for Cloud (Azure)](/azure/defender-for-cloud/managing-and-responding-alerts)
- [Microsoft Sentinel](/azure/sentinel/investigate-cases) incident response
- [Azure AD Identity Protection risks](/azure/active-directory/identity-protection/concept-identity-protection-risks)
- [Azure AD SecOps introduction](/azure/active-directory/fundamentals/security-operations-introduction)
- [Configure how users consent to applications](/azure/active-directory/manage-apps/configure-user-consent)
- [Configure the admin consent workflow](/azure/active-directory/manage-apps/configure-admin-consent-workflow)