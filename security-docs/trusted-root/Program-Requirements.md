---
title: Program Requirements - Microsoft Trusted Root Program 
description: This document provides details about the requirements all Certificate Authorities are required to adhere to in order to be compliant with our program. 
ms.date: 02/15/2024
ms.service: security
author: kasirota
ms.author: kasirota
ms.topic: conceptual
---


# Program Requirements - Microsoft Trusted Root Program
## 1. Introduction

The Microsoft Root Certificate Program supports the distribution of root certificates, enabling customers to trust Windows products. This page describes the Program's general and technical requirements.


 > [!NOTE]
 > * For information on the most-recent updates shipped, please see <https://aka.ms/rootupdates> 
 > * Bookmark this page as: <https://aka.ms/RootCert> 


## 2. Continuing Program Requirements
### Audit Requirements

1. Program Participants must provide to Microsoft evidence of a Qualifying Audit (see <https://aka.ms/auditreqs>) for each root, unconstrained subordinate CA, , and cross-signed certificate, before conducting commercial operations and thereafter on an annual basis.
2.  Program Participants must assume responsibility to ensure that all unconstrained subordinate CAs and cross-signed certificates meet the Program Audit Requirements.
3. CAs must publicly disclose all audit reports for unconstrained subordinate CAs.
4. CA providers must ensure their S/MIME enabled root CAs and all subordinate CAs capable of issuing S/MIME certificates have been and will continue to be audited against the most recent version of, at minimum, **one of the below sets of criteria**. This auditing must occur at least once a year. An initial audit period must begin no later than September 1, 2023. <br>
     - WebTrust Principles and Criteria for Certification Authorities – S/MIME <br>
     - ETSI EN 119 411-6 LCP, NCP, or NCP+ <br>


### Communication and Disclosure Requirements

4.   Program Participants must provide Microsoft the identities of at least two "Trusted Agents" to serve as representatives to the Program and one general email alias. Program Participants must inform Microsoft upon the removal or addition of personnel as a Trusted Agent. Program Participants agree to receive notices by e-mail and must provide Microsoft with an email address to receive official notices. Program Participants must agree that notice is effective when Microsoft sends an email or official letter. At least one of the contacts or aliases provided should be a 24/7 monitored communications channel for revocation requests or other incident management situations.

5.   The Program Participant must disclose its full PKI hierarchy (non-limited subordinate CA, cross-signed non-enrolled root CAs, subordinate CAs, EKUs, certificate constraints) to Microsoft on an annual basis, including certificates issued to CAs operated by external third parties within the CCADB.  Program Participants must keep this information accurate in the CCADB when changes occur. If a subordinate CA isn't publicly disclosed or audited, it must be domain-constrained. 

6.   Program Participants must inform Microsoft via email at least 120 days before transferring ownership of enrolled root or subordinate CA that chains to an enrolled root to another entity or person. 
 
7. Reason Code must be included in revocations for intermediate certificates. CAs must update the CCADB when revoking any intermediate certificates within 30 days. 

8.  Program Participants agree that Microsoft may contact customers that Microsoft believes may be substantially impacted by the pending removal of a root CA from the Program. 


### Other Requirements
9.  Commercial CAs may not enroll a root CA into the Program that is intended to be primarily trusted internally within an organization (i.e. Enterprise CAs).

10. If a CA uses a subcontractor to operate any aspect of its business, the CA will assume responsibility for the subcontractor's business operations.

11. If Microsoft, in its sole discretion, identifies a certificate   whose usage or attributes are determined to be contrary to the objectives of the Trusted Root Program, Microsoft will notify the responsible CA and request that it revokes the certificate. The CA must either revoke the certificate or request an exception from Microsoft within 24 hours of receiving Microsoft's notice. Microsoft will review submitted material and inform the CA of its final decision to grant or deny the exception at its sole discretion. In the event that Microsoft doesn't grant the exception, the CA must revoke the certificate within 24 hours of the exception being denied. 


------------------------------------------------------------------------

## 3. Program Technical Requirements

All CAs in the Program must comply with the Program Technical Requirements. If Microsoft determines that a CA isn't in compliance with the below requirements, Microsoft will exclude that CA from the
Program.

### A. Root Requirements

1.  Root certificates must be x.509 v3 certificates.
    1.  The CN attribute must identify the publisher and must be unique.
    2.  The CN attribute must be in a language that is appropriate for the CA's market and readable by a typical customer in that market.
    3.  Basic Constraints extension: must be cA=true.
    4.  Key Usage extension MUST be present and MUST be marked critical. Bit positions for KeyCertSign and cRLSign MUST be set. If the Root CA Private Key is used for signing OCSP responses, then the digitalSignature bit MUST be set.
        -   Root Key Sizes must meet the requirements detailed in "Key Requirements."
2.  Certificates to be added to the Trusted Root Store MUST be self-signed root certificates. 
3.   Newly minted Root CAs must be valid for a minimum of eight years, and a maximum of 25 years, from the date of submission.
4.  Participating Root CAs may not issue new 1024-bit RSA certificates from roots covered by these requirements.
5.   All issuing CA certificates must contain either a CDP extension with a valid CRL and/or an AIA extension to an OCSP responder. An end-entity certificate may contain either an AIA extension with a valid OCSP URL and/or a CDP extension pointing to a valid HTTP endpoint containing the CRL. If an AIA extension with a valid OCSP URL is NOT included, then the resulting CRL File should be <10MB. 
6.  Private Keys and subject names must be unique per root certificate; reuse of private keys or subject names in subsequent root certificates by the same CA may result in unexpected certificate chaining issues. CAs must generate a new key and apply a new subject name when generating a new root certificate prior to distribution by Microsoft.
7.  Government CAs must restrict server authentication to government-issued top level domains and may only issue other certificates to the ISO3166 country codes that the country has sovereign control over (see  <https://aka.ms/auditreqs> section III for the definition of a "Government CA"). These government-issued TLDs are referred to in each CA's respective contract. 
8. Issuing CA certificates that chain to a participating Root CA must separate Server Authentication, S/MIME, Code Signing, and Time Stamping uses. This means that a single Issuing CA must not combine server authentication with S/MIME, code signing, or time stamping EKU. A separate intermediate must be used for each use case. 
9. End-entity certificates must meet the requirements for algorithm type and key size for Subscriber certificates listed in Appendix A of the CAB Forum Baseline Requirements located at   https://cabforum.org/baseline-requirements-documents/.
10. CAs must declare one of the following policy OIDs in its Certificate Policy extension end-entity certificate.
    1. DV 2.23.140.1.2.1.
    2. OV 2.23.140.1.2.2.
    3. EV 2.23.140.1.1. 
    4. IV 2.23.140.1.2.3.
    5. Non-EV Code Signing 2.23.140.1.4.1.
    6. S/MIME Mailbox Validated Legacy 2.23.140.1.5.1.1.
    7. S/MIME Mailbox Validated Multipurpose 2.23.140.1.5.1.2.
    8. S/MIME Mailbox Validated Strict 2.23.140.1.5.1.3.
    9. S/MIME Organization Validated Legacy 2.23.140.1.5.2.1.
    10. S/MIME Organization Validated Multipurpose 2.23.140.1.5.2.2.
    11. S/MIME Organization Validated Strict 2.23.140.1.5.2.3.
    12. S/MIME Sponsor Validated Legacy 2.23.140.1.5.3.1.
    13. S/MIME Sponsor Validated Multipurpose 2.23.140.1.5.3.2.
    14. S/MIME Sponsor Validated Strict 2.23.140.1.5.3.3.
    15. S/MIME Individual Validated Legacy 2.23.140.1.5.4.1.
    16. S/MIME Individual Validated Multipurpose 2.23.140.1.5.4.2.
    17. S/MIME Individual Validated Strict 2.23.140.1.5.4.3.
11. Beginning August 2024, all custom EV SSL OIDs managed by the Trusted Root Program and our respective tooling will be removed and replaced with CA/B Forum compliant EV SSL OID (2.23.140.1.1). The Microsoft Edge team will implement checks for EV SSL OID (2.23.140.1.1) in the browser, so other EV SSL OIDs will no longer be accepted to align with Edge and to avoid incompatibilities. 
12. CAs may not have more than 2 OIDs applied to their root certificate.   
13. End-entity certificates that include a Basic Constraints extension in accordance with IETF RFC 5280 must have the cA field set to FALSE and the pathLenConstraint field must be absent.
14. A CA must technically constrain an OCSP responder such that the only EKU allowed is OCSP Signing.
15. A CA must be able to revoke a certificate to a specific date as requested by Microsoft.


### B. Signature Requirements

| Algorithm | All Uses Except for Code Signing and Time Stamping | Code Signing and Time Stamping Use |
| --- | --- | --- |
| Digest Algorithms |SHA2 (SHA256, SHA384, SHA512) | SHA2 (SHA256, SHA384, SHA512) |
| RSA | 2048 | 4096 (New roots only)|
| ECC / ECDSA | NIST P-256, P-384, P-521 | NIST P-256, P-384, P-521 |

**Please Note:** Signatures using elliptical curve cryptography (ECC), such as ECDSA, aren't supported in Windows and newer Windows security features. Users utilizing these algorithms and certificates will face various errors and potential security risks. The Microsoft Trusted Root Program recommends that ECC/ECDSA certificates shouldn't be issued to subscribers due to this known incompatibility and risk. 
 

### C. Revocation Requirements

1.  CAs must have a documented revocation policy and must have the ability to revoke any certificate it issues.
2. 	OCSP responder requirements:
    a.	Minimum validity of eight (8) hours; Maximum validity of seven (7) days; and
    b.	The next update must be available at least eight (8) hours before the current period expires. If the validity is more than 16 hours, then the next update must be available at ½ the validity period.
3.	CRL recommendations when OCSP is not present:
    a.	Should contain Microsoft-specific extension 1.3.6.1.4.1.311.21.4 (Next CRL Publish).
    b.	New CRL should be available at the Next CRL Publish time.
    c.	Maximum size of the CRL file (either full CRL or partitioned CRL) should not exceed 10M.
    Note: The goal of section 3.C.3- CRL Recommendations when OCSP is not present is to provide coverage for end users in cases of mass revocation. 
4.  The CA must not use the root certificate to issue end-entity certificates.
5.  If a CA issues Code Signing certificates, it must use a Time Stamp Authority that complies with RFC 3161, "Internet X.509 Public Key Infrastructure Time-Stamp Protocol (TSP)."
 

### D. Code Signing Root Certificate Requirements

1.  Root certificates that support code signing use may be removed from distribution by the Program 10 years from the date of distribution of a replacement rollover root certificate or sooner, if requested by the CA. 
2.  Root certificates that remain in distribution to support only code signing use beyond their algorithm security lifetime (e.g. RSA 1024  = 2014, RSA 2048 = 2030) may be set to 'disable' in the Windows 10 OS.
3.  Starting February 2024, Microsoft will no longer accept or recognize EV Code Signing Certificates, and CCADB will cease to accept EV Code Signing Audits. Beginning in August 2024, all EV Code Signing OIDs will be removed from existing roots in the Microsoft Trusted Root Program, and all Code Signing certificates will be treated equally.

 

### E. EKU Requirements

1.  CAs must provide a business justification for all of the EKUs assigned to their root certificate. Justification may be in the form of public evidence of a current business of issuing certificates of a type or types, or a business plan demonstrating an intention to issue those certificates in the near term (within one year of root certificate distribution by the Program).

2.  Microsoft will only enable the following EKUs:
    1.  Server Authentication =1.3.6.1.5.5.7.3.1
    2.  Client Authentication =1.3.6.1.5.5.7.3.2
    3.  Secure E-mail EKU=1.3.6.1.5.5.7.3.4
    4.  Time stamping EKU=1.3.6.1.5.5.7.3.8
    5.  Document Signing EKU=1.3.6.1.4.1.311.10.3.12
     -   This EKU is used for signing documents within Office. It isn't required for other document signing uses.
 

### F. Windows 10 Kernel Mode Code Signing (KMCS) Requirements

Windows 10 has heightened requirements to validate kernel-mode drivers. Drivers must be signed by both Microsoft and a Program partner using Extended Validation requirements. All developers who wish to have their kernel-mode drivers included in Windows must follow the procedures outlined by the Microsoft Hardware Development Team. For more information, see the [Partner Center for Windows Hardware](/windows-hardware/drivers/dashboard/). 
