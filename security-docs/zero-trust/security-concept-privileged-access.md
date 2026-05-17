---
title: Privileged access
description: Get a primer overview of privileged access
ms.date: 02/24/2025
ms.service: security
ms.subservice: zero-trust
ms.topic: concept-article
---

# Overview - privileged access

Privileged access sits across the [enterprise access model](security-adoption-discipline-identity-access-enterprise-model.md) and provides the only administrative path to the control plane. It defines who can configure systems, manage identities, enforce security, and ultimately shape the organization’s technology environment.

In modern enterprises, a relatively small number of identities - administrators, service accounts, and control plane roles have power and access to most business assets. These identities can:

- Modify access controls
- Change system configurations
- Access sensitive data
- Disable or bypass security protections

Attackers recognize this. Rather than attacking every system individually, they focus on:

- Stealing credentials.
- Escalating privileges.
- Moving laterally toward high-value roles.

Once privileged access is obtained, the attacker can operate with  speed and scale.

This is why modern security models treat privileged access differently:

- **It must be explicitly controlled**.
    For example, define privileged roles and onboarding through identity governance and privileged identity management (PIM), requiring approval and time-bound elevation nstead of permanent role assignments.
- **It must be isolated from normal activity**.
    For example, use separate administrative accounts and dedicated privileged access devices (PAWs) so privileged actions never occur from standard user sessions or unmanaged devices.
- **It must be continuously monitored**.
    For example, send privileged sign-ins, role activations, and policy changes to monitoring tools like Microsoft Sentinel to detect unusual usage patterns and trigger alerts or automated response.
- **It must be agreed that privileged access is a primary target of compromise**.
    For example, protect all privileged accounts with strong multifactor authentication (MFA), no standing access, and break-glass account controls, assuming attackers will attempt credential theft and privilege escalation.
    

Protecting privileged access requires looking beyond just roles and accounts to understanding all components that have privileged access. This includes:

- The identity control plane.
- Privileged devices, apps, and interfaces.
- Intermediary systems such as VPNs, PIM and privileged access management (PAM) systems.

Together, these define how control is exercised—and how it must be protected. 

The following graphic illustrates the potential attack surface for privileged access compromise.

:::image type="content" source="./media/security-adoption-discipline-privileged-access-attack.png" alt-text="Diagram showing the potential attack surface for privileged access." lightbox="./media/security-adoption-discipline-privileged-access-attack.png":::




## Identity control plane

The identity control plane is the layer that defines and governs who can hold privileged roles and how those privileges are assigned, elevated, and revoked across the organization. In a privileged access context, it includes privileged identities, role assignments, and approved elevation paths, forming the foundation that all other controls depend on.

Securing the identity control plane ensures that privilege is explicit, time-bound, strongly authenticated, and auditable, preventing unauthorized or uncontrolled access to the systems that ultimately control the entire environment.

The following diagram show that the control plane is centrally managed in cloud services (Microsoft Entra ID, Intune, Defender for Endpoint) and can only be accessed through a privileged access workstation (PAW), enforcing isolation, control, and secure administration of all privileged operations.

:::image type="content" source="./media/security-adoption-discipline-access-privileged-control.png" alt-text="Diagram showing Microsoft technologies that protect the identity control plane." lightbox="./media/security-adoption-discipline-access-privileged-control.png":::


### Control plane roles

Microsoft Entra ID has roles and permissions that are identified as privileged.

These roles and permissions can be used to delegate management of directory resources to other users, modify credentials, authentication or authorization policies, or access restricted data. Privileged role assignments can lead to elevation of privilege if not used in a secure and intended manner. 

- Review [privileged Microsoft Entra roles](/entra/identity/role-based-access-control/permissions-reference). 
- [Learn more](/entra/identity/role-based-access-control/privileged-roles-permissions) about viewing and using privileged roles.

## Privileged access workstations

A Privileged Access Workstation (PAW) is a dedicated, hardened device used only for performing administrative tasks. It is separate from normal user devices and is tightly secured to reduce the risk of credential theft, malware, or lateral movement.
PAWs enforce key protections such as:

- Strong authentication (for example, Windows Hello for Business)
- Device hardening (Credential Guard, Device Guard, Exploit Guard, AppLocker)
- Restricted usage (no general browsing or productivity activity)

The goal is to ensure that privileged credentials and actions are never exposed to untrusted environments.

The following diagram shows how the PAW in the only trusted access point into the control plane.

:::image type="content" source="./media/security-adoption-discipline-access-enterprise-privileged-device.png" alt-text="Diagram showing Microsoft technologies that protect privileged devices." lightbox="./media/security-adoption-discipline-access-enterprise-privileged-device.png":::


As shown in the diagram, all administrative actions flow through the PAW and are controlled as summarized in the table.

**Control** | **Implementation**
--- | ---
**Explicitly controlled** | Administrative access is granted only through policy-based identity controls, requiring strong authentication and approved, time-bound elevation.<br/></br> Device state must also meet compliance requirements before access is allowed.
**Isolated from normal activity** | Privileged operations are restricted to a dedicated PAW device with tightly controlled usage and connectivity. The PAW is not used for general productivity and has restricted internet access and secure remote connectivity to sensitive systems.
**Continuously monitored** |All identity activity, device state, and endpoint behavior are continuously collected and analyzed, enabling detection of abnormal privileged activity and rapid response.
**Assumed to be targeted** | The environment is hardened and continuously validated, assuming attackers will target privileged access. Devices are kept up to date, secure bootstrapping is enforced.


## Next steps

Deploy a [privileged access architecture](adopt/implement-privileged-access.md)