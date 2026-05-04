---
title: Microsoft Zero Trust Workshop - Networking
description: Learn about the Networking pillar in the Microsoft Zero Trust Workshop
ms.date: 04/18/2024
ms.service: security
author: rayne-wiselman
ms.author: raynew
ms.subservice: zero-trust
ms.topic: conceptual
---

# Network security in the Microsoft Zero Trust Workshop

In a Zero Trust architecture, you can no longer treat the network as a trusted entity behind your perimeter. Every connection needs to be verified, segmented, and monitored. The Network pillar is about ensuring that all traffic — internal, external, east‑west — is controlled, encrypted, and subject to adaptive controls, not just once at the firewall. 

Networking pillar guidance focuses on moving networking security closer to resources, apps, and data by authenticating and authorizing every request (“verify explicitly”), segmenting networks and limiting access (least privilege), and assuming compromise and restricting lateral movement (“assume breach”). The Networking workshop covers these implementation areas:

- **Implement a Zero Trust network model**: Adopt a risk-based networking strategy rather than relying on a trusted perimeter. Continuously verify every session based on identity, device state, and context. Use segmentation (network, app, user) to limit the “blast radius” if someone is compromised.
- **Encrypt all traffic**: Ensure that internal and external traffic is encrypted end-to-end. Use secure, identity-aware gateways to enforce encryption and access policies.
- **Enable secure outbound access**: Use a secure web gateway (SWG) to inspect and control outbound traffic based on identity and context. Define baseline Internet policies (e.g. block categories, safe browsing), and apply additional policies per user or group. 
- **Segment app access**: Isolate applications in the network and apply micro‑segmentation so that sensitive services are not exposed broadly. Use identity- and role-based policies to control who can access which application segments.
- **Improve visiblity and monitoring**: Deploy analytics to monitor network flows, detect anomalies, and drive threat detection. Log and audit network traffic, especially for segmentation boundaries and gateway access, to inform SecOps.

## Assess networking posture**

The Zero Trust Assessment tool  can assess your networking configuration against a range of security best practices. [Learn more](/security/zero-trust/assessment/overview).