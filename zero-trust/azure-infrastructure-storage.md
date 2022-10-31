---
title: Apply Zero Trust principles to Storage in Azure
description: Learn how to secure Azure storage with Zero Trust.  
ms.date: 
ms.service: security
author: brendacarter
ms.author: bcarter
ms.topic: conceptual
ms.collection: 
  - msftsolution-accesscontrol
  - msftsolution-scenario
  - zerotrust-solution
---
# Apply Zero Trust principles to Azure storage

In this article, you will learn to apply the principles of Zero Trust to Azure Storage:
- Verify explicitly
- Use least privileged access
- Assume breach

This article is part of a series of articles that demonstrate how to apply the principles of Zero Trust across an environment in Azure that includes Azure Storage services to support an IaaS workload.<br>
For more information, see [Overview – Apply Zero Trust principles to Azure infrastructure.](azure-infrastructure-overview.md)

## Storage architecture in Azure

Zero trust principles for Azure Storage are applied across the architecture, from the tenant and directory level down to the storage container at the data layer.

The following illustration provides a reference of logical architecture components.

:::image type="content" source="media/secure-storage/azure-infra-storage-subscription-architecture-1.png" alt-text="Diagram of logical architecture components." lightbox="media/secure-storage/azure-infra-storage-subscription-architecture-1.png":::

In the illustration:

- The storage account for the reference architecture is contained in a dedicated resource group. You can isolate each storage account in a different resource group for more granular Role-based access controls (RBAC). You can assign RBAC permissions to manage the storage account at the resource group or resource group level, and audit these with AAD logging and tools such as Privileged Identity Management. If running multiple applications or workloads with multiple corresponding storage accounts in one Azure subscription, it is important to limit each storage account's RBAC permissions to its corresponding owners, data custodians, controllers, etc.
- Azure storage services for the reference architecture are contained within a dedicated storage account. You can have one storage account for each type of storage workload.
- For a broader look at the reference architecture, see [Overview – Apply Zero Trust principles to Azure infrastructure.](azure-infrastructure-overview.md)

Azure Queues and Azure Tables are not illustrated. Use the same guidance in this article to secure these resources.

## What's in this article?

This article walks through the steps to apply the principles of Zero Trust across the reference architecture.

| **Step** | **Task** |
| --- | --- |
| 1 | Protect data in all three modes: data at rest, data in transit, data in use. |
| 2 | Verify users and control access to storage data with least privilege. |
| 3 | Logically separate or segregate critical data with network controls. |
| 4 | Use Defender for Storage for automated threat detection and protection. |

## Step 1. Protect data in all three modes: data at rest, data in transit, data in use

Most of the settings for protecting data at rest, in transit, and in use are configured when you create the storage account. Use the following recommendations to be sure these protections are configured. Also consider enabling Microsoft Defender for Cloud, as it will automatically evaluate your storage accounts against the Microsoft cloud security benchmark that outlines a security baseline for each Azure service.<br> 
For more information on these storage security controls, see [here](/security/benchmark/azure/baselines/storage-security-baseline).

### Use encryption in transit

Keep your data secure by enabling transport-level security between Azure and the client. Always use HTTPS to secure communication over the public internet. When you call the REST APIs to access objects in storage accounts, you can enforce the use of HTTPS by requiring [Secure Transfer Required](/azure/storage/common/storage-require-secure-transfer) for the storage account. Any request originating from an insecure connection is rejected.<br>
This configuration is enabled by default when you deploy a new Azure Storage Account (Secure by Default).<br>
Consider applying a policy to deny the deployment of insecure connections for Azure Storage (Secure by Design).<br>
This configuration also requires SMB 3.0 with Encryption.

### Prevent anonymous public read access

By default, public blob access is prohibited, but a user with the proper permissions can configure an accessible resource. To prevent data breaches from anonymous access, you should verify explicitly who has access to your data. Preventing this at the storage account level prevents a user from enabling this access at the container or blob level.<br> 
See [Prevent anonymous public read access to containers and blobs](/azure/storage/blobs/anonymous-read-access-prevent).

### Prevent shared key authorization

This configuration will force the storage account to reject all requests made with a shared key and require Azure AD authorization instead. Azure AD is a more secure choice as you can leverage risk-based access mechanisms to harden access to data tiers. <br>
See [Prevent Shared Key authorization for an Azure Storage account.](/azure/storage/common/shared-key-authorization-prevent?tabs=portal)

:::image type="content" source="media/secure-storage/storage-1.png" alt-text="Screenshot of Storage account Configuration." lightbox="media/secure-storage/storage-1.png":::

### Enforce a minimum required version of transport layer security (TLS)

The highest version Azure Storage currently supports is TLS 1.2. Enforcing a minimum TLS version will reject requests from clients using older versions.<br>
See [Prevent Shared Key authorization for an Azure Storage account.](/azure/storage/common/shared-key-authorization-prevent?tabs=portal).

### Define the scope for copy operations

Define the scope for copy operations: Restrict copy operations to only those from source storage accounts that are within the same Azure AD tenant or that have a [Private Link](/azure/storage/common/storage-network-security) to the same virtual network as the destination storage account.

Limiting copy operations to source storage accounts with private endpoints is the most restrictive option and will require that the source storage account has private endpoints enabled.

:::image type="content" source="media/secure-storage/storage-2.png" alt-text="Screenshot of Define Scope for Copy Operations."lightbox="media/secure-storage/storage-2.png":::

### Understand how encryption at rest works

All data written to Azure Storage is automatically encrypted by [Storage Service Encryption (SSE)](/azure/security/fundamentals/encryption-atrest) with a 256-bit Advanced Encryption Standard (AES) cipher. SSE automatically encrypts data when writing it to Azure Storage. When you read data from Azure Storage, Azure Storage decrypts the data before returning it. This process incurs no additional charges and doesn't degrade performance. Using customer-managed keys (CMK) provides additional capabilities to control rotation of the key encryption key or cryptographically erase data.

:::image type="content" source="media/secure-storage/storage-3.png" alt-text="Screenshot of Understand how encryption at rest works." lightbox= "media/secure-storage/storage-3.png":::

> [!NOTE]
> In order to utilize a customer-managed key for storage account encryption, you must enable it during account creation, and you should have a Key Vault with Key and Managed Identity with appropriate permissions already provisioned. Optionally, 256-bit AES encryption at the Azure Storage infrastructure level can also be enabled.

## Step 2. Verify users and control access to storage data with least privilege

First, use Azure Active Directory to govern access to storage accounts. Using [Role-based Access Control with Storage Accounts](/azure/storage/blobs/authorize-access-azure-active-directory) allows you to granularly define access based job function leveraging OAuth 2.0. You can align your granular access to your Conditional Access Policy.<br>
It is important to note that roles for storage accounts must be assigned at either the management or data level. Thus, if you are using Azure Active Directory as the authentication and authorization method, a user should be assigned the appropriate combination of roles to give them the least amount of privilege necessary to complete their job function.<br>
For a list of Storage Account Roles for granular access see [Azure built-in roles for Storage](/azure/role-based-access-control/built-in-roles#storage).<br>
RBAC assignments can be done through the Access Control option on the Storage Account and can be assigned at various scopes.

:::image type="content" source="media/secure-storage/storage-4.png" alt-text="Screenshot of Access Control." lightbox="media/secure-storage/storage-4.png":::

Another way to provide permissions that can be time-bound is through Shared Access Signatures. 
[Best Practices when using SAS](/azure/storage/common/storage-sas-overview#best-practices-when-using-sas) at a high level are:
- Always use HTTPS. If you have deployed the [suggested Azure Policies for Azure landing zones](https://github.com/Azure/Enterprise-Scale/blob/main/docs/ESLZ-Policies.md), secure transfer via HTTPS will be audited.
- Have a revocation plan
- Configure SAS expiration policies
- Validate permissions
- Use a user delegation SAS wherever possible. This SAS is signed with Azure AD credentials.

## Step 3. Logically separate or segregate critical data with network Controls

In this step, use the recommended controls to protect the network connections to and from Azure Storage services.<br>
The following illustration highlights the network connections to the Azure Storage services in the reference architecture.

:::image type="content" source="media/secure-storage/azure-infra-storage-network-2.png" alt-text="Diagram of Network connections to Azure Storage services." lightbox="media/secure-storage/azure-infra-storage-network-2.png":::

|Task | Description |
| --- | --- |
| Prevent public access, create network segmentation with [Private Endpoint](/azure/private-link/private-endpoint-overview) and Private Link. | Private endpoint allows you to connect to services with the use of a single private IP address on the virtual network leveraging Azure Private Link.<li> Enabling private endpoints allows the Azure platform to validate network connections and allow only the connection with explicit access to the private-link resource to gain access to subsequent resource. <li> You will need a separate private endpoint for each service on the Azure Storage Account.
| Use [Azure Private Link](/azure/private-link/private-link-overview) | Use Azure Private Link to access Azure Storage over a private endpoint in your virtual network. Use the [approval workflow](/azure/private-link/private-endpoint-overview) to automatically approve or manually request, as appropriate. |
| Prevent public access to your data sources using [Service Endpoints](/azure/virtual-network/virtual-network-service-endpoints-overview) | Network segmentation can be achieved using Service Endpoints by enabling private IP addresses in a VNET to reach an endpoint without using Public IP addresses. |

:::image type="content" source="media/secure-storage/storage-5.png" alt-text="Screenshot of Networking." lightbox="media/secure-storage/storage-5.png":::

## Step 4. Use Defender for Storage for automated threat detection and protection

[Microsoft Defender for Storage ](/azure/storage/common/azure-defender-storage-configure?tabs=azure-security-center)provides that additional level of intelligence that detects unusual and potentially harmful attempts to exploit your storage services. Microsoft Defender for Storage is built into Microsoft Defender for Cloud.

Defender for Storage will detect anomalous access pattern alerts such as:
- Access from unusual location
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

For more information on the architecture for threat protection across the reference architecture, see [Overview – Apply Zero Trust principles to Azure infrastructure.](azure-infrastructure-overview.md)

Once enabled, Defender for Storage will notify you of security alerts and recommendations for improving the security posture of your Azure storage accounts.

:::image type="content" source="media/secure-storage/storage-6.png" alt-text="Screenshot of Security Alert." lightbox="media/secure-storage/storage-6.png":::