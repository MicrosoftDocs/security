---
title: Security Incident Response Requirements - Microsoft Trusted Root Program
description: This document provides details about the Incident Response requirements all Certificate Authorities are required to adhere to in order to be compliant with our program. 
ms.date: 03/04/2019
ms.service: security
ms.author: kasirota
ms.topic: conceptual
---

# Security Incident Response Requirements - Microsoft Trusted Root Program

## Definitions


1.  "A compromise" means a direct or indirect incident, affecting either
    the CA or any of the CA's sub-roots or
    cross-signed, non-enrolled roots, that results in an actual or
    potential degradation of the security stature of the PKI, which
    includes hardware, software, or physical building issues.
2.  "Security Incident" or "Incident" means any of the following that
    occur at the CA or a sub-CA:
    1.  A Private Key compromise.
    2.  A mis-issued certificate.
    3.  A known or reasonably knowable, publicly reported compromise.
    4.  Any physical compromise of the CAs infrastructure (e.g. physical
        access control failure, building compromise, or a failure of the
        HVAC in the data center).
    5.  Any other issue that Microsoft identifies as calling into
        question the CA's integrity or trustworthiness.
3.  "Exceptional Circumstance(s)" means an incident(s) in which
    Microsoft believes that the PKI is compromised; as to affect the
    security posture of a large number of Microsoft's customers.


## CA Responsibilities in the Event of an Incident

In the event of a Security Incident, the CA must:

1.  Notify Microsoft as soon as is practical but no later than 24 hours
    from the time of the Security Incident by (a) completing the form
    located at https://aka.ms/rootnotify, and (b) sending the completed
    form to rootnotify\@microsoft.com. The form requires the following
    information (if known at the time):
    -   Who detected the incident.
    -   If available, who perpetrated the incident.
    -   When the CA discovered the incident.
    -   Where the incident occurred.
    -   Which Roots and, if requested by Microsoft, end-user
        certificates, were affected by the incident.
    -   Which, if any, sub-CAs were affected.
    -   What the CA believes to be the underlying cause of the incident.
    -   What remedial measures the CA has taken or will take that the CA
        believes will address the underlying cause of the incident.
    -   Any other information the CA believes to be appropriate.
    -   Any other information Microsoft requested when it responded to
        the initial notification.
2.  At Microsoft's request, the CA must provide a list of all
    certificates that were mis-issued as a result of the incident.
3.  At Microsoft's request, the CA must provide Microsoft with periodic
    reports at an interval specified by Microsoft. If Microsoft does not
    make a specific request within 24 hours of an initial notification,
    the CA must provide reports to Microsoft as it discovers any new
    information.
4.  The CA must provide a final Security Incident report to Microsoft
    that includes:
    -   A list of certificates and domains involved in the breach.
    -   How did the CA detect the incident? If the CA did not detect the
        breach, who did and why did the CA not detect?
    -   If there was a mismatch in the reports over time, why?
    -   Detailed description of the exploit.
    -   Details about what infrastructure was compromised.
    -   Details about how the infrastructure was compromised.
    -   A detailed timeline of events.
    -   The CA's interpretation of who perpetrated the breach.
    -   Log files (appendix only).
    -   Was the vulnerability detected by the CAs normal operation? If
        it was not, please explain why.
    -   Was the vulnerability discovered in the most-recent audit? If
        yes, then provide information if the vulnerability was
        remediated. If the vulnerability was not remediated, please
        provide information about the reason for not doing so.
    -   Was this vulnerability detected by the most-recent audit? If it
        was not, please explain why.
    -   If the vulnerability was detected in the most recent audit, was
        it remediated? If not please explain why.
    -   What changes to the CP/CPS policies will the CA make?
    -   Detailed description of how the issue was closed.
5.  If requested by Microsoft, a complete investigative and technical
    report of the compromise.

## Microsoft's Rights in the Event of an Incident

In the event of a Security Incident, Microsoft may at its sole
discretion, do any of the following:

1.  In an Exceptional Circumstance, immediately revoke any certificate
    the CA or any sub-CA has enrolled in the Program, otherwise it may
    revoke any certificate after providing seven days' notice to the CA.
2.  Microsoft may take action including, but not limited to marking
    files signed by compromised certificates as malware, blocking web
    navigation to sites served with compromised Server Authentication
    certificates, preventing delivery of mail signed by compromised
    Secure Email certificates, etc.
3.  Request that the CA make specific reports at a periodic interval to
    be determined by Microsoft.
4.  Specify a due date for the CA to submit to Microsoft a final
    Security Incident report.
5.  Communicate with affected third parties.
6.  Require the CA to employ, at the CA's expense, a third-party
    investigator to investigate the Security Incident and prepare the
    final Security Incident report.
7.  Disqualify any Qualifying Audit and require the CA to perform a new
    Qualifying Audit at the CA's sole expense.

 

## Microsoft's Responsibilities in the Event of a Security Incident

In the event that Microsoft exercises any of the rights described above,
Microsoft will:

1.  Notify the CA, in writing, of its intentions 7 days prior to
    Microsoft's action, except under Exceptional Circumstances, in which
    case Microsoft will make reasonable efforts to communicate with the
    CA prior to taking action; and
2.  Allow the CA to propose an alternate course of action, in which
    case, Microsoft will consider reasonable alternatives but reserves
    the right to reject such proposals if it deems the proposed course
    of action not to be in its customers' best interest.
