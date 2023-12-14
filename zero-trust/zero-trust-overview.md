---
title: What is Zero Trust?
description: Understand the Zero Trust security model, learn about the principles, and apply the Zero Trust architecture using Microsoft 365 and Microsoft Azure services.  
ms.date: 04/15/2022
ms.service: security
author: mjcaparas
ms.author: macapara
ms.topic: conceptual
ms.collection: 
  - highpri
  - zerotrust
---

# What is Zero Trust?

:::image type="icon" source="./media/icon-introduction-medium.png":::


Zero Trust is a security strategy. It is not a product or a service, but an approach in designing and implementing the following set of security principles:

- Verify explicitly
- Use least privilege access
- Assume breach

## Guiding principles of Zero Trust

| Verify explicitly | Use least privilege access | Assume breach |
|------|-------|------|
| Always authenticate and authorize based on all available data points. | Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection. | Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses. |

This is the core of **Zero Trust**. Instead of believing everything behind the corporate firewall is safe, the Zero Trust model assumes breach and verifies each request as though it originated from an uncontrolled network. Regardless of where the request originates or what resource it accesses, the Zero Trust model teaches us to "never trust, always verify."

It is designed to adapt to the complexities of the modern environment that embraces the mobile workforce, protects people, devices, applications, and data wherever they are located.

A Zero Trust approach should extend throughout the entire digital estate and serve as an integrated security philosophy and end-to-end strategy. This is done by implementing Zero Trust controls and technologies across six foundational elements. Each of these is a source of signal, a control plane for enforcement, and a critical resource to be defended.

:::image type="content" source="./media/diagram-zero-trust-security-elements.png" alt-text="Diagram of elements of visibility, automation, and orchestration in Zero Trust." border="false":::

Different organizational requirements, existing technology implementations, and security stages all affect how a Zero Trust security model implementation is planned. Using our experience in helping customers to secure their organizations, as well as in implementing our own Zero Trust model, we've developed the following guidance to assess your readiness and to help you build a plan to get to Zero Trust.

**You can organize your approach to Zero Trust around these key technology pillars:**

<br/>


<table border="0">
   <tbody>
      <tr>
         <td>
            <p><img src="media/icon-identity-small.png" alt="Fingerprint icon."></p>
         </td>
         <td>
            <p><strong>Secure identity with Zero Trust</strong> </p>
            <p>Identities—whether they represent people, services, or IoT devices—define the Zero Trust control plane. When an identity attempts to access a resource, verify that identity with strong authentication, and ensure access is compliant and typical for that identity. Follow least privilege access principles.</p>
         </td>
         <!--<td>
            <p><img src="./media/video-image-placeholder-01.png" alt="Video placeholder 1."></p>
         </td>-->
      </tr>
      <tr>
         <td>
            <p><img src="media/icon-endpoints-small.png" alt="Endpoint devices icon."></p>
         </td>
         <td>
            <p><strong>Secure endpoints with Zero Trust</strong> </p>
            <p>Once an identity has been granted access to a resource, data can flow to a variety of different endpoints—from IoT devices to smartphones, BYOD to partner-managed devices, and on-premises workloads to cloud-hosted servers. This diversity creates a massive attack surface area. Monitor and enforce device health and compliance for secure access.</p>
         </td>
         <!--<td>
            <p><img src="./media/video-image-placeholder-02.png" alt="Video placeholder 2."></p>
         </td>-->
      </tr>
      <tr>
         <td>
            <p><img src="media/icon-applications-small.png" alt="Application window icon."></p>
         </td>
         <td>
            <p><strong>Secure applications with Zero Trust</strong></p>
            <p>Applications and APIs provide the interface by which data is consumed. They may be legacy on-premises, lifted-and-shifted to cloud workloads, or modern SaaS applications. Apply controls and technologies to discover shadow IT, ensure appropriate in-app permissions, gate access based on real-time analytics, monitor for abnormal behavior, control user actions, and validate secure configuration options.</p>
         </td>
         <!--<td>
            <p><img src="./media/video-image-placeholder-03.png" alt="Video placeholder 3."></p>
         </td>-->
      </tr>
      <tr>
         <td>
            <p><img src="media/icon-data-small.png" alt="Ones and zeroes icon."></p>
         </td>
         <td>
            <p><strong>Secure data with Zero Trust</strong></p>
            <p>Ultimately, security teams are protecting data. Where possible, data should remain safe even if it leaves the devices, apps, infrastructure, and networks the organization controls. Classify, label, and encrypt data, and restrict access based on those attributes.</p>
         </td>
         <!--<td>
            <p><img src="./media/video-image-placeholder-04.png" alt="Video placeholder 4."></p>
         </td>-->
      </tr>
      <tr>
         <td>
            <p><img src="media/icon-infrastructure-small.png" alt="Data storage disks icon."></p>
         </td>
         <td>
            <p><strong>Secure infrastructure with Zero Trust</strong></p>
            <p>Infrastructure—whether on-premises servers, cloud-based VMs, containers, or micro-services—represents a critical threat vector. Assess for version, configuration, and JIT access to harden defense. Use telemetry to detect attacks and anomalies, and automatically block and flag risky behavior and take protective actions.</p>
         </td>
         <!--<td>
            <p><img src="./media/video-image-placeholder-05.png" alt="Video placeholder 5."></p>
         </td>-->
      </tr>
      <tr>
         <td>
            <p><img src="media/icon-networks-small.png" alt="Network diagram icon."></p>
         </td>
         <td>
            <p><strong>Secure networks with Zero Trust</strong></p>
            <p>All data is ultimately accessed over network infrastructure. Networking controls can provide critical controls to enhance visibility and help prevent attackers from moving laterally across the network. Segment networks (and do deeper in-network micro-segmentation) and deploy real-time threat protection, end-to-end encryption, monitoring, and analytics.</p>
         </td>
         <!--<td>
            <p><img src="./media/video-image-placeholder-06.png" alt="Video placeholder 6."></p>
         </td>-->
      </tr>
      <tr>
         <td>
            <p><img src="media/icon-visibility-automation-orchestration-small.png" alt="Gear icon."></p>
         </td>
         <td>
            <p><strong>Visibility, automation, and orchestration with Zero Trust</strong> </p>
            <p>In our Zero Trust guides, we define the approach to implement an end-to-end Zero Trust methodology across identities, endpoints and devices, data, apps, infrastructure, and network. These activities increase your visibility, which gives you better data for making trust decisions. With each of these individual areas generating their own relevant alerts, we need an integrated capability to manage the resulting influx of data to better defend against threats and validate trust in a transaction.</p>
         </td>
         <!--<td>
            <p><img src="./media/video-image-placeholder-07.png" alt="Video placeholder 7."></p>
         </td>-->
      </tr>
   </tbody>
</table>

With Zero Trust, we move away from a trust-by-default perspective to a trust-by-exception one. An integrated capability to automatically manage those exceptions and alerts is important so you can more easily find and detect threats, respond to them, and prevent or block undesired events across your organization.

## Zero Trust and the US Executive Order 14028 on Cybersecurity

[US executive order 14028, Improving the Nation's Cyber Security](https://www.whitehouse.gov/briefing-room/presidential-actions/2021/05/12/executive-order-on-improving-the-nations-cybersecurity), directs federal agencies on advancing security measures that drastically reduce the risk of successful cyberattacks against the federal government's digital infrastructure. On January 26, 2022, the [Office of Management and Budget (OMB)](https://www.whitehouse.gov/omb/) released the federal Zero Trust strategy in [memorandum 22-09](https://www.whitehouse.gov/wp-content/uploads/2022/01/M-22-09.pdf), in support of EO 14028. 

## Zero Trust for Microsoft 365

Microsoft 365 is built intentionally with many security and information protection capabilities to help you build Zero Trust into your environment. Many of the capabilities can be extended to protect access to other SaaS apps your organization uses and the data within these apps.

See these key resources to get started:

- [Zero Trust deployment plan with Microsoft 365](/microsoft-365/security/microsoft-365-zero-trust)
- [The Microsoft Zero Trust security model setup guide](https://go.microsoft.com/fwlink/?linkid=2222968)
- [Advanced deployment guide for Zero Trust with Microsoft 365 (requires sign-in)](https://go.microsoft.com/fwlink/?linkid=2224820) in the Microsoft 365 admin center

## Zero Trust for Microsoft Azure

These articles help you apply the principles of Zero Trust to your workloads and services in Microsoft Azure based on a multi-disciplinary approach to applying the Zero Trust principles.

- [Azure IaaS](azure-infrastructure-overview.md)
- [Azure Virtual Desktop](azure-infrastructure-avd.md)
- [Azure Virtual WAN](azure-virtual-wan.md)
- [IaaS applications in Amazon Web Services](secure-iaas-apps.md)
- [Microsoft Sentinel and Microsoft Defender XDR](/security/operations/siem-xdr-overview)

## Related links

- [Zero Trust Overview](https://www.youtube.com/watch?v=KlEKAzMQEOw&list=PLtVMyW0H7aiOQwZSsn2d-tg2z729ce1BZ&index=13):  This video provides information about:

    - Zero Trust definition
    - Zero Trust principles
    - Zero Trust core concepts
    - Rapid modernization plan (RaMP) quick wins

- [Zero Trust - The Open Group](https://www.youtube.com/watch?v=x0xlTVyX968&list=PLtVMyW0H7aiOQwZSsn2d-tg2z729ce1BZ&index=12): This video provides a perspective on Zero Trust from a standards organization.

## Next steps

On this site you can find:

- [Adoption framework](adopt/zero-trust-adoption-overview.md)
- [Concepts and deployment objectives](deploy/overview.md)
- [Zero Trust for small businesses](guidance-smb-partner.md)
- [Rapid Modernization Plan (RaMP) guidance](zero-trust-ramp-overview.md)
- [Microsoft 365 deployment plans](/microsoft-365/security/microsoft-365-zero-trust?bc=%2fsecurity%2fzero-trust%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fzero-trust%2ftoc.json)
- [Microsoft Azure deployment plans](azure-infrastructure-overview.md)
- [Integration guidance for ISVs](integrate/overview.md)
- [Developer guidance](develop/overview.md)
