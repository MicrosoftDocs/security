---
layout: LandingPage
title: Microsoft SDL Cryptographic Recommendations
description: This document contains recommendations and best practices for using encryption on Microsoft platforms. It is meant to be used as a reference when designing products to use the same APIs, algorithms, protocols and key lengths that Microsoft requires of its own products and services.
ms.date: 12/3/2018
ms.service: security
ms.author: bcowper
ms.topic: conceptual
---

# Microsoft SDL Cryptographic Recommendations

## Introduction
This document contains recommendations and best practices for using
encryption on Microsoft platforms. Much of the content here is
paraphrased or aggregated from Microsoft’s own internal security
standards used to create the Security Development Lifecycle. It is meant
to be used as a reference when designing products to use the same APIs,
algorithms, protocols and key lengths that Microsoft requires of its own
products and services.

Developers on non-Windows platforms may also benefit from these
recommendations. While the API and library names may be different, the
best practices involving algorithm choice, key length and data
protection are similar across platforms.

## Security Protocol, Algorithm and Key Length Recommendations

### SSL/TLS versions
Products and services should use cryptographically secure versions of
SSL/TLS:

  - TLS 1.2 should be enabled

  - TLS 1.1 and TLS 1.0 should be enabled for backward compatibility
    only

  - SSL 3 and SSL 2 should be disabled by default

### Symmetric Block Ciphers, Cipher Modes and Initialization Vectors 
_Block Ciphers_

For products using symmetric block ciphers:

  - Advanced Encryption Standard (AES) is recommended for new code.

  - Three-key triple Data Encryption Standard (3DES) is permissible in
    existing code for backward compatibility.

  - All other block ciphers, including RC2, DES, 2-Key 3DES, DESX, and
    Skipjack, should only be used for decrypting old data, and should be
    replaced if used for encryption.

For symmetric block encryption algorithms, a minimum key length of 128
bits is recommended. The only block encryption algorithm recommended for
new code is AES (AES-128, AES-192, and AES-256 are all acceptable,
noting that AES-192 lacks optimization on some processors). Three-key
3DES is currently acceptable if already in use in existing code;
transition to AES is recommended. DES, DESX, RC2, and Skipjack are no
longer considered secure. These algorithms should only be used for
decrypting existing data for the sake of backward-compatibility, and
data should be re-encrypted using a recommended block cipher.

_Cipher Modes_

Symmetric algorithms can operate in a variety of modes, most of which
link together the encryption operations on successive blocks of
plaintext and ciphertext.

Symmetric block ciphers should be used with one of the following cipher
modes:

  - [<span class="underline">Cipher Block
    Chaining</span>](https://en.wikipedia.org/wiki/Block_cipher_mode_of_operation)
    (CBC)

  - [<span class="underline">Ciphertext
    Stealing</span>](https://en.wikipedia.org/wiki/Ciphertext_stealing)
    (CTS)

  - [<span class="underline">XEX-Based Tweaked-Codebook with Ciphertext
    Stealing</span>](https://en.wikipedia.org/wiki/Disk_encryption_theory#XEX-based_tweaked-codebook_mode_with_ciphertext_stealing_.28XTS.29)
    (XTS)

Some other cipher modes like those included below have implementation
pitfalls that make them more likely to be used incorrectly. In
particular, the Electronic Code Book (ECB) mode of operation should be
avoided. Reusing the same initialization vector (IV) with block ciphers
in "streaming ciphers modes" such as CTR may cause encrypted data to be
revealed. Additional security review is recommended if any of the below
modes are used:

  - Output Feedback (OFB)

  - Cipher Feedback (CFB)

  - Counter (CTR)

  - Counter with CBC-MAC (CCM)

  - Galois/Counter Mode (GCM)

  - Anything else not on the "recommended" list above

_Initialization Vectors (IV)_

All symmetric block ciphers should also be used with a cryptographically
strong random number as an initialization vector. Initialization vectors
should never be a constant value. See Random Number Generators for
recommendations on generating cryptographically strong random numbers.

Initialization vectors should never be reused when performing multiple
encryption operations, as this can reveal information about the data
being encrypted, particularly when using streaming cipher modes like
Output Feedback (OFB) or Counter (CTR).

### Asymmetric Algorithms, Key Lengths, and Padding Modes 
_RSA_ 

  - RSA should be used for encryption, key exchange and signatures.

  - RSA encryption should use the OAEP or RSA-PSS padding modes.
    Existing code should use PKCS \#1 v1.5 padding mode for
    compatibility only.

  - Use of null padding is not recommended.

  - Keys \>= 2048 bits are recommended

_ECDSA_

  - ECDSA with \>= 256 bit keys is recommended

  - ECDSA-based signatures should use one of the three NIST-approved
    curves (P-256, P-384, or P521).

_ECDH_

  - ECDH with \>= 256 bit keys is recommended

  - ECDH-based key exchange should use one of the three NIST-approved
    curves (P-256, P-384, or P521).

_Integer Diffie-Hellman_

  - Key length \>= 2048 bits is recommended

  - The group parameters should either be a well-known named group
    (e.g., RFC 7919), or generated by a trusted party and authenticated
    before use

## Key Lifetimes

  - All asymmetric keys should have a maximum five-year lifetime,
    recommended one-year lifetime.

  - All symmetric keys should have a maximum three-year lifetime;
    recommended one-year lifetime.

  - You should provide a mechanism or have a process for replacing keys
    to achieve the limited active lifetime. After the end of its active
    lifetime, a key should not be used to produce new data (for example,
    for encryption or signing), but may still be used to read data (for
    example, for decryption or verification).

## Random Number Generators
All products and services should use cryptographically secure random
number generators when randomness is required.

CNG

  - Use
    [<span class="underline">BCryptGenRandom</span>](https://msdn.microsoft.com/en-us/library/windows/desktop/aa375458.aspx)
    with the BCRYPT\_USE\_SYSTEM\_PREFERRED\_RNG flag

CAPI

  - Use
    [<span class="underline">CryptGenRandom</span>](https://msdn.microsoft.com/en-us/library/windows/desktop/aa379942.aspx)
    to generate random values.

Win32/64

  - Legacy code can use
    [<span class="underline">RtlGenRandom</span>](https://msdn.microsoft.com/en-us/library/windows/desktop/aa387694.aspx)
    in kernel mode

  - New code should use
    [<span class="underline">BCryptGenRandom</span>](https://msdn.microsoft.com/en-us/library/windows/desktop/aa375458.aspx)
    or
    [<span class="underline">CryptGenRandom</span>.](https://msdn.microsoft.com/en-us/library/windows/desktop/aa379942.aspx)

  - The C function
    <span class="underline">[Rand\_s(](https://msdn.microsoft.com/en-us/library/sxtz2fa8.aspx))</span>
    is also recommended (which on Windows, calls
    [<span class="underline">CryptGenRandom</span>)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa379942.aspx)

  - Rand\_s() is a safe and performant replacement for Rand(). Rand()
    should not be used for any cryptographic applications, but is ok for
    internal testing only.

  - The
    [<span class="underline">SystemPrng</span>](https://msdn.microsoft.com/en-us/library/windows/desktop/dd408060.aspx)
    function is recommended for kernel-mode code.

.NET

  - Use
    [<span class="underline">RNGCryptoServiceProvider</span>](https://msdn.microsoft.com/en-us/library/system.security.cryptography.rngcryptoserviceprovider.aspx)
    or
    [<span class="underline">RNGCng</span>.](https://clrsecurity.codeplex.com/wikipage?title=Security.Cryptography.RNGCng&referringTitle=Security.Cryptography.dll)

Windows Store Apps

  - Store Apps can use
    [<span class="underline">CryptographicBuffer.GenerateRandom</span>](https://msdn.microsoft.com/en-us/library/windows/apps/windows.security.cryptography.cryptographicbuffer.generaterandom.aspx)
    or
    [<span class="underline">CryptographicBuffer.GenerateRandomNumber</span>.](https://msdn.microsoft.com/en-us/library/windows/apps/windows.security.cryptography.cryptographicbuffer.generaterandomnumber.aspx)

Not Recommended

  - Insecure functions related to random number generation include
    [<span class="underline">rand</span>,](https://msdn.microsoft.com/en-us/library/398ax69y.aspx)
    [<span class="underline">System.Random</span>](https://msdn.microsoft.com/en-us/library/system.random.aspx)
    (.NET),
    [<span class="underline">GetTickCount</span>](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724408.aspx)
    and [<span class="underline">GetTickCount64</span>
    ](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724411.aspx)

  - Use of the dual elliptic curve random number generator
    ("DUAL\_EC\_DRBG") algorithm is not recommended.

## Windows Platform-supported Crypto Libraries
On the Windows platform, Microsoft recommends using the crypto APIs
built into the operating system. On other platforms, developers may
choose to evaluate non-platform crypto libraries for use. In general,
platform crypto libraries will be updated more frequently since they
ship as part of an operating system as opposed to being bundled with an
application.

Any usage decision regarding platform vs non-platform crypto should be
guided by the following requirements:

1.  The library should be a current in-support version free of known
    security vulnerabilities

2.  The latest security protocols, algorithms and key lengths should be
    supported

3.  (Optional) The library should be capable of supporting older
    security protocols/algorithms for backwards compatibility only

_Native Code_

  - Crypto Primitives: If your release is on Windows or Windows Phone,
    use CNG if possible. Otherwise, use the CryptoAPI (also called CAPI,
    which is supported as a legacy component on Windows from Windows
    Vista onward).

  - SSL/TLS/DTLS:
    [<span class="underline">WinINet</span>,](https://msdn.microsoft.com/en-us/library/windows/desktop/aa385331\(v=vs.85\).aspx)
    [<span class="underline">WinHTTP</span>,](https://msdn.microsoft.com/en-us/library/aa382925\(v=VS.85\).aspx)
    [<span class="underline">Schannel</span>,](https://msdn.microsoft.com/en-us/library/windows/desktop/ms678421\(v=vs.85\).aspx)
    [<span class="underline">IXMLHTTPRequest2</span>,](https://msdn.microsoft.com/en-us/library/windows/desktop/hh831151.aspx)
    or
    [<span class="underline">IXMLHTTPRequest3</span>.](https://msdn.microsoft.com/en-us/library/windows/desktop/dn376398.aspx)

    - WinHTTP apps should be built with [<span class="underline">WinHttpSetOption</span><span class="underline"></span>](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384114\(v=vs.85\).aspx)<span class="underline">in order</span> to support TLS 1.2

  - Code signature verification:
    [<span class="underline">WinVerifyTrust</span>](https://msdn.microsoft.com/en-us/library/aa388208\(v=VS.85\).aspx)
    is the supported API for verifying code signatures on Windows
    platforms.

  - Certificate Validation (as used in restricted certificate validation
    for code signing or SSL/TLS/DTLS): CAPI2 API; for example, [<span class="underline">CertGetCertificateChain</span>](https://msdn.microsoft.com/en-us/library/windows/desktop/aa376078\(v=vs.85\).aspx) and [<span class="underline">CertVerifyCertificateChainPolicy</span>](https://msdn.microsoft.com/en-us/library/windows/desktop/aa377163\(v=vs.85\).aspx)

_Managed Code_

  - Crypto Primitives: Use the API defined in
    System.Security.Cryptography namespace---the CNG classes are
    preferred.

  - Use the latest version of the .Net Framework available. At a minimum
    this should be .Net Framework version 4.6. If an older version is
    required, ensure the
    [“<span class="underline">SchUseStrongCrypto</span>”](https://technet.microsoft.com/en-us/library/security/2960358.aspx#ID0ETHAE)
    regkey is set to enable TLS 1.2 for the application in question.

  - Certificate Validation: Use APIs defined under the
    [<span class="underline">System.Security.Cryptography.X509Certificates</span>](https://msdn.microsoft.com/en-us/library/system.security.cryptography.x509certificates.aspx)
    namespace.

  - SSL/TLS/DTLS: Use APIs defined under the System.Net namespace (for
    example,
    [<span class="underline">HttpWebRequest</span>)](https://msdn.microsoft.com/en-us/library/system.net.httpwebrequest.aspx).

## Key Derivation Functions
Key derivation is the process of deriving cryptographic key material
from a shared secret or a existing cryptographic key. Products should
use recommended key derivation functions. Deriving keys from user-chosen
passwords, or hashing passwords for storage in an authentication system
is a special case not covered by this guidance; developers should
consult an expert.

The following standards specify KDF functions recommended for use:

  - NIST SP 800-108: *Recommendation For Key Derivation Using
    Pseudorandom Functions*. In particular, the KDF in counter mode,
    with HMAC as a pseudorandom function

  - NIST SP 800-56A (Revision 2): *Recommendation for Pair-Wise Key
    Establishment Schemes Using Discrete Logarithm Cryptography*. In
    particular, the “Single-Step Key Derivation Function” in Section
    5.8.1 is recommended.

To derive keys from existing keys, use the
[<span class="underline">BCryptKeyDerivation</span>](https://msdn.microsoft.com/en-us/library/windows/desktop/hh448506\(v=vs.85\).aspx)
API with one of the algorithms:

  - BCRYPT\_SP800108\_CTR\_HMAC\_ALGORITHM

  - BCRYPT\_SP80056A\_CONCAT\_ALGORITHM

To derive keys from a shared secret (the output of a key agreement) use
the
[<span class="underline">BCryptDeriveKey</span>](https://msdn.microsoft.com/en-us/library/windows/desktop/aa375393\(v=vs.85\).aspx)
API with one of the following algorithms:

  - BCRYPT\_KDF\_SP80056A\_CONCAT

  - BCRYPT\_KDF\_HMAC

## Certificate Validation
Products that use SSL, TLS, or DTLS should fully verify the X.509
certificates of the entities they connect to. This includes verification
of the certificates’:

  - Domain name.

  - Validity dates (both beginning and expiration dates).

  - Revocation status.

  - Usage (for example, “Server Authentication” for servers, “Client
    Authentication” for clients).

  - Trust chain. Certificates should chain to a root certification
    authority (CA) that is trusted by the platform or explicitly
    configured by the administrator.

If any of these verification tests fail, the product should terminate
the connection with the entity.

Clients that trust “self-signed” certificates (for example, a mail
client connecting to an Exchange server in a default configuration) may
ignore certificate verification checks. However, self-signed
certificates do not inherently convey trust, support revocation, or
support key renewal. You should only trust selfsigned certificates if
you have obtained them from another trusted source (for example, a
trusted entity that provides the certificate over an authenticated and
integrity-protected transport).

## Cryptographic Hash Functions
Products should use the SHA-2 family of hash algorithms (SHA256, SHA384,
and SHA512). Truncation of cryptographic hashes for security purposes to
less than 128 bits is not recommended.

### MAC/HMAC/keyed hash algorithms
A message authentication code (MAC) is a piece of information attached
to a message that allows its recipient to verify both the authenticity
of the sender and the integrity of the message using a secret key.

The use of either a hash-based MAC
([<span class="underline">HMAC</span>)](https://csrc.nist.gov/publications/nistpubs/800-107-rev1/sp800-107-rev1.pdf)
or [<span class="underline">block-cipher-based
MAC</span>](https://csrc.nist.gov/publications/nistpubs/800-38B/SP_800-38B.pdf)
is recommended as long as all underlying hash or symmetric encryption
algorithms are also recommended for use; currently this includes the
HMAC-SHA2 functions (HMAC-SHA256, HMAC-SHA384 and HMAC-SHA512).

Truncation of HMACs to less than 128 bits is not recommended.

## Design and Operational Considerations
  - You should provide a mechanism for replacing cryptographic keys as
    needed. Keys should be replaced once they have reached the end of
    their active lifetime or if the cryptographic key is compromised.
    Whenever you renew a certificate, you should renew it with a new
    key.

  - Products using cryptographic algorithms to protect data should
    include enough metadata along with that content to support migrating
    to different algorithms in the future. This should include the
    algorithm used, key sizes, initialization vectors, and padding
    modes.
    
      - For more information on Cryptographic Agility, see
        [<span class="underline">Cryptographic Agility on
        MSDN</span>.](https://msdn.microsoft.com/en-us/magazine/ee321570.aspx)

  - Where available, products should use established, platform-provided
    cryptographic protocols rather than re-implementing them. This
    includes signing formats (e.g. use a standard, existing format).

  - Symmetric stream ciphers such as RC4 should not be used. Instead of
    symmetric stream ciphers, products should use a block cipher,
    specifically AES with a key length of at least 128 bits.

  - Do not report cryptographic operation failures to end-users. When
    returning an error to a remote caller (e.g. web client, or client in
    a client-server scenario), use a generic error message only.
    
      - Avoid providing any unnecessary information, such as directly
        reporting out-of-range or invalid length errors. Log verbose
        errors on the server only, and only if verbose logging is
        enabled.

  - Additional security review is highly recommended for any design
    incorporating the following:
    
      - A new protocol that is primarily focused on security (such as an
        authentication or authorization protocol)
    
      - A new protocol that uses cryptography in a novel or non-standard
        way o Example considerations include:
        
          - Will a product that implements the protocol call any crypto
            APIs or methods as part of the protocol implementation?
        
          - Does the protocol depend on any other protocol used for
            authentication or authorization?
        
          - Will the protocol define storage formats for cryptographic
            elements, such as keys?

  - Self-signed certificates are not recommended for production
    environments. Use of a self-signed certificate, like use of a raw
    cryptographic key, does not inherently provide users or
    administrators any basis for making a trust decision.
    
      - In contrast, use of a certificate rooted in a trusted
        certificate authority makes clear the basis for relying on the
        associated private key and enables revocation and updates in the
        event of a security failure.

## Encrypting Sensitive Data prior to Storage 
_DPAPI/DPAPI-NG_

For data that needs to be persisted across system reboots:

  - CryptProtectData

  - CryptUnprotectData

  - NCryptProtectSecret (Windows 8 CNG DPAPI)

For data that does not need to be persisted across system reboots:

  - CryptProtectMemory

  - CryptUnprotectMemory

For data that needs to be persisted and accessed by multiple domain
accounts and computers:

  - NCryptProtectSecret (in CNG DPAPI, available as of Windows 8)

  - [<span class="underline">Microsoft Azure KeyVault</span>
    ](https://azure.microsoft.com/en-us/services/key-vault/)

_SQL Server TDE_

You can use SQL Server Transparent Data Encryption (TDE) to protect
sensitive data.

You should use a TDE database encryption key (DEK) that meets the SDL
cryptographic algorithm and key strength requirements. Currently, only
AES\_128, AES\_192 and AES\_256 are recommended; TRIPLE\_DES\_3KEY is
not recommended.

There are some important considerations for using SQL TDE that you
should keep in mind:

  - SQL Server does not support encryption for
    [<span class="underline">FILESTREAM</span>](https://technet.microsoft.com/en-us/library/gg471497.aspx)
    data, even when TDE is enabled.

  - TDE does not automatically provide encryption for data in transit to
    or from the database; you should also enable encrypted connections
    to the SQL Server database. Please see
    [<span class="underline">Enable</span>
    <span class="underline">Encrypted Connections to the Database Engine
    (SQL Server Configuration
    Manager)</span>](https://technet.microsoft.com/en-us/library/ms191192.aspx)
    for guidance on enabling encrypted connections.

  - If you move a TDE-protected database to a different SQL Server
    instance, you should also move the certificate that protects the TDE
    Data Encryption Key (DEK) and install it in the master database of
    the destination SQL Server instance. Please see the TechNet article
    [<span class="underline">Move a TDE</span>
    <span class="underline">Protected Database to Another SQL
    Server</span>](https://technet.microsoft.com/en-us/library/ff773063.aspx)
    for more details.

_Credential Management_

Use the [<span class="underline">Windows Credential Manager
API</span>](https://msdn.microsoft.com/en-us/library/windows/desktop/aa374731.aspx#credentials_management_functions)
or [<span class="underline">Microsoft Azure
KeyVault</span>](https://azure.microsoft.com/en-us/services/key-vault/)
to protect password and credential data.

_Windows Store Apps_ 

Use the classes in the [<span class="underline">Windows.Security.Cryptography</span>](https://msdn.microsoft.com/en-us/library/windows/apps/windows.security.cryptography.aspx)
and
[<span class="underline">Windows.Security.Cryptography.DataProtection</span>](https://msdn.microsoft.com/en-us/library/windows/apps/windows.security.cryptography.dataprotection.aspx)
namespaces to protect secrets and sensitive data.

  - ProtectAsync

  - ProtectStreamAsync

  - UnprotectAsync

  - UnprotectStreamAsync

Use the classes in the
[<span class="underline">Windows.Security.Credentials</span>](https://msdn.microsoft.com/en-us/library/windows/apps/windows.security.credentials.aspx)
namespace to protect password and credential data.

_.NET_

For data that needs to be persisted across system reboots:

  - ProtectedData.Protect

  - ProtectedData.Unprotect

For data that does not need to be persisted across system reboots:

  - ProtectedMemory.Protect

  - ProtectedMemory.Unprotect

For configuration files, use

either
[<span class="underline">RSAProtectedConfigurationProvider</span>](https://msdn.microsoft.com/en-us/library/system.configuration.rsaprotectedconfigurationprovider.aspx)
or
[<span class="underline">DPAPIProtectedConfigurationProvider</span>](https://msdn.microsoft.com/en-us/library/system.configuration.dpapiprotectedconfigurationprovider.aspx)
to protect your configuration, using either RSA encryption or DPAPI,
respectively.

The RSAProtectedConfigurationProvider can be used across multiple
machines in a cluster. See [<span class="underline">Encrypting
Configuration Information Using Protected
Configuration</span>](https://msdn.microsoft.com/en-us/library/53tyfkaw.aspx)
for more information.