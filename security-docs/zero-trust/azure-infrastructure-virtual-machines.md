---
title: How do I apply Zero Trust principles to Azure virtual machines?
description: How to apply Zero Trust principles to virtual machines in Azure.  
ms.date: 02/12/2024
ms.service: security
author: rudneir2
ms.author: ruolivei
ms.topic: conceptual
ms.collection: 
  - msftsolution-azureiaas
  - msftsolution-scenario
  - zerotrust-solution
  - zerotrust-azure
---

<!---

Writers notes:

For updates to product names, please also update the appropriate figures.

To update figures that are not screen shots, your options are:

- Locate the source Visio file in internal storage.
- Use the published Visio file in the Microsoft Download Center (see the "Technical publications" section of this article).
- For figures that are published in Scalable Vector Graphics (SVG) format, save the SVG file from the article web page, insert into Visio, modify, and then save it as a new version of the SVG file.

For any updates to figures, please update the corresponding posters as needed (see the "Technical publications" section of this article) and republish the Visio and PDF files in the Microsoft Download Center.

For new articles in this content set, please:

- Add cross-links in the "Next Steps" section FROM all the other articles in this content set TO the new article.
- Add a link to the Zero Trust Guidance Center page (index.yml).
- Update the "Content architecture" figure in the apply-zero-trust-azure-services-overview.md article as needed.

--->

# Apply Zero Trust principles to virtual machines in Azure

**Summary:** To apply Zero Trust principles to Azure virtual machines, you must configure logical isolation with dedicated resource groups, leverage Role Based Access Control (RBAC), secure virtual machine boot components, enable customer-managed keys and double encryption, control installed applications, configure secure access and maintenance of virtual machines, and enable advanced threat detection and protection.

This article provides steps to apply the [principles of Zero Trust](zero-trust-overview.md) to virtual machines in Azure:

| Zero Trust principle | Definition | Met by |
| --- | --- | --- |
| Verify explicitly | Always authenticate and authorize based on all available data points. | Use secure access. |
| Use least privileged access |  Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection. | Leverage Role Based Access Control (RBAC) and control the applications running on virtual machines. |
| Assume breach | Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses. | Isolate virtual machines with resource groups, secure their components, use double encryption, and enable advanced threat detection and protection. |

This article is part of a series of articles that demonstrate how to apply the principles of Zero Trust across an environment in Azure that includes a spoke virtual network (VNet) hosting a virtual machine-based workload. For an overview, see [Apply Zero Trust principles to Azure infrastructure](azure-infrastructure-overview.md).

## Logical architecture for virtual machines

Zero Trust principles for virtual machines are applied across the logical architecture, from the tenant and directory level down to the data and application layer within each virtual machine.

The following diagram the logical architecture components.

:::image type="content" source="media/vm/vm-security-configure.svg" alt-text="The logical architecture for applying Zero Trust to an Azure virtual machine showing a subscription, a resource group, and virtual machine components within an Entra ID tenant." lightbox="media/vm/vm-security-configure.svg":::

In this diagram:

- **A** is a set of virtual machines isolated within a dedicated resource group that resides within an Azure subscription.
- **B** is the logical architecture for a single virtual machine with the following components called out: applications, operating system, disks, boot loaders, OS Kernel, drivers, and the Trusted Platform Module (TPM) component.

This article walks through the steps to apply the principles of Zero Trust across this logical architecture, using these steps.

:::image type="content" source="media/vm/azure-infra-vm-subscription-architecture-2.svg" alt-text="The logical architecture for applying Zero Trust to an Azure virtual machine in the five steps of this article." lightbox="media/vm/azure-infra-vm-subscription-architecture-2.svg":::

| Step | Task | Zero Trust principles applied |
| --- | --- | --- |
| 1 | Configure logical isolation by deploying virtual machines to a dedicated resource group. | Assume breach |
| 2 | Leverage Role Based Access Control (RBAC). | Verify explicitly <br> Use least privileged access |
| 3 | Secure virtual machine boot components including boot loaders, OS kernels, and drivers. Securely protect keys, certificates, and secrets in the Trusted Platform Module (TPM). | Assume breach |
| 4 | Enable customer-managed keys and double encryption. | Assume breach |
| 5 | Control the applications that are installed on virtual machines. | Use least privileged access |
| 6 | Configure secure access (not shown on the logical architecture figure). | Verify explicitly <br> Use least privileged access <br> Assume breach |
| 7 | Set up secure maintenance of virtual machines (not shown on the logical architecture figure). | Assume breach |
| 8 | Enable advanced threat detection and protection (not shown on the logical architecture figure). | Assume breach |

## Step 1: Configure logical isolation for virtual machines

Begin by isolating virtual machines within a dedicated resource group. You can isolate virtual machines into different resource groups based on purpose, data classification, and governance requirements, such as the need to control permissions and monitoring.

Using dedicated resource groups allows you to set policies and permissions that apply to all the virtual machines within the resource group. You can then use role based access control (RBAC) to create least privileged access to the Azure resources contained in the resource group.

For more information on creating and managing resource groups, see [Manage Azure resource groups by using the Azure portal](/azure/azure-resource-manager/management/manage-resource-groups-portal).

You assign a virtual machine to a resource group when you first create the virtual machine, as shown here.

:::image type="content" source="media/vm/vm-create-vm-1.png" alt-text="Screenshot of assigning a virtual machine to a resource group." lightbox="media/vm/vm-create-vm-1.png":::

## Step 2: Leverage Role Based Access Control (RBAC)

Zero Trust requires configuring least privileged access. To do so, you need to limit user access with just-in-time and just-enough access (JIT/JEA) based on their role, workload, and data classification.

The following built-in roles are commonly used for virtual machine access:

- **Virtual Machine User Login:**  View virtual machines in the portal and sign-in as a regular user.
- **Virtual Machine Administration Login:**  View virtual machines in the portal and sign-in to virtual machines as an Administrator.
- **Virtual Machine Contributor:**  Create and manage virtual machines, including reset root user's password and managed disks. Doesn't grant access to the management virtual network (VNet) or the ability to assign permissions to the resources.

To join a virtual machine to a VNet, you can use the custom permission **Microsoft.Network/virtualNetworks/subnets/join/action** to make a custom role.

When this custom role is used with Managed Identity and Conditional Access Policy, you can use device state, data classification, anomalies, location, and identity to force multifactor authentication and granularly allow access based on verified trust.

To extend your realm of control beyond the system and allow your Microsoft Entra tenant with Microsoft Intelligent Security Graph to support secure access, go to the **Management** blade of the virtual machine and turn on **System Assigned Managed Identity**, as shown here.

:::image type="content" source="media/vm/vm-create-vm-step2.png" alt-text="Screenshot of enabling system assigned managed identity." lightbox="media/vm/vm-create-vm-step2.png":::

> [!NOTE]
> This feature is only available for Azure Virtual Desktop, Windows Server 2019, Windows 10, and Linux Distros using certificate-based access.

## Step 3: Secure virtual machine boot components

Follow these steps:

- When you create the virtual machine, be sure you configure security for the boot components. Enhanced deployment of virtual machines allows you to select security type and use [Secure boot](/windows-hardware/design/device-experiences/oem-secure-boot) and [vTPM](/windows/security/information-protection/tpm/trusted-platform-module-overview).
- Securely deploy virtual machines with verified boot loaders, OS kernels, and drivers that are signed by trusted publishers to establish a "root ." If the image isn't signed by a trusted publisher, the virtual machine won't boot.
- Securely protect keys, certificates, and secrets in the virtual machines in a Trusted Platform Module.
- Gain insights and confidence of the entire boot chain's integrity.
- Ensure workloads are trusted and verifiable. The vTPM enables [attestation](/windows/security/information-protection/tpm/tpm-fundamentals#measured-boot-with-support-for-attestation) by measuring the entire boot chain of your virtual machine (UEFI, OS, system, and drivers).

Enhanced deployment of virtual machines allows you to select security type and use secure boot and vTPM when you create them, as shown here.

:::image type="content" source="media/vm/vm-create-vm-step3.png" alt-text="Screenshot of specifying security features for a virtual machine." lightbox="media/vm/vm-create-vm-step3.png":::

## Step 4: Enable customer-managed keys and double encryption

Using customer-managed keys and double encryption ensures that if a disk is exported, it isn't readable or able to function. By ensuring that the keys are privately held and disks are double encrypted, you protect against breaches that attempt to extract disk information.

For information on how to configure a customer-managed encryption key with Azure Key Vault, see [Use the Azure portal to enable server-side encryption with customer-managed keys for managed disks](/azure/virtual-machines/disks-enable-customer-managed-keys-portal). There's an additional cost for using Azure Key Vault.

[Enable server-side encryption of Azure Disk Storage](/azure/virtual-machines/disk-encryption) for:

- FIPS 140-2 compliant transparent encryption with [AES 256 encryption](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard).
- Greater flexibility to manage controls.
- Hardware (HSM) or software-defined encryption.

[Enable server-side encryption](/azure/virtual-machines/disks-enable-host-based-encryption-portal#prerequisites) at the host for end-to-end encryption of your virtual machine data.

<!---

- Encryption starts on the physical host, your virtual machine is allocated to
- Encrypts the OS and Temporary disks that are provisioned on the host; a ```--d``` carries it over to the storage service
- Double encryption on OS disks, Data disks, snapshots, and images

--->

After completing these procedures, you use your customer-managed encryption key to encrypt the disks within your virtual machine.

You select the encryption type on the **Disks** blade for the virtual machine configuration. For **Encryption type**, select **Double encryption with platform-managed and customer-managed keys**, as shown here.

:::image type="content" source="media/vm/vm-create-vm-step4.png" alt-text="Screenshot for selecting the encryption type for a virtual machine." lightbox="media/vm/vm-create-vm-step4.png":::

## Step 5: Control the applications installed on virtual machines

It's important to control the applications that are installed on your virtual machines:

- Browser extensions (APIs) are difficult to secure which can lead to malicious URL delivery.
- Unsanctioned apps can go unpatched as they're shadow IT objects (the IT teams aren't prepared or have no knowledge that these are installed).

You can use the Virtual Machine Applications feature to control the applications that are installed on virtual machines. With this feature, you select which virtual machine applications to install. This feature uses the Azure Compute Gallery to simplify management of applications for virtual machines. When used together with RBAC, you can ensure that only trusted applications are available for users.

You select the virtual machine applications on the **Advanced** blade for the virtual machine configuration, as show here.

:::image type="content" source="media/vm/vm-create-vm-step5.png" alt-text="Screenshot for configuring applications of a virtual machine." lightbox="media/vm/vm-create-vm-step5.png":::

## Step 6: Configure secure access

To configure secure access:

- Configure secure communication within the Azure environment between components that are accessing virtual machines directly
- Set up multifactor authentication with conditional access
- Use privileged access workstations (PAWs)

:::image type="content" source="media/vm/azure-infra-vm-secure-access.png" alt-text="The logical architecture for configuring secure access to a virtual machine." lightbox="media/vm/azure-infra-vm-secure-access.png":::

In the diagram:

- multifactor authentication with conditional access is set up within Microsoft Entra ID and related portals.
- Admins use privileged access workstations (PAWs) to access virtual machines directly.

### Configure secure communication within the Azure environment for virtual machines

First, be sure that communication between the components in the Azure environment is secure.

In the reference architecture, [Azure Bastion](/azure/bastion/bastion-overview#key-features) provides secure connections to virtual machines. Azure Bastion acts as an RDP/SSH broker and doesn't interact with the RDP protocol of your physical system. This also enables you to reduce the number of public-facing IP addresses.

The following diagram shows the components of secure communications for virtual machines.

:::image type="content" source="media/vm/azure-infra-vm-secure-comm.svg" alt-text="The components of secure communications for virtual machines within the Azure IaaS reference architecture." lightbox="media/vm/azure-infra-vm-secure-comm.svg":::

### Set up multifactor authentication with conditional access

In [Step 2. Leverage Role Based Access Control](#step-2-leverage-role-based-access-control-rbac), you configured Microsoft Entra integration and managed identity. This allows you to set up [Azure multifactor authentication for Azure Virtual Desktop](/azure/virtual-desktop/set-up-mfa) or for servers running [Windows Server 2019 or newer](/azure/active-directory/devices/howto-vm-sign-in-azure-ad-windows). You can also [Log in to a Linux VM with Microsoft Entra credentials](/azure/active-directory/devices/howto-vm-sign-in-azure-ad-linux). The added benefit of this is the machine that connects to the virtual machine must also be registered to your Microsoft Entra tenant to be allowed to connect.

When configuring multifactor authentication with conditional access and related policies, use the recommended policy set for Zero Trust as a guide. This includes **Starting point** policies that don't require managing devices. Ideally, the devices accessing your virtual machines are managed and you can implement the **Enterprise** policies, which is recommended for Zero Trust. For more information, see [Common Zero Trust identity and device access policies](/microsoft-365/security/office-365-security/identity-access-policies).

The following diagram shows the recommended policies for Zero Trust.

:::image type="content" source="media/identity-device-access-policies-byplan.svg" alt-text="Zero Trust identity and device access policies for three protection levels: Starting point, Enterprise, and Specialized security." lightbox="media/identity-device-access-policies-byplan.svg":::

Remember that usernames and passwords can be 100% compromised. Using multifactor authentication, you reduce your risk of compromise by 99.9%. This requires Microsoft Entra ID P1 licenses.

> [!NOTE]
> You can use VPNs used to connect to virtual machines in Azure as well. However, you should be sure to use methods to verify explicitly. Creating a tunnel that is "trusted" regardless of how they are used can be riskier than having specific connections that are highly verified.

No amount of security at the Network, Transport, or Application layers matters if you aren't coming from a trusted, verified, and secure source.

### Use PAWs

Use [Privileged Access Workstations (PAWs)](/security/compass/privileged-access-devices) to ensure devices that access virtual machines are healthy. PAWs are configured specifically for privileged access so that admins use a device that has:

- Security controls and policies that restrict local administrative access.
- Productivity tools to minimize the attack surface to only what's absolutely required for performing sensitive administrative tasks.

For more information on deployment options, see [Privileged access deployment](/security/compass/privileged-access-deployment).

## Step 7: Set up secure maintenance of virtual machines

Secure maintenance of virtual machines includes:

- Using anti-malware
- Automating virtual machine updates

### Use anti-malware on virtual machines

Anti-malware helps protect your virtual machine from threats such as malicious files and adware, etc. You can use anti-malware software from an option of vendors such as Microsoft, Symantec, Trend Micro, and Kaspersky.

[Microsoft Antimalware](/azure/security/fundamentals/antimalware) is a no-cost resource that provides real-time protection capability to assist in detection, quarantining and eradicating malicious software, spyware, and viruses:

- Runs in the background with the need of user interaction
- Provides alerts when unwanted or malicious software is downloaded, installed, or run
- Offers secure-by-default configuration and anti-malware monitoring
- Scheduled scanning
- Signature updates
- Antimalware Engine and Platform updates
- Active Protection
- Samples reporting
- Exclusions
- Antimalware event collection

### Automate virtual machine updates

Automating updates to systems ensures they are protected from the latest malware and misconfiguration exploits. There's automatic updating with aid in the trusted platform verification process.

Concentrate on [Azure Virtual Machine Maintenance and Updates](/azure/virtual-machines/maintenance-and-updates) to ensure your systems are hardened against configuration insecurities:

- [Azure Automation Update Management](/azure/architecture/hybrid/azure-update-mgmt) can assist in the management of your update process. With this utility, you can check the update status of your systems, manage, schedule, and reboot servers.
- The Azure [Virtual Machine Agent](/azure/virtual-machines/extensions/agent-windows) is used to manage your virtual machines and gives you the ability to use extensions for management.

[Operating systems supported by Update Management](/azure/automation/update-management/operating-system-requirements) include the following:

- Each Windows virtual machine - Update Management does a scan twice a day for each machine.
- Each Linux virtual machine - Update Management does a scan every hour.

See this additional guidance:

- [Plan deployment for updating Windows VMs in Azure](/azure/architecture/example-scenario/wsus/)
- [Use Azure Private Link to securely connect networks to Azure Automation](/azure/automation/how-to/private-link-security)
   Ensures virtual machines connect in an isolated controlled fashion and not over the internet for updates.

## Step 8: Enable advanced threat detection and protection

Threat protection for Azure infrastructure is provided by Microsoft Defender for Cloud. This protection is extended to virtual machines when you provision [Microsoft Defender for Servers](/azure/defender-for-cloud/defender-for-servers-introduction), as shown in the following diagram.

:::image type="content" source="media/vm/azure-infra-vm-threat-protection.svg" alt-text="The logical architecture showing how Microsoft Defender for Cloud along Microsoft Defender for Servers provides threat detection and protection for virtual machines." lightbox="media/vm/azure-infra-vm-threat-protection.svg":::

In the diagram:

- As described in the [Apply Zero Trust principles to Azure IaaS overview](azure-infrastructure-overview.md) article, Defender for Cloud is enabled at the level of an Azure subscription or at the level of an Azure management group that includes multiple Azure subscriptions.
- In addition to enabling Defender for Cloud, Defender for Servers is provisioned.

Advanced threat protection verifies the activities occurring on virtual machines based on Microsoft's threat intelligence. It looks for specific configurations and activities that suggest that there could be a breach. It enables the **Verify explicitly** and **Assume breach** Zero Trust principles.

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

### Secure your Azure virtual machine disks

|Training  | [Secure your Azure virtual machine disks](/training/modules/secure-your-azure-virtual-machine-disks) |
|---------|---------|
|:::image type="icon" source="media/secure-your-azure-virtual-machine-disks.svg" border="false"::: | Learn how to use Azure Disk Encryption (ADE) to encrypt OS and data disks on existing and new virtual machines. <br>In this module, you learn how to: <li>Determine which encryption method is best for your virtual machine. <li>Encrypt existing virtual machine disks using the Azure portal. <li>Encrypt existing virtual machine disks using PowerShell. <li>Modify Azure Resource Manager templates to automate disk encryption on new virtual machines.|
> [!div class="nextstepaction"]
> [Start >](/training/modules/secure-your-azure-virtual-machine-disks/)

For more training on Azure, see the entire Microsoft catalog:<br> 
[Browse all - Training | Microsoft Learn](/training/browse)

### Implement virtual machine host security in Azure

|Training  | [Implement virtual machine host security in Azure](/training/paths/implement-host-security) |
|---------|---------|
|:::image type="icon" source="media/implement-host-security.svg" border="false"::: | In this learning path, learn how to protect and harden your virtual machines in Azure. |
> [!div class="nextstepaction"]
> [Start >](/training/paths/implement-host-security)

For more training on virtual machines in Azure, see these resources in the Microsoft catalog:<br> 
[Virtual machines in Azure | Microsoft Learn](/training/browse/?products=azure&subjects=virtual-machine&expanded=infrastructure)

## Next Steps

See these additional articles for applying Zero Trust principles to Azure:

- [Azure IaaS overview](azure-infrastructure-overview.md)
  - [Azure storage](azure-infrastructure-storage.md)
  - [Spoke virtual networks](azure-infrastructure-iaas.md)
  - [Spoke virtual networks with Azure PaaS services](azure-infrastructure-paas.md)
  - [Hub virtual networks](azure-infrastructure-networking.md)
- [Azure Virtual Desktop](azure-infrastructure-avd.md)
- [Azure Virtual WAN](azure-virtual-wan.md)
- [IaaS applications in Amazon Web Services](secure-iaas-apps.md)
- [Microsoft Sentinel and Microsoft Defender XDR](/security/operations/siem-xdr-overview)

## Technical illustrations

This poster provides a single-page, at-a-glance view of the components of Azure IaaS as reference and logical architectures, along with the steps to ensure that these components have the "never trust, always verify" principles of the Zero Trust model applied.

| Item | Description |
|:-----|:-----|
|[![Thumbnail figure for the Apply Zero Trust to Azure IaaS infrastructure poster.](media/tech-illus/apply-zero-trust-to-Azure-IaaS-infra-poster-thumb.png)](https://download.microsoft.com/download/d/8/b/d8b38a95-803c-4956-88e6-c0de68f7f8e9/apply-zero-trust-to-Azure-IaaS-infra-poster.pdf) <br/> [PDF](https://download.microsoft.com/download/d/8/b/d8b38a95-803c-4956-88e6-c0de68f7f8e9/apply-zero-trust-to-Azure-IaaS-infra-poster.pdf) \| [Visio](https://download.microsoft.com/download/d/8/b/d8b38a95-803c-4956-88e6-c0de68f7f8e9/apply-zero-trust-to-Azure-IaaS-infra-poster.vsdx) <br/> Updated March 2024 | Use this illustration together with this article: [Apply Zero Trust principles to Azure IaaS overview](azure-infrastructure-overview.md) <br/><br/>**Related solution guides** <br/> <ul><li>[Azure Storage services](azure-infrastructure-storage.md)</li><li>[Spoke VNets](azure-infrastructure-iaas.md)</li><li>[Hub VNets](azure-infrastructure-networking.md)</li></ul>|

This poster provides the reference and logical architectures and the detailed configurations of the separate components of Zero Trust for Azure IaaS. Use the pages of this poster for separate IT departments or specialties or, with the Microsoft Visio version of the file, customize the diagrams for your infrastructure.

| Item | Description |
|:-----|:-----|
|[![Thumbnail figure for the Diagrams for applying Zero Trust to Azure IaaS infrastructure poster.](media/tech-illus/apply-zero-trust-to-Azure-IaaS-infra-diagrams-thumb.png)](https://download.microsoft.com/download/c/e/a/ceac5996-7cbf-4184-aed8-16dffcad3795/apply-zero-trust-to-Azure-IaaS-infra-diagrams.pdf) <br/> [PDF](https://download.microsoft.com/download/c/e/a/ceac5996-7cbf-4184-aed8-16dffcad3795/apply-zero-trust-to-Azure-IaaS-infra-diagrams.pdf) \| [Visio](https://download.microsoft.com/download/c/e/a/ceac5996-7cbf-4184-aed8-16dffcad3795/apply-zero-trust-to-Azure-IaaS-infra-diagrams.vsdx) <br/> Updated March 2024 | Use these diagrams together with the articles starting here: [Apply Zero Trust principles to Azure IaaS overview](azure-infrastructure-overview.md) <br/><br/>**Related solution guides** <br/> <ul><li>[Azure Storage services](azure-infrastructure-storage.md)</li><li>[Spoke VNets](azure-infrastructure-iaas.md)</li><li>[Hub VNets](azure-infrastructure-networking.md)</li></ul>|

For additional technical illustrations, click [here](zero-trust-tech-illus.md).
  
## References

- [Manage Azure resource groups with the Azure portal](/azure/azure-resource-manager/management/manage-resource-groups-portal)
- [Secure boot](/windows-hardware/design/device-experiences/oem-secure-boot)
- [Overview of vTPM](/windows/security/information-protection/tpm/trusted-platform-module-overview)
- [Attestation](/windows/security/information-protection/tpm/tpm-fundamentals#measured-boot-with-support-for-attestation)
- [Enable server-side encryption of Azure Disk Storage](/azure/virtual-machines/disk-encryption)
- [AES 256 encryption](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard)
- [Azure Bastion](/azure/bastion/bastion-overview#key-features)
- [Azure multifactor authentication for Azure Virtual Desktop](/azure/virtual-desktop/set-up-mfa)
- [Windows Servers 2019 or newer](/azure/active-directory/devices/howto-vm-sign-in-azure-ad-windows)
- [Log in to a Linux VM with Microsoft Entra credentials](/azure/active-directory/devices/howto-vm-sign-in-azure-ad-linux)
- [Common Zero Trust identity and device access policies](/microsoft-365/security/office-365-security/identity-access-policies)
- [Privileged Access Workstations (PAW)](/security/compass/privileged-access-devices)
- [Privileged access deployment](/security/compass/privileged-access-deployment)
- [Microsoft Anti-malware](/azure/security/fundamentals/antimalware)
- [Virtual Machine Agent](/azure/virtual-machines/extensions/agent-windows)
- [Plan deployment for updating Windows VMs in Azure - Azure Example Scenarios](/azure/architecture/example-scenario/wsus/)
- [Use Azure Private Link to securely connect networks to Azure Automation](/azure/automation/how-to/private-link-security)
- [Microsoft Defender for Servers](/azure/defender-for-cloud/defender-for-servers-introduction)
- [Microsoft Defender for Endpoint](https://www.microsoft.com/security/business/endpoint-security/microsoft-defender-endpoint?rtc=1)
- [Defender for Cloud's integrated vulnerability assessment](/microsoft-365/security/defender-vulnerability-management/defender-vulnerability-management)
