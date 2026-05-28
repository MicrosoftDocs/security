---
title: Microsoft Zero Trust Workshop - Networking
description: Learn about the Networking pillar in the Microsoft Zero Trust Workshop
ms.date: 05/24/2026
ms.service: security
author: rayne-wiselman
ms.author: raynew
ms.subservice: zero-trust
ms.topic: conceptual

#customer intent: As a security implementer, I want to understand how the Networking Zero Trust workshop can help with a network deployment that's aligned with Zero Trust principles and security best practices.
---

# Network security in the Microsoft Zero Trust Workshop

In a Zero Trust architecture, the network is no longer treated as a trusted boundary. Instead, it becomes a transport layer where every connection must be explicitly verified, authorized, and continuously monitored. The Network pillar focuses on securing access to applications and resources by enforcing identity- and context-aware controls, segmenting connectivity, and minimizing the ability for attackers to move laterally.

Network pillar guidance focuses on moving access control away from the perimeter and closer to applications and resources. It emphasizes verifying every connection using identity and device signals, enforcing least-privilege access through segmentation, and assuming breach by limiting exposure and restricting lateral movement.

## Workshop implementation

The Network workshop covers the implementation areas summarized in the table.

**Area** | **Details**
--- | ---
**Implement Zero Trust network access (ZTNA) for applications**  | Replace implicit trust in the corporate network with identity and context-based access decisions. <br/><br/>Connect users directly to applications using identity-aware access controls, and continuously evaluate sessions based on identity, device posture, risk signals, and location.
**Enable secure private access to internal applications**  |   Provide access to internal and private applications without exposing them to the public internet. <br/><br/>Use application proxies and identity-aware gateways to eliminate broad network-level access and reduce attack surface.
**Secure outbound internet access**  |   Use a secure web gateway (SWG) or similar cloud-delivered controls to inspect, filter, and control outbound traffic. <br/><br/>Apply policies based on user identity, device state, and risk to prevent access to malicious or inappropriate destinations.
**Segment networks and application access**  |   Implement segmentation and micro-segmentation across on-premises and cloud environments to limit connectivity between users, devices, and applications. <br/><br/>Restrict lateral movement by granting access only to explicitly authorized resources.
**Encrypt and protect all network traffic**  |  Ensure that all traffic—internal, external, and east-west—is encrypted in transit. <br/><br/>Use secure protocols and identity-aware gateways to maintain confidentiality and integrity of communications.
**Move enforcement closer to applications and data**  |   Shift enforcement from traditional perimeter controls to application-level and identity-aware controls.<br/><br/> Use reverse proxies, application gateways, and session-based controls to enforce policy at the point of access.
**Improve network visibility and continuous monitoring**  | Gain visibility into network traffic, application access patterns, and user activity. <br/><br/>Continuously monitor sessions and analyze logs from network controls, gateways, and segmentation boundaries to detect anomalies and support investigation.
**Integrate network signals into security operations (SecOps)** |   Feed network telemetry, access events, and traffic analytics into centralized monitoring and response systems.<br/><br/> Correlate network activity with identity, device, data, and infrastructure signals to detect threats, investigate incidents, and respond to suspicious behavior.



## Assess networking posture

The Zero Trust Assessment tool  can assess your networking configuration against a range of security best practices. [Learn more](/security/zero-trust/assessment/overview).

## Next steps

[Run an assessment](assessment/get-started.md), and begin the [Networking workshop](https://zerotrust.microsoft.com/).