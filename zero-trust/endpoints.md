---
title: Secure endpoints with Zero Trust
description: Not all endpoints are managed or even owned by the organization, leading to different device configurations and software patch levels. In a Zero Trust approach, the same security policies are applied regardless of the type of device or who owns it. 
ms.date: 09/01/2020
ms.service: security
author: garycentric
ms.author: v-gmoor
ms.topic: conceptual
---


# Secure endpoints with Zero Trust

:::image type="icon" source="./media/icon-endpoint-devices-medium.png":::

**Background**

The modern enterprise has an incredible diversity of endpoints accessing data. Not all endpoints are managed or even owned by the organization, leading to different device configurations and software patch levels. This creates a massive attack surface and, if left unresolved, accessing work data from untrusted endpoints can easily become the weakest link in your [Zero Trust](https://go.microsoft.com/fwlink/p/?LinkID=2109181&clcid=0x409&culture=en-us&country=US) security strategy.

Zero Trust adheres to the principle, "Never trust, always verify." In terms of endpoints, that means always verify *all* endpoints. That includes not only contractor, partner, and guest devices, but also [apps](https://aka.ms/ZTApplications) and devices used by employees to access work data, regardless of device ownership.  
  
In a Zero Trust approach, the same security policies are applied regardless of whether the device is corporate-owned or personally-owned through bring your own device (BYOD); whether the device is fully managed by IT, or only the apps and data are secured. The policies apply to all endpoints, whether PC, Mac, smartphone, tablet, wearable, or IoT device wherever they are connected, be it the secure corporate [network](https://aka.ms/ZTNetwork), home broadband, or public internet.

Most importantly, the health and trustworthiness of apps that run on those endpoints impacts your security posture. You need to prevent corporate data from leaking to untrusted or unknown apps or services, either accidentally or through malicious intent.

**There are a few key rules for securing devices and endpoints in a Zero Trust model:**

-   Zero Trust security policies are centrally enforced through the cloud and cover endpoint security, device configuration, app protection, device compliance, and risk posture.

-   The platform as well as the apps that run on the devices are securely provisioned, properly configured, and kept up to date.

-   There is automated and prompt response to contain access to corporate data within the apps in case of a security compromise.

-   The access control system ensures that all policy controls are in effect before the data is accessed.



## Endpoint Zero Trust deployment objectives

<div class="alert">
   <p><b>Before</b> most organizations <b>start the Zero Trust journey</b>, their endpoint security is set up as follows:</p>
   <ul>
      <li>
         <p>Endpoints are domain-joined and managed with solutions like Group Policy Objects or Configuration Manager. These are great options, but they don't leverage modern Windows 10 CSPs or require a separate cloud management gateway appliance to service cloud-based devices.</p>
      </li>
      <li>
         <p>Endpoints are required to be on a corporate network to access data. This could mean that the devices are required to physically be on-site to access the corporate network, or that they require VPN access, which increases the risk that a compromised device could access sensitive corporate resources.</p>
      </li>
   </ul>
</div>


<table border="0">
   <tr>
      <td colspan="2">
         <p>When implementing an end-to-end Zero Trust framework for securing endpoints, we recommend you focus first on these <b>initial deployment objectives</b>:</p>
	  </td>
   </tr>
   <tr>
      <td>
		 <p><img src="./media/icon-initial-deployment-small.png" alt="List icon with one checkmark."></p>
      </td>
      <td>
	     <p><b>I.</b> <a href="#i-endpoints-are-registered-with-a-cloud-identity-provider">Endpoints are registered with cloud identity providers.</a> In order to monitor security and risk across multiple endpoints used by any one person, you need <a href="https://aka.ms/ZTCrossPillars">visibility</a> in all devices and access points that may be accessing your resources.</p>
         <p><b>II.</b> <a href="#ii-access-is-only-granted-to-cloud-managed-and-compliant-endpoints">Access is only granted to cloud-managed and compliant endpoints and apps.</a> Set compliance rules to ensure that devices meet minimum security requirements before access is granted. Also, set remediation rules for noncompliant devices so that people know how to resolve the issue.</p>
	     <p><b>III.</b> <a href="#iii-dlp-policies-are-enforced-for-byod-and-corporate-devices">Data loss prevention (DLP) policies are enforced for corporate devices and BYOD.</a> Control what the user can do with the data after they have access. For instance, restrict file saving to untrusted locations (such as local disk), or restrict copy-and-paste sharing with a consumer communication app or chat app to protect data.</p>
      </td>
   </tr>
   <tr>
      <td colspan="2">
         <p>After these are completed, focus on these <b>additional deployment objectives</b>:</p>
      </td>
   </tr>
   <tr>
      <td>
		 <p><img src="./media/icon-additional-deployment-small.png" alt="List icon with two checkmarks."></p>
      </td>
      <td>
         <p><b>IV.</b> <a href="#iv-endpoint-threat-detection-is-used-to-monitor-device-risk">Endpoint threat detection is used to monitor device risk.</a> Use a single pane of glass to manage all endpoints in a consistent way, and use a SIEM to route endpoint logs and transactions such that you get fewer, but actionable, alerts.</p>
         <p><b>V.</b> <a href="#v-access-control-is-gated-on-device-risk-for-both-corporate-and-byo-devices">Access control is gated on endpoint risk for both corporate devices and BYOD.</a> Integrate data from Microsoft Defender Advanced Threat Protection (ATP), or other Mobile Threat Defense (MTD) vendors, as an information source for device compliance policies and device Conditional Access rules. The device risk will then directly influence what resources will be accessible by the user of that device.</p>
      </td>
   </tr>
</table>

## Endpoint Zero Trust deployment guide

This guide will walk you through the steps required to secure your devices following the principles of a Zero Trust security framework.


<!-- H2 heading, "Initial deployment objectives" -->
<br/><br/>
[!INCLUDE [H2 heading, Initial deployment objectives](./includes/deployment-objectives-initial.md)]


### I. Endpoints are registered with a cloud identity providers

To help limit risk exposure, you need to monitor every endpoint to ensure each one has a trusted identity, security policies are applied, and the risk level for things like malware or data exfiltration has been measured, remediated, or deemed acceptable.

After a device is registered, users can access your organization's restricted resources using their corporate username and password to sign in (or Windows Hello for Business).

:::image type="content" source="./media/steps-box-endpoints-1.png" alt-text="Diagram of the steps within phase 1 of the initial deployment objectives." border="true":::


#### Register corporate devices with Azure Active Directory (AD)

Follow these steps:

**New Windows 10 devices**

1.  Start up your new device and begin the OOBE (Out of Box Experience) process.

2.  On the **Sign in with Microsoft** screen, type your work or school email address.

3.  On the **Enter your password** screen, type your password.

4.  On your mobile device, approve your device so it can access your account.

5.  Complete the OOBE process, including setting your privacy settings and setting up Windows Hello (if necessary).

6.  Your device is now joined to your organization's network.

**Existing Windows 10 devices**

1.  Open **Settings**, and then select **Accounts**.

2.  Select **Access work or school,** and then select **Connect**.  
 
    :::image type="content" source="./media/endpoints/screenshot-access-work-school-settings.png" alt-text="Access work or school in Settings." border="false":::

3.  On the **Set up a work or school account** screen, select **Join this device to Azure AD**.

    :::image type="content" source="./media/endpoints/screenshot-set-up-work-school-account-settings.png" alt-text="Set up a work or school account in Settings." border="false":::

4.  On the **Let's get you signed in** screen, type your email address (for example, _alain\@contoso.com_), and then select **Next**.

5.  On the **Enter password** screen, type your password, and then select **Sign in**.

6.  On your mobile device, approve your device so it can access your account.

7.  On the **Make sure this is your organization** screen, review the information to make sure it's right, and then select **Join**.

8.  On the **You\'re all set** screen, click **Done**.


#### Register personal Windows devices with Azure AD

Follow these steps:

1.  Open **Settings**, and then select **Accounts**.

2.  Select **Access work or school**, and then select **Connect** from the **Access work or school** screen.

    :::image type="content" source="./media/endpoints/screenshot-access-work-school-settings.png" alt-text="Access work or school in Settings." border="false":::

1.  On the **Add a work or school account** screen, type in your email address for your work or school account, and then select **Next**. For example, _alain\@contoso.com_.

2.  Sign in to your work or school account, and then select **Sign in**.

3.  Complete the rest of the registration process, including approving your identity verification request (if you use two-step verification) and setting up Windows Hello (if necessary).


#### Enable and configure Windows Hello for Business

To allow users an alternative sign-in method that replaces a password, such as PIN, biometric authentication, or fingerprint reader, [enable Windows Hello for Business on users' Windows 10 devices](https://docs.microsoft.com/mem/intune/protect/windows-hello).

The following Microsoft Intune and Azure AD actions are completed in the [Microsoft Endpoint Manager admin center](https://endpoint.microsoft.com/#home):

Start by creating a Windows Hello for Business enrollment policy in Microsoft Intune.

1.  Go to Devices &gt; Enrollment &gt; Enroll devices &gt; Windows enrollment &gt; Windows Hello for Business.

    :::image type="content" source="./media/endpoints/screenshot-windows-hello-business-settings.png" alt-text="Windows Hello for Business in Microsoft Intune." border="true":::

1.  Select from the following options for Configure Windows Hello for Business:

    1.  **Disabled.** If you don't want to use Windows Hello for Business, select this setting. If disabled, users can't provision Windows Hello for Business except on Azure AD-joined mobile phones where provisioning may be required.

    1.  **Enabled.** Select this setting if you want to configure Windows Hello for Business settings. When you select Enabled, additional settings for Windows Hello become visible.

    1.  **Not configured.** Select this setting if you don't want to use Intune to control Windows Hello for Business settings. Any existing Windows Hello for Business settings on Windows 10 devices isn't changed. All other settings on the pane are unavailable.

If you selected Enabled, [configure the required settings](https://docs.microsoft.com/mem/intune/protect/identity-protection-configure) that are applied to all enrolled Windows 10 devices and Windows 10 mobile devices.

1.  Use a Trusted Platform Module (TPM). A TPM chip provides an additional layer of data security. Choose one of the following values:

    1.  **Required**. Only devices with an accessible TPM can provision Windows Hello for Business.

    1.  **Preferred**. Devices first attempt to use a TPM. If this option isn't available, they can use software encryption.

2.  Set a minimum PIN length and Maximum PIN length. This configures devices to use the minimum and maximum PIN lengths that you specify to help ensure secure sign-in. The default PIN length is six characters, but you can enforce a minimum length of four characters. The maximum PIN length is 127 characters.

3.  Set a PIN expiration (days). It's good practice to specify an expiration period for a PIN, after which users must change it. The default is 41 days.

4.  Remember PIN history. Restricts the reuse of previously used PINs. By default, the last 5 PINs can't be reused.

5.  Use enhanced anti-spoofing, when available. This configures when the anti-spoofing features of Windows Hello are used on devices that support it. For example, detecting a photograph of a face instead of a real face.

6.  Allow phone sign-in. If this option is set to Yes, users can use a remote passport to serve as a portable companion device for desktop computer authentication. The desktop computer must be Azure AD joined, and the companion device must be configured with a Windows Hello for Business PIN.

After you configure these settings, select **Save.**

After configuring the settings that apply to all enrolled Windows 10 devices and Windows 10 mobile devices, [set up Windows Hello for Business Identity Protection profiles](https://docs.microsoft.com/mem/intune/protect/identity-protection-configure) to customize Windows Hello for Business security settings for specific end user devices.

1.  Select **Devices &gt; Configuration profiles &gt; Create profile &gt; Windows 10 and Later &gt; Identity Protection**.

    :::image type="content" source="./media/endpoints/screenshot-create-profile-windows-10-identity-protection.png" alt-text="Screenshot of Create a profile with platform set to Windows 10 and profile set to Identity protection." border="true":::

1.  Configure Windows Hello for Business. Choose how you want to configure Windows Hello for Business.

    :::image type="content" source="./media/endpoints/screenshot-identity-protection-windows-10-configuration-settings.png" alt-text="Screenshot of Configuration settings under Identity protection in Configuration profiles." border="true":::

    1.  Minimum PIN length.

    1.  Lowercase letters in PIN.

    1.  Uppercase letters in PIN.

    1.  Special characters in PIN.

    1.  PIN Expiration (days).

    1.  Remember PIN history.

    1.  Enable PIN recovery. Allows user to use the Windows Hello for Business PIN recovery service.

    1.  Use a Trusted Platform Module (TPM). A TPM chip provides an additional layer of data security.

    1.  Allow biometric authentication. Enables biometric authentication, such as facial recognition or fingerprint, as an alternative to a PIN for Windows Hello for Business. Users must still configure a PIN in case biometric authentication fails.

    1.  Use enhanced anti-spoofing, when available. Configures when the anti-spoofing features of Windows Hello are used on devices that support it (for example, detecting a photograph of a face instead of a real face).

    1.  Use security keys for sign-in. This setting is available for devices that run Windows 10 version 1903 or later. Use it to manage support for using Windows Hello security keys for sign-in.

Finally, you can create additional device restriction policies to further lock down corporate-owned devices.

> [!TIP]
> [Learn about implementing an end-to-end identity Zero strategy](https://aka.ms/ZTIdentity).

### II. Access is only granted to cloud-managed and compliant endpoints and apps

Once you have identities for all the endpoints accessing corporate resources and before access is granted, you want to ensure that they meet the [minimum security requirements](https://docs.microsoft.com/mem/intune/protect/device-compliance-get-started) set by your organization.

After establishing compliance policies to gate access of corporate resources to trusted endpoints and mobile and desktop [applications](https://aka.ms/ZTApplications), all users can access organizational data on mobile devices and a minimum or maximum operating system version is installed on all devices. Devices are not jail-broken or rooted.

Also, [set remediation rules](https://docs.microsoft.com/mem/intune/protect/actions-for-noncompliance) for noncompliant devices, such as blocking a noncompliant device or offering the user a grace period to get compliant.

:::image type="content" source="./media/steps-box-endpoints-2.png" alt-text="Diagram of the steps within phase 2 of the initial deployment objectives." border="true":::


#### Create a compliance policy with Microsoft Intune (all platforms)

Follow these steps to [create a compliance policy](https://docs.microsoft.com/mem/intune/protect/create-compliance-policy):

1.  Select Devices &gt; Compliance policies &gt; Policies &gt; Create Policy.

1.  Select a Platform for this policy (Windows 10 used for example below).

1.  Select the desired Device Health configuration.

    :::image type="content" source="./media/endpoints/screenshot-windows-10-compliance-policy-device-health-settings.png" alt-text="Screenshot of Device Health in Windows 10 compliance policy settings." border="true":::

1.  Configure minimum or maximum Device Properties.

    :::image type="content" source="./media/endpoints/screenshot-windows-10-compliance-policy-device-properties-settings.png" alt-text="Screenshot of Device Properties in Windows 10 compliance policy settings." border="true":::

1.  Configure Configuration Manager Compliance. This requires all compliance evaluations in Configuration Manager to be compliant and is only applicable for comanaged Windows 10 devices. All Intune-only devices will return N/A.

1.  Configure System Security Settings.

    :::image type="content" source="./media/endpoints/screenshot-windows-10-compliance-policy-system-security-settings.png" alt-text="Screenshot of System Security in Windows 10 compliance policy settings." border="true":::

1.  Configure Microsoft Defender Antimalware.

    :::image type="content" source="./media/endpoints/screenshot-windows-10-compliance-policy-defender-settings.png" alt-text="Screenshot of Microsoft Defender in Windows 10 compliance policy settings." border="true":::

1.  Configure the required Microsoft Defender ATP machine risk score.

    :::image type="content" source="./media/endpoints/screenshot-windows-10-compliance-policy-defender-atp-settings.png" alt-text="Screenshot of Microsoft Defender ATP in Windows 10 compliance policy settings." border="true":::

1.  On the Actions for noncompliance tab, specify a sequence of actions to apply automatically to devices that do not meet this compliance policy.

    :::image type="content" source="./media/endpoints/screenshot-actions-noncompliance-settings.png" alt-text="Screenshot of Actions for noncompliance in compliance policy settings." border="true":::


#### Automate notification email and add additional remediation actions for noncompliant devices in Intune (all platforms)

When their endpoints or apps become non-compliant, users are guided through self-remediation. Alerts are automatically generated with additional alarms and automated actions set for certain thresholds. You can set [non-compliance](https://docs.microsoft.com/mem/intune/protect/create-compliance-policy) remediation actions.

Take these steps:

1.  Select **Devices &gt; Compliance policies &gt; Notifications &gt; Create notification**.

1.  Create a notification message template.

    :::image type="content" source="./media/endpoints/screenshot-create-notifications-message-template.png" alt-text="Screenshot of Create notification in compliance policy settings." border="true":::

1.  Select **Devices &gt; Compliance policies &gt; Policies**, select one of your policies, and then select **Properties**.

1.  Select **Actions for noncompliance &gt; Add**.

1.  Add actions for noncompliance:

    :::image type="content" source="./media/endpoints/screenshot-actions-noncompliance-settings.png" alt-text="Screenshot of Actions for noncompliance in compliance policy settings." border="true":::

    1.  Set up an automated email to users with noncompliant devices.

    1.  Set up an action to remotely lock noncompliant devices.

    1.  Set up an action to automatically retire a noncompliant device after a set number of days.


### III. Data loss prevention (DLP) policies are enforced for corporate devices and BYOD

Once data access is granted, you want to control what the user can do with the data. For example, if a user accesses a document with a corporate identity, you want to prevent that document from being saved in an unprotected consumer storage location, or from being shared with a consumer communication or chat app.

:::image type="content" source="./media/steps-box-endpoints-3.png" alt-text="Diagram of the steps within phase 3 of the initial deployment objectives." border="true":::


#### Apply recommended security settings

First, [apply security settings recommended by Microsoft to Windows 10 devices](https://docs.microsoft.com/mem/intune/protect/security-baselines) to protect corporate data (Requires Windows 10 1809 and later):

Use Intune security baselines to help you secure and protect your users and devices. Security baselines are preconfigured groups of Windows settings that help you apply a known group of settings and default values that are recommended by the relevant security teams.

Follow these steps:

1.  Select Endpoint security &gt; Security baselines to view the list of available baselines.

2.  Select the baseline you\'d like to use, and then select **Create profile**.

3.  On the Configuration settings tab, view the groups of Settings that are available in the baseline you selected. You can expand a group to view the settings in that group and the default values for those settings in the baseline. To find specific settings:

    1.  Select a group to expand and review the available settings.

    1.  Use the Search bar and specify keywords that filter the view to display only those groups that contain your search criteria.

    1.  Reconfigure the default settings to meet your business needs.  

        :::image type="content" source="./media/endpoints/screenshot-create-profile-application-management-settings.png" alt-text="Screenshot of Application Management settings in Create Profile." border="false":::

4.  On the Assignments tab, select groups to include and then assign the baseline to one or more groups. To fine-tune the assignment, use Select groups to exclude.


#### Ensure updates are deployed automatically to endpoints

[Configure Windows 10 devices](https://docs.microsoft.com/mem/intune/protect/windows-update-for-business-configure)

Configure Windows Updates for Business to simplify the update management experience for users and ensure that devices are automatically updated to meet the required compliance level.

Follow these steps:

1.  Manage Windows 10 software updates in Intune by creating update rings and enabling a collection of settings that configure when Windows 10 updates will be installed.

    1.  Select **Devices &gt; Windows &gt; Windows 10 Update Rings &gt; Create**.

    1.  Under **Update ring settings**, configure settings for your business needs.

        :::image type="content" source="./media/endpoints/screenshot-update-settings-user-experience-settings.png" alt-text="Screenshot of Update settings and User experience settings." border="true":::

    1.  Under **Assignments**, choose + Select groups to include, and then assign the update ring to one or more groups. To fine-tune the assignment, use + Select groups to exclude.


1.  Manage Windows 10 feature updates in Intune to bring devices to the Windows version you specify (i.e., 1803 or 1809) and freeze the feature set on those devices until you choose to update them to a later Windows version.

    1.  Select **Devices &gt; Windows &gt; Windows 10 Feature updates &gt; Create**.

    1.  Under **Basics**, specify a name, a description (optional), and, for **Feature update to deploy**, select the version of Windows with the feature set you want, and then select **Next**.

    1.  Under **Assignments**, choose and select groups to include and then assign the feature update deployment to one or more groups.

[Configure iOS devices](https://docs.microsoft.com/mem/intune/protect/software-updates-ios)

For corporate-enrolled devices, configure iOS updates to simplify the update management experience for users and ensure that devices are automatically updated to meet the required compliance level. Configure iOS update policy.

Follow these steps:

1.  Select Devices &gt; Update policies for iOS/iPadOS &gt; Create profile.

2.  On the Basics tab, specify a name for this policy, specify a description (optional), and then select **Next**.

3.  On the Update policy settings tab, configure the following:

    1.  Select version to install. You can choose from:

        1.  Latest update: This deploys the most recently released update for iOS/iPadOS.

        1. Any previous version that is available in the dropdown box. If you select a previous version, you must also deploy a device configuration policy to delay visibility of software updates.

    1.  Schedule type: Configure the schedule for this policy:

        1.  Update at next check-in. The update installs on the device the next time it checks in with Intune. This is the simplest option and has no additional configurations.

        1. Update during scheduled time. You configure one or more windows of time during which the update will install upon check-in.

        1. Update outside of scheduled time. You configure one or more windows of time during which the updates won't install upon check-in.

    1.  Weekly schedule: If you choose a schedule type other than update at next check-in, configure the following options:

        :::image type="content" source="./media/endpoints/screenshot-create-profile-update-policy-settings.png" alt-text="Screenshot of Update policy settings in Create profile." border="true":::

1.  Choose a time zone.

2.  Define a time window. Define one or more blocks of time that restrict when the updates install. Options include start day, start time, end day, and end time. By using a start day and end day, overnight blocks are supported. If you do not configure times to start or end, the configuration results in no restriction and updates can install at any time.


#### Ensure devices are encrypted

[Configure Bitlocker to encrypt Windows 10 devices](https://docs.microsoft.com/mem/intune/protect/encrypt-devices)

1.  Select **Devices &gt; Configuration profiles &gt; Create profile**.

2.  Set the following options:

    1.  Platform: Windows 10 and later

    1.  Profile type: Endpoint protection  

        :::image type="content" source="./media/endpoints/screenshot-devices-configuration-profiles-create-profile-windows.png" alt-text="Screenshot of Create a profile in Devices Configuration profiles for Windows 10." border="false":::

3.  Select **Settings &gt; Windows Encryption**.

    :::image type="content" source="./media/endpoints/screenshot-devices-configuration-create-profile-endpoint-protection.png" alt-text="Screenshot of Endpoint protection in Create profile." border="false":::

4.  Configure settings for BitLocker to meet your business needs, and then select **OK**.

[Configure FileVault encryption on macOS devices](https://docs.microsoft.com/mem/intune/protect/encrypt-devices-filevault)

1.  Select **Devices &gt; Configuration profiles &gt; Create profile**.

2.  Set the following options:

    1.  Platform: macOS.

    1.  Profile type: Endpoint protection.  

        :::image type="content" source="./media/endpoints/screenshot-devices-configuration-profiles-create-profile-macos.png" alt-text="Screenshot of Create a profile in Devices Configuration profiles for mac OS." border="false":::

3.  Select **Settings &gt; FileVault**. 

    :::image type="content" source="./media/endpoints/screenshot-create-profile-Endpoint-protection-filevault.png" alt-text="Screenshot of File Vault under Endpoint protection in Create profile." border="false":::

4.  For FileVault, select **Enable**.

5.  For Recovery key type, only Personal key is supported.

6.  Configure the remaining FileVault settings to meet your business needs, and then select **OK**.


#### Create application protection policies to protect corporate data at the app-level

To ensure your data remains safe or contained in a managed app, [create app protection policies (APP)](https://docs.microsoft.com/mem/intune/apps/app-protection-policy). A policy can be a rule that is enforced when the user attempts to access or move \"corporate\" data, or a set of actions that are prohibited or monitored when the user is inside the app.

The APP data protection framework is organized into three distinct configuration levels, with each level building off the previous level:

-   **Enterprise basic data protection** (Level 1) ensures that apps are protected with a PIN and encrypted, and performs selective wipe operations. For Android devices, this level validates Android device attestation. This is an entry-level configuration that provides similar data protection control in Exchange Online mailbox policies and introduces IT and the user population to APP.

-   **Enterprise enhanced data protection** (Level 2) introduces APP data leakage prevention mechanisms and minimum OS requirements. This is the configuration that is applicable to most mobile users accessing work or school data.

-   **Enterprise high data protection** (Level 3) introduces advanced data protection mechanisms, enhanced PIN configuration, and APP Mobile Threat Defense. This configuration is desirable for users that are accessing high-risk data.

Follow these steps:

1.  In Intune portal, choose **Apps** &gt; **App protection policies**. This selection opens the **App protection policies** details, where you create new policies and edit existing policies.

2.  Select **Create policy** and select either **iOS/iPadOS** or **Android**. The **Create policy** pane is displayed.

3.  Choose the apps that you would like to apply the App Protection Policy to.

4.  Configure Data Protection Settings:

    1.  **iOS/iPadOS data protection.** For information, see [iOS/iPadOS app protection policy settings - Data protection](https://docs.microsoft.com/mem/intune/apps/app-protection-policy-settings-ios#data-protection).

    1.  **Android data protection.** For information, see [Android app protection policy settings - Data protection](https://docs.microsoft.com/mem/intune/apps/app-protection-policy-settings-android#data-protection).

5.  Configure Access Requirement Settings:

    1.  **iOS/iPadOS access requirements**. For information, see [iOS/iPadOS app protection policy settings - Access requirements](https://docs.microsoft.com/mem/intune/apps/app-protection-policy-settings-ios#access-requirements).

    1.  **Android access requirements.** For information, see [Android app protection policy settings - Access requirements](https://docs.microsoft.com/mem/intune/apps/app-protection-policy-settings-android#access-requirements).

6.  Configure Conditional Launch Settings:

    1.  **iOS/iPadOS conditional launch**. For information, see [iOS/iPadOS app protection policy settings - Conditional launch](https://docs.microsoft.com/mem/intune/apps/app-protection-policy-settings-ios#conditional-launch).

    1.  **Android conditional launch**. For information, see [Android app protection policy settings - Conditional launch](https://docs.microsoft.com/mem/intune/apps/app-protection-policy-settings-android#conditional-launch).

7.  Click **Next** to display the **Assignments** page.

8.  When you are done, click **Create** to create the app protection policy in Intune.

> [!TIP]
> [Learn about implementing an end-to-end Zero Trust strategy for data](https://aka.ms/ZTData).


<!-- H2 heading, "Additional deployment objectives" -->
<br/><br/>
[!INCLUDE [H2 heading, Additional deployment objectives](./includes/deployment-objectives-additional.md)]


### IV. Endpoint threat detection is used to monitor device risk

Once you've accomplished your first three objectives, the next step is to configure endpoint security so that advanced protection is provisioned, activated, and monitored. A single pane of glass is used to consistently manage all endpoints together.


#### Route endpoint logs and transactions to a SIEM or Power BI

Using the Intune Data warehouse, [send device and app management data to reporting or SIEM tools](https://docs.microsoft.com/mem/intune/developer/reports-nav-intune-data-warehouse) for intelligent filtering of alerts to reduce noise.

Follow these steps:

1.  Select **Reports &gt; Intune Data warehouse &gt; Data warehouse**.

2.  Copy the custom feed URL. For example:
    `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=v1.0`

3.  Open Power BI Desktop or your SIEM solution.


#### From your SIEM solution

Choose the option to import or get data from an Odata feed.


#### From PowerBI

1.  From the menu, select **File &gt; Get Data &gt; OData feed**.

2.  Paste the custom feed URL that you copied from the earlier step into the URL box in the OData feed window.

3.  Select **Basic**.

4.  Select **OK**.

5.  Select **Organization account**, and then sign in with your Intune credentials.

    :::image type="content" source="./media/endpoints/screenshot-powerbi-basic-organizational-account-odata-feed.png" alt-text="Screenshot of OData feed setting in Organizational account." border="false":::

1.  Select **Connect**. The Navigator will open and show you the list of tables in the Intune Data Warehouse.

2.  Select the devices and the ownerTypes tables. Select **Load**. Power BI loads data to the model.

3.  Create a relationship. You can import multiple tables to analyze not just the data in a single table, but related data across tables. Power BI has a feature called autodetect that attempts to find and create relationships for you. The tables in the Data Warehouse have been built to work with the autodetect feature in Power BI. However, even if Power BI doesn't automatically find the relationships, you can still manage the relationships.

4.  Select **Manage Relationships**.

5.  Select **Autodetect** if Power BI has not already detected the relationships.

6.  Learn [advanced ways to set up PowerBI visualizations](https://docs.microsoft.com/mem/intune/developer/reports-proc-create-with-odata#create-a-treemap-visualization).


### V. Access control is gated on endpoint risk for both corporate devices and BYOD

#### Corporate devices are enrolled with a cloud enrollment service such as DEP, Android Enterprise, or Windows AutoPilot

Building and maintaining customized operating system images is a time-consuming process, and may include spending time applying custom operating system images to new devices to prepare them for use.

-   With Microsoft Intune cloud enrollment services, you can give new devices to your users without the need to build, maintain, and apply custom operating system images to the devices.

-   Windows Autopilot is a collection of technologies used to set up and preconfigure new devices, getting them ready for productive use. You can also use Windows Autopilot to reset, repurpose, and recover devices.

-   [Configure Windows Autopilot to automate Azure AD Join](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot) and enroll new corporate-owned devices into Intune.

-   [Configure Apple DEP](https://docs.microsoft.com/mem/intune/enrollment/device-enrollment-program-enroll-ios) to automatically enroll iOS and iPadOS devices.

## Products covered in this guide

**Microsoft Azure**

[Azure Active Directory](https://azure.microsoft.com/services/active-directory/)

**Microsoft 365**

[Microsoft Endpoint Manager](https://www.microsoft.com/endpointmanager)
(includes Microsoft Intune and Configuration Manager)

[Microsoft Defender Advanced Threat Protection](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp#:~:text=Microsoft%20Defender%20ATP%20is%20a%20unified%20endpoint%20security,support%20via%20our%20first-party%20offerings%20and%20through%20partners%3A)

[Bitlocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)

## Conclusion

A Zero Trust approach can significantly strengthen the security posture of your devices and endpoints. For further information or help with implementation, please contact your Customer Success team, or continue to read through the other chapters of this guide that spans all Zero Trust pillars.


<br/><br/>
[!INCLUDE [navbar, bottom](./includes/navbar-bottom.md)]

