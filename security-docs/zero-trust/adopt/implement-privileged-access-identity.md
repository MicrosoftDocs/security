---
title: Phase 1-Secure the identity control plane
description: Learn how to configure the identity control plan in a privileged access architecture
ms.date: 05/05/2025
ms.service: security
author: rayne-wiselman
ms.author: raynew
ms.subservice: zero-trust
ms.topic: conceptual
---


# Phase 1 - Secure the identity control plane

This article is part of the [Implement a privileged access architecture](implement-privileged-access.md) solution guide, which provides phased implementation guidance aligned to the [privileged access architecture](../security-adoption-scenario-privileged-access.md) under the *[Protect critical business assets](../security-adotpion-scenario-secure-assets.md)* business scenario.

Privileged access is the highest-impact security risk in most organizations because it enables direct control over identity systems, cloud control planes, and business-critical assets.


This article helps you to implement Phase 1 of the [Implement a privileged access architecture](implement-privileged-access.md) solution. 

During Phase 1 you secure the identity control plane by defining and protecting privileged identities, role assignments, and authorized elevation paths.

Implement Phase 1 first. Later phases to secure privileged access devices, enforce Conditional Access policy, and monitor access depend on having clean, well-governed privileged identities and explicit elevation paths.

## Protection goals

Phase 1 ensures that privileged access is:

- **Explicit**: Privilege is granted only through defined elevation paths. It's never implicit or accidental.
- **Temporary**: Privilege expires automatically.
- **Strongly authenticated**: Elevation requires strong authentication.
- **Auditable**: All privilege changes and elevations are logged.
- **Recoverable**: Emergency access exists without weakening controls.

### Protection scope

Phase 1 focuses on two foundational components of privileged access:

- **Privileged identities**: Identities that can perform privileged actions, including:

    - Dedicated administrative user accounts
    - Administrative groups
    - Service principals and managed identities
    - Azure RBAC role assignments
    - Emergency (break‑glass) access accounts (if they don't exist).
- **Authorized elevation paths**: Mechanisms that allow users to move from non‑privileged to privileged states, such as:

    - Time‑bound role activation using - Privileged Identity Management (PIM)
    - Approval workflows for sensitive roles
    - Explicit administrative sessions
**Emergency recovery access**: Configuring break-glass accounts if these don't already exist.


These components operate in the control plane. If they are compromised, attackers can grant themselves privileged access without touching devices or access policies.

## Risks mitigated

**Risk** | **Why it matters** | **Phase 1 mitigation**
--- | --- | ---
**Uncontrolled creation of privileged identities** | Attackers create new admins or role assignments silently. | Establish authoritative privileged identities and roles.<br/>Restrict who can manage identity systems.<br/>Treat identity systems as privileged assets.
**Silent privilege escalation** | Privilege gained through groups, RBAC, or nested assignments. | Rationalize roles, use group‑based assignments, remove standing access.
**Persistent (standing) administrative access** | Stolen credentials retain permanent privilege. | Replace standing privilege with time‑bound elevation.
**Weak or implicit elevation paths** | Attackers use same paths as admins. | Define secure, explicit, auditable elevation workflows
**Bypassing downstream protections** | Privilege gained before device or policy enforcement.| Identity control plane secured first.
**Irrecoverable identity compromise** | No safe way to regain control. | Create protected emergency access accounts.
**Low identity security posture** | Weak identity controls undermine all later phases.| Raise identity systems to highest security level.


## Phase outcomes

After completing this phase:

- All privileged access is tied to known, explicit identities and roles.
- All privilege is temporary, auditable, and intentional.
- Standing administrative access is removed.
- Identity systems are treated as privileged assets.
- Recovery from identity compromise is possible without weakening controls.
- No new privileged risk is introduced during modernization.

This phase also stops the creation of new privileged risk while auditing and modernization continue.

## Prerequisites

Before you start configuring Phase 1, note the following prerequisites:

Review the documentation:

- [Review the overview article](implement-privileged-access.md) for this solution.
- Work through the [planning article](implement-privileged-access-plan.md) to agree on which roles and identities perform privileged work.

Within your organization:

- Make sure you have an active, owned Microsoft Entra ID tenant. We recommended Microsoft Entra ID P2 (for privileged identity governance).
- This solution assumes you have Microsoft 365 Enterprise E5. For more information, see [Microsoft 365 Enterprise licensing](https://www.microsoft.com/licensing/product-licensing/microsoft-365-enterprise).
- Make sure you have at least two [emergency access accounts](/entra/identity/role-based-access-control/security-emergency-access) defined.
- Clear ownership for identity governance and role management.
- Creating secure admin accounts exposes them to the workstation used during setup. Make sure that initial configuration is performed from a known‑safe device.


## Step 1: Audit privileged access

Establish a complete inventory of privileged identities and access paths. Audit the following sources.

**Source** | **Details**
--- | ---
**Microsoft Entra directory roles** | Identify [privileged roles](/entra/identity/role-based-access-control/permissions-reference) that can directly or indirectly lead to tenant dominance by altering identity, access, or trust boundaries in the identity control plane. <br/><br/>For each role:<br/>- Identify direct versus group‑based assignments.<br/>- Identify permanent versus PIM‑eligible assignments<br/>- Capture current activation state.
**Group-based privilege** | Find out who is privileged indirectly and would be missed if you only look at users.<br/><br/>- Review nested group membership<br/>- Identify users, service principals, and managed identities<br/>- Record how privilege is inherited
**Azure RBAC roles** | Find out what these privileged identities can do outside the directory itself.<br/><br/>Audit assignments at management group, subscription, and resource scopes<br/>Identify identities with broad or cascading permissions
**Non-human identities** | Find out which non-human identities are part of the privileged access service, including:<br/><br/>Service principals and managed identities<br/>Automation accounts and scripts<br/>Application permissions with tenant or resource control.

The result is an authoritative privileged identity inventory.


### Identify directory roles

Audit who can change identity, authentication, or tenant-wide configuration.

1. In the [Microsoft Entra Admin Center](https://entra.microsoft.com), navigate to **Entra ID** > **Roles & Admins**.
1. Select **All roles**. This page lists all built-in and custom Microsoft Entra directory roles, including tenant-wide admin roles such as Global Administrator and Privileged Role Administrator.

    - Privileged roles are any that can assign roles, modify security/authentication, or manage apps, devices, or security policies.
    - A full list of privileged built-in roles is also available [in the documentation](/entra/identity/role-based-access-control/permissions-reference).
    - If you can't check all roles at minimum audit:  Global Admin, Privileged Role Admin, Exchange Admin, SharePoint Admin.

1. For each privileged role, first check direct assignments. For each directly assigned principal (user, group, or service principal (app/managed identity)), check how the role is granted and current state.
    - A permanent assignment means that the role is always on. An identity signs in and is already privileged with an **Active (permanent)** status. This is obviously high-risk.
    - A PIM eligible assignment means that the role is available but not active until it's activated. The user must activate the role. It's usually time-limited and often requires a justification. Status can be **Active** or **Eligible** if the user can become privileged but isn't currently activated.

1. Now switch to group assignments. This is important since it checks indirectly assigned privileged inherited via groups. 
1. Open each group that's assigned the privileged role.
1. Expand group members, expand nested groups, and record Users, Service Principals and Managed identities. 
1. For each identity confirm how the privilege is held:
    - Is the role assigned via group or nested group?
    - Is the role permanent or PIM eligible?
    - What's the current state?


After completing this step, you've captured the identity control plane, and have an authoritative privileged identity inventory for Microsoft Entra.


### Identify Azure RBAC roles

Now that you know which identities are privileged, let's check what they can do outside of the Microsoft Entra Directory. Where else do they have control, and at what scope? 
 
1. For each privileged principal that you've identified, determine roles.
1. Start at the highest scope (management groups).
    1. In the Azure portal > **Management groups**, go to **Access control (IAM) > **Role assignments**.
    1. Use **Filter** > **Assigned to** and search for the principal name.
    1. Record any results, including role name and scope.

    If you find identities here, it indicates that they have broad Azure control, since Azure RBAC roles assigned at the management group scope cascade down to all child subscriptions and resources.
1. Now follow the same procedures for Azure portal > **Subscriptions**.

    Identities with Azure RBAC roles assigned at the subscription level are privileged and can grant or delegate access.
1. If identities weren't found at the management group or subscription level, you can check at the resource groups level with the same procedure in Azure portal > **Resource groups**.
1. You might also want to check whether principals have control on strategic individual resources such as Key vaults, storage accounts, virtual machines, or automation accounts. To do that, check **Access control (IAM)** > **Assigned to** for each individual resource.

### Record results.

1. For each account you identified, capture audit details in a mapping table.
1. Identify high-risk accounts with broad privileges, and create a mapping table that will provide information about role scope (blast radius) and type of work.

    **Account** | **Entra role** | **Azure RBAC role** | **Scope** | **Privileged work**
    --- | --- | --- | --- | ---
    alice@contoso.com | Global Admin | Owner | Sub1, Sub2 | Manage users, roles, subscriptions.

1. If you want to add more about observed behavior for an account you can:
    1. Review sign-in logs for information about apps, client endpoints, and authentication flows.
    1. Correlate information with audit and activity logs to check whether an account is used, and whether it changed policy, modified resources/subscriptions, or performance some other activity.

## Step 2: Assess your existing configuration

With your inventory in place, you can use the [Zero Trust Assessment tool](/assessment/overview.md) to evaluate how privileged access is configured across your environment and identify gaps in control. 

While the Assessment tool doesn't replace  a full inventory, it uses role and policy data as input to help you understand: 

- Whether privileged roles are protected (MFA, Conditional Access).
- Whether privileged access is governed (PIM, JIT/JEA patterns).
- Whether policies are consistently applied.
- Where gaps exist across identities, devices, and access policies 

[Learn more](/entra/fundamentals/configure-security?toc=/security/zero-trust/toc.json&bc=/security/zero-trust/toc.json) about assessing identity with the tool. 


## Step 3: Establish dedicated administrative identities

Remove privileged roles from standard user accounts. 

Create dedicated administrative accounts that:

- Are used only for privileged tasks
- Have no productivity access (email, Teams, browsing)
- Are eligible for privilege via PIM, not permanently assigned

Remove all privileged role assignments from standard user identities.


### Create admin accounts

1. In the [Microsoft Entra Admin Center](https://entra.microsoft.com), navigate to **Microsoft Entra ID** > **Users**.
1. Select **New user** and configure the user settings. then select **Create**.
    - Name: Secure Workstation Administrator.
    - User principle name: secure-ws-admin@contoso.com
    - Authentication method: Password (temporary).
    - Directory roles: None
    - Usage location: Set to operational location.

This provides you with a clean admin identity with no privilege. 



## Step 4: Create identities for PAWs

In later procedures you set up a privileged admin workstation (PAW). 

If you want to define identities that can access PAWs but that can't perform privileged actions, you can:

- Create an identity that can only sign into PAWs.
- Create a security group that controls who is allowed to sign into the PAWs. 
    - This group never grants admin rights, it's used for conditional access (allow only Secure Workstation Users to sign in to PAWs, block other users ) and to apply specific group-based PAW licensing.
    - Typical members of this group include SOC analyst, operators, and auditors.


### Create a sign-in identity

1. In the [Microsoft Entra Admin Center](https://entra.microsoft.com), navigate to **Microsoft Entra ID** > **Users**.
1. Select **New user** and configure the user settings. then select **Create**.
    - Name: Secure Workstation User.
    - User principle name: secure-ws-user@contoso.com
    - Directory roles: None

### Create a PAW access security group

Configure a group that controls who can sign in to the PAWs

1. In the [Microsoft Entra Admin Center](https://entra.microsoft.com), navigate to **Microsoft Entra ID** > **Groups** > **New group**. 
1. Configure the group settings, and then select **Create**.
    - Group: Security
    - User principle name: Secure Workstation Users
    - Membership: Assigned
    - Directory roles: None

1. Add only PAW sign-in identities to the group, not admins by default.


## Step 5: Create administrative control groups

Create security groups that define who is eligible for privileged roles.
These groups:

- Are marked as role‑assignable
- Are managed through PIM
- Do not grant privilege by membership alone
- Serve as authorization boundaries for elevation

Membership changes are treated as privileged actions and reviewed regularly

1. In the [Microsoft Entra Admin Center](https://entra.microsoft.com), navigate to **Microsoft Entra ID** > **Groups** > **New group**.
1. Configure the group settings, and then select **Create**.
    - **Group type**: Security
    - **Name**: Secure Workstation Admins
    - **Membership type**: Assigned

1. Add dedicated admin identities. Don't use standard accounts and treat membership changes as sensitive. Review regularly. 

This group will later be:

- Marked as *role-assignable*
- Assigned directory roles via PIM as **eligible** (not active)
- Use as the primary targeting mechanism for privileged access policies

## Step 6: Configure PIM

If Privileged Identity Management isn't already enabled, do that now. 

Ensure you're signed in as a Global Administrator or Privileged Role Administrator.


### Enable PIM for directory roles

1. In the [Microsoft Entra Admin Center](https://entra.microsoft.com), navigate to **Identity governance** > **Privileged Identity Management**.. 
1. Select **Microsoft Entra roles**.

## Remove permanent roles

1. In **Microsoft Entra roles**, select **Roles**.
1. Open privileged access roles identified for your organization. 

    The minimum set recommended by Microsoft is as follows:
        - Global Administrator
        - Privileged Role Administrator
        - Security Administrator
        - Exchange Administrator
        - SharePoint Administrator
1. Select **Assignments**.
1. For each **Active** (permanent) assignment:
    - Remove the permanent assignment
    - Re-add the user or group as **Eligible**.

After this, users do not have admin privileges unless they activate them.

### Configure activation settings

For each privileged role, do the following:

1. In **PIM** > **Microsoft Entra roles**, select **Settings**.
1. Select the role > **Edit**.
1. Configure settings:
    - Require activation
    - Require MFA on activation
    - Require justification
    - Set maximum activation duration (for example: 1–4 hours for high‑impact roles)
    - Require approval (for Global Admin, Privileged Role Admin, Security Admin)
    - Select one or more approvers

1. Select **Update**.

### Use group-based role assignments

We recommend assigning roles to groups, not individual users, for scale and governance.

Create a role-assignable security group and assign it to an Entra role (e.g., Exchange Admin). Then manage membership (who can get the role) via your governance process, and optionally via PIM for Groups.

1. Create a security group with  the setting **Microsoft Entra roles can be assigned to this group** enabled.
1. In PIM > **Microsoft Entra roles**, select **Add assignments**.
1. Assign the group as **Eligible** for the role.
1. Add or remove users from the group instead of modifying role assignments directly.

This group becomes the authorization boundary for privileged access.


At the completion of Step 5, The following is configured:

- No standing administrative access
- Privilege is requested, approved, time‑bound, logged
- Elevation paths are explicit and reviewable

## Step 7: Configure emergency accounts

If you don't already have emergency access accounts in place, configure them now. They're required to recover from identity lockout scenarios caused by Conditional Access, MFA outages, or misconfiguration.

Ensure you're signed in as a Global Administrator or Privileged Role Administrator to create at least two emergency access accounts.

1. In the [Microsoft Entra Admin Center](https://entra.microsoft.com), navigate to **Users** > **All users**.
1. Select **New user**, and create a cloud-only user.

- Use the *.onmicrosoft.com domain
- Use a non‑obvious name (not “breakglass”)

1. Assign the Global Administrator role.
- Do not make this role PIM‑eligible — it must be permanent.
- Use a strong, long password, stored securely offline.
- Configure phishing‑resistant authentication (for example, FIDO2 / passkey or certificate‑based auth)
- Do not tie MFA to a personal phone or email address.

Repeat to create a second emergency account.

### Exclude emergency accounts from Conditional Access

This ensures recovery is always possible.

1. In the [Microsoft Entra Admin Center](https://entra.microsoft.com), navigate to **Protection** >  **Conditional Access**.
1. For every policy:

    - Edit **Assignments**.
    - Exclude at least one emergency access account.

Make sure not to exclude regular admin accounts — only the emergency accounts.

### Monitor emergency account usage

1. Enable alerts on:
    - Sign‑ins by emergency accounts
    - Role changes involving these accounts

1. Treat any use as a security incident unless pre-approved.
1. Review usage periodically.


At the completion of Step 6, The following is configured:

- The identity control plane is recoverable
- Later phases (PAWs, Conditional Access) won’t risk permanent lockout
- Emergency access is isolated, monitored, and rarely used


## Next steps

After securing the identity control plan, restrict where privilege can be exercised with [secure Privileged Access Workstations (PAWs)](implement-privileged-access-devices.md).

