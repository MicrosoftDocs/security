---
title: Apply Zero Trust principles to storage in Azure
description: Learn how to secure Azure storage with Zero Trust.  
ms.date: 02/09/2023
ms.service: security
author: sikovatc
ms.author: sikovatc
ms.topic: conceptual
ms.collection: 
  - msftsolution-azureiaas
  - msftsolution-scenario
  - zerotrust-solution
---

# Apply Zero Trust principles to Azure storage

This article provides steps to apply the [principles of Zero Trust](zero-trust-overview.md#guiding-principles-of-zero-trust) to Azure Storage:

| Zero Trust principle | Definition | Met by |
| --- | --- | --- |
| Verify explicitly | Always authenticate and authorize based on all available data points. | Verify user credentials and access. |
| Use least privileged access |  Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection. | Control access to storage data with least privileges. |
| Assume breach | Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses. | Protect data at rest, data in transit, and data in use. Separate critical data with network controls. Use Defender for Storage for automated threat detection and protection. |

This article is part of a series of articles that demonstrate how to apply the principles of Zero Trust across an environment in Azure that includes Azure Storage services to support an IaaS workload. For an overview, see [Apply Zero Trust principles to Azure infrastructure](azure-infrastructure-overview.md).

## Storage architecture in Azure

You apply Zero Trust principles for Azure Storage across the architecture, from the tenant and directory level down to the storage container at the data layer.

The following diagram shows the logical architecture components.

:::image type="content" source="media/secure-storage/azure-infra-storage-subscription-architecture-1.png" alt-text="Diagram of logical architecture components for Azure Storage services.":::

In the diagram:

- The storage account for the reference architecture is contained in a dedicated resource group. You can isolate each storage account in a different resource group for more granular role-based access controls (RBAC). You can assign RBAC permissions to manage the storage account at the resource group or resource group level and audit these with Azure Active Directory (Azure AD) logging and tools such as Privileged Identity Management (PIM). If you're running multiple applications or workloads with multiple corresponding storage accounts in one Azure subscription, it is important to limit each storage account's RBAC permissions to its corresponding owners, data custodians, controllers, etc.
- Azure storage services for this diagram are contained within a dedicated storage account. You can have one storage account for each type of storage workload.
- For a broader look at the reference architecture, see the [Apply Zero Trust principles to Azure infrastructure overview](azure-infrastructure-overview.md).

The diagram doesn't include Azure Queues and Azure Tables. Use the same guidance in this article to secure these resources.

## What's in this article?

This article walks through the steps to apply the principles of Zero Trust across the reference architecture.

| Step | Task | Zero Trust principle(s) applied |
| --- | --- | --- |
| 1 | Protect data in all three modes: data at rest, data in transit, data in use. | Assume breach |
| 2 | Verify users and control access to storage data with least privileges. | Verify explicitly <br> Use least privileged access |
| 3 | Logically separate or segregate critical data with network controls. | Assume breach |
| 4 | Use Defender for Storage for automated threat detection and protection. | Assume breach |

## Step 1. Protect data in all three modes: data at rest, data in transit, data in use

You configure most of the settings for protecting data at rest, in transit, and in use, when you create the storage account. Use the following recommendations to be sure you configure these protections. Also consider enabling Microsoft Defender for Cloud to automatically evaluate your storage accounts against the [Microsoft cloud security benchmark](/security/benchmark/azure/introduction) that outlines a security baseline for each Azure service.

For more information on these storage security controls, see [here](/security/benchmark/azure/baselines/storage-security-baseline).

### Use encryption in transit

Keep your data secure by enabling transport-level security between Azure and the client. Always use HTTPS to secure communication over the public internet. When you call the REST APIs to access objects in storage accounts, you can enforce the use of HTTPS by requiring [Secure Transfer Required](/azure/storage/common/storage-require-secure-transfer) for the storage account. Any request originating from an insecure connection is rejected.

This configuration is enabled by default when you deploy a new Azure Storage Account (Secure by Default).

Consider applying a policy to deny the deployment of insecure connections for Azure Storage (Secure by Design).

This configuration also requires SMB 3.0 with Encryption.

### Prevent anonymous public read access

By default, public blob access is prohibited, but a user with the proper permissions can configure an accessible resource. To prevent data breaches from anonymous access, you should specify who has access to your data. Preventing this at the storage account level prevents a user from enabling this access at the container or blob level.

For more information, see [Prevent anonymous public read access to containers and blobs](/azure/storage/blobs/anonymous-read-access-prevent).

### Prevent shared key authorization

This configuration forces the storage account to reject all requests made with a shared key and require Azure AD authorization instead. Azure AD is a more secure choice as you can use risk-based access mechanisms to harden access to data tiers. For more information, see [Prevent Shared Key authorization for an Azure Storage account](/azure/storage/common/shared-key-authorization-prevent?tabs=portal).

You configure data protection for all three modes from the configuration settings of a storage account, as shown here.

:::image type="content" source="media/secure-storage/storage-1.png" alt-text="Screenshot of configuring data protection for all three modes for a storage account." lightbox="media/secure-storage/storage-1.png":::

These settings can't be changed after you create the storage account.

### Enforce a minimum required version of transport layer security (TLS)

The highest version Azure Storage currently supports is TLS 1.2. Enforcing a minimum TLS version rejects requests from clients using older versions. For more information, see [Enforce a minimum required version of TLS for requests to a storage account](/azure/storage/common/transport-layer-security-configure-minimum-version).

### Define the scope for copy operations

Define the scope for copy operations to restrict copy operations to only those from source storage accounts that are within the same Azure AD tenant or that have a [Private Link](/azure/storage/common/storage-network-security) to the same virtual network (VNet) as the destination storage account.

Limiting copy operations to source storage accounts with private endpoints is the most restrictive option and requires that the source storage account has private endpoints enabled.

You configure a scope for copy operations from the configuration settings of a storage account, as shown here.

:::image type="content" source="media/secure-storage/storage-2.png" alt-text="Screenshot of defining the scope for copy operations for a storage account."lightbox="media/secure-storage/storage-2.png":::

### Understand how encryption at rest works

All data written to Azure Storage is automatically encrypted by [Storage Service Encryption (SSE)](/azure/security/fundamentals/encryption-atrest) with a 256-bit Advanced Encryption Standard (AES) cipher. SSE automatically encrypts data when writing it to Azure Storage. When you read data from Azure Storage, Azure Storage decrypts the data before returning it. This process incurs no additional charges and doesn't degrade performance. Using customer-managed keys (CMK) provides additional capabilities to control rotation of the key encryption key or cryptographically erase data.

You enable CMK from the **Encryption** blade when creating a storage account, as shown here.

:::image type="content" source="media/secure-storage/storage-3.png" alt-text="Screenshot of enabling CMK for a storage account." lightbox= "media/secure-storage/storage-3.png":::

You can also enable infrastructure encryption, which provides double encryption at both the service and infrastructure levels. This setting can't be changed after you create the storage account.

> [!NOTE]
> In order to utilize a customer-managed key for storage account encryption, you must enable it during account creation and you should have a Key Vault with Key and Managed Identity with appropriate permissions already provisioned. Optionally, 256-bit AES encryption at the Azure Storage infrastructure level can also be enabled.

## Step 2. Verify users and control access to storage data with the least privileges

First, use Azure AD to govern access to storage accounts. Using [Role-based Access Control with Storage Accounts](/azure/storage/blobs/authorize-access-azure-active-directory) allows you to granularly define access based job function using OAuth 2.0. You can align your granular access to your Conditional Access Policy.

It is important to note that roles for storage accounts must be assigned at either the management or data level. Thus, if you're using Azure AD as the authentication and authorization method, a user should be assigned the appropriate combination of roles to give them the least amount of privilege necessary to complete their job function.

For a list of Storage Account Roles for granular access see [Azure built-in roles for Storage](/azure/role-based-access-control/built-in-roles#storage). RBAC assignments are done through the Access Control option on the Storage Account and can be assigned at various scopes.

You configure access control from the **Access Control (IAM)** settings of a storage account, as shown here.

:::image type="content" source="media/secure-storage/storage-4.png" alt-text="Screenshot of configuring access control for a storage account." lightbox="media/secure-storage/storage-4.png":::

You can check the access levels of users, groups, service principals, or managed identities and add a role assignment.

Another way to provide permissions that are time-bound is through Shared Access Signatures (SAS). [Best Practices when using SAS](/azure/storage/common/storage-sas-overview#best-practices-when-using-sas) at a high level are the following:

- Always use HTTPS. If you have deployed the [suggested Azure Policies for Azure landing zones](https://github.com/Azure/Enterprise-Scale/wiki/ALZ-Policies), secure transfer via HTTPS will be audited.
- Have a revocation plan.
- Configure SAS expiration policies.
- Validate permissions.
- Use a user delegation SAS wherever possible. This SAS is signed with Azure AD credentials.

## Step 3. Logically separate or segregate critical data with network controls

In this step, you use the recommended controls to protect the network connections to and from Azure Storage services.

The following diagram highlights the network connections to the Azure Storage services in the reference architecture.

:::image type="content" source="media/secure-storage/azure-infra-storage-network-2.png" alt-text="Diagram of network connections to Azure Storage services." lightbox="media/secure-storage/azure-infra-storage-network-2.png":::

|Task | Description |
| --- | --- |
| Prevent public access, create network segmentation with [Private Endpoint](/azure/private-link/private-endpoint-overview) and Private Link. | Private endpoint allows you to connect to services with the use of a single private IP address on the VNet using Azure Private Link. <li> Enabling private endpoints allows the Azure platform to validate network connections and allow only the connection with explicit access to the private-link resource to gain access to subsequent resources. <li> You'll need a separate private endpoint for each service on the Azure Storage Account.
| Use [Azure Private Link](/azure/private-link/private-link-overview) | Use Azure Private Link to access Azure Storage over a private endpoint in your VNet. Use the [approval workflow](/azure/private-link/private-endpoint-overview) to automatically approve or manually request, as appropriate. |
| Prevent public access to your data sources using [Service Endpoints](/azure/virtual-network/virtual-network-service-endpoints-overview) | You can do network segmentation using Service Endpoints by enabling private IP addresses in a VNet to reach an endpoint without using public IP addresses. |

You configure private endpoints from the **Networking** settings of a storage account, as shown here.

:::image type="content" source="media/secure-storage/storage-5.png" alt-text="Screenshot of configuring a private endpoint for a storage account." lightbox="media/secure-storage/storage-5.png":::

## Step 4. Use Defender for Storage for automated threat detection and protection

[Microsoft Defender for Storage](/azure/storage/common/azure-defender-storage-configure?tabs=azure-security-center) provides that additional level of intelligence that detects unusual and potentially harmful attempts to exploit your storage services. Microsoft Defender for Storage is built into Microsoft Defender for Cloud.

Defender for Storage detects anomalous access pattern alerts such as:

- Access from unusual locations
- Application Anomaly
- Anonymous access
- Anomalous extract/upload alerts
- Data Exfiltration
- Unexpected delete
- Upload Azure Cloud Service package
- Suspicious storage activities alerts
- Access permission change
- Access Inspection
- Data Exploration

For more information about threat protection across the reference architecture, see the [Apply Zero Trust principles to Azure infrastructure overview](azure-infrastructure-overview.md).

Once enabled, Defender for Storage notifies you of security alerts and recommendations for improving the security posture of your Azure storage accounts.

Here's an example security alert for a storage account with a description of the alert and prevention measures highlighted.

:::image type="content" source="media/secure-storage/storage-6.png" alt-text="Screenshot of an example security alert for a storage account." lightbox="media/secure-storage/storage-6.png":::

## Recommended training

### Configure Storage security

|Training  |[Configure Storage security](/training/modules/configure-storage-security/)|
|---------|---------|
|:::image type="icon" source="media/storage-security-configure.png" border="false"::: | Learn how to configure common Azure Storage security features like storage access signatures.<br> In this module, you learn how to: <li> Configure a shared access signature (SAS), including the uniform resource identifier (URI) and SAS parameters. <li> Configure Azure Storage encryption. <li> Implement customer-managed keys.<li> Recommend opportunities to improve Azure Storage security.|
> [!div class="nextstepaction"]
> [Start >](/training/modules/configure-storage-security/1-introduction)

For more training on security in Azure, see these resources in the Microsoft catalog:<br> 
[Security in Azure | Microsoft Learn](/training/browse/?subjects=security&products=azure)

## Next Steps

- [Apply Zero Trust principles to virtual machines in Azure](azure-infrastructure-virtual-machines.md)
- [Apply Zero Trust principles to spoke virtual networks in Azure](azure-infrastructure-iaas.md)
- [Apply Zero Trust principles to hub virtual networks in Azure](azure-infrastructure-networking.md)
  
## References

Refer to the links below to learn about the various services and technologies mentioned in this article.

- [Secure transfer for Azure Storage Accounts](/azure/storage/common/storage-require-secure-transfer)
- [Prevent anonymous public read access to containers and blobs](/azure/storage/blobs/anonymous-read-access-prevent)
- [Prevent Shared Key authorization for an Azure Storage Account](/azure/storage/common/shared-key-authorization-prevent)
- [Network security for Storage Accounts](/azure/storage/common/storage-network-security)
- [Private Endpoints and Private Link for Storage Accounts](/azure/storage/common/storage-private-endpoints)
- [Storage Service Encryption (SSE)](/azure/security/fundamentals/encryption-atrest) 
- [Role-based Access Control for Storage Accounts](/azure/storage/blobs/authorize-access-azure-active-directory)
- [Azure Blob Backup](/azure/backup/blob-backup-configure-manage)
- [Best Practices when using SAS](/azure/storage/common/storage-sas-overview#best-practices-when-using-sas)
- [Review of Private Endpoints](/azure/private-link/private-endpoint-overview)
- [Review of Service Endpoints](/azure/virtual-network/virtual-network-service-endpoints-overview)
- [Microsoft Defender for Storage](/azure/storage/common/azure-defender-storage-configure?tabs=azure-security-center)