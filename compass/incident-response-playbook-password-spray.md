---
title: Password spray investigation
description: Learn how to identify and investigate password spray attacks, protect data, and minimize further risks.
keywords: password spray, password, investigation, attack, email, microsoft threat protection, microsoft 365, search, security, query, telemetry, security events, antivirus, firewall
search.product: DART
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords: 
  - NOCSH
ms.author: josephd
author: JoeDavies-MSFT
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: 
  - M365-security-compliance
  - m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
---

# Password spray investigation

This article provides guidance on identifying and investigating password spray attacks within your organization and take the required remedial action to protect information and minimize further risks.

This article contains the following sections:

- **Prerequisites:** This section covers the specific requirements you need to complete before starting the investigation, either on the customer side or for you as the investigator. For example, logging that should be turned on, roles and permissions required, among others.
- **Workflow:** This section is a Visio chart of the logical flow that you should follow to perform this investigation.
- **Checklist:** This section contains a list of tasks for each of the steps in the flow chart. This checklist can be helpful in highly regulated environments to verify what you have done or simply as a quality gate for yourself.
- **Investigation steps:** This section includes a detailed step-by-step guidance for this specific investigation.
- **Recovery:** This section contains high-level steps on how to recover/mitigate from a password spray attack.
- **References:** This section contains additional reading and reference materials from internal playbooks to website resources.

## Prerequisites

This section provides guidance on the system requirements. Before starting the investigation, make sure you have completed the setup for logs and alerts, and the following configurations.

### Set up [ADFS logging](https://docs.microsoft.com/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-logging)

#### Event logging on ADFS 2016

By default, the Microsoft Active Directory Federation Services (ADFS) in Windows Server 2016 has a basic level of auditing enabled. With basic auditing, administrators can see five or less events for a single request.

To view the current auditing level, you can use this PowerShell command:

```powershell
Get-AdfsProperties
```

![adfs](./media/incident-response-playbook-password-spray/adfsproperties.png)

This table contains the auditing levels that are available.

| **Audit level** | **PowerShell syntax** | **Description** |
|-----------------|-----------------------|---------------------------------|
| None            | Set-AdfsProperties -AuditLevel - None    | Auditing is disabled and no events will be logged                                         |
| Basic (Default) | Set-AdfsProperties -AuditLevel - Basic   | No more than 5 events will be logged for a single request                                 |
| Verbose         | Set-AdfsProperties -AuditLevel - Verbose | All events will be logged. This will log a significant amount of information per request. |

To raise or lower the auditing level, use this PowerShell command:

```powershell
Set-AdfsProperties -AuditLevel
```

### Set up ADFS 2012 R2/2016/2019 security logging

1. Click **Start**, navigate to **Programs &gt; Administrative Tools**, and then click **Local Security Policy**.
2. Navigate to the **Security Settings\\Local Policies\\User Rights Management** folder, and then double-click **Generate security audits**.
3. On the **Local Security Setting** tab, verify that the ADFS service account is listed. If it is not present, click **Add User** or **Group** and add it to the list, and then click **OK**.
4. To enable auditing, open a command prompt with elevated privileges and run the following command:

    ```powershell
    auditpol.exe /set /subcategory:"Application Generated" /failure:enable /success:enable
    ```

5. Close **Local Security Policy**.
6. Next, open the ADFS Management snap-in, click **Start**, navigate to **Programs > Administrative Tools**, and then click **ADFS Management**.
7. In the **Actions** pane, click **Edit Federation Service Properties**.
8. In the **Federation Service Properties** dialog box, click the **Events** tab.
9. Select the **Success audits** and **Failure audits** check boxes.
10. Click **OK** to finish and save the configuration.

### Install Azure AD Connect Health for ADFS

The Azure Active Directory (Azure AD) Connect Health for ADFS agent allows you to have greater visibility into the customers federation environment. It provides customers with several pre-configured dashboards like usage, performance monitoring as well as risky IP reports.

To install ADFS Connect Health, go through the [requirements for using Azure AD Connect Health](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-health-agent-install#requirements), and then install the [Azure ADFS Connect Health Agent](https://go.microsoft.com/fwlink/?LinkID=518973).

### Set up [risky IP alerts](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/monitor-your-adfs-sign-in-activity-using-azure-ad-connect-health/ba-p/245395)

Once Azure AD Connect Health for ADFS is configured, the customer should set the thresholds for alerting based on what is suitable for their environment.

:::image type="content" source="./media/incident-response-playbook-password-spray/Thresholdsettings.png" alt-text="riskyiplalerts"::: 

### Set up SIEM tool alerts on Azure Sentinel

To set up SIEM tool alerts, go through the tutorial on [out of the box alerting](https://docs.microsoft.com/azure/sentinel/tutorial-detect-threats-built-in).

### SIEM integration into MCAS

Connect the Security Information and Event Management (SIEM) tool to the Microsoft Cloud App Security (MCAS), which currently supports Micro Focus ArcSight and generic common event format (CEF).

For more information, see [Generic SIEM Integration](https://docs.microsoft.com/cloud-app-security/siem).

### SIEM integration with Graph API

You can connect SIEM with the Microsoft Graph Security API by using any of the following options:

- **Directly using the supported integration options** – Refer to the list of supported integration options like writing code to directly connect your application to derive rich insights. Leverage samples to get started.
- **Use native integrations and connectors built by Microsoft partners** – Refer to the Microsoft Graph Security API partner solutions to use these integrations.
- **Use connectors built by Microsoft** – Refer to the list of connectors that you can use to connect with the API through a variety of solutions for Security Incident and Event Management (SIEM), Security Response and Orchestration (SOAR), Incident Tracking and Service Management (ITSM), reporting, and so on.

For more information, see [security solution integrations using the Microsoft Graph Security API](https://docs.microsoft.com/graph/security-integration#list-of-connectors-from-microsoft).

### Using Splunk

You can also use the Spunk platform to set up alerts.

- Watch this video tutorial on how to create [Spunk alerts](https://www.splunk.com/view/SP-CAAAGYG)
- For more information, see [Spunk alerting manual](https://docs.splunk.com/Documentation/Splunk/8.0.4/Alert/AlertWorkflowOverview)

## Workflow

<!--
![workflow](./media/incident-response-playbook-password-spray/Pwdsprayflow.png)
--> 

[![Password spray investigation workflow](./media/incident-response-playbook-password-spray/Pwdsprayflow.png)](https://github.com/MicrosoftDocs/security/raw/public/compass/media/incident-response-playbook-password-spray/Pwdsprayflow.png)

## Checklist

#### Investigation triggers

- Rceived a trigger from SIEM, firewall logs or Azure AD
- Identity Protection Password Spray feature or Risky IP
- Large number of failed logins (Event ID 411)
- Spike in Azure AD Connect Health for ADFS
- Another security incident (for example, phishing)
- Unexplained activity – Sign-in from unfamiliar location, user getting unexpected MFA prompts

### Investigation

- What is being alerted?
- Can you confirm this is a password spray?
- Determine timeline for attack
- Determine IP address/addresses of the attack
- Filter successful logins for this time period and IP address, including successful password but failed MFA
- Check [MFA reporting](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-reporting)
- Is there anything out of the ordinary on the account – new device, new OS, new IP address used etc. Use MCAS or AIP to detect suspicious activity
- Inform local authorities/third parties for assistance
- If compromise suspected check for data exfiltration
- Check associated account for suspicious behaviour
- Check accounts of anyone working in the same office/delegated access - password hygiene (make sure they are not using the same password as the compromised account)
- Run ADFS Help

#### Mitigations

Check the [References](#references) section for guidance on how to enable features.

- [Block IP address of attacker](https://docs.microsoft.com/azure/active-directory/conditional-access/block-legacy-authentication)  (keep an eye out for changes to another IP address)
- Changed user’s password of suspected compromise
- [Enable ADFS Extranet Lockout](https://docs.microsoft.com/windows-server/identity/ad-fs/operations/configure-ad-fs-extranet-soft-lockout-protection)
- [Disabled Legacy authentication](https://docs.microsoft.com/azure/active-directory/conditional-access/block-legacy-authentication)
- [Enabled Azure Identity Protection](https://docs.microsoft.com/azure/active-directory/identity-protection/howto-identity-protection-configure-risk-policies)  (sign in and user risk policies)
- [Enabled MFA](https://docs.microsoft.com/azure/active-directory/authentication/tutorial-enable-azure-mfa)  (if not already)
- [Enabled Password Protection](https://docs.microsoft.com/azure/active-directory/authentication/howto-password-ban-bad-on-premises-operations)
- [Deploy Azure AD Connect Health for ADFS](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-health-agent-install#installing-the-azure-ad-connect-health-agent-for-ad-fs)  (if not already)

#### Recovery

- Tag bad IP address in MCAS, SIEM, ADFS and Azure AD
- [MFA as primary authentication](https://docs.microsoft.com/windows-server/identity/ad-fs/operations/configure-ad-fs-and-azure-mfa)
- [Configure SIEM integrations with Cloud](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration)
- Configure Alerting - Identity Protection, ADFS Health Connect, SIEM and Cloud App Security
- Lessons Learnt (include key stakeholders, third parties, communication teams)
- Security posture review/improvements
- [Plan to run regular attack simulators](https://docs.microsoft.com/microsoft-365/security/office-365-security/attack-simulator)

## Investigation steps

### Password spray incident response

Let’s understand a few password spray attack techniques before proceeding with the investigation.

**Password compromise:** An attacker has successfully guessed the user’s password but has not been able to access the account due to other controls such as multi-factor authentication (MFA).

**Account compromise:** An attacker has successfully guessed the user’s password and has successfully gained access to the account.

### Environment discovery

#### Identify authentication type

As the very first step, you need to check what authentication type is used for a tenant/verified domain that you are investigating.

To obtain the authentication status for a specific domain name, use the [Get-MsolDomain](https://docs.microsoft.com/powershell/module/msonline/get-msoldomain) PowerShell command. Here's an example:

```powershell
Connect-MsolService
Get-MsolDomain -DomainName "contoso.com"
```

### Is the authentication federated or managed?

If the authentication is federated, then successful logins will be stored in the Azure AD. The failed logins will be in their Identity Provider (IDP). For more information, see  [ADFS troubleshooting and event logging](https://docs.microsoft.com/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-logging).

If the authentication type is managed, (Cloud only, password hash sync (PHS) or pass-through authentication (PTA)), then successful and failed logins will be stored in the Azure AD sign-In logs.

>[!Note]
>The [Staged Rollout](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-staged-rollout) feature allows the tenant domain name to be federated but specific users to be managed. Determine if any users are members of this group.
>

### Is the Azure AD Connect Health enabled for ADFS?

- The [RiskyIP report](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-health-adfs-risky-ip)  will provide suspect IPs and date/time. Notifications should be enabled.
- Also check the [federated logins investigation from the Phishing playbook](incident-response-playbook-phishing.md#federated-scenario)

### Is the advanced logging enabled in ADFS?

- This is a requirement for ADFS Connect Health but it can be enabled independently
- See how to [enable ADFS Health Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-health-agent-install#installing-the-azure-ad-connect-health-agent-for-ad-fs))
- Also check the [Federated logins investigation from the Phishing playbook](incident-response-playbook-phishing.md#federated-scenario)

### Are the logs stored in SIEM?

To check whether the customer is storing and correlating logs in the Security Information and Event Management (SIEM) or in any other system, check the following:

- Log analytics- pre-built queries
- Sentinel- pre-built queries
- Splunk – pre-built queries
- Firewall logs
- UAL if > 30 days

### Understanding Azure AD and MFA reporting

It is important that you understand the logs that you are seeing to be able to determine compromise. Below are our quick guides to understanding Azure AD Sign-Ins and MFA reporting to help with this. Refer to these articles:

- MFA reporting](<https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-reporting>)
- [Understanding Sign Ins](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-sign-ins)

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

Unusual spikes in activity are key indicators through Azure AD Health Connect (assuming this is installed). Other indicators are:

- Alerting through SIEM shows a spike when you collate the logs.
- Larger than normal log size for ADFS failed logins (this can be an alert in SIEM tool).
- Increased amounts of 342/411 event IDs – username or password is incorrect. Or 516 for extranet lockout.
- Hit failed authentication request threshold – Risky IP in Azure AD or SIEM tool alert/both 342 and 411 errors (To be able to view this information, the advanced logging should be turned on.)

### Risky IP in Azure AD Health Connect portal

Risky IP will alert when the customized threshold has been reached for bad passwords in an hour and bad password count in a day as well as extranet lockouts.

![riskyipreport](./media/incident-response-playbook-password-spray/RiskyIPReport.jpg)

*Risky IP report data*

The details of failed attempts are available in the tabs **IP address** and **extranet lockouts**.

![ipaddresstable](./media/incident-response-playbook-password-spray/ipaddress1.png)

*IP address and extranet lockouts in the Risky IP report*

### Detect password spray in Azure Identity Protection

Azure Identity Protection is an Azure AD Premium P2 feature that has a password-spray detection risk alert and search feature that you can be utilize to get additional information or set up automatic remediation.

![detectpwd](./media/incident-response-playbook-password-spray/Detectpwd.png)

*Details of password spray attack*

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
3. Determine the attacker IP address (might be multiple sources and multiple IP addresses) from the firewall, ADFS, SIEM or Azure AD.
4. Once password spray confirmed, you might have to inform the local agencies (police, third parties, among others).
5. Collate and monitor the following Event IDs for ADFS:

    **ADFS 2012 R2**

    - Audit event 403 – user agent making the request
    - Audit event 411 – failed authentication requests
    - Audit event 516 – extranet lockout
    - Audit Event 342 – failed authentication requests
    - Audit Event 412 - Successful log in

6. To collect the *Audit Event 411 - failed authentication requests,* use the following [script](https://docs.microsoft.com/samples/browse/?redirectedfrom=TechNet-Gallery):

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
    {$PastPeriod = (Get-Date).AddDays(-($PastDays))    } 
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
    if ($BN -ge 9200) {Get-Winevent  -FilterHashTable @{LogName= "Security"; >StartTime=$PastPeriod; ID=411} -ErrorAction SilentlyContinue | Where-Object{$_.Message -match "The user name or password is incorrect"} |  % { 
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

1. Collate all successful logins for this time on ADFS (if federated). A quick login and logout (at the same second) can be an indicator of a password being guessed successfully and being tried by the attacker.
2. Collate any Azure AD successful or interrupted events for this time-period for both federated and managed scenarios.

### Monitor and collate Event IDs from Azure AD

See how to find the [meaning of error logs](https://login.microsoftonline.com/error).  

The following Event IDs from Azure AD are relevant:

- 50057 - User account was disabled
- 50055 - Password expired
- 50072 – User prompted to provide MFA
- 50074 - MFA required
- 50079 - user needs to register security info
- 53003 - User blocked by Conditional Access
- 53004 - Cannot configure MFA due to suspicious activity
- 530032 - Blocked by Conditional Access on Security Policy
- Sign-In status Success, Failure, Interrupt

### Collate event IDs from Sentinel playbook

You can get all the Event IDs from the Sentinel Playbook that is available on [GitHub](https://github.com/Azure/Azure-Sentinel/blob/49fee965c9def6890b7e5f2ad96cc1a89d73db26/Detections/SigninLogs/SigninPasswordSpray.yaml).

### Isolate and confirm attack

Isolate the ADFS and Azure AD successful and interrupted sign-in events. These are your accounts of interest.

Block the IP Address ADFS 2012R2 and above for federated authentication. Here's an example:

```powershell
Set-AdfsProperties -AddBannedIps "1.2.3.4", "::3", "1.2.3.4/16"
```

### **Collect ADFS logs**

Collect multiple event IDs within a time frame. Here's an example:

```powershell
Get-WinEvent -ProviderName 'ADFS' | Where-Object { $_.ID -eq '412' -or $_.ID -eq '411' -or $_.ID -eq '342' -or $_.ID -eq '516' -and $_.TimeCreated -gt ((Get-Date).AddHours(-"8")) }
```

### Collate ADFS logs in Azure AD

Azure AD Sing-In reports include ADFS sign-in activity for customers who use Azure AD Connect Health. Filter sign-in logs by Token Issuer Type "Federated".

Here’s an example PowerShell command to retrieve sign-in logs for a specific IP address:

```powershell
Get-AzureADIRSignInDetail -TenantId b446a536-cb76-4360-a8bb-6593cf4d9c7f -IpAddress 131.107.128.76
```

Also, search the Azure portal for time frame, IP address and successful and interrupted login as shown in these images.

:::image type="content" source="./media/incident-response-playbook-password-spray/Selectingtimeframe.jpg" alt-text="timeframe"::: 

*Searching for logins within a specific time frame*

:::image type="content" source="./media/incident-response-playbook-password-spray/Selectingipaddress.jpg" alt-text="ipaddress"::: 

*Searching for logins on a specific IP address*

:::image type="content" source="./media/incident-response-playbook-password-spray/Selectingstatus.jpg" alt-text="status"::: 

*Searching for logins based on the status*

You can then download this data as a *.csv* file for analysis. For more information, see [Sign-in activity reports in the Azure Active Directory portal](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-sign-ins).

### Prioritize findings

It is important to be able to react to the most critical threat. This can be the attacker has successfully obtained access to an account and therefore can access/exfiltrate data. The attacker has got the password but may not be able to access the account for example they have the password but are not passing the MFA challenge. Also the attacker could not be guessing passwords correctly but continuing to try. During analysis, prioritize these findings:

- Successful logins by known attacker IP address
- Interrupted sign-in by known attacker IP address
- Unsuccessful logins by known attacker IP address
- Other unknown IP address successful logins

### Check legacy authentication

Most attacks use legacy authentication. There are a number of ways to determine the protocol of the attack.

1. In Azure AD, navigate to **Sign-Ins** and filter on **Client App.**
2. Select all the legacy authentication protocols that are listed.

    :::image type="content" source="./media/incident-response-playbook-password-spray/Legacyauthenticationchecks.jpg" alt-text="authenticationcheck"::: 
 
    *List of legacy protocols*

3. Or if you have an Azure workspace, you can use the pre-built legacy authentication workbook located in the Azure Active Directory portal under **Monitoring and Workbooks**.

    :::image type="content" source="./media/incident-response-playbook-password-spray/authenticationbook.png" alt-text="workbook"::: 

    *Legacy authentication workbook*

### Block IP address Azure AD for managed scenario (PHS including staging)

1. Navigate to **New named locations**.

    :::image type="content" source="./media/incident-response-playbook-password-spray/Namedlocation.jpg" alt-text="namedlocation"::: 

2. Create a CA policy to target all applications and block for this named location only.

### Has the user used this operating system, IP, ISP, device or browser before?

If the user has not used them before and this activity is unusual, then flag the user and investigate all their activities.

### Is the IP marked as “risky”?  

Ensure you record successful passwords but failed multi-factor authentication (MFA) responses, as this activity indicates that the attacker is getting the password but not passing MFA.  
Set aside any account that appears to be a normal login, for example, passed MFA, location and IP not out of the ordinary.

### MFA reporting

It is important to also check MFA logs as an attacker could have successfully guessed a password but be failing the MFA prompt. The Azure AD MFA logs shows authentication details for events when a user is prompted for multi-factor authentication. Check and make sure there are no large suspicious MFA logs in Azure AD. For more information, see [how to use the sign-ins report to review Azure AD Multi-Factor Authentication events](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-reporting).

### Additional checks

In the Microsoft Cloud App Security (MCAS), investigate activities and file access of the compromised account. For more information, see:

- [Investigate compromise with MCAS](https://docs.microsoft.com/cloud-app-security/investigate)
- [Investigate anomalies with MCAS](https://docs.microsoft.com/cloud-app-security/investigate-anomaly-alerts)

Check whether the user has access to additional resources, such as virtual machines (VMs), domain account permissions, storage, among others.  
If data has been breached, then you should inform additional agencies, such as the police.

## Immediate remedial actions

1. Change the password of any account that is suspected to have been breached or if the account password has been discovered. Additionally, block the user. Make sure you follow the guidelines for [revoking emergency access](https://docs.microsoft.com/azure/active-directory/enterprise-users/users-revoke-access).
2. Mark any account that has been compromised as “*compromised*” in Azure Identity Protection.
3. Block the IP address of the attacker. Be cautious while performing this action as attackers can use legitimate VPNs and this could create more risk as they change IP addresses as well. If you are using Cloud Authentication, then block the IP address in MCAS or Azure AD. If federated, you need to block the IP address at the firewall level in front of the ADFS service.
4. [Block legacy](https://docs.microsoft.com/azure/active-directory/conditional-access/block-legacy-authentication) authentication if it is being used (this action, however, could impact business).
5. [Enable MFA](https://docs.microsoft.com/azure/active-directory/authentication/tutorial-enable-azure-mfa) if it is not already done.
6. [Enable Identity Protection](https://docs.microsoft.com/azure/active-directory/identity-protection/howto-identity-protection-configure-risk-policies) for the user risk and sign-in risk
7. Check the data that has been compromised (emails, SharePoint, OneDrive, apps). See how to use the [activity filter on MCAS](https://docs.microsoft.com/cloud-app-security/activity-filters).
8. Maintain password hygiene. For more information, see [Azure AD password protection](https://www.microsoft.com/research/publication/password-guidance/).
9. You can also refer to [ADFS Help](https://adfshelp.microsoft.com/TroubleshootingGuides/Workflow/a73d5843-9939-4c03-80a1-adcbbf3ccec8).

## Recovery

### Password protection

Implement password protection on Azure AD and on-premises by enabling the custom-banned password lists. This configuration will prevent users from setting weak passwords or passwords associated with your organization:

:::image type="content" source="./media/incident-response-playbook-password-spray/Passwordprotection.jpg" alt-text="pwdprotection"::: 

*Enabling password protection*

For more information, see [how to defend against password spray attacks](https://www.microsoft.com/en-u/microsoft-365/blog/2018/03/05/azure-ad-and-adfs-best-practices-defending-against-password-spray-attacks/).

### Tagging IP address

Tag the IP addresses in MCAS to receive alerts related to future use:

:::image type="content" source="./media/incident-response-playbook-password-spray/IPaddresstag.jpg" alt-text="ipaddresstag"::: 

*Tagging IP addresses*

In the MCAS, “tag” IP address for the IP scope and set up an alert for this IP range for future reference and accelerated response.

:::image type="content" source="./media/incident-response-playbook-password-spray/ipaddressalert.png" alt-text="ipaddressalert"::: 

*Setting alerts for a specific IP address*

### Configure alerts

Depending on your organization needs, you can configure alerts.

[Set up alerting in your SIEM tool](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration)  and look at improving logging gaps. Integrate ADFS, Azure AD, Office 365 and MCAS logging.

Configure the threshold and alerts in ADFS Health Connect and Risky IP portal.

:::image type="content" source="./media/incident-response-playbook-password-spray/thresholdsettings.png" alt-text="threshold"::: 

*Configure threshold settings*

![configurenotifications](./media/incident-response-playbook-password-spray/configurenotifications.png)

*Configure notifications*

See how to [configure alerts in the Identity Protection portal](https://docs.microsoft.com/azure/active-directory/identity-protection/howto-identity-protection-configure-notifications).

### Set up sign-in risk policies with either Conditional Access or Identity Protection

- [Configure Sign-In risk](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-risk)
- [Configure User Risk](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-risk-user)
- [Configure policy alerts in Cloud App Security](https://docs.microsoft.com/cloud-app-security/cloud-discovery-policies)

## Recommended defenses

- Educate end users, key stakeholders, front line operations, technical teams, cyber security and communications teams
- Review security control and make necessary changes to improve or strengthen security control within your organization
- Suggest Azure AD configuration assessment
- Run regular [attack simulator](https://docs.microsoft.com/microsoft-365/security/office-365-security/attack-simulator) exercises

## References

### Prerequisites

- [Sentinel Alerting](https://docs.microsoft.com/azure/sentinel/tutorial-detect-threats-built-in)
- [SIEM integration into MCAS](https://docs.microsoft.com/cloud-app-security/siem)
- [SIEM integration with Graph API](https://docs.microsoft.com/graph/security-integration#list-of-connectors-from-microsoft)
- [Splunk alerting video](https://www.splunk.com/view/SP-CAAAGYG)
- [Splunk alerting manual](https://docs.splunk.com/Documentation/Splunk/8.0.4/Alert/AlertWorkflowOverview)
- [Installing ADFS Health Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-health-agent-install#installing-the-azure-ad-connect-health-agent-for-ad-fs)
- [Understanding Azure AD sign-in logs](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-sign-ins)
- [Understanding MFA reporting](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-reporting)

### Mitigations

- [Mitigations for password spray](https://www.microsoft.com/en-u/microsoft-365/blog/2018/03/05/azure-ad-and-adfs-best-practices-defending-against-password-spray-attacks/)
- [Enable password protection](https://docs.microsoft.com/azure/active-directory/authentication/howto-password-ban-bad-on-premises-operations)
- [Block legacy authentication](https://docs.microsoft.com/azure/active-directory/conditional-access/block-legacy-authentication)
- [Block IP address on ADFS](https://docs.microsoft.com/windows-server/identity/ad-fs/operations/configure-ad-fs-banned-ip)
- [Access controls (including blocking IP addresses) ADFS v3](https://docs.microsoft.com/windows-server/identity/ad-fs/operations/access-control-policies-w2k12)
- [ADFS Password Protection](https://docs.microsoft.com/windows-server/identity/ad-fs/technical-reference/ad-fs-password-protection)
- [Enable ADFS Extranet Lockout](https://docs.microsoft.com/windows-server/identity/ad-fs/operations/configure-ad-fs-extranet-soft-lockout-protection)
- [MFA as primary authentication](https://docs.microsoft.com/windows-server/identity/ad-fs/operations/configure-ad-fs-and-azure-mfa)
- [Enable Identity Protection](https://docs.microsoft.com/azure/active-directory/identity-protection/overview-identity-protection)
- [Azure AD audit activity reference](https://docs.microsoft.com/azure/active-directory/reports-monitoring/reference-audit-activities)
- [Azure AD audit logs schema](https://docs.microsoft.com/azure/active-directory/reports-monitoring/reference-azure-monitor-audit-log-schema)
- [Azure AD sign-in logs schema](https://docs.microsoft.com/azure/active-directory/reports-monitoring/reference-azure-monitor-sign-ins-log-schema)
- [Azure AD audit log Graph API](https://docs.microsoft.com/graph/api/resources/azure-ad-auditlog-overview)
- [Risky IP Alerts](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/monitor-your-adfs-sign-in-activity-using-azure-ad-connect-health/ba-p/245395)
- [ADFS Help](https://adfshelp.microsoft.com/TroubleshootingGuides/Workflow/a73d5843-9939-4c03-80a1-adcbbf3ccec8)

### Recovery

- [SIEM tool integrations](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration)
- [Create MCAS alerts](https://docs.microsoft.com/cloud-app-security/cloud-discovery-policies)
- [Create Risky IP and ADFS Health Connect Alerts](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-health-adfs-risky-ip)
- [Identity Protection alerts](https://docs.microsoft.com/azure/active-directory/identity-protection/howto-identity-protection-configure-notifications)
- [Attack simulator](https://docs.microsoft.com/microsoft-365/security/office-365-security/attack-simulator)


## Additional incident response playbooks

Examine guidance for identifying and investigating these additional types of attacks:

- [Phishing](incident-response-playbook-phishing.md)
- [App consent](incident-response-playbook-app-consent.md)
