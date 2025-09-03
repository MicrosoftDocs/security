---
title: Get started with the Zero Trust Assessment?
description: DESCRIPTION

ms.service: security
ms.subservice: zero-trust
ms.topic: overview
ms.date: 07/01/2025

author: HULKsmashGithub
ms.author: jayrusso
manager: dougeby
ms.reviewer: 
---
# Get started with the Zero Trust Assessment

As the security threat landscape evolves, Microsoft responds and reevaluates default tenant security settings. Microsoft uses insights, experience, and learnings to update these settings over time.

Microsoft publishes guidance on how to [Configure Microsoft Entra for increased security](configure-security.md). This guidance helps you act quickly, reevaluate existing tenant security settings, and make changes ahead of product updates.

Manually checking a tenant's configuration against published guidance can be time consuming and error prone.   

Use the Zero Trust Assessment module to run an automated security assessment. It checks your tenant configuration and recommends ways to improve security.

> [!TIP]
> This initial release works only with Microsoft Entra.

## Prerequisites

- PowerShell 7. To install it, see [Install PowerShell on Windows, Linux, and macOS](/powershell/scripting/install/installing-powershell?view=powershell-7.4).
- Global Administrator role

> [!NOTE]
> You need to be a Global Administrator to connect to Microsoft Graph and consent to permissions.   
> You can run the Zero Trust Assessment with the Global Reader role.

## Install the PowerShell modules

Follow these steps to install the assessment and connect to Microsoft Graph and your tenant:

### Open PowerShell 7

Launch PowerShell 7.

### Install the Zero Trust Assessment module

1. Run this command to install the `ZeroTrustAssessmentV2` module:

```powershell
Install-Module ZeroTrustAssessmentV2 -Scope CurrentUser
```

2. When you're prompted to install modules from an untrusted repository, type `A`, and then press **Enter** to select **Yes to All**.


### Install the Az.Accounts module

Run this command to install the `Az.Accounts` module:

```powershell
Install-Module Az.Accounts -Scope CurrentUser
```

### Update the modules

Run these commands to update the modules to the latest versions:

```powershell
Update-Module ZeroTrustAssessmentV2 -Force -Scope CurrentUser
Update-Module Az.Accounts -Force -Scope CurrentUser
```

## Connect to Microsoft Graph and Microsoft Azure

To run the Zero Trust Assessment module, connect to Microsoft Graph and, optionally, Microsoft Azure. The Zero Trust Assessment module connects to Microsoft Graph first, then to Microsoft Azure.

Run this command to connect to Microsoft Graph:

```powershell
Connect-ZtAssessment
```

When you connect using Microsoft Graph PowerShell, it requests these permissions:  

- Read audit log data
- Read cross-tenant basic information
- Read directory data
- Read Azure AD recommendations
- Read identity risk event information
- Read identity risky user information
- Read your organization's policies
- Read your organization's Conditional Access policies
- Read consent and permission grant policies
- Read privileged access to Azure AD
- Read all usage reports
- Read all eligible role assignments for your company's directory
- Read, update, and delete all eligible role assignments for your company's directory
- Read role management data for all Azure Role-Based Access Control (RBAC) providers
- Read all users' authentication methods
- View users' basic profile
- Maintain existing access to data

### Sign in to Microsoft Graph 

1. Sign in to Microsoft Graph as a Global Administrator.
1. Select **Consent on behalf of your organization** to accept the requested permissions.
1. Select **Accept**.   

> [!NOTE]
> The consent prompt appears only if the Microsoft Graph PowerShell app doesn't already have these permissions. The next time you connect, you don't need to consent to the permissions again.

:::image type="content" source="media/how-to-zero-trust-assessment/graph-permissions.png" alt-text="Screenshot of the Microsoft Graph permissions requested list.":::   

### Sign in to Microsoft Azure

A second window opens for the Microsoft Azure sign-in. When prompted, sign in to Microsoft Azure as a Global Administrator.

The Microsoft Azure sign-in is required to check for the export of audit and sign-in logs. If you don't have Microsoft Azure, close the window without signing in, and ignore the warning. The assessment skips the test that relies on Microsoft Azure.

:::image type="content" source="media/how-to-zero-trust-assessment/azure-sign-in.png" alt-text="Screenshot of the Microsoft Azure sign in page.":::   

If you have multiple subscriptions, select a tenant and a subscription when prompted.

:::image type="content" source="media/how-to-zero-trust-assessment/subscription-options.png" alt-text="Screenshot of the Azure subscription selection options in the PowerShell 7 console.":::   

## Run the assessment

The Zero Trust Assessment is read-only. It runs and stores all data locally on the desktop. It's a good practice to store the assessment report securely and delete the generated folder and its contents from the local drive once the assessment is complete.

After providing Global Administrator consent to the permissions, you can run the assessment as a Global Reader.

Use this command to run the assessment:

```powershell
Invoke-ZtAssessment
```

The assessment saves the results in the current working folder `.\ZeroTrustReport\ZeroTrustAssessmentReport.html`. After the assessment completes, the report automatically opens in the default browser.

You can use the `-Path` parameter to provide a custom location to store the assessment report. For example, the following command saves the report in the folder `C:/MyAssessment01/ZeroTrustAssessmentReport.html`:

```powershell
Invoke-ZtAssessment --Path C:/MyAssessment01
```

> [!NOTE]
> For large tenants, the Zero Trust Assessment might take more than 24 hours to run. Don't abort the assessment while it's running, even if the assessment logs warnings and errors.

## Review assessment results

After the assessment runs, the report opens the **Overview** tab in your default browser. The **Overview** tab shows key Zero Trust-related information about the tenant.

:::image type="content" source="media/how-to-zero-trust-assessment/results-overview.png" alt-text="Screenshot of assessment results on the Overview tab." lightbox="media/how-to-zero-trust-assessment/results-overview-expanded.png":::

The **Identity** tab shows a list of results from the checks run against the tenant. The results show the **Risk** and test result **Status** of each check.

:::image type="content" source="media/how-to-zero-trust-assessment/results-identity.png" alt-text="Screenshot of assessment results on the Identity tab." lightbox="media/how-to-zero-trust-assessment/results-identity-expanded.png":::   

To see more details, select a result. The details describe what was checked and list recommended remediation actions to address the tenant configuration.

:::image type="content" source="media/how-to-zero-trust-assessment/results-details-expanded.png" alt-text="Screenshot of the detail of a test result that includes what was checked and remediation actions." lightbox="media/how-to-zero-trust-assessment/results-details-expanded.png":::   

## Report issues

If you run into any issues or have questions about the results, report them to the account contact who suggested that you run the assessment. If an issue occurs, export a troubleshooting log by following these steps:

1. Create an export package by running this command in the same session where you ran the assessment. Set the date to match the date of your run.

```powershell
New-PSFSupportPackage -Path C:\AssessmentLog_2025_01_01 -Force
```

2. Zip the **AssessmentLog** folder.
1. Zip the folder created by Invoke-ZtAssessment (the default is `ZeroTrustAssessment`). 
1. Share both folders with your contact at Microsoft.

## Remove the Zero Trust Assessment module

To remove the Zero Trust Assessment module, follow these steps: 
1. Remove the PowerShell module. 
1. Remove the app registration and consent. 
1. Delete the folder created by the Zero Trust Assessment module.

## FAQs

For frequently asked questions, see [Zero Trust Assessment FAQ](faq-zero-trust-assessment.yml).

## Related content