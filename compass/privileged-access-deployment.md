---
title: Deploying a privileged access solution
description: Configuring and deploying components of a privileged access solution

ms.service: security
ms.subservice: 
ms.topic: how-to
ms.date: 06/07/2021

ms.author: joflore
author: MicrosoftGuyJFlo
manager: daveba
ms.reviewer: frasim
---
# Privileged access deployment

This document will guide you through implementing the technical components of the [privileged access strategy](), including secure accounts, workstations and devices, and interface security (with conditional access policy).

![Summary of security level profiles](./media/privileged-access-deployment/privileged-access-deployment-profile-summary.png)

This guidance sets up all of the profiles for all three security levels and should be assigned your organizations roles based on the [Privileged access security levels](privileged-access-security-levels.md) guidance. Microsoft recommends configuring them in the order described in the [rapid modernization plan (RAMP)](security-rapid-modernization-plan.md)

## License requirements

The concepts covered in this guide assume you have Microsoft 365 Enterprise E5 or an equivalent SKU. Some of the recommendations in this guide can be implemented with lower SKUs. For more information, see [Microsoft 365 Enterprise licensing](https://www.microsoft.com/licensing/product-licensing/microsoft-365-enterprise).

To automate license provisioning, consider [group-based licensing](/azure/active-directory/enterprise-users/licensing-groups-assign) for your users.

## Azure Active Directory configuration

Azure Active Directory (Azure AD) manages users, groups, and devices for your administrator workstations. Enable identity services and features with an [administrator account](/azure/active-directory/roles/permissions-reference).

When you create the secured workstation administrator account, you expose the account to your current workstation. Make sure you use a known safe device to do this initial configuration and all global configuration. To reduce the attack exposure for the first-time experience, consider following the [guidance to prevent malware infections](/windows/security/threat-protection/intelligence/prevent-malware-infection).

Require multi-factor authentication, at least for your administrators. See [Conditional Access: Require MFA for administrators](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) for implementation guidance.

### Azure AD users and groups

1. From the Azure portal, browse to **Azure Active Directory** > **Users** > **New user**.
1. Create your device user by following the steps in the [create user tutorial](/Intune/quickstart-create-user).
1. Enter:
   * **Name** - Secure Workstation User
   * **User name** - `secure-ws-user@contoso.com`
   * **Directory role** - **Limited administrator** and select the **Intune Administrator** role.
   * **Usage Location** - **United Kingdom**

1. Select **Create**.

Create your device administrator user.

1. Enter:

   * **Name** - Secure Workstation Administrator
   * **User name** - `secure-ws-admin@contoso.com`
   * **Directory role** - **Limited administrator** and select the **Intune Administrator** role.

1. Select **Create**.

Next, you create four groups: **Secure Workstation Users**, **Secure Workstation Admins**, **Emergency BreakGlass** and **Secure Workstation Devices**.

From the Azure portal, browse to **Azure Active Directory** > **Groups** > **New group**.

1. For the workstation users group, you might want to configure [group-based licensing](/azure/active-directory/enterprise-users/licensing-groups-assign) to automate provisioning of licenses to users.
1. For the workstation users group, enter:

   * **Group type** - Security
   * **Group name** - Secure Workstation Users
   * **Membership type** - Assigned

1. Add your secure workstation user: `secure-ws-user@contoso.com`
1. You can add any other users that will be using secure workstations.
1. Select **Create**.
1. For the Privileged Workstation Admins group, enter:

   * **Group type** - Security
   * **Group name** - Secure Workstation Admins
   * **Membership type** - Assigned

1. Add your secure workstation user: `secure-ws-admin@contoso.com`
1. You can add any other users that will be managing secure workstations.  
1. Select **Create**.
1. For the Emergency BreakGlass group, enter:

   * **Group type** - Security
   * **Group name** - Emergency BreakGlass
   * **Membership type** - Assigned
  
1. Select **Create**.
1. Add Emergency Access accounts to this group.
1. For the workstation devices group, enter:

   * **Group type** - Security
   * **Group name** - Secure Workstations
   * **Membership type** - Dynamic Device
   * **Dynamic Membership rules** - `(device.devicePhysicalIds -any _ -contains "[OrderID]:PAW")`

1. Select **Create**.

### Azure AD device configuration

#### Specify who can join devices to Azure AD

Configure your devices setting in Active Directory to allow your administrative security group to join devices to your domain. To configure this setting from the Azure portal:

1. Go to **Azure Active Directory** > **Devices** > **Device settings**.
1. Choose **Selected** under **Users may join devices to Azure AD**, and then select the "Secure Workstation Users" group.

#### Remove local admin rights

This method requires that users of the VIP, DevOps, and Privileged workstations have no administrator rights on their machines. To configure this setting from the Azure portal:

1. Go to **Azure Active Directory** > **Devices** > **Device settings**.
1. Select **None** under **Additional local administrators on Azure AD joined devices**.

Refer to [How to manage the local administrators group on Azure AD joined devices](/azure/active-directory/devices/assign-local-admin) for details on how to manage members of the local administrators group.

#### Require multi-factor authentication to join devices

To further strengthen the process of joining devices to Azure AD:

1. Go to **Azure Active Directory** > **Devices** > **Device settings**.
1. Select **Yes** under **Require Multi-Factor Auth to join devices**.
1. Select **Save**.

#### Configure mobile device management

From the Azure portal:

1. Browse to **Azure Active Directory** > **Mobility (MDM and MAM)** > **Microsoft Intune**.
1. Change the **MDM user scope** setting to **All**.
1. Select **Save**.

These steps allow you to manage any device with Microsoft Endpoint Manager. For more information, see [Intune Quickstart: Set up automatic enrollment for Windows 10 devices](/Intune/quickstart-setup-auto-enrollment). You create Intune configuration and compliance policies in a future step.

### Azure AD Conditional Access

Azure AD Conditional Access can help restrict privileged administrative tasks to compliant devices. Predefined members of the **Secure Workstation Users** group are required to perform multi-factor authentication when signing in to cloud applications. A best practice is to exclude emergency access accounts from the policy. For more information, see [Manage emergency access accounts in Azure AD](/azure/active-directory/roles/security-emergency-access).

#### Conditional Access only allowing secured workstation ability to access Azure portal

Azure AD offers the ability to manage and restrict, who and what can access your Azure cloud management portal. Enabling [Conditional Access](/azure/active-directory/conditional-access/overview) will assure that only your secure workstation can manage or change resources. It's essential that while deploying this feature you consider, if [emergency access](/azure/active-directory/roles/security-emergency-access) functionality can or should be used only for extreme cases and the account managed through policy.

 > [!NOTE]
 > You will need to create a user group, and include your emergency user that can bypass the Conditional Access policy. For our example we have a security group called **Emergency BreakGlass**

1. In the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431), choose **Devices** > **Conditional Access** > **New Policy**.
1. Provide a **Name** for the policy.
1. Select **User and Groups** > **Select users and groups**
1. Select **Include** > **Directory roles** > Choose the roles > Global Administrator, Privileged Role Administrator, Privileged Authentication Administrator, Security Administrator, Compliance Administrator, Conditional Access Administrator, Application Administrator, Cloud Application Administrator, Intune Service Administrator
1. Select **Exclude** > Choose **Users and groups** > Select **Select excluded users** > Select your **Emergency BreakGlass** group.
1. Select **Cloud apps or actions** > Select **All cloud apps**
1. Select **Conditions** > Select **Device Platforms** > Choose configure **Yes** > Select **Select Device platforms** Choose **Windows**
1. Select **Access controls** > Select **Grant Access** **Yes** > Choose **Require device to be marked as compliant**.
1. Select **Enable Policy** > **On**

This policy set will ensure that your Administrators must use a compliant Windows device, which is set by Microsoft Endpoint Manager, and Microsoft Defender for Endpoint.

Organizations should also consider blocking legacy authentication protocols in their environments. There are multiple ways to accomplish this task, for more information about blocking legacy authentication protocols, see the article, [How to: Block legacy authentication to Azure AD with Conditional Access](/azure/active-directory/conditional-access/block-legacy-authentication).

## Microsoft Intune configuration

### Device enrollment deny BYOD

In our sample, we recommend that BYOD devices not be permitted. Using [Intune BYOD enrollment](/mem/intune/enrollment/windows-enrollment-methods) allows users to enroll devices that are less, or not trusted. However it's important to note that in organizations that have a limited budget to purchase new devices, looking to use existing hardware fleet, or considering non-windows devices, might consider the BYOD capability in Intune to deploy the Enterprise profile.

The following guidance will configure Enrollment for deployments that will deny BYOD access.

### Set enrollment restrictions preventing BYOD

1. In the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431), choose > **Devices** > **Enrollment restrictions** > choose the default restriction **All Users**  
1. Select **Properties** > Platform settings **Edit**
1. Select **Block** for All types, except Windows MDM.
1. Select **Block** for all Personally owned items.

### Create an Autopilot deployment profile

After creating a device group, you must create a deployment profile to configure the Autopilot devices.

1. In the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431), choose **Device enrollment** > **Windows enrollment** > **Deployment Profiles** > **Create Profile**.
1. Enter:
   * Name - **Secure workstation deployment profile**.
   * Description - **Deployment of secure workstations**.
   * Set **Convert all targeted devices to Autopilot** to **Yes**. This setting makes sure that all devices in the list get registered with the Autopilot deployment service. Allow 48 hours for the registration to be processed.

1. Select **Next**.

   * For **Deployment mode**, choose [**Self-Deploying (Preview)**](/mem/autopilot/self-deploying). Devices with this profile are associated with the user who enrolls the device. During the deployment, it is advisable to use the Self-Deployment mode features to include:
      * Enrolls the device in Intune Azure AD automatic MDM enrollment, and only allow for a device to be accessed until all policies, applications, certificates, and networking profiles are provisioned on the device.
      * User credentials are required to enroll the device. It's essential to note that deploying a device in the **Self-Deploying** mode will allow you to deploy laptops in a shared model. No user assignment will happen until the device is assigned to a user for the first time. As a result, any user policies such as BitLocker will not be enabled until a user assignment is completed. For more information about how to log on to a secured device, see [selected profiles](/intune/device-profile-assign). 
   * Select your Language (Region), User account type **standard**. 

1. Select **Next**.

   * Select a scope tag if you have preconfigured one.

1. Select **Next**.
1. Choose **Assignments** > **Assign to** > **Selected Groups**. In **Select groups to include**, choose **Secure Workstations**.
1. Select **Next**.
1. Select **Create** to create the profile. The Autopilot deployment profile is now available to assign to devices.

Device enrollment in Autopilot provides a different user experience based on device type and role. In our deployment example, we illustrate a model where the secured devices are bulk deployed and can be shared, but when used for the first time, the device is assigned to a user. For more information, see [Intune Autopilot device enrollment](/intune/device-enrollment).

### Enrollment Status Page

The Enrollment Status Page (ESP) displays provisioning progress after a new device is enrolled. To ensure that devices are fully configured before use, Intune provides a means to **Block device use until all apps and profiles are installed**.

#### Create and assign enrollment status page profile

1. In the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431), choose **Devices** > **Windows** > **Windows enrollment** > **Enrollment Status Page** > **Create profile**.
1. Provide a **Name** and **Description**.
1. Choose **Create**.
1. Choose the new profile in the **Enrollment Status Page** list.
1. Set **Show app profile installation progress** to **Yes**.
1. Set **Block device use until all apps and profiles are installed** to **Yes**.
1. Choose **Assignments** > **Select groups** > choose `Secure Workstation` group > **Select** > **Save**.
1. Choose **Settings** > choose the settings you want to apply to this profile > **Save**.

### Configure Windows Update

Keeping Windows 10 up to date is one of the most important things you can do. To maintain Windows in a secure state, you deploy an [update ring](/deployment/update/waas-deployment-rings-windows-10-updates) to manage the pace that updates are applied to workstations. 

This guidance recommends that you create a new update ring and change the following default settings:

1. In the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431), choose **Devices** > **Software updates** > **Windows 10 Update Rings**.
1. Enter:
   * Name - **Azure-managed workstation updates**
   * Servicing channel - **Semi-annual channel**
   * Quality update deferral (days) - **3**
   * Feature update deferral period (days) - **3**
   * Automatic update behavior - **Auto install and reboot without end-user control**
   * Block user from pausing Windows updates - **Block**
   * Require user's approval to restart outside of work hours - **Required**
   * Allow user to restart (engaged restart) - **Required**
   * Transition users to engaged restart after an auto-restart (days) - **3**
   * Snooze engaged restart reminder (days) - **3**
   * Set deadline for pending restarts (days) - **3**

1. Select **Create**.
1. On the **Assignments** tab, add the **Secure Workstations** group.

For more information about Windows Update policies, see [Policy CSP - Update](/windows/client-management/mdm/policy-csp-update).

### Microsoft Defender for Endpoint Intune integration

[Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) and Microsoft Intune work together to help prevent security breaches. They can also limit the impact of breaches. ATP capabilities provide real-time threat detection as well as enable extensive auditing and logging of the end-point devices.

To configure integration of Windows Defender for Endpoint and Microsoft Endpoint Manager:

1. In the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431), choose **Endpoint Security** > **Microsoft Defender ATP**.
1. In step 1 under **Configuring Windows Defender ATP**, select **Connect Windows Defender ATP to Microsoft Intune in the Windows Defender Security Center​**.
1. In the Windows Defender Security Center:

   1. Select **Settings** > **Advanced features**.
   1. For **Microsoft Intune connection**, choose **On**.
   1. Select **Save preferences**.

1. After a connection is established, return to Microsoft Endpoint Manager and select **Refresh** at the top.
1. Set **Connect Windows devices version(20H2) 19042.450 and above to Windows Defender ATP** to **On**.
1. Select **Save**.

### Create the device configuration profile to onboard Windows devices

1. Sign in to the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431), choose **Endpoint security** > **Endpoint detection and response** > **Create profile**.
1. For **Platform**, select **Windows 10 and Later**.
1. For **Profile type**, select **Endpoint detection and response**, and then select **Create**.
1. On the **Basics** page, enter a *PAW - Defender for Endpoint* in the Name field and *Description* (optional) for the profile, then choose **Next**.
1. On the **Configuration settings** page, configure the following option in **Endpoint Detection and Response**:
  
   * **Sample sharing for all files**: Returns or sets the Microsoft Defender Advanced Threat Protection Sample Sharing configuration parameter.

     [Onboard Windows 10 machines using Microsoft Endpoint Configuration Manager](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-sccm) has more details on these Microsoft Defender ATP settings.

1. Select **Next** to open the **Scope tags** page. Scope tags are optional. Select **Next** to continue.

1. On the **Assignments** page, select *Secure Workstation* group. For more information on assigning profiles, see [Assign user and device profiles](/mem/intune/configuration/device-profile-assign).

   Select **Next**.

1. On the **Review + create** page, when you're done, choose **Create**. The new profile is displayed in the list when you select the policy type for the profile you created.
 **OK**, and then **Create** to save your changes, which creates the profile.

For more information, see [Windows Defender Advanced Threat Protection](/Windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection).

### Finish workstation profile hardening

To successfully complete the hardening of the solution, download and execute the appropriate script. Find the download links for your desired **profile level**:

| Profile | Download location | Filename |
| --- | --- | --- |
| Enterprise | https://aka.ms/securedworkstationgit | Enterprise-Workstation-Windows10-(20H2).ps1 |
| Specialized | https://aka.ms/securedworkstationgit | Specialized - Windows10-(20H2).ps1 |
| Privileged | https://aka.ms/securedworkstationgit | Privileged-Windows10-(20H2).ps1 |

> [!NOTE]
> The removal of of admin rights and access, as well as, Application execution control (AppLocker) are managed by the policy profiles that are deployed.  

After the script successfully executes, you can make updates to profiles and policies in Intune. The scripts will create policies and profiles for you, but you must assign the policies to your **Secure Workstations** device group.

* Here's where you can find the Intune device configuration profiles created by the scripts: **Azure portal** > **Microsoft Intune** > **Device configuration** > **Profiles**.
* Here's where you can find the Intune device compliance policies created by the scripts: **Azure portal** > **Microsoft Intune** > **Device Compliance** > **Policies**.

Run the Intune data export script `DeviceConfiguration_Export.ps1` from the [DeviceConfiguration GitHub repository](https://github.com/microsoftgraph/powershell-intune-samples/tree/master/DeviceConfiguration) to export all current Intune profiles for comparison, and evaluation of the profiles.

## Set rules in the Endpoint Protection Configuration Profile for Microsoft Defender Firewall

Windows Defender Firewall policy settings are included in the Endpoint Protection Configuration Profile. The behavior of the policy applied in described in the table below.

| Profile |Inbound Rules | Outbound Rules | Merge behavior |
| --- | --- | --- | --- |
| Enterprise | Block | Allow | Allow |
| Specialized | Block | Allow | Block |
| Privileged | Block | Block  | Block|

**Enterprise**: This configuration is the most permissive as it mirrors the default behavior of a Windows Install. All inbound traffic is blocked except for rules that are explicitly defined in the local policy rules as merging of local rules is set to allowed.  All outbound traffic is allowed.

**Specialized**: This configuration is more restrictive as it ignores all locally defined rules on the device. All inbound traffic is blocked including locally defined rules the policy includes two rules to allow Delivery Optimization to function as designed. All outbound traffic is allowed.

**Privileged**: All inbound traffic is blocked including locally defined rules the policy includes two rules to allow Delivery Optimization to function as designed. Outbound traffic is also blocked apart from explicit rules that allow DNS, DHCP, NTP, NSCI, HTTP, and HTTPS traffic. This configuration not only reduces the attack surface presented by the device to the network it limits the outbound connections that the device can establish to only those connections required to administer cloud services.

| Rule | Direction | Action | Application / Service | Protocol | Local Ports | Remote Ports |
| --- | --- | --- | --- | --- | --- | --- |
| World Wide Web Services (HTTP Traffic-out) | Outbound | Allow | All | TCP | All ports | 80 |
| World Wide Web Services (HTTPS Traffic-out) | Outbound | Allow | All | TCP | All ports | 443 |
| Core Networking - Dynamic Host Configuration Protocol for IPv6(DHCPV6-Out) | Outbound | Allow | %SystemRoot%\system32\svchost.exe | TCP | 546| 547 |
| Core Networking - Dynamic Host Configuration Protocol for IPv6(DHCPV6-Out) | Outbound | Allow | Dhcp | TCP | 546| 547 |
| Core Networking - Dynamic Host Configuration Protocol for IPv6(DHCP-Out) | Outbound | Allow | %SystemRoot%\system32\svchost.exe | TCP | 68 | 67 |
| Core Networking - Dynamic Host Configuration Protocol for IPv6(DHCP-Out) | Outbound | Allow | Dhcp | TCP | 68 | 67 |
| Core Networking - DNS (UDP-Out) | Outbound | Allow | %SystemRoot%\system32\svchost.exe | UDP | All Ports | 53 |
| Core Networking - DNS (UDP-Out) | Outbound | Allow | Dnscache | UDP | All Ports | 53 |
| Core Networking - DNS (TCP-Out) | Outbound | Allow | %SystemRoot%\system32\svchost.exe | TCP | All Ports | 53 |
| Core Networking - DNS (TCP-Out) | Outbound | Allow | Dnscache | TCP | All Ports | 53 |
| NSCI Probe (TCP-Out) | Outbound | Allow | %SystemRoot%\system32\svchost.exe | TCP | All ports | 80 |
| NSCI Probe - DNS (TCP-Out) | Outbound | Allow | NlaSvc | TCP | All ports | 80 |
| Windows Time (UDP-Out) | Outbound | Allow | %SystemRoot%\system32\svchost.exe | TCP | All ports | 80 |
| Windows Time Probe - DNS (UDP-Out) | Outbound | Allow | W32Time | UDP | All ports | 123 |
| Delivery Optimization (TCP-In) | Inbound | Allow | %SystemRoot%\system32\svchost.exe | TCP | 7680 | All ports |
| Delivery Optimization (TCP-In) | Inbound | Allow | DoSvc | TCP | 7680 | All ports |
| Delivery Optimization (UDP-In) | Inbound | Allow | %SystemRoot%\system32\svchost.exe | UDP | 7680 | All ports |
| Delivery Optimization (UDP-In) | Inbound | Allow | DoSvc | UDP | 7680 | All ports |

> [!NOTE]
> There are two rules defined for each rule in the Microsoft Defender Firewall configuration. To restrict the inbound and outbound rules to Windows Services, e.g. DNS Client, both the service name, DNSCache, and the executable path, C:\Windows\System32\svchost.exe, need to be defined as separate rule rather than a single rule that is possible using Group Policy.

You can make additional changes to the management of both inbound and outbound rules as needed for your permitted and blocked services. For more information, see [Firewall configuration service](/windows/security/threat-protection/windows-firewall/create-windows-firewall-rules-in-intune).

### URL lock proxy

Restrictive URL traffic management includes:

* Deny All outbound traffic except selected Azure and Microsoft services including Azure Cloud Shell and the ability to allows self-service password reset.
* The Privileged profile restricts the endpoints on the internet that the device can connect to using the following URL Lock Proxy configuration.

```
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Internet Settings]
"ProxyEnable"=dword:00000001
"ProxyServer"="127.0.0.2:8080"
"ProxyOverride"="*.azure.com;*.azure.net;*.microsoft.com;*.windowsupdate.com;*.microsoftonline.com;*.microsoftonline.cn;*.windows.net;*.windowsazure.com;*.windowsazure.cn;*.azure.cn;*.loganalytics.io;*.applicationinsights.io;*.vsassets.io;*.azure-automation.net;*.visualstudio.com,portal.office.com;*.aspnetcdn.com;*.sharepointonline.com;*.msecnd.net;*.msocdn.com;*.webtrends.com"
"AutoDetect"=dword:00000000
```

The endpoints listed in the ProxyOverride list are limited to those endpoints needed to authenticate to Azure AD and access Azure or Office 365 management interfaces.  To extend to other cloud services, add their administration URL to the list. This approach is designed to limit access to the wider internet to protect privileged users from internet-based attacks. If this approach is deemed too restrictive, then consider using the approach described below for the privileged role.

## Enable Microsoft Cloud Application Security, URLs restricted list to approved URLs (Allow most)

In our roles deployment it is recommended that for Enterprise, and Specialized deployments, where a strict *deny all* web browsing is not desirable, that using the capabilities of a Cloud Access Security Broker (CASB) such as [Microsoft Cloud App. Security (MCAS)](/cloud-app-security/what-is-cloud-app-security) be utilized to block access to risky, and questionable web sites. The solution addresses a simple way to block applications and websites that have been curated. This solution is similar to getting access to the block list from sites such as the Spamhaus Project who maintains [the Domain Block List (DBL)](https://www.spamhaus.org/dbl/): a good resource to use as an advanced set of rules to implement for blocking sites. 

The solution will provide you:

* Visibility: detect all cloud services; assign each a risk ranking; identify all users and third-party apps able to log in
* Data security: identify and control sensitive information (DLP); respond to classification labels on content
* Threat protection: offer adaptive access control (AAC); provide user and entity behavior analysis (UEBA); mitigate malware
* Compliance: supply reports and dashboards to demonstrate cloud governance; assist efforts to conform to data residency and regulatory compliance requirements

Enable MCAS and connect to Defender ATP to block access the risky URLs:

* In [Microsoft Defender Security Center](https://securitycenter.windows) > Settings > Advanced features, set Microsoft Cloud App Security integration > **ON**
* In [Microsoft Defender Security Center](https://securitycenter.windows)  > Settings > Advanced features, set Custom network indicators >  **ON**
* In [Microsoft Cloud App Security portal](https://portal.cloudappsecurity.com) > Settings > Microsoft Defender ATP integration > Select **Block unsanctioned apps**  

## Manage local applications

The secure workstation moves to a truly hardened state when local applications are removed, including productivity applications. Here, you add Visual Studio Code to allow connection to Azure DevOps for GitHub to manage code repositories.

### Configuring the Company Portal your for custom apps

An Intune-managed copy of the [Company Portal](/Intune/store-apps-company-portal-app) gives you on-demand access to additional tools that you can push down to users of the secured workstations.

In a secured mode, application installation is restricted to managed applications that are delivered by Company Portal. However, installing the Company Portal requires access to Microsoft Store. In your secured solution, you [add and assign the Windows 10 Company Portal app for Autopilot provisioned devices](/mem/intune/apps/store-apps-company-portal-autopilot).

> [!NOTE]
> Make sure you assign the Company Portal app to the **Secure Workstation Device Tag** group used to assign the Autopilot profile.

### Deploy applications using Intune

In some situations, applications like the Microsoft Visual Studio Code are required on the secured workstation. The following example provides instructions to install Microsoft Visual Studio Code to users in the security group **Secure Workstation Users**.

Visual Studio Code is provided as an EXE package so it needs to be packaged as an `.intunewin` format file for deployment using Microsoft Endpoint Manager using the [Microsoft Win32 Content Prep Tool](https://github.com/Microsoft/Microsoft-Win32-Content-Prep-Tool).

Download the Microsoft Win32 Content Prep Tool locally to a workstation and copy it to a directory for packaging, for example, C:\Packages. Then create a Source and Output directory under C:\Packages.

#### Package Microsoft Visual Studio Code

1. Download the offline installer [Visual Studio Code for Windows 64-bit](https://aka.ms/win32-x64-user-stable).
1. Copy the downloaded Visual Studio Code exe file to `C:\Packages\Source`
1. Open a PowerShell console and navigate to `C:\Packages`
1. Type `.\IntuneWinAppUtil.exe -c C:\Packages\Source\ -s C:\Packages\Source\VSCodeUserSetup-x64-1.51.1.exe -o C:\Packages\Output\VSCodeUserSetup-x64-1.51.1`
1. Type `Y` to create the new output folder. The intunewin file for Visual Studio Code will be created in this folder.

#### Upload VS Code to Microsoft Endpoint Manager

1. In the **Microsoft Endpoint Manager admin center**, browse to **Apps** > **Windows** > **Add**
1. Under **Select app type**, choose **Windows app (Win32)**
1. Click **Select app package file**, click **Select a file**, then select the `VSCodeUserSetup-x64-1.51.1.intunewin` from `C:\Packages\Output\VSCodeUserSetup-x64-1.51.1`. Click **OK**
1. Enter `Visual Studio Code 1.51.1` in the Name field
1. Enter a description for Visual Studio Code in the **Description** field
1. Enter `Microsoft Corporation` in the **Publisher** Field
1. Download `https://jsarray.com/images/page-icons/visual-studio-code.png` and select image for the logo. Select **Next**
1. Enter `VSCodeSetup-x64-1.51.1.exe /SILENT` in the **Install command** field
1. Enter `C:\Program Files\Microsoft VS Code\unins000.exe` in the **Uninstall command** field
1. Select **Determine behavior based on return codes** from the **Device Restart behavior** dropdown list.  Select **Next**
1. Select **64-bit** from the **Operating system architecture** checkbox dropdown
1. Select **Windows 10 1903** from the **Minimum operating system** checkbox dropdown. Select **Next**
1. Select **Manually configure** detection rules from the **Rules format** dropdown list
1. Click **Add** and then select **File** form the **Rule type** dropdown
1. Enter `C:\Program Files\Microsoft VS Code` in the **Path** field
1. Enter `unins000.exe` in the **File or folder** field
1. Select **File or folder exists** from the dropdown list, Select **OK** and then select **Next**
1. Select **Next** as there are no dependencies on this package
1. Select **Add Group** under **Available for enrolled devices**, add **Privileged Users group**.  Click **Select** to confirm group. Select **Next** 
1. Click **Create**

### Use PowerShell to create custom apps and settings

There are some configuration settings that we recommend, including two Defender for Endpoint recommendations, that must be set using PowerShell. These configuration changes cannot be set via policies in Intune.

You can also use PowerShell to extend host management capabilities. The [PAW-DeviceConfig.ps1]() script from GitHub is an example script that configures the following settings:

* Removes Internet Explorer
* Removes PowerShell 2.0
* Removes Windows Media Player
* Removes Work Folders Client
* Removes XPS Printing
* Enables and configures Hibernate
* Implements registry fix to enable AppLocker DLL rule processing
* Implements registry settings for two Microsoft Defender for Endpoint recommendations that cannot be set using Endpoint Manager.
  * Require users to elevate when setting a network's location
  * Prevent saving of network credentials
* Disable Network Location Wizard - prevents users from setting network location as Private and therefore increasing the attack surface exposed in Windows Firewall
* Configures Windows Time to use NTP and sets the Auto Time service to Automatic
* Downloads and sets the desktop background to a specific image to easily identify the device as a ready-to-use, privileged workstation.

The [PAW-DeviceConfig.ps1]() script from GitHub.

1. Download the script [PAW-DeviceConfig.ps1] to a local device.
1. Browse to the **Azure portal** > **Microsoft Intune** > **Device configuration** > **PowerShell scripts** > **Add**.
vProvide a **Name** for the script and specify the **Script location**.
1. Select **Configure**.
   1. Set **Run this script using the logged on credentials** to **No**.
   1. Select **OK**.
1. Select **Create**.
1. Select **Assignments** > **Select groups**.
   1. Add the security group **Secure Workstations**.
   1. Select **Save**.

## Validate and test your deployment with your first device

This enrollment assumes that you will use a physical computing device. It is recommended that as part of the procurement process that the OEM, Reseller, distributor, or partner [register devices in Windows Autopilot](/mem/autopilot/add-devices).

However for testing it is possible to stand up [Virtual Machines](/windows/deployment/windows-autopilot/demonstrate-deployment-on-vm) as a test scenario. However note enrollment of personally joined devices will need to be revised to allow this method of joining a client.

This method works for Virtual Machines or physical devices that have not been previously registered.

1. Start the device and wait for the username dialog to be presented
1. Press `SHIFT + F10` to display command prompt
1. Type `PowerShell`, hit Enter
1. Type `Set-ExecutionPolicy RemoteSigned`, hit Enter
1. Type `Install-Script GetWindowsAutopilotInfo`, hit Enter
1. Type `Y` and click Enter to accept PATH environment change
1. Type `Y` and click Enter to install NuGet provider
1. Type `Y` to trust the repository 
1. Type Run `Get-WindowsAutoPilotInfo -GroupTag PAW –outputfile C:\device1.csv`
1. Copy the CSV from the Virtual Machine or Physical device

## Import devices into Autopilot

1. In the **Microsoft Endpoint Manager admin center**, go to **Devices** > **Windows Devices** > **Windows enrollment** > **Devices**
1. Select **Import** and choose your CSV file.
1. Wait for the `Group Tag` to be updated to `PAW` and the `Profile Status` to change to `Assigned`. 

   > [!NOTE]
   > The Group Tag is used by the Secure Workstation dynamic group to make the device a member of its group, 

1. Add the device to the **Secure Workstations** security group.
1. On the Windows 10 device you wish to configure, go to **Windows Settings** > **Update & Security** > **Recovery**.
   1. Choose **Get started** under **Reset this PC**.
   1. Follow the prompts to reset and reconfigure the device with the profile and compliance policies configured.

After you have configured the device, complete a review and check the configuration. Confirm that the first device is configured correctly before continuing your deployment.

### Assign devices

To assign devices and users, you need to map the [selected profiles](/intune/device-profile-assign) to your security group. All new users who require permissions to the service must be added to the security group as well.

## Using Microsoft Defender for Endpoint to monitor and respond to security incidents

* Continuously observe and monitor vulnerabilities and misconfigurations
* Utilize Microsoft Defender for Endpoint to prioritize dynamic threats in the wild
* Drive correlation of vulnerabilities with endpoint detection and response (EDR) alerts
* Use the dashboard to identify machine-level vulnerability during investigations
* Push out remediations to Intune

Configure your [Microsoft Defender Security Center](https://securitycenter.windows.com/machines). Using guidance at [Threat & Vulnerability Management dashboard overview](/windows/security/threat-protection/microsoft-defender-atp/tvm-dashboard-insights).

### Monitoring application activity using Advanced Threat Hunting

Starting at the Specialized workstation, AppLocker is enabled for monitoring of application activity on a workstation. By default Defender for Endpoint captures AppLocker events and Advanced Hunting Queries can be used to determine what applications, scripts, DLL files are being blocked by AppLocker.

> [!NOTE]
> The Specialized and Privileged workstation profiles contain the AppLocker policies. Deployment of the policies is required for monitoring of application activity on a client.

From the Microsoft Defender Security Center Advanced Hunting pane, use the following query to return AppLocker events

```Kusto
DeviceEvents
| where Timestamp > ago(7d) and
ActionType startswith "AppControl"
| summarize Machines=dcount(DeviceName) by ActionType
| order by Machines desc
```

## Monitoring

* Understand how to review your [Exposure Score](/windows/security/threat-protection/microsoft-defender-atp/tvm-exposure-score)
* Review [Security recommendation](/windows/security/threat-protection/microsoft-defender-atp/tvm-security-recommendation)
* Manage security [remediations](/windows/security/threat-protection/microsoft-defender-atp/tvm-remediation)
* Manage [endpoint detection and response](/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response)
* Monitor profiles with [Intune profile monitoring](/intune/device-profile-monitor).

## Next steps

- [Securing privileged access overview](overview.md)
- [Privileged access strategy](privileged-access-strategy.md)
- [Measuring success](privileged-access-success-criteria.md)
- [Security levels](privileged-access-security-levels.md)
- [Privileged access accounts](privileged-access-accounts.md)
- [Intermediaries](privileged-access-intermediaries.md)
- [Interfaces](privileged-access-interfaces.md)
- [Privileged access devices](privileged-access-devices.md)
- [Enterprise access model](privileged-access-access-model.md)
