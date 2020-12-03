---
title: Program Requirements - Microsoft Trusted Root Program 
description: This document provides details about the requirements all Certificate Authorities are required to adhere to in order to be compliant with our program. 
ms.date: 02/04/2020
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

1.  Program Participants must provide to Microsoft evidence of a Qualified Audit (see <https://aka.ms/auditreqs>) for each root, unconstrained subordinate CA, , and cross-signed certificate, before conducting commercial operations and thereafter on an annual basis.
2.  Program Participants must assume responsibility to ensure that all unconstrained subordinate CAs and cross-signed certificates meet the Program Audit Requirements.
3. CAs must publicly disclose all audit reports for unconstrained subordinate CAs.


### Communication and Disclosure Requirements

4.   Program Participants must provide Microsoft the identities of at least two "Trusted Agents" to serve as representatives to the Program and one general email alias. Program Participants must inform Microsoft upon the removal or addition of personnel as a Trusted Agent. Program Participants agree to receive notices by e-mail and must provide Microsoft with an email address to receive official notices. Program Participants must agree that notice is effective when Microsoft sends an email or official letter. At least one of the contacts or aliases provided should be a 24/7 monitored communications channel for revocation requests or other incident management situations.

5.   The Program Participant must disclose its full PKI hierarchy (non-limited subordinate CA, cross-signed non-enrolled root CAs, subordinate CAs, EKUs, certificate constraints) to Microsoft on an annual basis, including certificates issued to CAs operated by external third parties within the CCADB.  Program Participants must keep this information accurate in the CCADB when changes occur. If a subordinate CA is not publicly disclosed or audited, it must be domain-constrained. 

6.   Program Participants must inform Microsoft via email at least 120 days before transferring ownership of enrolled root or subordinate CA that chains to an enrolled root to another entity or person. 
 
7. Reason Code must be included in revocations for intermediate certificates. CAs must update the CCADB when revoking any intermediate certificates within 30 days. 

8.  Program Participants agree that Microsoft may contact customers that Microsoft believes may be substantially impacted by the pending removal of a root CA from the Program. 

### Other Requirements
9.  Commercial CAs may not enroll a root CA into the Program that is intended to be primarily trusted internally within an organization (i.e. Enterprise CAs).

10. If a CA uses a subcontractor to operate any aspect of its business, the CA will assume responsibility for the subcontractor's business operations.

11. If Microsoft, in its sole discretion, identifies a certificate   whose usage or attributes are determined to be contrary to the objectives of the Trusted Root Program, Microsoft will notify the responsible CA and request that it revoke the certificate. The CA must either revoke the certificate or request an exception from Microsoft within 24 hours of receiving Microsoft's notice. Microsoft will review submitted material and inform the CA of its final decision to grant or deny the exception at its sole discretion. In the event that Microsoft does not grant the exception, the CA must revoke the certificate within 24 hours of the exception being denied. 


------------------------------------------------------------------------

## 3. Program Technical Requirements

All CAs in the Program must comply with the Program Technical Requirements. If Microsoft determines that a CA is not in compliance with the below requirements, Microsoft will exclude that CA from the
Program.

### A. Root Requirements

1.  Root certificates must be x.509 v3 certificates.
    1.  The CN attribute must identify the publisher and must be unique.
    2.  The CN attribute must be in a language that is appropriate for the CA's market and readable by a typical customer in that market.
    3.  Basic Constraints extension: must be cA=true.
    4.  Key Usage extension MUST be present and MUST be marked critical. Bit positions for KeyCertSign and cRLSign MUST be set. If the Root CA Private Key is used for signing OCSP responses, then the digitalSignature bit MUST be set.
        -   Root Key Sizes must meet the requirements detailed in "Key Requirements".
2.  Certificates to be added to the Trusted Root Store MUST be self-signed root certificates. 
3.   Newly minted Root CAs must be valid for a minimum of 8 years, and a maximum of 25 years, from the date of submission.
5.  Participating Root CAs may not issue new 1024-bit RSA certificates from roots covered by these requirements.
6.  All end-entity certificates must contain an AIA extension with a valid OCSP URL. These certificates may also contain a CDP extension that contains a valid CRL URL. All other certificate types must contain either an AIA extension with an OCSP URL or a CDP extension with a valid CRL URL
7.  Private Keys and subject names must be unique per root certificate; reuse of private keys or subject names in subsequent root certificates by the same CA may result in unexpected certificate chaining issues. CAs must generate a new key and apply a new subject name when generating a new root certificate prior to distribution by Microsoft.
8.  Government CAs must restrict server authentication to government-issued top level domains and may only issue other certificates to the ISO3166 country codes that the country has sovereign control over (see  <https://aka.ms/auditreqs> section III for the definition of a "Government CA"). These government-issued TLDs are referred to in each CA's respective contract. 
9. Issuing CA certificates that chain to a participating Root CA  must be constrained to a single EKU (e.g., separate Server Authentication, S/MIME, Code Signing, and Time Stamping uses. This means that a single Issuing CA must not combine server authentication with S/MIME, code signing or time stamping EKU.  A separate intermediate must be used for each use case.
10. End-entity certificates must meet the requirements for algorithm type and key size for Subscriber certificates listed in Appendix A of the CAB Forum Baseline Requirements located at   https://cabforum.org/baseline-requirements-documents/.
11. CAs must declare one of the following policy OIDs in its Certificate Policy extension end-entity certificate: 
    1. DV 2.23.140.1.2.1 
    2. OV 2.23.140.1.2.2
    3. EV 2.23.140.1.1. 
    4. IV 2.23.140.1.2.3 
    5. EV Code Signing 2.23.140.1.3
    6. Non-EV Code Signing 2.23.140.1.4.1
12. End-entity certificates that include a Basic Constraints extension in accordance with IETF RFC 5280 must have the cA field set to FALSE and the pathLenConstraint field must be absent.
13. A CA must technically constrain an OCSP responder such that the only EKU allowed is OCSP Signing.


### B. Key Requirements

| Algorithm | All Uses Except for Code Signing and Time Stamping | Code Signing and Time Stamping Use |
| --- | --- | --- |
| Digest Algorithms |SHA2 (SHA256, SHA384, SHA512) | SHA2 (SHA256, SHA384, SHA512) |
| RSA | 2048 | 4096 (New roots only)|
| ECC / ECDSA | NIST P-256, P-384, P-521 | NIST P-256, P-384, P-521 |

 

### C. Revocation Requirements

1.  The CA must have a documented revocation policy and must have the ability to revoke any certificate it issues.
2.  CAs that issue Server Authentication certificates must support the following OCSP responder requirements:
    1.  Minimum validity of eight (8) hours; Maximum validity of seven (7) days; and
    2.  The next update must be available at least eight (8) hours before the current period expires. If the validity is more than 16 hours, then the next update must be available at ½ of the validity period.
3.  All certificates issued from a root CA must support either the CRL distribution point extension and/or AIA containing an OCSP responder URL.
4.  The CA must not use the root certificate to issue end-entity certificates.
5.  If a CA issues Code Signing certificates, it must use a Time Stamp Authority that complies with RFC 3161, "Internet X.509 Public Key Infrastructure Time-Stamp Protocol (TSP)."

 

### D. Code Signing Root Certificate Requirements

1.  New root CAs that support code-signing infrastructure must be signed with using the SHA2 hashing algorithm.
2.  Root certificates that support code signing use may be removed from distribution by the Program 10 years from the date of distribution of a replacement rollover root certificate or sooner, if requested by the CA. 
3.  Root certificates that remain in distribution to support only code signing use beyond their algorithm security lifetime (e.g. RSA 1024  = 2014, RSA 2048 = 2030) may be set to 'disable' in the Windows 10 OS. 

 

### E. EKU Requirements

1.  CAs must provide a business justification for all of the EKUs assigned to their root certificate. Justification may be in the form of public evidence of a current business of issuing certificates of a type or types, or a business plan demonstrating an intention to issue those certificates in the near term (within one year of root certificate distribution by the Program).

2.  Microsoft will only enable the following EKUs:
    1.  Server Authentication =1.3.6.1.5.5.7.3.1
    2.  Client Authentication =1.3.6.1.5.5.7.3.2
    3.  Secure E-mail EKU=1.3.6.1.5.5.7.3.4
    4.  Code Signing EKU=1.3.6.1.5.5.7.3.3
    5.  Time stamping EKU=1.3.6.1.5.5.7.3.8
    6.  Document Signing EKU=1.3.6.1.4.1.311.10.3.12
     -   This EKU is used for signing documents within Office. It is not required for other document signing uses.
    
 
 

### F. Windows 10 Kernel Mode Code Signing (KMCS) Requirements

Windows 10 has heightened requirements to validate kernel-mode
drivers.  Drivers must be signed by both Microsoft and a Program partner
using Extended Validation requirements.   All developers who wish to
have their kernel-mode drivers included in Windows must follow the
procedures outlined by the Microsoft Hardware Development Team.  Program
documentation can be found
[here](https://docs.microsoft.com/windows-hardware/drivers/dashboard/)

------------------------------------------------------------------------	

## 4. Technical Best Practices	


Though not required by Microsoft, the following represents what	
Microsoft believes to be the best practices that each CA should follow.	

1.  Microsoft recommends that each CA have an established communication channel to its customers. For example, if Microsoft were to notify the CA that Microsoft was disabling weak file hashes, the CA should have a method to notify its customers to use the updated signtool.exe file.	
2.  Because root certificates will be removed without regard to any unexpired end entity certificates issued from them, the CAs should plan to cease issuing end entity certificates for uses besides code  signing such that those certificates expire according to these root removal guidelines.	
3.  While Windows will not enforce specific policies on Secure Email certificates, Microsoft recommends that CAs start issuing new Secure Email certificates using the SHA-2 algorithm.	
4.  Microsoft recommends an OCSP responder maximum validity period of one (1) day.








