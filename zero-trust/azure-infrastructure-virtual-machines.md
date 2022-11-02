---
title: Apply Zero Trust principles to virtual machines in Azure 
description: Learn how to secure virtual machines in Azure with Zero Trust.  
ms.date: 10/20/2022
ms.service: security
author: sikovatc
ms.author: sikovatc
ms.topic: conceptual
ms.collection: 
  - msftsolution-accesscontrol
  - msftsolution-scenario
  - zerotrust-solution
---
# Apply Zero Trust principles to virtual machines(VM)

This article helps you apply the principles of Zero Trust to virtual machines in Azure:

- Verify explicitly
- Use least privileged access
- Assume breach

This article is part of a series of articles that demonstrate how to apply the principles of Zero Trust across an environment in Azure that includes a spoke Vnet hosting a virtual machine-based workload. For more information, see [Overview – Apply Zero Trust principles to Azure infrastructure.](azure-infrastructure-overview.md)

## Logical architecture for virtual machines

Zero trust principles for virtual machines are applied across the logical architecture, from the tenant and directory level down to the data and application layer within each virtual machine.

The following illustration provides a reference of logical architecture components.

:::image type="content" source="media/vm/storage-security-configure.png" alt-text="Diagram of storage security configuration." lightbox="media/vm/storage-security-configure.png":::

In this illustration:

- Illustrated on the left (A) is a series of virtual machines isolated within a dedicated resource group that sits within an Azure Subscription. 
- Illustrated on the right (B) is the logical architecture for a single virtual machine with the following components called out — applications, operating system, disks, boot loaders, OS Kernel, drivers, and the TPM component.

This article walks through the steps to apply the principles of Zero Trust across this logical architecture. The steps are illustrated and described below.

:::image type="content" source="media/vm/azure-infra-vm-subscription-architecture-2.png" alt-text="Diagram of virtual machines logical architecture components." lightbox="media/vm/azure-infra-vm-subscription-architecture-2.png":::

The following table describes the tasks that are numbered in the illustration.

| Step | Task |
| --- | --- |
| 1 | Configure logical isolation by deploying virtual machines to a dedicated resource group. |
| 2 | Leverage Role Based Access Control (RBAC). |
| 3 | Secure virtual machine boot components — boot loaders, OS kernels, and drivers. Securely protect keys, certificates and secrets in the Trusted Platform Module (TPM). |
| 4 | Enable customer-managed keys and double encryption. |
| 5 | Control the applications that are installed on virtual machines. |
| 6 | Configure secure access (not illustrated). |
| 7 | Set up secure maintenance of virtual machines (not illustrated). |
| 8 | Enable advanced threat detection and protection (not illustrated). |

## Step 1. Configure logical isolation for virtual machines

Begin by isolating virtual machines within a dedicated resource group. You can isolate virtual machines into different resource groups based on purpose, data classification, and governance requirements, such as the need to control permissions and monitoring.

Using dedicated resource groups allows you to set policies and permissions that apply to all the virtual machines within the resource group. This is also where you use Role Based Access Control (RBAC) to create least privilege access to the Azure resources contained in the resource group.

For more information on creating and managing resource groups, see [Manage Azure resource groups by using the Azure portal](/azure/azure-resource-manager/management/manage-resource-groups-portal).

You assign a virtual machine to a resource group when you first create the virtual machine, as called out in the screen capture below.

:::image type="content" source="media/vm/vm-create-vm-1.png" alt-text="Screenshot of create a virtual machine step 1." lightbox="media/vm/vm-create-vm-1.png":::

## Step 2. Leverage Role Based Access Control (RBAC)

Zero Trust requires configuring least privileged access. To do so, you need to limit user access with just-in-time and just-enough access (JIT/JEA) based on their role, workload, and data classification.

The following built-in roles are commonly used for virtual machine (VM) access:

- **Virtual Machine User Login:**  View virtual machines in the portal and login as a regular user.
- **Virtual Machine Administration Login:**  View virtual machines in the portal and login to virtual machines as an Administrator.
- **Virtual Machine Contributor:**  Create and manage virtual machines, including reset root user's password and managed disks. Does not grant access to the management virtual network or the ability to assign permissions to the resources.

To join a VM to a virtual network, you can use the custom permission **Microsoft.Network/virtualNetworks/subnets/join/action** to make a custom role.

When this custom role is leveraged in conjunction with Managed Identity and Conditional Access Policy, you can use device state, data classification, anomalies, location, and identity to force multi-factor authentication and granularly allow access based on verified trust.

To extend your realm of control beyond the system and allow your Azure AD tenant with Microsoft Intelligent Security Graph to support secure access, go to the Management blade of the virtual machine and turn on System Assigned Managed Identity.

:::image type="content" source="media/vm/vm-create-id-azuread.png" alt-text="Screenshot of create vm identity azure ad." lightbox="media/vm/vm-create-id-azuread.png":::

> [!NOTE]
> This feature is only available for Azure Virtual Desktop, Windows SVR 2019, Windows 10, and Linux Distros using certificate-based access.

## Step 3. Secure virtual machine boot components

Follow  the steps given below:
- When you create the virtual machine, be sure you configure security for the boot components. Enhanced deployment of VMs allows you to select security type and use [Secure boot](/windows-hardware/design/device-experiences/oem-secure-boot) and [vTPM](/windows/security/information-protection/tpm/trusted-platform-module-overview).
- Securely deploy virtual machines with verified boot loaders, OS kernels, and drivers that are signed by trusted publishers to establish a "root of trust". If the image is not signed by a trusted publisher, the virtual machine will not boot.
- Securely protect keys, certificates, and secrets in the virtual machines in a Trusted Platform Module.
- Gain insights and confidence of the entire boot chain's integrity.
- Ensure workloads are trusted and verifiable. The vTPM enables [attestation](/windows/security/information-protection/tpm/tpm-fundamentals#measured-boot-with-support-for-attestation) by measuring the entire boot chain of your VM (UEFI, OS, system, and drivers).

Enhanced deployment of virtual machines allows you to select security type and use Secure boot and vTPM. See callout #2 in the screen capture below.

:::image type="content" source="media/vm/vm-create-vm-step3.png" alt-text="Screenshot of create vm step3." lightbox="media/vm/vm-create-vm-step3.png":::

## Step 4. Enable customer-managed keys and double encryption

Using customer-managed keys and double encryption ensures that if a disk is exported, it is not readable or able to function. By ensuring that the keys are privately held and disks are double encrypted, you protect against breaches that attempt to extract disk information.

For information on how to configure a customer-managed encryption key with Azure Key Vault, see [Use the Azure portal to enable server-side encryption with customer-managed keys for managed disks](/azure/virtual-machines/disks-enable-customer-managed-keys-portal). There is an additional cost for using Azure Key Vault.

[Enable server-side encryption of Azure Disk Storage](/azure/virtual-machines/disk-encryption)
- FIPS 140-2 compliant transparent encryption with [AES 256 encryption](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard)
- Greater flexibility to manage controls
- Can be hardware (HSM) or software defined

[Enable server-side encryption](/azure/virtual-machines/disks-enable-host-based-encryption-portal#prerequisites) at the host for end-to-end encryption of your VM data
- Encryption starts on the physical host, your VM is allocated to
- Encrypts the OS and Temporary disks that are provisioned on the host; a ```--d``` carries it over to the storage service
- Double encryption on OS disks, Data disks, snapshots, and images

After this is complete, you can begin using your customer-managed encryption key to encrypt the disks within your virtual machine.

In the screen shot below, you select the encryption type on the Disks section for the virtual machine configuration. Select **Double encryption with platform-managed and customer-managed keys.**

:::image type="content" source="media/vm/vm-step4.png" alt-text="Screenshot of vm step 4." lightbox="media/vm/vm-step4.png":::

## Step 5. Control the applications installed on virtual machines

It's important to control the applications that can be installed on your virtual machines:
- Browser extensions (APIs) are difficult to secure which can lead to malicious URL delivery.
- Unsanctioned apps can go unpatched as they are shadow IT objects (the IT teams are not prepared or have no knowledge that these are installed).

You can use the VM Applications feature to control the applications that are installed on virtual machines. With this feature, you select which VM applications to install. This feature leverages the Azure Compute Gallery to simplify management of applications for virtual machines. When used together with RBAC, you can ensure that only trusted applications are available for users.

:::image type="content" source="media/vm/vm-step5.png" alt-text="Screenshot of vm step5." lightbox="media/vm/vm-step5.png":::

## Step 6. Configure secure access

To configure secure access:
- Configure secure communication within the Azure environment between components that are accessing virtual machines directly.
- Set up multi-factor authentication with conditional access
- Use privileged access workstations (PAWS)

:::image type="content" source="media/vm/azure-infra-vm-secure-access-3.png" alt-text="Diagram of configuring secure access." lightbox="media/vm/azure-infra-vm-secure-access-3.png":::

In the illustration:

- Multi-factor authentication with conditional access is set up within Azure AD and related portals.
- Admins should use privileged access workstations (PAWs) to access virtual machines directly.

### Configure secure communication within the Azure environment for virtual machines

First, be sure that communication between the components in the Azure environment is secure.

In the reference architecture, [Azure Bastion](/azure/bastion/bastion-overview#key-features) provides secure connection to virtual machines. Azure Bastion acts as an RDP/SSH broker and does not interact with the RDP protocol of your physical system. This also enables you to reduce the number of public facing IP addresses.

:::image type="content" source="media/vm/azure-infra-vm-network-4.png" alt-text="Diagram of Configure secure communication." lightbox="media/vm/azure-infra-vm-network-4.png":::

### Set up multi-factor authentication with conditional access

In Step 2, Leverage Role Based Access Control, you configured Azure Active Directory Integration and Managed Identity. This allows you to set up [Azure multifactor authentication for Azure Virtual Desktop](/azure/virtual-desktop/set-up-mfa) or for [Windows Servers 2019 or newer](/azure/active-directory/devices/howto-vm-sign-in-azure-ad-windows). You can also [Log in to a Linux VM with Azure Active Directory credentials](/azure/active-directory/devices/howto-vm-sign-in-azure-ad-linux). The added benefit of this is the machine that connects to the virtual machine must also be registered to your Azure AD tenant to be allowed to connect.

When configuring multi-factor authentication with conditional access and related policies, use the recommended policy set for Zero Trust as a guide. This includes "Starting point" policies that don't require managing devices. Ideally, the devices accessing your virtual machines are managed and you can implement the "Enterprise" level, which is recommended for Zero Trust. For more information, see [Common Zero Trust identity and device access policies](/microsoft-365/security/office-365-security/identity-access-policies).

The following diagram illustrates the recommended policies for Zero Trust.

:::image type="content" source="media/vm/identity-device-access-policies-byplan.png" alt-text="Diagram of authentication with conditional access." lightbox="media/vm/identity-device-access-policies-byplan.png":::

Remember, username and passwords can be compromised 100%. Using multi-factor authentication, you reduce your risk of compromise by 99.9%. (This requires Azure AD P1 license).

> [!NOTE]
> VPNs can be used to connect to virtual machines in Azure as well. However, you should be sure to use methods to verify explicitly. Creating a tunnel that is "trusted" regardless of how they are used can be riskier than having specific connections that are highly verified.

No amount of security at the Network, Transport of Application layers will matter if you are not coming from a trusted, verified and secure source.

### Use privileged access workstations (PAWs)

Use [Privileged Access Workstations (PAW)](/security/compass/privileged-access-devices) to ensure devices that access virtual machines are healthy. PAWs are configured specifically for privileged access to ensure admins connect to a device that is not compromised.

For more information on deployment options, see [Privileged access deployment](/security/compass/privileged-access-deployment).

## Step 7. Set up secure maintenance of virtual machines

Secure maintenance of virtual machines includes:
- Using antimalware
- Automating virtual machine updates

### Use antimalware on virtual machines

Antimalware helps protect your virtual machine from threats such as malicious files and adware, etc. You can use antimalware software from an option of vendors such as Microsoft, Symantec, Trend Micro, and Kaspersky.

[Microsoft Antimalware](/azure/security/fundamentals/antimalware) is a no cost resource that provides real-time protection capability to assist in detection, quarantining and eradicating malicious software, spyware, and viruses:
- Runs in the background with the need of user interaction
- Provide alerts when unwanted or malicious software is downloaded, installed, or run
- Offers secure-by-default configuration and antimalware monitoring
- Scheduled scanning
- Signature updates
- Antimalware Engine and Platform updates
- Active Protection
- Samples reporting
- Exclusions
- Antimalware event collection

### Automate virtual machine updates

Automating updates to systems will ensure they are protected from the latest malware and misconfiguration exploits. There is automatic updating with aid in the trusted platform verification process.

Concentrate on [Azure Virtual Machine Maintenance and Updates](/azure/virtual-machines/maintenance-and-updates) to ensure your systems are hardened against configuration insecurities:
- [Azure Automation Update Management](/azure/architecture/hybrid/azure-update-mgmt) can assist in the management of your update process. With this utility, you can check the update status of your systems, manage, schedule, and reboot servers.
- The Azure [Virtual Machine Agent](/azure/virtual-machines/extensions/agent-windows) is used to manage your virtual machines and gives you the ability to use extensions for management.

[Supported OS types for Update Management with Azure Automation](/azure/automation/automation-update-management#supported-client-types) include the following:
- Each Windows machine - Update Management does a scan twice a day for each machine.
- Each Linux machine - Update Management does a scan every hour.

Additional guidance:
- [Plan deployment for updating Windows VMs in Azure - Azure Example Scenarios.](/azure/architecture/example-scenario/wsus/)
- [Use Azure Private Link to securely connect networks to Azure Automation](/azure/automation/how-to/private-link-security): Ensures VMs connect in an isolated controlled fashion and not over the internet for updates.

## Step 8. Enable advanced threat detection and protection

Threat protection for Azure infrastructure is provided by Defender for Cloud. This protection is extended to virtual machines when you provision [Microsoft Defender for Servers](/azure/defender-for-cloud/defender-for-servers-introduction).

:::image type="content" source="media/vm/azure-infra-vm-threat-protection-6.png" alt-text="Diagram of enable threat protection." lightbox="media/vm/azure-infra-vm-threat-protection-6.png":::

In the illustration:

- As described in the [Overview – Apply Zero Trust principles to Azure infrastructure](azure-infrastructure-overview.md) article, Microsoft Defender for Cloud is enabled at the level of an Azure subscription or at the level of an Azure management group that includes multiple Azure subscriptions.
- In addition to enabling Defender for Cloud, Defender for Servers is provisioned.

Advanced threat protection verifies the activities occurring on virtual machines based on Microsoft's threat intelligence. It looks for specific configurations and activities that suggest that there could be a breach. It enables the _verify explicitly_ and _assume breach_ principles.

Microsoft Defender for Servers includes the following:

- Access to the [Microsoft Defender for Endpoint](https://www.microsoft.com/security/business/endpoint-security/microsoft-defender-endpoint?rtc=1) data that is related to vulnerabilities, installed software, and alerts for your endpoints for endpoint detection and response (EDR).
- [Defender for Cloud's integrated vulnerability assessment](/microsoft-365/security/defender-vulnerability-management/defender-vulnerability-management) scanner for servers.
- Discover vulnerabilities and misconfigurations in real time with Microsoft Defender for Endpoint, and without the need of other agents or periodic scans.
- [Defender for Cloud's integrated Qualys scanner for Azure and hybrid machines](/azure/defender-for-cloud/deploy-vulnerability-assessment-vm) allows you to use a leading tool in real-time vulnerability identification without the need of a Qualys license.
- Implement [Just-in-time virtual machine access in Defender for Cloud](/azure/defender-for-cloud/just-in-time-access-usage). This creates an explicit deny rule for RDP/SSH and gives you JIT access at the server level when you need it and allows you to limit the period of access.
- [File integrity monitoring in Defender for Cloud](/azure/defender-for-cloud/file-integrity-monitoring-overview) provides you to change monitoring of files and registries of the operations system, application software, and other changes that allow you to validate the integrity of your file systems.
- [Adaptive application controls in Defender for Cloud](/azure/defender-for-cloud/adaptive-application-controls) provides an automated solution for creating and defining allow list for known safe applications and generates security alerts if a new application runs other than those you define as safe for use.
- [Adaptive network hardening in Defender for Cloud](/azure/defender-for-cloud/adaptive-network-hardening?WT.mc_id=Portal-Microsoft_Azure_Security) uses machine learning algorithms that calculate your current traffic, threat intelligence, indicators of compromise, and known trusted configurations to provide recommendations for hardening your Network Security Groups.

## Recommended training

- [Secure your Azure virtual machine disks](/training/modules/secure-your-azure-virtual-machine-disks)
- [Implement virtual machine host security in Azure](/training/paths/implement-host-security)

## Next Steps

- [Apply Zero Trust principles to Storage in Azure](azure-infrastructure-storage.md)
- [Apply Zero Trust principles to Spoke Virtual Network in Azure](azure-infrastructure-iaas.md)
- [Apply Zero Trust principles to Hub Virtual network in Azure](azure-infrastructure-networking.md)
  
## References 
- [Manage Azure resource groups by using the Azure portal](/azure/azure-resource-manager/management/manage-resource-groups-portal)
- [Secure boot](/windows-hardware/design/device-experiences/oem-secure-boot)
- [Overview of vTPM](/windows/security/information-protection/tpm/trusted-platform-module-overview)
- [attestation](/windows/security/information-protection/tpm/tpm-fundamentals#measured-boot-with-support-for-attestation)
- [Enable server-side encryption of Azure Disk Storage](/azure/virtual-machines/disk-encryption)
- [AES 256 encryption](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard)
- [Azure Bastion](/azure/bastion/bastion-overview#key-features)
- [Azure multifactor authentication for Azure Virtual Desktop](/azure/virtual-desktop/set-up-mfa)
- [Windows Servers 2019 or newer](/azure/active-directory/devices/howto-vm-sign-in-azure-ad-windows)
- [Log in to a Linux VM with Azure Active Directory credentials](/azure/active-directory/devices/howto-vm-sign-in-azure-ad-linux)
- [Common Zero Trust identity and device access policies](/microsoft-365/security/office-365-security/identity-access-policies)
- [Privileged Access Workstations (PAW)](/security/compass/privileged-access-devices)
- [Privileged access deployment](/security/compass/privileged-access-deployment)
- [Microsoft Antimalware](/azure/security/fundamentals/antimalware)
- [Virtual Machine Agent](/azure/virtual-machines/extensions/agent-windows)
- [Plan deployment for updating Windows VMs in Azure - Azure Example Scenarios.](/azure/architecture/example-scenario/wsus/)
- [Use Azure Private Link to securely connect networks to Azure Automation.](/azure/automation/how-to/private-link-security)
- [Microsoft Defender for Servers](/azure/defender-for-cloud/defender-for-servers-introduction)
- [Microsoft Defender for Endpoint](https://www.microsoft.com/security/business/endpoint-security/microsoft-defender-endpoint?rtc=1)
- [Defender for Cloud's integrated vulnerability assessment](/microsoft-365/security/defender-vulnerability-management/defender-vulnerability-management)