---
title: How to Use Zero Trust Assessment for Your Tenant
description: Run an automated Zero Trust Assessment to evaluate your tenant's security configuration. Learn how to install, connect, and review results for improved security.

ms.service: security
ms.subservice: zero-trust
ms.topic: overview
ms.date: 10/10/2025

author: HULKsmashGithub
ms.author: jayrusso
manager: dougeby
ms.reviewer: joflore

ms.custom: sfi-ga-nochange
---
# Get started with the Zero Trust Assessment

The Zero Trust Assessment checks your tenant configuration and recommends ways to improve security.

:::image type="content" source="media/sample-test.png" alt-text="Screenshot of a sample test from the Zero Trust Assessment tool." lightbox="media/sample-test.png":::

## Prerequisites

- PowerShell 7. To install it, see [Install PowerShell on Windows, Linux, and macOS](/powershell/scripting/install/installing-powershell).
- To connect and consent to the required permissions the first time, you need to be a [Global Administrator](/entra/identity/role-based-access-control/permissions-reference#global-administrator). 
   - Subsequent runs can use the [Global Reader](/entra/identity/role-based-access-control/permissions-reference#global-reader) role.

## Install the PowerShell modules

Follow these steps to install or update the assessment and connect to Microsoft Graph and your tenant:

1. Open a new PowerShell 7 window 
1. Run the following command to install the `ZeroTrustAssessmentV2` module:

   ```powershell
   Install-Module ZeroTrustAssessmentV2 -Scope CurrentUser
   ```

1. Run the following command to install the `Az.Accounts` module:

   ```powershell
   Install-Module Az.Accounts -Scope CurrentUser
   ```

### Update the modules

If you've already installed the module in the past you can update the modules to the latest version using the following:

   ```powershell
   Update-Module ZeroTrustAssessmentV2 -Force -Scope CurrentUser
   Update-Module Az.Accounts -Force -Scope CurrentUser
   ```

## Connect to Microsoft Graph and Microsoft Azure

To run the Zero Trust Assessment module, connect to Microsoft Graph and Microsoft Azure. The Zero Trust Assessment module connects to Microsoft Graph first, then to Microsoft Azure.

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
- [Read, update, and delete all eligible role assignments for your company's directory](#why-is-the-roleeligibilityschedulereadwritedirectory-permission-requested-for-a-read-only-report)
- Read role management data for all Azure Role-Based Access Control (RBAC) providers
- Read all users' authentication methods
- View users' basic profile
- Read Microsoft Intune apps
- Read Microsoft Intune device configuration and policies
- Read Microsoft Intune RBAC settings
- Read Microsoft Intune configuration
- Maintain existing access to data

> [!NOTE]
> The consent prompt appears only if the Microsoft Graph PowerShell app doesn't already have these permissions. The next time you connect, you won't need to consent to the permissions again.

### Sign in to Microsoft Graph 

1. Sign in to Microsoft Graph as a Global Administrator.
1. Select **Accept**.   

### Sign in to Microsoft Azure

A second window opens for the Microsoft Azure sign-in. When you're prompted, sign in to Microsoft Azure as a Global Administrator.

The Microsoft Azure sign-in is required to check for the export of audit and sign-in logs. If you don't have Microsoft Azure, close the window without signing in and ignore the warning. The assessment skips the test that relies on Microsoft Azure.

If you have multiple subscriptions, select a tenant and a subscription when prompted.

:::image type="content" source="media/subscription-options.png" alt-text="Screenshot of the Azure subscription selection options in the PowerShell 7 console.":::   

## Run the assessment

The Zero Trust Assessment is read-only. It runs and stores all data locally on the desktop. It's a good practice to store the assessment report securely and delete the generated folder and its contents from the local drive once the assessment is complete.

After you provide Global Administrator consent to the permissions in the first run, subsequent runs can be performed as a Global Reader.

To run the assessment, use this command:

   ```powershell
   Invoke-ZtAssessment
   ```

The assessment saves the results in the current working folder `.\ZeroTrustReport\ZeroTrustAssessmentReport.html`. After the assessment completes, the report opens automatically in the default browser.

Use the `-Path` parameter to provide a custom location to store the assessment report. For example, the following command saves the report in the folder `C:/MyAssessment01/ZeroTrustAssessmentReport.html`:

   ```powershell
   Invoke-ZtAssessment --Path C:/MyAssessment01
   ```

> [!TIP]
> For large tenants, the Zero Trust Assessment might take more than 24 hours to run. Don't stop the assessment while it's running, even if the assessment logs warnings and errors.

## Review assessment results

After the assessment runs, the report opens the **Overview** tab in your default browser. The **Overview** tab shows key Zero Trust-related information about the tenant.

:::image type="content" source="media/results-overview.png" alt-text="Screenshot of assessment results on the Overview tab." lightbox="media/results-overview.png":::

The **Identity** and **Devices** tabs show a list of results from the tests run against the tenant. The results show the **Risk** and result **Status** of each test.

:::image type="content" source="media/results-identity.png" alt-text="Screenshot of assessment results on the Identity tab." lightbox="media/results-identity.png":::   

To see more details about a test, select a result. The details describe what was tested and list recommended remediation actions to address the tenant configuration.

:::image type="content" source="media/results-details.png" alt-text="Screenshot of the detail of a test result that includes what was tested and remediation actions." lightbox="media/results-details.png":::   

## Remove the Zero Trust Assessment module

To remove the Zero Trust Assessment module: 

1. Remove the PowerShell module.
1. Remove the app registration and consent.
1. Delete the folder that the Zero Trust Assessment module created.

## FAQs

### Why is the RoleEligibilitySchedule.ReadWrite.Directory permission requested for a read-only report?

The [List roleAssignmentScheduleRequests](/graph/api/rbacapplication-list-roleassignmentschedulerequests) Graph API call requires the `RoleEligibilitySchedule.ReadWrite.Directory` permission. To avoid making changes, run this report as a Global Reader.

### How can I know what the script does?

The code for this assessment is open source. Review it at `https://github.com/microsoft/zerotrustassessment/tree/psnext/src/powershell`.

### Why did I get the exception error, "The type initializer for 'DuckDB.NET.Data.DuckDBConnectionStringBuilder' threw an exception."?

On a new installation of Windows, you might see the following error:

> The type initializer for 'DuckDB.NET.Data.DuckDBConnectionStringBuilder' threw an exception.
> Inner exception: Unable to load DLL 'duckdb' or one of its dependencies: The specified module could not be found. (0x8007007E)
> Inner exception type: DllNotFoundException

This error occurs because you're running on a system that doesn't include Microsoft Visual C++ 2015-2022 Redistributable (x64) - Microsoft.VCRedist.2015+.x64. VCRedist usually installs when you install Microsoft products such as Microsoft Office or Microsoft Entra Connect Sync. If you're using a new device, you might need to install this component manually. See [Latest Microsoft Visual C++ Redistributable version](/cpp/windows/latest-supported-vc-redist).

### How do I get support?

Raise support issues on the [Zero Trust Assessment GitHub repo](https://github.com/microsoft/zerotrustassessment/issues).

## Related content

- [Zero Trust assessment rubric](reference-zero-trust-assessment-rubric.md)
- [Configure Microsoft Entra for increased security](/entra/fundamentals/configure-security) 
- [Configure Microsoft Intune for increased security](/intune/intune-service/protect/zero-trust-configure-security)