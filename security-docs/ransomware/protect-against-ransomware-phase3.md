---
title: "Make it hard for ransomware attacks to happen to your organization"
ms.author: dansimp
author: dansimp
f1.keywords:
- NOCSH
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: microsoft-365-security
localization_priority: Normal
ms.collection:
- msftsolution-ransomware
ms.custom: cxdef-zt-ransomware
description: How to stop ransomware attacks by making it hard for a cybercriminal to get into your environment. Use ransomware prevention to reduce your risks.
ms.date: 03/25/2024
---

# Make it hard for ransomware attacks to get into your organization

In this phase, you make the attackers work *harder* to get into your on-premises or cloud systems by gradually removing risks at the points of entry.

While many of these changes will be familiar and easy to do, **it's extremely important that your work on this part of the strategy not slow your progress on the other to critically important parts!**

Here are the links to review the three part cyber security plan:

- [Have a recovery plan](protect-against-ransomware-phase1.md)
- [A plan to limit the harm done](protect-against-ransomware-phase2.md)
- [Make it hard to get in](protect-against-ransomware-phase3.md)

## Remote access

Getting access to your organization's intranet through a remote access connection is an attack vector for ransomware attackers.

Once an on-premises user account is compromised, an attacker is free to roam on an intranet to gather intelligence, elevate privileges, and install ransomware. The Colonial Pipeline cyberattack in 2021 is an example.

### Program and project member accountabilities for remote access

This table describes the overall protection of your remote access solution from ransomware in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

|Lead|Implementor|Accountability|
|---|---|---|
|CISO or CIO||Executive sponsorship|
|Program lead on the [Central IT](/azure/cloud-adoption-framework/organize/central-it) Infrastructure/Network Team||Drive results and cross-team collaboration|
||IT and [Security](/azure/cloud-adoption-framework/organize/cloud-security-architecture) Architects|Prioritize component integration into architectures|
||[Central IT](/azure/cloud-adoption-framework/organize/central-it) Identity Team|Configure Microsoft Entra ID and conditional access policies|
||[Central IT](/azure/cloud-adoption-framework/organize/central-it) Operations|Implement changes to environment|
||Workload Owners|Assist with RBAC permissions for app publishing|
||[Security Policy and Standards](/azure/cloud-adoption-framework/organize/cloud-security-policy-standards)|Update standards and policy documents|
||[Security Compliance Management](/azure/cloud-adoption-framework/organize/cloud-security-compliance-management)|Monitor to ensure compliance|
||User Education Team|Update any guidance on workflow changes and perform education and change management|

### Implementation checklist for remote access

Apply these best practices to protect your remote access infrastructure from ransomware attackers.

|Done|Task|Description|
|---|---|---|
|<input type="checkbox" />|Maintain software and appliance updates. Avoid missing or neglecting manufacturer protections (security updates, supported status).|Attackers use well-known vulnerabilities that have not yet been patched as attack vectors.|
|<input type="checkbox" />|Configure Microsoft Entra ID for existing remote access by including enforcing [Zero Trust](https://www.microsoft.com/security/business/zero-trust) user and device validation with Conditional Access.|Zero Trust provides multiple levels of securing access to your organization.|
|<input type="checkbox" />|Configure security for existing third-party VPN solutions (Cisco [AnyConnect](/azure/active-directory/saas-apps/cisco-anyconnect), Palo Alto Networks [GlobalProtect](/azure/active-directory/saas-apps/palo-alto-networks-globalprotect-tutorial) & [Captive Portal](/azure/active-directory/saas-apps/paloaltonetworks-captiveportal-tutorial), Fortinet [FortiGate SSL VPN](/azure/active-directory/saas-apps/fortigate-ssl-vpn-tutorial), Citrix [NetScaler](/azure/active-directory/saas-apps/citrix-netscaler-tutorial), [Zscaler Private Access (ZPA)](/azure/active-directory/saas-apps/zscalerprivateaccess-tutorial), and [more](/azure/active-directory/saas-apps/tutorial-list)).|Take advantage of the built-in security of your remote access solution.|
|<input type="checkbox" />|Deploy [Azure Point-to-Site (P2S) VPN](/azure/vpn-gateway/openvpn-azure-ad-tenant#enable-authentication) to provide remote access.|Take advantage of integration with Microsoft Entra ID and your existing Azure subscriptions.|
|<input type="checkbox" />|Publish on-premises web apps with [Microsoft Entra application proxy](/azure/active-directory/manage-apps/application-proxy-integrate-with-remote-desktop-services).|Apps published with Microsoft Entra application proxy do not need a remote access connection.|
|<input type="checkbox" />|Secure access to Azure resources with [Azure Bastion](/azure/bastion/bastion-overview).|Securely and seamlessly connect to your Azure virtual machines over SSL.|
|<input type="checkbox" />|Audit and monitor to find and fix deviations from baseline and potential attacks (see [Detection and Response](protect-against-ransomware-phase2.md#ransomware-detection-and-response)).|Reduce risk from ransomware activities that probe baseline security features and settings.|

## Email and collaboration

Implement best practices for email and collaboration solutions to make it more difficult for attackers to abuse them, while allowing your workers to access external content easily and safely.

Attackers frequently enter the environment by transferring malicious content in with authorized collaboration tools such as email and file sharing and convincing users to run it. Microsoft has invested in enhanced mitigations that vastly increase protection against these attack vectors.

### Program and project member accountabilities for email and collaboration

This table describes the overall protection of your email and collaboration solutions from ransomware in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

|Lead|Implementor|Accountability|
|---|---|---|
|CISO, CIO, or Identity Director||Executive sponsorship|
|Program lead from the [Security Architecture](/azure/cloud-adoption-framework/organize/cloud-security-architecture) team||Drive results and cross-team collaboration|
||IT Architects|Prioritize component integration into architectures|
||Cloud Productivity or End User Team|Enable Defender for Office 365, ASR, and AMSI|
||[Security Architecture](/azure/cloud-adoption-framework/organize/cloud-security-architecture) / [Infrastructure + Endpoint](/azure/cloud-adoption-framework/organize/cloud-security-infrastructure-endpoint)|Configuration assistance|
||User Education Team|Update guidance on workflow changes|
||[Security Policy and Standards](/azure/cloud-adoption-framework/organize/cloud-security-policy-standards)|Update standards and policy documents|
||[Security Compliance Management](/azure/cloud-adoption-framework/organize/cloud-security-compliance-management)|Monitor to ensure compliance|

### Implementation checklist for email and collaboration

Apply these best practices to protect your email and collaboration solutions from ransomware attackers.

|Done|Task|Description|
|---|---|---|
|<input type="checkbox" />|Enable [AMSI for Office VBA](https://www.microsoft.com/security/blog/2018/09/12/office-vba-amsi-parting-the-veil-on-malicious-macros/).|Detect Office macro attacks with endpoint tools like [Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection).|
|<input type="checkbox" />|Implement Advanced Email security using [Defender for Office 365](/microsoft-365/security/office-365-security/office-365-atp) or a similar solution.|Email is a common entry point for attackers.|
|<input type="checkbox" />|[Deploy attack surface reduction (ASR) rules](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-deployment) to block common attack techniques including: <br><br> - Endpoint abuse such as credential theft, ransomware activity, and suspicious use of PsExec and WMI. <br><br> - Weaponized Office document activity such as advanced macro activity, executable content, process creation, and process injection initiated by Office applications. <br><br> **Note:** Deploy these rules in audit mode first, then assess any negative impact, and then deploy them in block mode.|ASR provides additional layers of protect specifically targeted at mitigating common attack methods.|
|<input type="checkbox" />|Audit and monitor to find and fix deviations from baseline and potential attacks (see [Detection and Response](protect-against-ransomware-phase2.md#ransomware-detection-and-response)).|Reduces risk from ransomware activities that probe baseline security features and settings.|

## Endpoints

Implement relevant security features and rigorously follow software maintenance best practices for endpoints (devices) and applications, prioritizing applications and server/client operating systems directly exposed to Internet traffic and content.

Internet-exposed endpoints are a common entry vector that provides attackers access to the organization's assets. Prioritize blocking common OS and application vulnerabilities with preventive controls to slow or stop them from executing the next stages.

### Program and project member accountabilities for enbpoints

This table describes the overall protection of your endpoints from ransomware in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

|Lead|Implementor|Accountability|
|---|---|---|
|Business leadership accountable for business impact of both downtime and attack damage||Executive sponsorship (maintenance)|
|[Central IT](/azure/cloud-adoption-framework/organize/central-it) Operations or CIO||Executive sponsorship (others)|
|Program lead from the [Central IT](/azure/cloud-adoption-framework/organize/central-it) Infrastructure Team||Drive results and cross-team collaboration|
||IT and [Security](/azure/cloud-adoption-framework/organize/cloud-security-architecture) Architects|Prioritize component integration into architectures|
||[Central IT](/azure/cloud-adoption-framework/organize/central-it) Operations|Implement changes to environment|
||Cloud Productivity or End User Team|Enable attack surface reduction|
||Workload/App Owners|Identify maintenance windows for changes|
||[Security Policy and Standards](/azure/cloud-adoption-framework/organize/cloud-security-policy-standards)|Update standards and policy documents|
||[Security Compliance Management](/azure/cloud-adoption-framework/organize/cloud-security-compliance-management)|Monitor to ensure compliance|

### Implementation checklist for endpoints

Apply these best practices to all Windows, Linux, MacOS, Android, iOS, and other endpoints.

|Done|Task|Description|
|---|---|---|
|<input type="checkbox" />|Block known threats with [attack surface reduction](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-deployment) rules, [tamper protection](/microsoft-365/security/defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection), and [block at first site](/windows/security/threat-protection/microsoft-defender-antivirus/configure-block-at-first-sight-microsoft-defender-antivirus).|Don't let lack of use of these built-in security features be the reason an attacker entered your organization.|
|<input type="checkbox" />|Apply [Security Baselines](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/bg-p/Microsoft-Security-Baselines) to harden internet-facing Windows servers and clients and Office applications.|Protect your organization with the minimum level of security and build from there.|
|<input type="checkbox" />|Maintain your software so that it is: <br><br> - Updated: Rapidly deploy critical security updates for operating systems, browsers, & email clients <br><br> - Supported:  Upgrade operating systems and software for versions supported by your vendors.|Attackers are counting on you missing or neglecting manufacturer updates and upgrades.|
|<input type="checkbox" />|Isolate, disable, or retire insecure systems and protocols, including [unsupported operating systems](/lifecycle/) and [legacy protocols](https://techcommunity.microsoft.com/t5/core-infrastructure-and-security/retire-those-old-legacy-protocols/ba-p/259396).|Attackers use known vulnerabilities of legacy devices, systems, and protocols as entry points into your organization.|
|<input type="checkbox" />|Block unexpected traffic with host-based firewall and network defenses.|Some malware attacks rely on unsolicited inbound traffic to hosts as a way of making a connection for an attack.|
|<input type="checkbox" />|Audit and monitor to find and fix deviations from baseline and potential attacks (see [Detection and Response](protect-against-ransomware-phase2.md#ransomware-detection-and-response)).|Reduces risk from ransomware activities that probe baseline security features and settings.|

## Accounts

Just as antique skeleton keys won’t protect a house against a modern-day burglar, passwords cannot protect accounts against common attacks we see today. While multi-factor authentication (MFA) was once a burdensome extra step, passwordless authentication improves the sign-in experience using biometric approaches that don’t require your users to remember or type a password. Additionally, a [Zero Trust](https://www.microsoft.com/security/business/zero-trust) infrastructure stores information about trusted devices, which reduce prompting for annoying out-of-band MFA actions.

Starting with high-privilege administrator accounts, rigorously follow these best practices for account security including using passwordless or MFA.

### Program and project member accountabilities for accounts

This table describes the overall protection of your accounts from ransomware in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

|Lead|Implementor|Accountability|
|---|---|---|
|CISO, CIO, or Identity Director||Executive sponsorship|
|Program lead from [Identity and Key Management](/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) or [Security Architecture](/azure/cloud-adoption-framework/organize/cloud-security-architecture) teams||Drive results and cross-team collaboration|
||IT and [Security](/azure/cloud-adoption-framework/organize/cloud-security-architecture) Architects|Prioritize component integration into architectures|
||[Identity and Key Management](/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) or [Central IT](/azure/cloud-adoption-framework/organize/central-it) Operations|Implement configuration changes|
||[Security Policy and Standards](/azure/cloud-adoption-framework/organize/cloud-security-policy-standards)|Update standards and policy documents|
||[Security Compliance Management](/azure/cloud-adoption-framework/organize/cloud-security-compliance-management)|Monitor to ensure compliance|
||User Education Team|Update password or sign-in guidance and perform education and change management|

### Implementation checklist for accounts

Apply these best practices to protect your accounts from ransomware attackers.

|Done|Task|Description|
|---|---|---|
|<input type="checkbox" />|Enforce strong MFA or passwordless sign-in for all users. Start with administrator and [priority](/microsoft-365/admin/setup/priority-accounts) accounts using one or more of: <br><br> - Passwordless authentication with [Windows Hello](/windows/security/identity-protection/hello-for-business/hello-identity-verification) or the [Microsoft Authenticator app](/azure/active-directory/authentication/howto-authentication-phone-sign-in). <br><br> - [Azure Multi-Factor Authentication](/azure/active-directory/authentication/howto-mfa-userstates). <br><br> - A third-party MFA solution.|Make it harder for an attacker to perform a credential compromise by just determining a user account password.|
|<input type="checkbox" />|Increase password security: <br><br> - For Microsoft Entra accounts, use [Microsoft Entra Password Protection](/azure/active-directory/authentication/concept-password-ban-bad) to detect and block known weak passwords and additional weak terms that are specific to your organization. <br><br> - For on-premises Active Directory Domain Services (AD DS) accounts, [Extend Microsoft Entra Password Protection](/azure/active-directory/authentication/concept-password-ban-bad-on-premises) to AD DS accounts.|Ensure that attackers can't determine common passwords or passwords based on your organization name.|
|<input type="checkbox" />|Audit and monitor to find and fix deviations from baseline and potential attacks (see [Detection and Response](protect-against-ransomware-phase2.md#ransomware-detection-and-response)).|Reduces risk from ransomware activities that probe baseline security features and settings.|

### Implementation results and timelines

Try to achieve these results within 30 days:

- 100 % of employees are actively using MFA
- 100 % deployment of higher password security

## Additional ransomware resources

Key information from Microsoft:

- [The growing threat of ransomware](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/), Microsoft On the Issues blog post on July 20, 2021
- [Human-operated ransomware](human-operated-ransomware.md)
- [Rapidly protect against ransomware and extortion](protect-against-ransomware.md)
- [2021 Microsoft Digital Defense Report](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (see pages 10-19)
- [Ransomware: A pervasive and ongoing threat](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) threat analytics report in the Microsoft Defender portal
- Microsoft's Detection and Response Team (DART) ransomware [approach](/security/operations/incident-response-playbook-dart-ransomware-approach) and [case study](dart-ransomware-case-study.md)

Microsoft 365:

- [Deploy ransomware protection for your Microsoft 365 tenant](/microsoft-365/solutions/ransomware-protection-microsoft-365)
- [Maximize Ransomware Resiliency with Azure and Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Recover from a ransomware attack](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [Malware and ransomware protection](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Protect your Windows 10 PC from ransomware](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [Handling ransomware in SharePoint Online](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- [Threat analytics reports for ransomware](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) in the Microsoft Defender portal

Microsoft Defender XDR:

- [Find ransomware with advanced hunting](/microsoft-365/security/defender/advanced-hunting-find-ransomware)

Microsoft Azure:

- [Azure Defenses for Ransomware Attack](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [Maximize Ransomware Resiliency with Azure and Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Backup and restore plan to protect against ransomware](/azure/security/fundamentals/backup-plan-to-protect-against-ransomware)
- [Help protect from ransomware with Microsoft Azure Backup](https://www.youtube.com/watch?v=VhLOr2_1MCg) (26 minute video)
- [Recovering from systemic identity compromise](/azure/security/fundamentals/recover-from-identity-compromise)
- [Advanced multistage attack detection in Microsoft Sentinel](/azure/sentinel/fusion#ransomware)
- [Fusion Detection for Ransomware in Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Microsoft Defender for Cloud Apps:

- [Create anomaly detection policies in Defender for Cloud Apps](/cloud-app-security/anomaly-detection-policy)

Microsoft Security team blog posts:

- [3 steps to prevent and recover from ransomware (September 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [A guide to combatting human-operated ransomware: Part 1 (September 2021)](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/)

  Key steps on how Microsoft's Detection and Response Team (DART) conducts ransomware incident investigations.

- [A guide to combatting human-operated ransomware: Part 2 (September 2021)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  Recommendations and best practices.

- [Becoming resilient by understanding cybersecurity risks: Part 4—navigating current threats (May 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  See the **Ransomware** section.

- [Human-operated ransomware attacks: A preventable disaster (March 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  Includes attack chain analyses of actual attacks.

- [Ransomware response—to pay or not to pay? (December 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [Norsk Hydro responds to ransomware attack with transparency (December 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
