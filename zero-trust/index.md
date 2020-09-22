---
title: Zero Trust Deployment Center
description: The Zero Trust model assumes a breach and verifies each request as though it originated from an uncontrolled network. Regardless of where the request originates or what resource it accesses, the Zero Trust model teaches us to never trust and to always verify.
ms.date: 09/01/2020
ms.service: security
author: garycentric
ms.author: v-gmoor
ms.topic: conceptual
---

# Zero Trust Deployment Center

## Assess Zero Trust readiness and build a plan

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

## Guiding principles of Zero Trust

| Verify&nbsp;explicitly | Use least privileged access | Assume breach |
|------|-------|------|
| Always authenticate and authorize based on all available data points. | Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection. | Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses. |


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

:::image type="content" source="./media/zero-trust-security-elements-diagram.png" alt-text="Diagram of elements of visibility, automation, and orchestration in Zero Trust." border="false":::

**Follow the steps below to mature your organization's approach to
security and optimize how Zero Trust is implemented:**

:::row::: <!-- ROW: Identity -->
   :::column:::
:::image type="content" source="./media/icon-fingerprint.png" alt-text="Fingerprint icon." border="false":::
   :::column-end:::
   :::column span="3":::
[**Secure identity with Zero Trust**](https://aka.ms/ZTIdentity)

Identities—whether they represent people, services, or IoT devices—define the Zero Trust control plane. When an identity attempts to access a resource, verify that identity with strong authentication, and ensure access is compliant and typical for that identity. Follow least privilege access principles.
   :::column-end:::
<!-- Placeholder for video link.
   :::column span="2":::
[:::image type="content" source="./media/video-image-placeholder-01.png" alt-text="Placeholder 1." border="false":::](https://www.youtube.com/watch?v=gA5q0_3bxPs)
   :::column-end:::
-->
:::row-end:::
:::row::: <!-- ROW: Endpoints -->
   :::column:::
:::image type="content" source="./media/icon-endpoint-devices.png" alt-text="Endpoint devices icon." border="false":::
   :::column-end:::
   :::column span="3":::
[**Secure endpoints with Zero Trust**](https://aka.ms/ZTDevices)

Once an identity has been granted access to a resource, data can flow to a variety of different endpoints—from IoT devices to smartphones, BYOD to partner-managed devices, and on-premises workloads to cloud-hosted servers. This diversity creates a massive attack surface area. Monitor and enforce device health and compliance for secure access.
   :::column-end:::
<!-- Placeholder for video link.
   :::column span="2":::
[:::image type="content" source="./media/video-image-placeholder-02.png" alt-text="Placeholder 2." border="false":::](https://youtu.be/T6eWZbIP67E)
   :::column-end:::
-->
:::row-end:::
:::row::: <!-- ROW: Applications -->
   :::column:::
:::image type="content" source="./media/icon-application-window.png" alt-text="Application window icon." border="false":::
   :::column-end:::
   :::column span="3":::
[**Secure applications with Zero Trust**](https://aka.ms/ZTApplications)

Applications and APIs provide the interface by which data is consumed. They may be legacy on-premises, lifted-and-shifted to cloud workloads, or modern SaaS applications. Apply controls and technologies to discover shadow IT, ensure appropriate in-app permissions, gate access based on real-time analytics, monitor for abnormal behavior, control user actions, and validate secure configuration options.
   :::column-end:::
<!-- Placeholder for video link.
   :::column span="2":::
[:::image type="content" source="./media/video-image-placeholder-03.png" alt-text="Placeholder 3." border="false":::](https://youtu.be/6jsOaz1uS08)
   :::column-end:::
-->
:::row-end:::
:::row::: <!-- ROW: Data -->
   :::column:::
:::image type="content" source="./media/icon-ones-and-zeroes.png" alt-text="Ones and zeroes icon." border="false":::
   :::column-end:::
   :::column span="3":::
[**Secure data with Zero Trust**](https://aka.ms/ZTData)

Ultimately, security teams are protecting data. Where possible, data should remain safe even if it leaves the devices, apps, infrastructure, and networks the organization controls. Classify, label, and encrypt data, and restrict access based on those attributes.
   :::column-end:::
<!-- Placeholder for video link.
   :::column span="2":::
[:::image type="content" source="./media/video-image-placeholder-04.png" alt-text="Placeholder 4." border="false":::](https://youtu.be/XFg3szECXiw)
   :::column-end:::
-->
:::row-end:::
:::row::: <!-- ROW: Infrastructure -->
   :::column:::
:::image type="content" source="./media/icon-data-storage-disks.png" alt-text="Data storage disks icon." border="false":::
   :::column-end:::
   :::column span="3":::
[**Secure infrastructure with Zero Trust**](https://aka.ms/ZTInfrastructure)

Infrastructure—whether on-premises servers, cloud-based VMs, containers, or micro-services—represents a critical threat vector. Assess for version, configuration, and JIT access to harden defense. Use telemetry to detect attacks and anomalies, and automatically block and flag risky behavior and take protective actions.
   :::column-end:::
<!-- Placeholder for video link.
   :::column span="2":::
[:::image type="content" source="./media/video-image-placeholder-05.png" alt-text="Placeholder 5." border="false":::](https://youtu.be/Nr01LAPaaik)
   :::column-end:::
-->
:::row-end:::
:::row::: <!-- ROW: Networks -->
   :::column:::
:::image type="content" source="./media/icon-network-diagram.png" alt-text="Network diagram icon." border="false":::
   :::column-end:::
   :::column span="3":::
[**Secure networks with Zero Trust**](https://aka.ms/ZTNetwork)

All data is ultimately accessed over network infrastructure. Networking controls can provide critical controls to enhance visibility and help prevent attackers from moving laterally across the network. Segment networks (and do deeper in-network micro-segmentation) and deploy real-time threat protection, end-to-end encryption, monitoring, and analytics.
   :::column-end:::
<!-- Placeholder for video link.
   :::column span="2":::
[:::image type="content" source="./media/video-image-placeholder-06.png" alt-text="Placeholder 6." border="false":::](https://youtu.be/8CBfhBCtGGw)
   :::column-end:::
-->
:::row-end:::
:::row::: <!-- ROW: Visibility, automation, and orchestration -->
   :::column:::
:::image type="content" source="./media/icon-gear.png" alt-text="Gear icon." border="false":::
   :::column-end:::
   :::column span="3":::
[**Visibility, automation, and orchestration with Zero Trust**](https://aka.ms/ZTCrossPillars)

In our Zero Trust guides, we define the approach to implement an end-to-end Zero Trust methodology across identities, endpoints and devices, data, apps, infrastructure, and network. These activities increase your visibility, which gives you better data for making trust decisions. With each of these individual areas generating their own relevant alerts, we need an integrated capability to manage the resulting influx of data to better defend against threats and validate trust in a transaction.
   :::column-end:::
<!-- Placeholder for video link.
   :::column span="2":::
[:::image type="content" source="./media/video-image-placeholder-07.png" alt-text="Placeholder 7." border="false":::](https://youtu.be/FgC-kVfcgm8)
   :::column-end:::
-->
:::row-end:::

With Zero Trust, we move away from a trust-by-default perspective to a trust-by-exception one. An integrated capability to automatically manage those exceptions and alerts is important so you can more easily find and detect threats, respond to them, and prevent or block undesired events across your organization.




<p class=MsoNormal style='line-height:107%'><span style='position:absolute; z-index:-1895825408;margin-left:-15px;margin-top:9px;width:50px;height:50px'><img width=50 height=50 src="icon-fingerprint.png" alt="Fingerprint icon."></span></p>

<p class=MsoListParagraph style='margin-bottom:6.0pt'><b><span style='font-family:"Segoe UI",sans-serif;color:#0078D4'>Secure identity </span></b><b><span style='font-family:"Segoe UI",sans-serif;color:black'>with Zero Trust - </span></b><a href="https://aka.ms/ZTIdentity"><span style='font-family:"Segoe UI",sans-serif'>aka.ms/ZTIdentity</span></a></p>

<p class=MsoNormal style='margin-top:0in;margin-right:0in;margin-bottom:.25in;
margin-left:.5in'><span style='position:absolute;z-index:-1895825407;
left:0px;margin-left:-2px;margin-top:102px;width:27px;height:23px'><img
width=27 height=23
src="MSFT_Zero_Trust_Deployment_Guidance%20-%20Intro%20(review%20document)_files/image003.jpg"></span><span
style='font-family:"Segoe UI",sans-serif;color:black'>Identities—whether they
represent people, services, or IoT devices—define the Zero Trust control plane.
When an identity attempts to access a resource, verify that identity with
strong authentication, and ensure access is compliant and typical for that
identity. Follow least privilege access principles.</span></p>

<p class=MsoListParagraph style='margin-top:6.0pt;margin-right:0in;margin-bottom:
6.0pt;margin-left:.5in'><b><span style='font-family:"Segoe UI",sans-serif;
color:#0078D4'>Secure endpoints </span></b><b><span style='font-family:"Segoe UI",sans-serif;
color:black'>with Zero Trust - </span></b><a href="https://aka.ms/ZTDevices"><span
style='font-family:"Segoe UI",sans-serif'>aka.ms/ZTEndpoints</span></a></p>

<p class=MsoNormal style='margin-top:0in;margin-right:0in;margin-bottom:.25in;
margin-left:.5in'><span style='position:absolute;z-index:251658245;left:0px;
margin-left:-1px;margin-top:117px;width:26px;height:26px'><img width=26
height=26
src="MSFT_Zero_Trust_Deployment_Guidance%20-%20Intro%20(review%20document)_files/image004.png"></span><span
style='font-family:"Segoe UI",sans-serif;color:black'>Once an identity has been
granted access to a resource, data can flow to a variety of different endpoints—from
IoT devices to smartphones, BYOD to partner-managed devices, and on-premises
workloads to cloud-hosted servers. This diversity creates a massive attack
surface area. Monitor and enforce device health and compliance for secure
access.</span></p>

<p class=MsoListParagraph style='margin-bottom:6.0pt'><b><span
style='font-family:"Segoe UI",sans-serif;color:#0078D4'>Secure applications </span></b><b><span
style='font-family:"Segoe UI",sans-serif;color:black'>with Zero Trust - </span></b><a
href="https://aka.ms/ZTApplications"><span style='font-family:"Segoe UI",sans-serif'>aka.ms/ZTApplications</span></a></p>

<p class=MsoNormal style='margin-top:0in;margin-right:0in;margin-bottom:.25in;
margin-left:.5in'><span style='font-family:"Segoe UI",sans-serif;color:black'>Applica</span></p>

<p class=MsoNormal style='margin-top:0in;margin-right:0in;margin-bottom:.25in;
margin-left:.5in'><span style='font-family:"Segoe UI",sans-serif;color:black'>ztions
and APIs provide the interface by which data is consumed. They may be legacy
on-premises, lifted-and-shifted to cloud workloads, or modern SaaS
applications. Apply controls and technologies to discover shadow IT, ensure
appropriate in-app permissions, gate access based on real-time analytics, monitor
for abnormal behavior, control user actions, and validate secure configuration
options.</span></p>

<p class=MsoListParagraph style='margin-bottom:6.0pt'><span style='position:
absolute;z-index:-1895825406;left:0px;margin-left:1px;margin-top:0px;
width:25px;height:22px'><img width=25 height=22
src="MSFT_Zero_Trust_Deployment_Guidance%20-%20Intro%20(review%20document)_files/image005.png"></span><b><span
style='font-family:"Segoe UI",sans-serif;color:#0078D4'>Secure data </span></b><b><span
style='font-family:"Segoe UI",sans-serif;color:black'>with Zero Trust - </span></b><a
href="https://aka.ms/ZTData"><span style='font-family:"Segoe UI",sans-serif'>aka.ms/ZTData</span></a></p>

<p class=MsoNormal style='margin-top:0in;margin-right:0in;margin-bottom:.25in;
margin-left:.5in'><span style='position:absolute;z-index:-1895825405;
left:0px;margin-left:2px;margin-top:80px;width:23px;height:25px'><img width=23
height=25
src="MSFT_Zero_Trust_Deployment_Guidance%20-%20Intro%20(review%20document)_files/image006.jpg"></span><span
style='font-family:"Segoe UI",sans-serif;color:black'>Ultimately, security
teams are protecting data. Where possible, data should remain safe even if it
leaves the devices, apps, infrastructure, and networks the organization
controls. Classify, label, and encrypt data, and restrict access based on those
attributes.</span></p>

<p class=MsoListParagraph style='margin-bottom:6.0pt'><b><span
style='font-family:"Segoe UI",sans-serif;color:#0078D4'>Secure infrastructure </span></b><b><span
style='font-family:"Segoe UI",sans-serif;color:black'>with Zero Trust - </span></b><a
href="https://aka.ms/ZTInfrastructure"><span style='font-family:"Segoe UI",sans-serif'>aka.ms/ZTInfrastructure</span></a></p>

<p class=MsoNormal style='margin-top:0in;margin-right:0in;margin-bottom:.25in;
margin-left:.5in'><span style='position:absolute;z-index:-1895825404;
left:0px;margin-left:0px;margin-top:101px;width:24px;height:24px'><img
width=24 height=24
src="MSFT_Zero_Trust_Deployment_Guidance%20-%20Intro%20(review%20document)_files/image007.jpg"></span><span
style='font-family:"Segoe UI",sans-serif;color:black'>Infrastructure—whether
on-premises servers, cloud-based VMs, containers, or micro-services—represents
a critical threat vector. Assess for version, configuration, and JIT access to
harden defense. Use telemetry to detect attacks and anomalies, and
automatically block and flag risky behavior and take protective actions.</span></p>

<p class=MsoListParagraph style='margin-bottom:6.0pt'><b><span
style='font-family:"Segoe UI",sans-serif;color:#0078D4'>Secure networks </span></b><b><span
style='font-family:"Segoe UI",sans-serif;color:black'>with Zero Trust - </span></b><a
href="https://aka.ms/ZTNetwork"><span style='font-family:"Segoe UI",sans-serif'>aka.ms/ZTNetwork</span></a></p>

<p class=MsoNormal style='margin-top:0in;margin-right:0in;margin-bottom:12.0pt;
margin-left:.5in'><span style='font-family:"Segoe UI",sans-serif'>All data is
ultimately accessed over network infrastructure. Networking controls can
provide critical controls to enhance visibility and help prevent attackers from
moving laterally across the network. Segment networks (and do deeper in-network
micro-segmentation) and deploy real-time threat protection, end-to-end
encryption, monitoring, and analytics<a name="_Securing_Identity_with"></a>.</span></p>

<b><span style='font-size:11.0pt;font-family:"Segoe UI",sans-serif;color:#0078D4'><br
clear=all style='page-break-before:always'>
</span></b>

<p class=MsoNormal><b><span style='font-family:"Segoe UI",sans-serif;
color:#0078D4'>&nbsp;</span></b></p>

<p class=MsoNormal><b><span style='font-family:"Segoe UI",sans-serif;
color:#0078D4'>&nbsp;</span></b></p>

<p class=MsoNormal style='margin-top:0in;margin-right:0in;margin-bottom:12.0pt;
margin-left:.5in'><span style='position:absolute;z-index:-1895823355;
left:0px;margin-left:0px;margin-top:0px;width:24px;height:24px'><img width=24
height=24
src="MSFT_Zero_Trust_Deployment_Guidance%20-%20Intro%20(review%20document)_files/image008.png"></span><b><span
style='font-family:"Segoe UI",sans-serif;color:#0078D4'>Visibility, automation,
and orchestration</span></b><span style='font-family:"Segoe UI",sans-serif'> <b><span
style='color:black'>with Zero Trust</span></b> - </span><a
href="https://aka.ms/ZTCrossPillars"><span style='font-family:"Segoe UI",sans-serif'>aka.ms/ZTCrossPillars</span></a></p>

<p class=MsoNormal style='margin-top:0in;margin-right:0in;margin-bottom:12.0pt;
margin-left:.5in'><span style='font-family:"Segoe UI",sans-serif'>In our Zero
Trust guides, we define the approach to implement an end-to-end Zero Trust
methodology across identities, endpoints and devices, data, apps,
infrastructure, and network. These activities increase your visibility, which
gives you better data for making trust decisions. With each of these individual
areas generating their own relevant alerts, we need an integrated capability to
manage the resulting influx of data to better defend against threats and
validate trust in a transaction.</span></p>

