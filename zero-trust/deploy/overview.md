---
title: Zero Trust deployment for technology pillars overview
description: Learn how to deploy Zero Trust solutions to keep your organization secure.
ms.date: 02/26/2024
ms.service: security
author: mjcaparas
ms.author: macapara
ms.topic: conceptual
ms.collection:
  - highpri
  - zerotrust-pillar
---

# Zero Trust deployment for technology pillars

Because your organization might already have elements of Zero Trust protections already in place, this documentation set provides conceptual information to get you started and deployment plans and implementation recommendations for end-to-end adherence to Zero Trust principles. Each article acts as a checklist of deployment objectives with steps and links to more information.

You deploy Zero Trust principles across your IT infrastructure by implementing Zero Trust controls and technologies across seven technology pillars. Six of these pillars are signal sources, a control plane for enforcement, and a critical resource to be defended. Across these is the pillar that collects those signals and provides visibility for security incidents and automation and orchestration for responding to and mitigating cybersecurity threats.

:::image type="content" source="../media/diagram-zero-trust-security-elements.png" alt-text="Diagram of elements of visibility, automation, and orchestration in Zero Trust." border="false":::

The following articles provide conceptual information and deployment objectives for these seven technology pillars. Use these articles to assess your readiness and build a deployment plan to apply [Zero Trust principles](../zero-trust-overview.md).

| Technology pillar | Description |
| --- | --- |
| [![Fingerprint icon](../media/icon-identity-small.png)](identity.md) <br> [Identities](identity.md) | Identities—whether they represent people, services, or IoT devices—define the Zero Trust control plane. When an identity attempts to access a resource, verify that identity with strong authentication, and ensure access is compliant and typical for that identity. Follow least privilege access principles. |
| [![Endpoints icon.](../media/icon-endpoints-small.png)](endpoints.md) <br> [Endpoints](endpoints.md) |  Once an identity has been granted access to a resource, data can flow to a variety of different endpoints (devices), from IoT devices to smartphones, BYOD to partner-managed devices, and on-premises workloads to cloud-hosted servers. This diversity creates a massive attack surface area. Monitor and enforce device health and compliance for secure access. |
| [![Application window icon.](../media/icon-applications-small.png)](applications.md) <br> [Applications](applications.md)| Applications and APIs provide the interface by which data is consumed. They may be legacy on-premises workloads, lifted-and-shifted to cloud workloads, or modern SaaS applications. Apply controls and technologies to discover shadow IT, ensure appropriate in-app permissions, gate access based on real-time analytics, monitor for abnormal behavior, control user actions, and validate secure configuration options. |
| [![Ones and zeroes icon.](../media/icon-data-small.png)](data.md) <br> [Data](data.md)  | [Ultimately, security teams are protecting data. Where possible, data should remain safe even if it leaves the devices, apps, infrastructure, and networks the organization controls. Classify, label, and encrypt data, and restrict access based on those attributes. |
| [![Data storage disks icon.](../media/icon-infrastructure-small.png)](infrastructure.md) <br> [Infrastructure](infrastructure.md) | Infrastructure—whether on-premises servers, cloud-based VMs, containers, or micro-services—represents a critical threat vector. Assess for version, configuration, and JIT access to harden defense. Use telemetry to detect attacks and anomalies, and automatically block and flag risky behavior and take protective actions. |
| [![Network diagram icon.](../media/icon-networks-small.png)](networks.md) <br> [Networks](networks.md) | All data is ultimately accessed over network infrastructure. Networking controls can provide critical controls to enhance visibility and help prevent attackers from moving laterally across the network. Segment networks (and do deeper in-network micro-segmentation) and deploy real-time threat protection, end-to-end encryption, monitoring, and analytics. |
| [![Gear icon.](../media/icon-visibility-automation-orchestration-small.png)](visibility-automation-orchestration.md) <br> [Visibility, automation, and orchestration](visibility-automation-orchestration.md) | In our Zero Trust guides, we define the approach to implement an end-to-end Zero Trust methodology across identities, endpoints (devices), data, apps, infrastructure, and network. These activities increase your visibility, which gives you better data for making trust decisions. With each of these individual areas generating their own relevant alerts, we need an integrated capability to manage the resulting influx of data to better defend against threats and validate trust in a transaction. |


## Recommended training

|Training  | [Establish the guiding principles and core components of Zero Trust](/training/paths/zero-trust-principles/) |
|---------|---------|
|:::image type="icon" source="../media/basics-of-zero-trust.png" border="false"::: | Use this learning path to understand the basics of applying Zero Trust principles to the key technology pillars of identities, endpoints, application access, networks, infrastructure, and data. |
> [!div class="nextstepaction"]
> [Start >](/training/paths/zero-trust-principles/)

## Additional Zero Trust resources

Use these additional Zero Trust resources based on a documentation set or roles in your organization.

### Documentation set

Follow this table for the best Zero Trust documentation sets for your needs.

| Documentation set | Helps you... | Roles |
| --- | --- | --- |
| [Adoption framework](../adopt/zero-trust-adoption-overview.md) for phase and step guidance for key business solutions and outcomes | Apply Zero Trust protections from the C-suite to the IT implementation. | Security architects, IT teams, and project managers |
| [Zero Trust for small businesses](../guidance-smb-partner.md) | Apply Zero Trust principles to small business customers. | Customers and partners working with Microsoft 365 for business |
| [Zero Trust Rapid Modernization Plan (RaMP)](../zero-trust-ramp-overview.md) for project management guidance and checklists for easy wins | Quickly implement key layers of Zero Trust protection. | Security architects and IT implementers |
| [Zero Trust deployment plan with Microsoft 365](/microsoft-365/security/microsoft-365-zero-trust?bc=%2fsecurity%2fzero-trust%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fzero-trust%2ftoc.json) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to your Microsoft 365 tenant. | IT teams and security staff |
| [Zero Trust for Copilot for Microsoft 365](../zero-trust-microsoft-365-copilot.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Copilot for Microsoft 365. | IT teams and security staff |
| [Zero Trust for Azure services](../azure-infrastructure-overview.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Azure workloads and services. | IT teams and security staff |
| [Partner integration with Zero Trust](../integrate/overview.md) for design guidance for technology areas and specializations | Apply Zero Trust protections to partner Microsoft cloud solutions. | Partner developers, IT teams, and security staff |
| [Develop using Zero Trust principles](../develop/overview.md) for application development design guidance and best practices | Apply Zero Trust protections to your application. | Application developers |

### Your role

Follow this table for the best documentation sets for the roles in your organization.

| Role | Documentation set | Helps you... |
| --- | --- | --- |
| Security architect <br><br> IT project manager <br><br> IT implementer | [Adoption framework](../adopt/zero-trust-adoption-overview.md) for phase and step guidance for key business solutions and outcomes| Apply Zero Trust protections from the C-suite to the IT implementation. |
| Customer or partner for Microsoft 365 for business | [Zero Trust for small businesses](../guidance-smb-partner.md) | Apply Zero Trust principles to small business customers.  |
| Security architect <br><br> IT implementer | [Zero Trust Rapid Modernization Plan (RaMP)](../zero-trust-ramp-overview.md) for project management guidance and checklists for easy wins | Quickly implement key layers of Zero Trust protection. |
| Member of an IT or security team for Microsoft 365 | [Zero Trust deployment plan with Microsoft 365](/microsoft-365/security/microsoft-365-zero-trust?bc=%2fsecurity%2fzero-trust%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fzero-trust%2ftoc.json) for stepped and detailed design and deployment guidance for Microsoft 365 | Apply Zero Trust protections to your Microsoft 365 tenant. |
| Member of an IT or security team for Microsoft Copilots | [Zero Trust for Copilot for Microsoft 365](../zero-trust-microsoft-365-copilot.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Copilot for Microsoft 365. |
| Member of an IT or security team for Azure services | [Zero Trust for Azure services](../azure-infrastructure-overview.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Azure workloads and services. |
| Partner developer or member of an IT or security team | [Partner integration with Zero Trust](../integrate/overview.md) for design guidance for technology areas and specializations | Apply Zero Trust protections to partner Microsoft cloud solutions. |
| Application developer | [Develop using Zero Trust principles](../develop/overview.md) for application development design guidance and best practices | Apply Zero Trust protections to your application. |
