---
title: Password spray investigation
description: Learn how to identify and investigate password spray attacks, protect data, and minimize further risks.
keywords: password spray, password, investigation, attack, email, microsoft threat protection, microsoft 365, search, security, query, telemetry, security events, antivirus, firewall, Microsoft 365 Defender
search.product: DART
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
  - NOCSH
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
  - zerotrust-solution
  - msftsolution-secops
ms.topic: article
ms.subservice:: m365d
ms.custom: cxdef-zt-ransomware, has-azure-ad-ps-ref, azure-ad-ref-level-one-done
---

# Password spray investigation

This article provides guidance on identifying and investigating password spray attacks within your organization and take the required remedial action to protect information and minimize further risks.

This article contains the following sections:

- **Prerequisites:** Covers the specific requirements you need to complete before starting the investigation. For example, logging that should be turned on, roles and permissions required, among others.
- **Workflow:** Shows the logical flow that you should follow to perform this investigation.
- **Checklist:** Contains a list of tasks for each of the steps in the flow chart. This checklist can be helpful in highly regulated environments to verify what you have done or simply as a quality gate for yourself.
- **Investigation steps:** Includes a detailed step-by-step guidance for this specific investigation.
- **Recovery:** Contains high-level steps on how to recover/mitigate from a password spray attack.
- **References:** Contains more reading and reference materials.

## Prerequisites

Before starting the investigation, make sure you have completed the setup for logs and alerts and other system requirements.

For Microsoft Entra monitoring, follow our recommendations and guidance in our [Microsoft Entra SecOps Guide](/azure/active-directory/fundamentals/security-operations-introduction).

### Set up [ADFS logging](/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-logging)

#### Event logging on ADFS 2016

By default, the Microsoft Active Directory Federation Services (ADFS) in Windows Server 2016 has a basic level of auditing enabled. With basic auditing, administrators can see five or less events for a single request. Set logging to the highest level and send the AD FS (& security) logs to a SIEM to correlate with AD authentication and Microsoft Entra ID.

To view the current auditing level, you can use this PowerShell command:

```powershell
Get-AdfsProperties
```

![adfs](./media/incident-response-playbook-password-spray/adfsproperties.png)

This table contains the auditing levels that are available.

|Audit level|PowerShell syntax|Description|
|---|---|---|
|None|`Set-AdfsProperties -AuditLevel None`|Auditing is disabled and no events will be logged|
|Basic (Default)|`Set-AdfsProperties -AuditLevel Basic`|No more than five events will be logged for a single request|
|Verbose|`Set-AdfsProperties -AuditLevel Verbose`|All events will be logged. This level will log a significant amount of information per request.|

To raise or lower the auditing level, use this PowerShell command:

```powershell
Set-AdfsProperties -AuditLevel <None | Basic | Verbose>
```

### Set up ADFS 2012 R2/2016/2019 security logging

1. Click **Start**, navigate to **Programs &gt; Administrative Tools**, and then click **Local Security Policy**.
2. Navigate to the **Security Settings\\Local Policies\\User Rights Management** folder, and then double-click **Generate security audits**.
3. On the **Local Security Setting** tab, verify that the ADFS service account is listed. If it isn't present, click **Add User** or **Group** and add it to the list, and then click **OK**.
4. To enable auditing, open a command prompt with elevated privileges and run the following command:

    ```DOS
    auditpol.exe /set /subcategory:"Application Generated" /failure:enable /success:enable
    ```

5. Close **Local Security Policy**.
6. Next, open the ADFS Management snap-in, click **Start**, navigate to **Programs > Administrative Tools**, and then click **ADFS Management**.
7. In the **Actions** pane, click **Edit Federation Service Properties**.
8. In the **Federation Service Properties** dialog box, click the **Events** tab.
9. Select the **Success audits** and **Failure audits** check boxes.
10. Click **OK** to finish and save the configuration.

<a name='install-azure-ad-connect-health-for-adfs'></a>

### Install Microsoft Entra Connect Health for ADFS

The Microsoft Entra Connect Health for ADFS agent allows you to have greater visibility into your federation environment. It provides you with several preconfigured dashboards like usage, performance monitoring and risky IP reports.

To install ADFS Connect Health, go through the [requirements for using Microsoft Entra Connect Health](/azure/active-directory/hybrid/how-to-connect-health-agent-install#requirements), and then install the [Azure ADFS Connect Health Agent](https://go.microsoft.com/fwlink/?LinkID=518973).

### Set up risky IP alerts using the [ADFS Risky IP Report Workbook](/azure/active-directory/hybrid/how-to-connect-health-adfs-risky-ip-workbook#:~:text=The%20risky%20IP%20workbook%20analyzes%20data%20from%20ADFSSignInLogs,on%20designated%20error%20thresholds%20and%20detection%20window%20length.)

After Microsoft Entra Connect Health for ADFS is configured, you should monitor and set up alerting using the ADFS Risky IP report workbook and Azure Monitor. The benefits of using this report are:

- Detection of IP addresses that exceed a threshold of failed password-based logins.
- Supports failed logins due to bad password or due to extranet lockout state.
- Supports enabling alerts through Azure Alerts.
- Customizable threshold settings that match with the security policy of an organization.
- Customizable queries and expanded visualizations for further analysis.
- Expanded functionality from the previous Risky IP report, which will be deprecated after January 24, 2022.

### Set up SIEM tool alerts on Microsoft Sentinel

To set up SIEM tool alerts, go through the tutorial on [out of the box alerting](/azure/sentinel/tutorial-detect-threats-built-in).

### SIEM integration into Microsoft Defender for Cloud Apps

Connect the Security Information and Event Management (SIEM) tool to Microsoft Defender for Cloud Apps, which currently supports Micro Focus ArcSight and generic common event format (CEF).

For more information, see [Generic SIEM Integration](/cloud-app-security/siem).

### SIEM integration with Graph API

You can connect SIEM with the Microsoft Graph Security API by using any of the following options:

- **Directly using the supported integration options** – Refer to the list of supported integration options like writing code to directly connect your application to derive rich insights. Use samples to get started.
- **Use native integrations and connectors built by Microsoft partners** – Refer to the Microsoft Graph Security API partner solutions to use these integrations.
- **Use connectors built by Microsoft** – Refer to the list of connectors that you can use to connect with the API through various solutions for Security Incident and Event Management (SIEM), Security Response and Orchestration (SOAR), Incident Tracking and Service Management (ITSM), reporting, and so on.

For more information, see [security solution integrations using the Microsoft Graph Security API](/graph/security-integration#list-of-connectors-from-microsoft).

### Using Splunk

You can also use the Splunk platform to set up alerts.

- Watch this video tutorial on how to create [Splunk alerts](https://www.splunk.com/en_us/resources/videos/splunk-tutorial-creating-alerts-in-splunk-enterprise-6.html)
- For more information, see [Splunk alerting manual](https://docs.splunk.com/Documentation/Splunk/8.0.4/Alert/AlertWorkflowOverview)

## Workflow

[![Password spray investigation workflow](./media/incident-response-playbook-password-spray/Pwdsprayflow.png)]

You can also:

- Download the password spray and other incident response playbook workflows as a [PDF](https://download.microsoft.com/download/2/9/a/29a32dc4-d126-42af-a825-ffb944135a50/Incident-Response-Playbook-Workflows.pdf).
- Download the password spray and other incident response playbook workflows as a [Visio file](https://download.microsoft.com/download/2/9/a/29a32dc4-d126-42af-a825-ffb944135a50/Incident-Response-Playbook-Workflows.vsdx).

## Checklist

### Investigation triggers

- Received a trigger from SIEM, firewall logs, or Microsoft Entra ID
- Microsoft Entra ID Protection Password Spray feature or Risky IP
- Large number of failed sign-ins (Event ID 411)
- Spike in Microsoft Entra Connect Health for ADFS
- Another security incident (for example, phishing)
- Unexplained activity, such as a sign-in from unfamiliar location or a user getting unexpected MFA prompts

### Investigation

- What is being alerted?
- Can you confirm this is a password spray?
- Determine timeline for attack.
- Determine the IP address(es) of the attack.
- Filter on successful sign-ins for this time period and IP address, including successful password but failed MFA
- Check [MFA reporting](/azure/active-directory/authentication/howto-mfa-reporting)
- Is there anything out of the ordinary on the account, such as new device, new OS, new IP address used? Use Defender for Cloud Apps or Azure Information Protection to detect suspicious activity.
- Inform local authorities/third parties for assistance.
- If you suspect a compromise, check for data exfiltration.
- Check associated account for suspicious behavior and look to correlate to other possible accounts and services as well as other malicious IP addresses.
- Check accounts of anyone working in the same office/delegated access - password hygiene (make sure they aren't using the same password as the compromised account)
- Run ADFS help

#### Mitigations

Check the [References](#references) section for guidance on how to enable features.

- [Block IP address of attacker](/azure/active-directory/conditional-access/block-legacy-authentication) (keep an eye out for changes to another IP address)
- Changed user's password of suspected compromise
- [Enable ADFS Extranet Lockout](/windows-server/identity/ad-fs/operations/configure-ad-fs-extranet-soft-lockout-protection)
- [Disabled Legacy authentication](/azure/active-directory/conditional-access/block-legacy-authentication)
- [Enabled Azure Identity Protection](/azure/active-directory/identity-protection/howto-identity-protection-configure-risk-policies) (sign in and user risk policies)
- [Enabled MFA](/azure/active-directory/authentication/tutorial-enable-azure-mfa) (if not already)
- [Enabled Password Protection](/azure/active-directory/authentication/howto-password-ban-bad-on-premises-operations)
- [Deploy Microsoft Entra Connect Health for ADFS](/azure/active-directory/hybrid/how-to-connect-health-agent-install#installing-the-azure-ad-connect-health-agent-for-ad-fs) (if not already)

#### Recovery

- Tag bad IP address in Defender for Cloud Apps, SIEM, ADFS and Microsoft Entra ID
- Check for other forms of mailbox persistence such as forwarding rules or other delegations added
- [MFA as primary authentication](/windows-server/identity/ad-fs/operations/configure-ad-fs-and-azure-mfa)
- [Configure SIEM integrations with Cloud](/microsoft-365/security/office-365-security/siem-server-integration)
- Configure Alerting - Identity Protection, ADFS Health Connect, SIEM and Defender for Cloud Apps
- Lessons Learnt (include key stakeholders, third parties, communication teams)
- Security posture review/improvements
- [Plan to run regular attack simulators](/microsoft-365/security/office-365-security/attack-simulator)

You can also download the password spray and other incident playbook checklists as an [Excel file](https://download.microsoft.com/download/2/9/a/29a32dc4-d126-42af-a825-ffb944135a50/Incident-Response-Playbook-Checklists.xlsx).

## Investigation steps

### Password spray incident response

Let's understand a few password spray attack techniques before proceeding with the investigation.

**Password compromise:** An attacker has successfully guessed the user's password but hasn't been able to access the account due to other controls such as multifactor authentication (MFA).

**Account compromise:** An attacker has successfully guessed the user's password and has successfully gained access to the account.

### Environment discovery

#### Identify authentication type

As the first step, you need to check what authentication type is used for a tenant/verified domain that you're investigating.

To obtain the authentication status for a specific domain name, use the [Get-MgDomain](/powershell/module/microsoft.graph.identity.directorymanagement/get-mgdomain?view=graph-powershell-1.0&preserve-view=true) PowerShell command. Here's an example:

```powershell
Connect-MgGraph
Get-MgDomain -Name "contoso.com"
```

### Is the authentication federated or managed?

If the authentication is federated, then successful sign-ins will be stored in Microsoft Entra ID. The failed sign-ins will be in their Identity Provider (IDP). For more information, see [ADFS troubleshooting and event logging](/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-logging).

If the authentication type is managed, (Cloud only, password hash sync (PHS) or pass-through authentication (PTA)), then successful and failed sign-ins will be stored in the Microsoft Entra sign-in logs.

>[!Note]
>The [Staged Rollout](/azure/active-directory/hybrid/how-to-connect-staged-rollout) feature allows the tenant domain name to be federated but specific users to be managed. Determine if any users are members of this group.
>

<a name='is-azure-ad-connect-health-enabled-for-adfs'></a>

### Is Microsoft Entra Connect Health enabled for ADFS?

- The [RiskyIP report](/azure/active-directory/hybrid/how-to-connect-health-adfs-risky-ip) will provide suspect IPs and date/time. Notifications should be enabled.
- Also check the [federated sign-ins investigation from the Phishing playbook](incident-response-playbook-phishing.md#federated-scenario)

### Is the advanced logging enabled in ADFS?

- This is a requirement for ADFS Connect Health but it can be enabled independently
- See how to [enable ADFS Health Connect](/azure/active-directory/hybrid/how-to-connect-health-agent-install#installing-the-azure-ad-connect-health-agent-for-ad-fs))
- Also check the [Federated sign-ins investigation from the Phishing playbook](incident-response-playbook-phishing.md#federated-scenario)

### Are the logs stored in SIEM?

To check whether you are storing and correlating logs in a Security Information and Event Management (SIEM) or in any other system, check the following:

- Log analytics- pre-built queries
- Sentinel- pre-built queries
- Splunk – pre-built queries
- Firewall logs
- UAL if > 30 days

<a name='understanding-azure-ad-and-mfa-reporting'></a>

### Understanding Microsoft Entra ID and MFA reporting

It is important that you understand the logs that you are seeing to be able to determine compromise. Below are our quick guides to understanding Microsoft Entra Sign-Ins and MFA reporting to help with this. Refer to these articles:

- [MFA reporting](</azure/active-directory/authentication/howto-mfa-reporting>)
- [Understanding Sign Ins](/azure/active-directory/reports-monitoring/concept-sign-ins)

### Incident triggers

An incident trigger is an event or a series of events that causes predefined alert to trigger. An example of this is the number of bad password attempts has gone above your predefined threshold. Below are further examples of triggers that can be alerted in password spray attacks and where these alerts are surfaced. Incident triggers include:

- Users
- IP
- User agent strings
- Date/time
- Anomalies
- Bad password attempts

    :::image type="content" source="./media/incident-response-playbook-password-spray/Badpwdattempt.jpg" alt-text="pwdattempts":::
    *Graph depicting number of bad password attempts*

Unusual spikes in activity are key indicators through Microsoft Entra Health Connect (assuming this is installed). Other indicators are:

- Alerting through SIEM shows a spike when you collate the logs.
- Larger than normal log size for ADFS failed sign-ins (this can be an alert in SIEM tool).
- Increased amounts of 342/411 event IDs – username or password is incorrect. Or 516 for extranet lockout.
- Hit failed authentication request threshold – Risky IP in Microsoft Entra ID or SIEM tool alert/both 342 and 411 errors (To be able to view this information, the advanced logging should be turned on.)

<a name='risky-ip-in-azure-ad-health-connect-portal'></a>

### Risky IP in Microsoft Entra Health Connect portal

Risky IP will alert when the customized threshold has been reached for bad passwords in an hour and bad password count in a day as well as extranet lockouts.

![Example of risky IP report data](./media/incident-response-playbook-password-spray/RiskyIPReport.jpg)

*Risky IP report data*

The details of failed attempts are available in the tabs **IP address** and **extranet lockouts**.

![ipaddresstable](./media/incident-response-playbook-password-spray/ipaddress1.png)

*IP address and extranet lockouts in the Risky IP report*

### Detect password spray in Azure Identity Protection

Azure Identity Protection is a Microsoft Entra ID P2 feature that has a password-spray detection risk alert and search feature that you can utilize to get additional information or set up automatic remediation.

:::image type="content" source="./media/incident-response-playbook-password-spray/Detectpwd.png" alt-text="Example of password spray attack":::

*Details of a password spray attack*

### Low and slow attack indicators

Low and slow attack indicators are those where thresholds for account lockout or bad passwords are not being hit. You can detect these indicators through:

- Failures in GAL order
- Failures with repetitive attributes (UA, target AppID, IP block/location)
- Timing – automated sprays tend to have a more regular time interval between attempts.

### Investigation and mitigation

>[!Note]
>You can perform investigation and mitigation simultaneously during sustained/ongoing attacks.
>

1. Turn advanced logging on ADFS if it is not already turned on.
2. Determine the date and time of start of the attack.
3. Determine the attacker IP address (might be multiple sources and multiple IP addresses) from the firewall, ADFS, SIEM or Microsoft Entra ID.
4. Once password spray confirmed, you might have to inform the local agencies (police, third parties, among others).
5. Collate and monitor the following Event IDs for ADFS:

    **ADFS 2012 R2**

    - Audit event 403 – user agent making the request
    - Audit event 411 – failed authentication requests
    - Audit event 516 – extranet lockout
    - Audit Event 342 – failed authentication requests
    - Audit Event 412 - Successful log in

6. To collect the *Audit Event 411 - failed authentication requests,* use the following [script](/samples/browse/?redirectedfrom=TechNet-Gallery):

    ```powershell
    PARAM ($PastDays = 1, $PastHours)
    #************************************************
    #ADFSBadCredsSearch.ps1
    #Version 1.0
    #Date: 6-20-2016
    #Author: Tim Springston [MSFT]
    #Description: This script will parse the ADFS server's (not proxy) security ADFS
    #for events which indicate an incorrectly entered username or password. The script can specify a
    #past period to search the log for and it defaults to the past 24 hours. Results >#will be placed into a CSV for
    #review of UPN, IP address of submitter, and timestamp.
    #************************************************
    cls
    if ($PastHours -gt 0)
    {$PastPeriod = (Get-Date).AddHours(-($PastHours))}
    else
    {$PastPeriod = (Get-Date).AddDays(-($PastDays))}
    $Outputfile = $Pwd.path + "\BadCredAttempts.csv"
    $CS = get-wmiobject -class win32_computersystem
    $Hostname = $CS.Name + '.' + $CS.Domain
    $Instances = @{}
    $OSVersion = gwmi win32_operatingsystem
    [int]$BN = $OSVersion.Buildnumber
    if ($BN -lt 9200){$ADFSLogName = "AD FS 2.0/Admin"}
    else {$ADFSLogName = "AD FS/Admin"}
    $Users = @()
    $IPAddresses = @()
    $Times = @()
    $AllInstances = @()
    Write-Host "Searching event log for bad credential events..."
    if ($BN -ge 9200) {Get-Winevent -FilterHashTable @{LogName= "Security"; >StartTime=$PastPeriod; ID=411} -ErrorAction SilentlyContinue | Where-Object{$_.Message -match "The user name or password is incorrect"} | % {
    $Instance = New-Object PSObject
    $UPN = $_.Properties[2].Value
    $UPN = $UPN.Split("-")[0]
    $IPAddress = $_.Properties[4].Value
    $Users += $UPN
    $IPAddresses += $IPAddress
    $Times += $_.TimeCreated
    add-member -inputobject $Instance -membertype noteproperty -name >"UserPrincipalName" -value $UPN
    add-member -inputobject $Instance -membertype noteproperty -name "IP Address" ->value $IPAddress
    add-member -inputobject $Instance -membertype noteproperty -name "Time" -value >($_.TimeCreated).ToString()
    $AllInstances += $Instance
    $Instance = $null
    }
    }
    $AllInstances | select * | Export-Csv -Path $Outputfile -append -force ->NoTypeInformation
    Write-Host "Data collection finished. The output file can be found at >$outputfile`."
    $AllInstances = $null
    ```

#### ADFS 2016/2019

Along with the above event IDs, collate the *Audit Event 1203 – Fresh Credential Validation Error*.

1. Collate all successful sign-ins for this time on ADFS (if federated). A quick sign-in and logout (at the same second) can be an indicator of a password being guessed successfully and being tried by the attacker.
2. Collate any Microsoft Entra successful or interrupted events for this time-period for both federated and managed scenarios.

<a name='monitor-and-collate-event-ids-from-azure-ad'></a>

### Monitor and collate Event IDs from Microsoft Entra ID

See how to find the [meaning of error logs](https://login.microsoftonline.com/error).

The following Event IDs from Microsoft Entra ID are relevant:

- 50057 - User account was disabled
- 50055 - Password expired
- 50072 - User prompted to provide MFA
- 50074 - MFA required
- 50079 - user needs to register security info
- 53003 - User blocked by Conditional Access
- 53004 - Cannot configure MFA due to suspicious activity
- 530032 - Blocked by Conditional Access on Security Policy
- Sign-In status Success, Failure, Interrupt

### Collate event IDs from Sentinel playbook

You can get all the Event IDs from the Sentinel Playbook that is available on [GitHub](https://github.com/Azure/Azure-Sentinel/blob/49fee965c9def6890b7e5f2ad96cc1a89d73db26/Detections/SigninLogs/SigninPasswordSpray.yaml).

### Isolate and confirm attack

Isolate the ADFS and Microsoft Entra successful and interrupted sign-in events. These are your accounts of interest.

Block the IP Address ADFS 2012R2 and above for federated authentication. Here's an example:

```powershell
Set-AdfsProperties -AddBannedIps "1.2.3.4", "::3", "1.2.3.4/16"
```

### **Collect ADFS logs**

Collect multiple event IDs within a time frame. Here's an example:

```powershell
Get-WinEvent -ProviderName 'ADFS' | Where-Object { $_.ID -eq '412' -or $_.ID -eq '411' -or $_.ID -eq '342' -or $_.ID -eq '516' -and $_.TimeCreated -gt ((Get-Date).AddHours(-"8")) }
```

<a name='collate-adfs-logs-in-azure-ad'></a>

### Collate ADFS logs in Microsoft Entra ID

Microsoft Entra Sign-In reports include ADFS sign-in activity when you use Microsoft Entra Connect Health. Filter sign-in logs by Token Issuer Type "Federated".

Here's an example PowerShell command to retrieve sign-in logs for a specific IP address:

```powershell
Get-AzureADIRSignInDetail -TenantId b446a536-cb76-4360-a8bb-6593cf4d9c7f -IpAddress 131.107.128.76
```

Also, search the Azure portal for time frame, IP address and successful and interrupted sign-in as shown in these images.

:::image type="content" source="./media/incident-response-playbook-password-spray/Selectingtimeframe.jpg" alt-text="timeframe":::

*Searching for sign-ins within a specific time frame*

:::image type="content" source="./media/incident-response-playbook-password-spray/Selectingipaddress.jpg" alt-text="ipaddress":::

*Searching for sign-ins on a specific IP address*

:::image type="content" source="./media/incident-response-playbook-password-spray/Selectingstatus.jpg" alt-text="status":::

*Searching for sign-ins based on the status*

You can then download this data as a *.csv* file for analysis. For more information, see [Sign-in activity reports in the Microsoft Entra admin center](/azure/active-directory/reports-monitoring/concept-sign-ins).

### Prioritize findings

It is important to be able to react to the most critical threat. This can be the attacker has successfully obtained access to an account and therefore can access/exfiltrate data. The attacker has the password but may not be able to access the account for example they have the password but are not passing the MFA challenge. Also, the attacker could not be guessing passwords correctly but continuing to try. During analysis, prioritize these findings:

- Successful sign-ins by known attacker IP address
- Interrupted sign-in by known attacker IP address
- Unsuccessful sign-ins by known attacker IP address
- Other unknown IP address successful sign-ins

### Check legacy authentication

Most attacks use legacy authentication. There are a number of ways to determine the protocol of the attack.

1. In Microsoft Entra ID, navigate to **Sign-Ins** and filter on **Client App.**
2. Select all the legacy authentication protocols that are listed.

    :::image type="content" source="./media/incident-response-playbook-password-spray/Legacyauthenticationchecks.jpg" alt-text="authenticationcheck":::

    *List of legacy protocols*

3. Or if you have an Azure workspace, you can use the pre-built legacy authentication workbook located in the Microsoft Entra admin center under **Monitoring and Workbooks**.

    :::image type="content" source="./media/incident-response-playbook-password-spray/authenticationbook.png" alt-text="workbook":::

    *Legacy authentication workbook*

<a name='block-ip-address-azure-ad-for-managed-scenario-phs-including-staging'></a>

### Block IP address Microsoft Entra ID for managed scenario (PHS including staging)

1. Navigate to **New named locations**.

    :::image type="content" source="./media/incident-response-playbook-password-spray/Namedlocation.jpg" alt-text="Example of a new named location":::

2. Create a CA policy to target all applications and block for this named location only.

### Has the user used this operating system, IP, ISP, device, or browser before?

If the user has not used them before and this activity is unusual, then flag the user and investigate all of their activities.

### Is the IP marked as "risky"?

Ensure you record successful passwords but failed multifactor authentication (MFA) responses, as this activity indicates that the attacker is getting the password but not passing MFA.
Set aside any account that appears to be a normal sign-in, for example, passed MFA, location and IP not out of the ordinary.

### MFA reporting

It is important to also check MFA logs as an attacker could have successfully guessed a password but be failing the MFA prompt. The Microsoft Entra multifactor authentication logs shows authentication details for events when a user is prompted for multifactor authentication. Check and make sure there are no large suspicious MFA logs in Microsoft Entra ID. For more information, see [how to use the sign-ins report to review Microsoft Entra multifactor authentication events](/azure/active-directory/authentication/howto-mfa-reporting).

### Additional checks

In Defender for Cloud Apps, investigate activities and file access of the compromised account. For more information, see:

- [Investigate compromise with Defender for Cloud Apps](/cloud-app-security/investigate)
- [Investigate anomalies with Defender for Cloud Apps](/cloud-app-security/investigate-anomaly-alerts)

Check whether the user has access to additional resources, such as virtual machines (VMs), domain account permissions, storage, among others.
If data has been breached, then you should inform additional agencies, such as the police.

## Immediate remedial actions

1. Change the password of any account that is suspected to have been breached or if the account password has been discovered. Additionally, block the user. Make sure you follow the guidelines for [revoking emergency access](/azure/active-directory/enterprise-users/users-revoke-access).
2. Mark any account that has been compromised as "*compromised*" in Azure Identity Protection.
3. Block the IP address of the attacker. Be cautious while performing this action as attackers can use legitimate VPNs and this could create more risk as they change IP addresses as well. If you are using Cloud Authentication, then block the IP address in Defender for Cloud Apps or Microsoft Entra ID. If federated, you need to block the IP address at the firewall level in front of the ADFS service.
4. [Block legacy](/azure/active-directory/conditional-access/block-legacy-authentication) authentication if it is being used (this action, however, could impact business).
5. [Enable MFA](/azure/active-directory/authentication/tutorial-enable-azure-mfa) if it is not already done.
6. [Enable Identity Protection](/azure/active-directory/identity-protection/howto-identity-protection-configure-risk-policies) for the user risk and sign-in risk
7. Check the data that has been compromised (emails, SharePoint, OneDrive, apps). See how to use the [activity filter in Defender for Cloud Apps](/cloud-app-security/activity-filters).
8. Maintain password hygiene. For more information, see [Microsoft Entra password protection](https://www.microsoft.com/research/publication/password-guidance/).
9. You can also refer to [ADFS Help](https://adfshelp.microsoft.com/TroubleshootingGuides/Workflow/a73d5843-9939-4c03-80a1-adcbbf3ccec8).

## Recovery

### Password protection

Implement password protection on Microsoft Entra ID and on-premises by enabling the custom-banned password lists. This configuration will prevent users from setting weak passwords or passwords associated with your organization:

:::image type="content" source="./media/incident-response-playbook-password-spray/Passwordprotection.jpg" alt-text="pwdprotection":::

*Enabling password protection*

For more information, see [how to defend against password spray attacks](https://www.microsoft.com/en-us/microsoft-365/blog/2018/03/05/azure-ad-and-adfs-best-practices-defending-against-password-spray-attacks/).

### Tagging IP address

Tag the IP addresses in Defender for Cloud Apps to receive alerts related to future use:

:::image type="content" source="./media/incident-response-playbook-password-spray/IPaddresstag.jpg" alt-text="Example of tagging an IP address":::

*Tagging IP addresses*

In Defender for Cloud Apps, "tag" IP address for the IP scope and set up an alert for this IP range for future reference and accelerated response.

:::image type="content" source="./media/incident-response-playbook-password-spray/ipaddressalert.png" alt-text="Example of setting up an IP address alert":::

*Setting alerts for a specific IP address*

### Configure alerts

Depending on your organization needs, you can configure alerts.

[Set up alerting in your SIEM tool](/microsoft-365/security/office-365-security/siem-server-integration) and look at improving logging gaps. Integrate ADFS, Microsoft Entra ID, Office 365 and Defender for Cloud Apps logging.

Configure the threshold and alerts in ADFS Health Connect and Risky IP portal.

:::image type="content" source="./media/incident-response-playbook-password-spray/thresholdsettings.png" alt-text="Example of configuring threshold settings":::

*Configure threshold settings*

![Example of configuring notifications](./media/incident-response-playbook-password-spray/configurenotifications.png)

*Configure notifications*

See how to [configure alerts in the Identity Protection portal](/azure/active-directory/identity-protection/howto-identity-protection-configure-notifications).

### Set up sign-in risk policies with either Conditional Access or Identity Protection

- [Configure Sign-In risk](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk)
- [Configure User Risk](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk-user)
- [Configure policy alerts in Defender for Cloud Apps](/cloud-app-security/cloud-discovery-policies)

## Recommended defenses

- Educate end users, key stakeholders, front line operations, technical teams, cyber security and communications teams
- Review security control and make necessary changes to improve or strengthen security control within your organization
- Suggest Microsoft Entra configuration assessment
- Run regular [attack simulator](/microsoft-365/security/office-365-security/attack-simulator) exercises

## References

### Prerequisites

- [Sentinel Alerting](/azure/sentinel/tutorial-detect-threats-built-in)
- [SIEM integration into Defender for Cloud Apps](/cloud-app-security/siem)
- [SIEM integration with Graph API](/graph/security-integration#list-of-connectors-from-microsoft)
- [Splunk alerting manual](https://docs.splunk.com/Documentation/Splunk/8.0.4/Alert/AlertWorkflowOverview)
- [Installing ADFS Health Connect](/azure/active-directory/hybrid/how-to-connect-health-agent-install#installing-the-azure-ad-connect-health-agent-for-ad-fs)
- [Understanding Microsoft Entra sign-in logs](/azure/active-directory/reports-monitoring/concept-sign-ins)
- [Understanding MFA reporting](/azure/active-directory/authentication/howto-mfa-reporting)

### Mitigations

- [Mitigations for password spray](https://www.microsoft.com/microsoft-365/blog/2018/03/05/azure-ad-and-adfs-best-practices-defending-against-password-spray-attacks/)
- [Enable password protection](/azure/active-directory/authentication/howto-password-ban-bad-on-premises-operations)
- [Block legacy authentication](/azure/active-directory/conditional-access/block-legacy-authentication)
- [Block IP address on ADFS](/windows-server/identity/ad-fs/operations/configure-ad-fs-banned-ip)
- [Access controls (including blocking IP addresses) ADFS v3](/windows-server/identity/ad-fs/operations/access-control-policies-w2k12)
- [ADFS Password Protection](/windows-server/identity/ad-fs/technical-reference/ad-fs-password-protection)
- [Enable ADFS Extranet Lockout](/windows-server/identity/ad-fs/operations/configure-ad-fs-extranet-soft-lockout-protection)
- [MFA as primary authentication](/windows-server/identity/ad-fs/operations/configure-ad-fs-and-azure-mfa)
- [Enable Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection)
- [Microsoft Entra audit activity reference](/azure/active-directory/reports-monitoring/reference-audit-activities)
- [Microsoft Entra audit logs schema](/azure/active-directory/reports-monitoring/reference-azure-monitor-audit-log-schema)
- [Microsoft Entra sign-in logs schema](/azure/active-directory/reports-monitoring/reference-azure-monitor-sign-ins-log-schema)
- [Microsoft Entra audit log Graph API](/graph/api/resources/azure-ad-auditlog-overview)
- [Risky IP Alerts](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/monitor-your-adfs-sign-in-activity-using-azure-ad-connect-health/ba-p/245395)
- [ADFS Help](https://adfshelp.microsoft.com/TroubleshootingGuides/Workflow/a73d5843-9939-4c03-80a1-adcbbf3ccec8)

### Recovery

- [SIEM tool integrations](/microsoft-365/security/office-365-security/siem-server-integration)
- [Create Defender for Cloud Apps alerts](/cloud-app-security/cloud-discovery-policies)
- [Create Risky IP and ADFS Health Connect Alerts](/azure/active-directory/hybrid/how-to-connect-health-adfs-risky-ip)
- [Identity Protection alerts](/azure/active-directory/identity-protection/howto-identity-protection-configure-notifications)
- [Attack simulator](/microsoft-365/security/office-365-security/attack-simulator)

## Additional incident response playbooks

Examine guidance for identifying and investigating these additional types of attacks:

- [Phishing](incident-response-playbook-phishing.md)
- [App consent](incident-response-playbook-app-consent.md)
- [Microsoft DART ransomware approach and best practices](incident-response-playbook-dart-ransomware-approach.md)

## Incident response resources

- [Overview](incident-response-overview.md) for Microsoft security products and resources for new-to-role and experienced analysts
- [Planning](incident-response-planning.md) for your Security Operations Center (SOC)
- [Microsoft 365 Defender](/microsoft-365/security/defender/incidents-overview) incident response
- [Microsoft Defender for Cloud (Azure)](/azure/defender-for-cloud/managing-and-responding-alerts)
- [Microsoft Sentinel](/azure/sentinel/investigate-cases) incident response
