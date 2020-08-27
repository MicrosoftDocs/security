---
title: Zero Trust Deployment Center
description: The Zero Trust model assumes a breach and verifies each request as though it originated from an uncontrolled network. Regardless of where the request originates or what resource it accesses, the Zero Trust model teaches us to never trust and to always verify.
ms.date: 09/01/2020
ms.service: security
author: garycentric
ms.author: v-gmoor
ms.topic: conceptual
---

Zero Trust Deployment Center
============================

**Assess Zero Trust readiness and build a plan**

Today, organizations need a new security model that effectively adapts
to the complexity of the modern environment, embraces the mobile
workforce, and protects people, devices, applications, and data wherever
they are located.

This is the core of **Zero Trust**. Instead of believing everything
behind the corporate firewall is safe, the Zero Trust model assumes
breach and verifies each request as though it originated from an
uncontrolled network. Regardless of where the request originates or what
resource it accesses, the Zero Trust model teaches us to "never trust,
always verify."

**Guiding principles of Zero Trust**

<table>
<thead>
<tr class="header">
<th><strong>Verify explicitly</strong></th>
<th><strong>Use least privileged access</strong></th>
<th><strong>Assume breach</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Always authenticate and authorize based on all available data points.</td>
<td>Limit user access with<br />
Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection.</td>
<td>Minimize blast radius and segment access. Verify<br />
end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses.</td>
</tr>
</tbody>
</table>

A Zero Trust approach should extend throughout the entire digital estate
and serve as an integrated security philosophy and end-to-end strategy.
This is done by implementing Zero Trust controls and technologies across
six foundational elements. Each of these is a source of signal, a
control plane for enforcement, and a critical resource to be defended.

Different organizational requirements, existing technology
implementations, and security stages all affect how a Zero Trust
security model implementation is planned. Using our experience in
helping customers to secure their organizations, as well as in
implementing our own Zero Trust model, we've developed the following
guidance to assess your readiness and to help you build a plan to get to
Zero Trust.

<img src=".//media/image1.png" style="width:5.82154in;height:1.56944in" />

**Follow the steps below to mature your organization's approach to
security and optimize how Zero Trust is implemented:**

<img src=".//media/image2.png" style="width:0.51701in;height:0.51701in" />

**Secure identity with Zero Trust -**
[aka.ms/ZTIdentity](https://aka.ms/ZTIdentity)

> <img src=".//media/image3.png" style="width:0.28564in;height:0.23809in" />Identities---whether
> they represent people, services, or IoT devices---define the Zero
> Trust control plane. When an identity attempts to access a resource,
> verify that identity with strong authentication, and ensure access is
> compliant and typical for that identity. Follow least privilege access
> principles.

**Secure endpoints with Zero Trust -**
[aka.ms/ZTEndpoints](https://aka.ms/ZTDevices)

> <img src=".//media/image4.emf" style="width:0.27292in;height:0.27292in" />Once
> an identity has been granted access to a resource, data can flow to a
> variety of different endpoints---from IoT devices to smartphones, BYOD
> to partner-managed devices, and on-premises workloads to cloud-hosted
> servers. This diversity creates a massive attack surface area. Monitor
> and enforce device health and compliance for secure access.

**Secure applications with Zero Trust -**
[aka.ms/ZTApplications](https://aka.ms/ZTApplications)

> Applications and APIs provide the interface by which data is consumed.
> They may be legacy on-premises, lifted-and-shifted to cloud workloads,
> or modern SaaS applications. Apply controls and technologies to
> discover shadow IT, ensure appropriate in-app permissions, gate access
> based on real-time analytics, monitor for abnormal behavior, control
> user actions, and validate secure configuration options.

<img src=".//media/image5.png" style="width:0.26189in;height:0.22618in" />**Secure
data with Zero Trust -** [aka.ms/ZTData](https://aka.ms/ZTData)

> <img src=".//media/image7.png" style="width:0.2375in;height:0.26181in" />Ultimately,
> security teams are protecting data. Where possible, data should remain
> safe even if it leaves the devices, apps, infrastructure, and networks
> the organization controls. Classify, label, and encrypt data, and
> restrict access based on those attributes.

**Secure infrastructure with Zero Trust -**
[aka.ms/ZTInfrastructure](https://aka.ms/ZTInfrastructure)

> <img src=".//media/image8.png" style="width:0.24653in;height:0.24653in" />Infrastructure---whether
> on-premises servers, cloud-based VMs, containers, or
> micro-services---represents a critical threat vector. Assess for
> version, configuration, and JIT access to harden defense. Use
> telemetry to detect attacks and anomalies, and automatically block and
> flag risky behavior and take protective actions.

**Secure networks with Zero Trust -**
[aka.ms/ZTNetwork](https://aka.ms/ZTNetwork)

> All data is ultimately accessed over network infrastructure.
> Networking controls can provide critical controls to enhance
> visibility and help prevent attackers from moving laterally across the
> network. Segment networks (and do deeper in-network
> micro-segmentation) and deploy real-time threat protection, end-to-end
> encryption, monitoring, and analytics.

**  
**

> <img src=".//media/image9.png" style="width:0.24653in;height:0.24653in" />**Visibility,
> automation, and orchestration** **with Zero Trust** -
> [aka.ms/ZTCrossPillars](https://aka.ms/ZTCrossPillars)
>
> In our Zero Trust guides, we define the approach to implement an
> end-to-end Zero Trust methodology across identities, endpoints and
> devices, data, apps, infrastructure, and network. These activities
> increase your visibility, which gives you better data for making trust
> decisions. With each of these individual areas generating their own
> relevant alerts, we need an integrated capability to manage the
> resulting influx of data to better defend against threats and validate
> trust in a transaction.
>
> With Zero Trust, we move away from a trust-by-default perspective to a
> trust-by-exception one. An integrated capability to automatically
> manage those exceptions and alerts is important so you can more easily
> find and detect threats, respond to them, and prevent or block
> undesired events across your organization.
