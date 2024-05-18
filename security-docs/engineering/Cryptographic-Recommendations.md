---
title: Microsoft SDL cryptographic recommendations
description: Best practices and guidance for using encryption on Microsoft platforms as part of the security development lifecycle.

ms.service: security
ms.subservice: 
ms.topic: conceptual
ms.date: 05/17/2024

ms.author: joflore
author: MicrosoftGuyJFlo
manager: amycolannino
ms.reviewer: joylynnkirui
---
# Microsoft SDL cryptographic recommendations

Use this information as a reference when designing products to use the same APIs, algorithms, protocols, and key lengths that Microsoft requires of its own products and services. Much of the content is based on Microsoft’s own internal security standards used to create the Security Development Lifecycle. 

Developers on non-Windows platforms might benefit from these recommendations. While the API and library names might be different, the best practices involving algorithm choice, key length, and data protection are similar across platforms.

## Security protocol, algorithm, and key length recommendations

### TLS/SSL versions

Products and services should use cryptographically secure versions of TLS/SSL:

- TLS 1.3 must be enabled
- TLS 1.2 can be enabled to improve compatibility with older clients
- TLS 1.1, TLS 1.0, SSL 3, and SSL 2 must be disabled by default

### Symmetric block ciphers, cipher modes, and initialization vectors

#### Block ciphers

For products using symmetric block ciphers:

- Advanced Encryption Standard (AES) is recommended.
- All other block ciphers, including Triple Data Encryption Algorithm (TDEA), RC4, must be replaced if used for encryption.

For symmetric block encryption algorithms, a minimum key length of 128 bits is, but we recommend supporting 256-bit keys. The only block encryption algorithm recommended for new code is AES (AES-128, AES-192, and AES-256 are all acceptable, noting that AES-192 lacks optimization on some processors).

#### Cipher modes

Symmetric algorithms can operate in various modes, most of which link together the encryption operations on successive blocks of plaintext and ciphertext.

Symmetric block ciphers should be used with one of the following cipher modes:

- [Cipher Block Chaining (CBC)]()
- [Ciphertext Stealing (CTS)]()
- [XEX-Based Tweaked-Codebook with Ciphertext Stealing (XTS)]()

Some other cipher modes like those that follow have implementation pitfalls that make them more likely to be used incorrectly. In particular, the Electronic Code Book (ECB) mode of operation should be avoided. Reusing the same initialization vector (IV) with block ciphers in "streaming ciphers modes" such as CTR might cause encrypted data to be revealed. Extra security review is recommended if any of the below modes are used:

- Output Feedback (OFB)
- Cipher Feedback (CFB)
- Counter (CTR)
- Anything else not on the preceding "recommended" list

#### Initialization vectors (IV)

All symmetric block ciphers should also be used with a cryptographically strong random number as an initialization vector. Initialization vectors should never be a constant value. See Random Number Generators for recommendations on generating cryptographically strong random numbers.

Initialization vectors should never be reused when performing multiple encryption operations. Reuse can reveal information about the data being encrypted, particularly when using streaming cipher modes like Output Feedback (OFB) or Counter (CTR).

#### AES-GCM & AES-CCM recommendations

AES-GCM (Galois/Counter Mode) and AES-CCM (Counter with CBC-MAC) are widely used authenticated encryption modes. They combine confidentiality and integrity protection, making them useful for secure communication. However, their fragility lies in nonce reuse. When the same nonce (initialization vector) is used twice, it can lead to catastrophic consequences.

We recommend following the nonce guidelines as described in [NIST SP 800-38D, Recommendation for Block Cipher Modes of Operation: Galois/Counter Mode (GCM) and GMAC](), taking special attention to section 8.3 regarding the maximum number of invocations.

Another option would be generated unique AES-GCM/CCM keys for every message being encrypted, effectively limiting the maximum number of invocations to 1. This approach is recommended for encrypting data at rest, where using a counter or making sure that you can track the maximum number of invocations for a given key would be impractical.

For encrypting data at rest, you can also consider using AES-CBC with a message authentication code (MAC) as an alternative using an Encrypt-then-MAC scheme, making sure you use separate keys for encryption and for the MAC.

#### Integrity verification

It's a common misconception that encryption by default provides both confidentiality and integrity assurance. Many encryption algorithms don't provide any integrity checking and might be vulnerable to tampering attacks. Extra steps must be taken to ensure the integrity of data before sending and after receiving.

If you can't use an authenticated encryption algorithm with associated data (AEAD) such as AES-GCM, an alternative would be to validate the integrity with a message authentication code (MAC) using an Encrypt-then-MAC scheme, making sure you use separate keys for encryption and for the MAC.

Using a separate key for encryption and for the MAC is essential. If it isn't possible to store the two keys, a valid alternative is to derive two keys from the main key using a suitable key derivation function (KDF), one for encryption purposes and one for MAC. For more information, see [SP 800-108 Rev. 1, Recommendation for Key Derivation Using Pseudorandom Functions | CSRC (nist.gov)]().

### Asymmetric algorithms, key lengths, and padding modes

#### RSA

- RSA should be used for encryption, key exchange, and signatures.
- RSA encryption should use the OAEP or RSA-PSS padding modes.
- Existing code should use PKCS #1 v1.5 padding mode for compatibility only.
- Use of null padding isn't recommended.
- A minimum of a 2048-bit key length is recommended, but we recommend supporting a 3072-bit key length.

#### ECDSA and ECDH

- ECDH-based key exchange and ECDSA-based signatures should use one of the three NIST-approved curves (P-256, P-384, or P521).
- Support for P-256 should be considered the minimum, but we recommend supporting P-384.

#### Integer Diffie-Hellman

- Key length >= 2048 bits is recommended0
- The group parameters should either be a well-known named group (for example, RFC 7919), or generated by a trusted party and authenticated before use.

## Key lifetimes

- Define a [cryptoperiod]() for all keys.
   - For example: A symmetric key for data encryption, often referred as data encryption key or DEK, might have a usage period of up to two years for encrypting data, also known as the originator usage period. You might define that it has a valid usage period for decryption for three more years, also known as the recipient-usage period.
- You should provide a mechanism or have a process for replacing keys to achieve the limited active lifetime. After the end of its active lifetime, a key shouldn't be used to produce new data (for example, for encryption or signing), but might still be used to read data (for example, for decryption or verification).

## Random number generators

All products and services should use cryptographically secure random number generators when randomness is required.

### CNG

- Use [BCryptGenRandom]() with the BCRYPT_USE_SYSTEM_PREFERRED_RNG flag.

### Win32/64

- Legacy code can use [RtlGenRandom]() in kernel mode.
- New code should use [BCryptGenRandom]() or [CryptGenRandom]().
- The C function [Rand_s()]() is also recommended (which on Windows, calls CryptGenRandom).
- Rand_s() is a safe and performant replacement for Rand().
- Rand() must not be used for any cryptographic applications.

### .NET

- Use [RandomNumberGenerator]().

### PowerShell

- Use [Get-SecureRandom (PowerShell)]().

### Windows Store apps

- Windows Store apps can use [CryptographicBuffer.GenerateRandom]() or [CryptographicBuffer.GenerateRandomNumber]().

### Not recommended

- Insecure functions related to random number generation include: [rand](), [System.Random (.NET)](), [GetTickCount](), [GetTickCount64](), and [Get-Random (PowerShell cmdlet)]().
- Use of the dual elliptic curve random number generator ("DUAL_EC_DRBG") algorithm isn't recommended.

## Windows platform supported crypto libraries

On the Windows platform, Microsoft recommends using the crypto APIs built into the operating system. On other platforms, developers might choose to evaluate nonplatform crypto libraries for use. In general, platform crypto libraries are updated more frequently since they ship as part of an operating system as opposed to being bundled with an application.

Any usage decision regarding platform vs nonplatform crypto should be guided by the following requirements:

1. The library should be a current in-support version free of known security vulnerabilities.
2. The latest security protocols, algorithms, and key lengths should be supported.
3. (Optional) The library should be capable of supporting older security protocols/algorithms for backwards compatibility only.

### Native code

- Crypto Primitives: If your release is on Windows, use CNG if possible.
- Code signature verification: [WinVerifyTrust]() is the supported API for verifying code signatures on Windows platforms.
- Certificate Validation (as used in restricted certificate validation for code signing or SSL/TLS/DTLS): CAPI2 API; for example, [CertGetCertificateChain]() and [CertVerifyCertificateChainPolicy]().

### Managed code

- Crypto Primitives: Use the API defined in [System.Security.Cryptography]() namespace.
- Use the latest version of .NET available.

## Key derivation functions

Key derivation is the process of deriving cryptographic key material from a shared secret or an existing cryptographic key. Products should use recommended key derivation functions. Deriving keys from user-chosen passwords, or hashing passwords for storage in an authentication system is a special case not covered by this guidance; developers should consult an expert.

The following standards specify KDF functions recommended for use:

- [NIST SP 800-108 (Revision 1)](): Recommendation For Key Derivation Using Pseudorandom Functions. In particular, the KDF in counter mode, with HMAC as a pseudorandom function
- [NIST SP 800-56A (Revision 3)](): Recommendation for Pair-Wise Key Establishment Schemes Using Discrete Logarithm Cryptography.

To derive keys from existing keys, use the [BCryptKeyDerivation]() API with one of the algorithms:

- BCRYPT_SP800108_CTR_HMAC_ALGORITHM
- BCRYPT_SP80056A_CONCAT_ALGORITHM

To derive keys from a shared secret (the output of a key agreement), use the [BCryptDeriveKey]() API with one of the following algorithms:

- BCRYPT_KDF_SP80056A_CONCAT
- BCRYPT_KDF_HMAC

## Certificate validation

Products that use TLS, or DTLS should fully verify the X.509 certificates of the entities they connect to. This process includes verification of the following parts of the certificate:

- Domain name.
- Validity dates (both beginning and expiration dates).
- Revocation status.
- Usage (for example, "Server Authentication" for servers, "Client Authentication" for clients).
- Trust chain. Certificates should chain to a root certification authority (CA) trusted by the platform or explicitly configured by the administrator.

If any of these verification tests fail, the product should terminate the connection with the entity.

Don't use "self-signed" certificates. Self-signed don't inherently convey trust, support revocation, or support key renewal.

## Cryptographic hash functions

Products should use the SHA-2 family of hash algorithms (SHA-256, SHA-384, and SHA-512). Truncation of cryptographic hashes for security purposes to less than 128 bits isn't recommended. While the usage of SHA-256 is the minimum, we recommend supporting SHA-384.

### MAC/HMAC/keyed hash algorithms

A message authentication code (MAC) is a piece of information attached to a message that allows its recipient to verify both the authenticity of the sender and the integrity of the message using a secret key.

The use of either a [hash-based MAC (HMAC)]() or [block-cipher-based MAC]() is recommended as long as all underlying hash or symmetric encryption algorithms are also recommended for use; currently this includes the HMAC-SHA2 functions (HMAC-SHA256, HMAC-SHA384, and HMAC-SHA512). While the usage of HMAC-SHA256 is the minimum, we recommend supporting HMAC-SHA384.

Truncation of HMACs to less than 128 bits isn't recommended.

## Design and operational considerations

- You should provide a mechanism for replacing cryptographic keys as needed. Keys should be replaced once they reach the end of their active lifetime or the cryptographic key is compromised. Whenever you renew a certificate, you should renew it with a new key.
- Products using cryptographic algorithms to protect data should include enough metadata along with that content to support migrating to different algorithms in the future. This metadata should include the algorithm used, key sizes, and padding modes.
   - For more information on Cryptographic Agility, see the article [Cryptographic Agility]().
- Where available, products should use established, platform-provided cryptographic protocols rather than reimplementing them, including signing formats (for example, use a standard, existing format).
- Symmetric stream ciphers such as RC4 shouldn't be used. Instead of symmetric stream ciphers, products should use a block cipher, specifically AES with a key length of at least 128 bits.
- Don't report cryptographic operation failures to end-users. When returning an error to a remote caller (for example, web client, or client in a client-server scenario), use a generic error message only.
   - Avoid providing any unnecessary information, such as directly reporting out-of-range or invalid length errors. Log verbose errors on the server only, and only if verbose logging is enabled.
- Extra security review is highly recommended for any design incorporating the following items:
   - A new protocol that is primarily focused on security (such as an authentication or authorization protocol)
   - A new protocol that uses cryptography in a novel or nonstandard way. Example considerations include:
      - Will a product that implements the protocol call any crypto APIs or methods as part of the protocol implementation?
      - Does the protocol depend on any other protocol used for authentication or authorization?
      - Will the protocol define storage formats for cryptographic elements, such as keys?
- Self-signed certificates aren't recommended. Use of a self-signed certificate, like use of a raw cryptographic key, doesn't inherently provide users or administrators any basis for making a trust decision.
   - In contrast, use of a certificate rooted in a trusted certificate authority makes clear the basis for relying on the associated private key and enables revocation and updates if there's a security failure.
