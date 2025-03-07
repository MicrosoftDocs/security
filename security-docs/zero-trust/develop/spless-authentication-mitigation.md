---
title: SP-Less Authentication Mitigation
description: Learn about the mitigation steps tenant administrators should perform for SP-less authentication behavior deprecation including verifying access, creating an enterprise application, and verifying tokens.
author: shirlingxu
ms.author: xushirling
ms.topic: conceptual
ms.date: 03/03/2025
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
---

Microsoft Entra ID will no longer support SP-less authentication behavior by **March 2026**. In this article, you'll learn how to take action for the SP-less authentication behavior deprecation as a tenant administrator, 
including verifying access, creating an enterprise application, and verifying tokens.

# Mitigation Steps:

## Verify Access:
First, verify that access by the named application(s) to the resource(s) listed is necessary. The application’s sign-in activity can be reviewed by the resource tenant’s administrator via [sign-in logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins). In SP-less 
authentication, the Service principal ID (aka client ID) of an application making an SP-Less auth is shown as “00000000-0000-0000-0000-000000000000” in the sign-in logs of the resource/target tenant.  

### Using Sign-In Logs to Find SP-Less Applications:
1. Navigate to the [Entra Portal](https://entra.microsoft.com/#home).
2. On the left navigation panel, go to **Identity** > **Show more...** > **Monitoring & health** > **Sign-in logs**.
3. Go to the **Service principal sign-ins** tab.
4. Filter by **Service principal ID**, and enter “00000000-0000-0000-0000-000000000000” in the input field.
5. Change the Date sorting to be **Custom time interval**, and set it to 30 days.
6. Click on a log to view the details, and navigate to the **Application ID** in the side panel to find the Client Application ID for the next step.

## Create Enterprise Application:
Then, as a resource tenant administrator, [create an enterprise application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/create-service-principal-cross-tenant?pivots=msgraph-powershell) in the resource tenant for each of the named applications. The resource tenant administrator must
register the application using the Client App ID noted in the email received or through the method above, also available from sign-in logs.

## Verify Tokens:
Finally, the administrator of the resource tenant should verify that the tokens issued to the application are no longer SP-less. This can verified in sign-in logs. The Service principal ID should appear with a unique 
numerical, non-zero, GUID in the format “########-####-####-####-############.”

# FAQ:

## What is happening?
Entra ID will block authentication for multi-tenant applications that are currently able to authenticate without an enterprise application registration in tenants.  This behavior has already been blocked for most resources, but we are now addressing a few remaining exceptions. This scenario is also known as Service-Principal-Less or “SP-Less Authentication.” This is a preventive security measure. SP-less authentication issues tokens without permissions and without an object identifier (object ID). 

## Why are we making these changes?
We are deprecating SP-less authentication behavior by making “requireClientServicePrincipal” a requirement for all applications in order to improve our “Security by default” 
([See authentication behaviors](https://learn.microsoft.com/en-us/graph/api/resources/authenticationbehaviors?view=graph-rest-beta&preserve-view=true)).  SP-less 
authentication can be abused if the resource applications (i.e. APIs) perform incomplete validations.  Microsoft has verified validations for its resource applications. However, with this action, the risk of this gap re-appearing in future versions or being exploited in third-party resources outside Microsoft’s control is minimized. 

Additionally, by enforcing the requirement that applications must be registered in every tenant where they authenticate, we reinforce tenant administrator’s governance of all access, including the ability to write conditional access policies for these applications. 

## When do you need to take action by? 
You must act **before March 1, 2026**, to avoid partial authentication failure of applications. 


