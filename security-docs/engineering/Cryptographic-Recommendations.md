---
title: Microsoft SDL cryptographic recommendations
description: Best practices and guidance for using encryption on Microsoft platforms as part of the security development lifecycle.

ms.service: security
ms.subservice: 
ms.topic: conceptual
ms.date: 05/19/2024
ms.author: laramiller
author: laramillermsft
ms.reviewer: laramiller, raulga
---
# Microsoft SDL Cryptographic Recommendations
Use this information as a reference when designing products to use the same APIs, algorithms, protocols, and key lengths that Microsoft requires of its own products and services. Much of the content is based on Microsoft’s own internal security standards used to create the Security Development Lifecycle.

Developers on non-Windows platforms might benefit from these recommendations. While the API and library names might be different, the best practices involving algorithm choice, key length, and data protection are similar across platforms.

## Security protocol, algorithm, and key length recommendations

### TLS/SSL versions
Products and services should use cryptographically secure versions of TLS/SSL:

  - TLS 1.3 must be enabled

  - TLS 1.2 can be enabled to improve compatibility with older clients.

  - TLS 1.1, TLS 1.0, SSL 3, and SSL 2 must be disabled

### Symmetric block ciphers, cipher modes, and initialization vectors
_Block ciphers_

For products using symmetric block ciphers:

  - Advanced Encryption Standard (AES) is required.

  - All other block ciphers, including 3DES (Triple DES/TDEA), and RC4 must be replaced if used for encryption.

For symmetric block encryption algorithms, we recommend supporting 256-bit keys, 
but allow down to 128-bits. The only block encryption algorithm recommended for new code is AES (AES-128, AES-192, and AES-256 are all acceptable, noting that AES-192 lacks optimization on some processors).

_Cipher modes_

Symmetric algorithms can operate in various modes, most of which link together the encryption operations on successive blocks of plaintext and ciphertext.

Symmetric block ciphers should be used with one of the following cipher modes:

  - [Cipher Block Chaining (CBC)](https://en.wikipedia.org/wiki/Block_cipher_mode_of_operation)

  - [Ciphertext Stealing (CTS)](https://en.wikipedia.org/wiki/Ciphertext_stealing)

  - [XEX-Based Tweaked-Codebook with Ciphertext Stealing (XTS)](https://en.wikipedia.org/wiki/Disk_encryption_theory#XEX-based_tweaked-codebook_mode_with_ciphertext_stealing_.28XTS.29)

Some other cipher modes like those that follow have implementation pitfalls that make them more likely to be used incorrectly. In particular, the Electronic Code Book (ECB) mode of operation must be avoided. Reusing the same initialization vector (IV) with block ciphers in "streaming ciphers modes" such as CTR might cause encrypted data to be revealed. Extra security review is recommended if any of the below modes are used:

  - Output Feedback (OFB)

  - Cipher Feedback (CFB)

  - Counter (CTR)

  - Anything else not on the preceeding "recommended" list above

_Initialization vectors (IV)_

All symmetric block ciphers should also be used with a cryptographically strong random number as an initialization vector. Initialization vectors should never be a constant or predicable value. See Random Number Generators for recommendations on generating cryptographically strong random numbers.

Initialization vectors should never be reused when performing multiple encryption operations. Reuse can reveal information about the data being encrypted, particularly when using streaming cipher modes like Output Feedback (OFB) or Counter (CTR).

### AES-GCM & AES-CCM recommendations
AES-GCM (Galois/Counter Mode) and AES-CCM (Counter with CBC-MAC) are widely used authenticated encryption modes. They combine confidentiality and integrity protection, making them useful for secure communication. However, their fragility lies in nonce reuse. When the same nonce (initialization vector) is used twice, it can lead to catastrophic consequences.  

We recommend following the nonce guidelines as described in [NIST SP 800-38D, Recommendation for Block Cipher Modes of Operation: Galois/Counter Mode (GCM) and GMAC](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-38d.pdf), taking special attention to sections 8.1, 8.2, and 8.3 regarding uniqueness requirements on the key and nonce/IV.

Another option would be to generate unique AES-GCM/CCM keys for every message being encrypted, effectively limiting the maximum number of invocations to 1. This approach is recommended for encrypting data at rest, where using a counter or making sure that you can track the maximum number of invocations for a given key would be impractical.

For encrypting data at rest, you can also consider using AES-CBC with a message authentication code (MAC) as an alternative using an Encrypt-then-MAC scheme, making sure you use separate keys for encryption and for the MAC.

_Integrity verification_
It's a common misconception that encryption by default provides both confidentiality and integrity assurance. Many encryption algorithms don't provide any integrity checking and might be vulnerable to tampering attacks. Extra steps must be taken to ensure the integrity of data before sending and after receiving.
 
If you can't use an authenticated encryption algorithm with associated data (AEAD) such as AES-GCM, an alternative would be to validate the integrity with a message authentication code (MAC) using an Encrypt-then-MAC scheme, making sure you use separate keys for encryption and for the MAC.

Using a separate key for encryption and for the MAC is essential. If it isn't possible to store the two keys, a valid alternative is to derive two keys from the main key using a suitable key derivation function (KDF), one for encryption purposes and one for MAC. For more information, see [SP 800-108 Rev. 1, Recommendation for Key Derivation Using Pseudorandom Functions | CSRC (nist.gov)]([https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-38d.pdf](https://csrc.nist.gov/pubs/sp/800/108/r1/upd1/final).

### Asymmetric algorithms, key lengths, and padding modes
_RSA_

  -	RSA can be used for key transport, key exchange, and signatures.
    
  -	RSA encryption should use the OAEP or RSA-PSS padding modes.
    
  -	Existing code may use PKCS #1 v1.5 padding mode for signing.
    
  -	Usage of PKCS#1 v1.5 for encryption is not allowed.
    
  -	Use of null padding isn't recommended.
    
  -	A 2048-bit key length is the minimum, but we recommend supporting a 3072-bit key length.

_ECDSA and ECDH_

  - ECDH-based key exchange and ECDSA-based signatures should use one of the three NIST-approved curves (P-256, P-384, or P521).
  
  -	Support for P-256 should be considered the minimum, but we recommend supporting P-384.

_ML-DSA_

  - Must use the [FIPS 204 standard](https://csrc.nist.gov/pubs/fips/204/final). Do not use the versions in the draft standard.
    
  - It is recommended using ML-DSA in combination with a classic signature algorithm (i.e. ECDSA or RSA). Using combiners defined by [IETF (draft)](https://lamps-wg.github.io/draft-composite-sigs/draft-ietf-lamps-pq-composite-sigs.html) or other standards is preferred for interoperability.
    
  - For ML-DSA, a valid hybrid (composite) mechanism is to sign the same data with both a classic and ML-DSA, and verify both (if either verification fails, the verification fails).

_ML-KEM_

  - Must use the [FIPS 203 standard](https://csrc.nist.gov/pubs/fips/203/final). Do not use the versions in the draft standard.
    
  -	It is recommended using a combiner or hybrid cryptosystem combining ML-KEM and a classic KEM algorithm (i.e. ECDH). Using combiners defined by [IETF (draft)](https://aka.ms/ietf-lamps-pq-composite-kem) or other standards is preferred for interoperability.

_SLH-DSA_

  - Must use the [FIPS 205 standard](https://csrc.nist.gov/pubs/fips/205/final). Do not use the versions in the draft standard.
    
  -	All SLH-DSA parameter sets are allowed, but the recommended parameter set will depend on the use case.
    
  - No known security difference between SHA-2 & SHAKE (SHA-3) versions

_LMS & XMSS_

  - It is safe to support LMS or XMSS for signature verification.
  
  - It is strongly recommended to consult with a subject matter expert before implementing/deploying infrastructure for signing and key generation. No weakness is known, but human-induced error is very possible and easy to make as it is critical to properly manage the state.

_Integer Diffie-Hellman_

  - Although Integer Diffie-Hellman (DH) is approved for key exchange, it is not the most efficient by modern standards. It is strongly recommended to use ECDH instead.
  - Key length >= 2048 bits is recommended0
  - The group parameters should either be a well-known named group (for example, [RFC 7919](https://datatracker.ietf.org/doc/html/rfc7919)), or generated by a trusted party and authenticated before use.

## Key Lifetimes

  - Define a [cryptoperiod](https://csrc.nist.gov/glossary/term/Cryptoperiod#:%7E:text=Cryptoperiod%20Definitions%3A%20The%20time%20span%20during%20which%20a,given%20system%20or%20application%20may%20remain%20in%20effect.) for all keys.
    
    - For example: A symmetric key for data encryption, often referred as data encryption key or DEK, might have a usage period of up to two years for encrypting data, also known as the originator usage period. You might define that it has a valid usage period for decryption for three more years, also known as the recipient-usage period.
      
  -	You should provide a mechanism or have a process for replacing keys to achieve the limited active lifetime. After the end of its active lifetime, a key must not be used to produce new data (for example, for encryption or signing), but might still be used to read data (for example, for decryption or verification).

## Random Number Generators
All products and services should use cryptographically secure random number generators when randomness is required.

_CNG_
 
 - Use BCryptGenRandom with the BCRYPT_USE_SYSTEM_PREFERRED_RNG flag.

_Win32/64_

  -	Legacy code can use [RtlGenRandom](https://msdn.microsoft.com/library/windows/desktop/aa387694.aspx) in kernel mode.
    
  - New code should use [BCryptGenRandom](https://msdn.microsoft.com/library/windows/desktop/aa375458.aspx) or [CryptGenRandom](https://msdn.microsoft.com/library/windows/desktop/aa379942.aspx).
    
  - The C function [Rand_s()](https://msdn.microsoft.com/library/sxtz2fa8.aspx) is also recommended (which on Windows, calls [CryptGenRandom](https://msdn.microsoft.com/library/windows/desktop/aa379942.aspx)).
    
  - Rand_s() is a safe and performant replacement for Rand().
    
  - Rand() must not be used for any cryptographic applications.

_.NET_

  - Use [RandomNumberGenerator](https://learn.microsoft.com/en-us/dotnet/api/system.security.cryptography.randomnumbergenerator).

_PowerShell_

  - Use [Get-SecureRandom (PowerShell)](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-securerandom).

_Windows Store apps_

  - Windows Store apps can use [CryptographicBuffer.GenerateRandom](https://msdn.microsoft.com/library/windows/apps/windows.security.cryptography.cryptographicbuffer.generaterandom.aspx) or [CryptographicBuffer.GenerateRandomNumber](https://msdn.microsoft.com/library/windows/apps/windows.security.cryptography.cryptographicbuffer.generaterandomnumber.aspx).

_Not Recommended_

  - Insecure functions related to random number generation include: [rand](https://msdn.microsoft.com/library/398ax69y.aspx), [System.Random (.NET)](https://msdn.microsoft.com/library/system.random.aspx), [GetTickCount](https://msdn.microsoft.com/library/windows/desktop/ms724408.aspx), [GetTickCount64](https://msdn.microsoft.com/library/windows/desktop/ms724411.aspx), and [Get-Random (PowerShell cmdlet)](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-random).

  - Use of the dual elliptic curve random number generator ("DUAL_E\_DRBG") algorithm is not permitted.

## Windows platform-supported crypto libraries
On the Windows platform, Microsoft recommends using the crypto APIs built into the operating system. On other platforms, developers might choose to evaluate nonplatform crypto libraries for use. In general, platform crypto libraries are updated more frequently since they ship as part of an operating system as opposed to being bundled with an application.

Any usage decision regarding platform vs nonplatform crypto should be guided by the following requirements:

  - The library should be a current in-support version free of known security vulnerabilities.
    
  - The latest security protocols, algorithms, and key lengths should be supported.
    
  -	(Optional) The library should be capable of supporting older security protocols/algorithms for backwards compatibility only.

_Native code_

  -	Crypto Primitives: If your release is on Windows, use CNG if possible.
  
  -	Code signature verification: [WinVerifyTrust](https://msdn.microsoft.com/library/aa388208(v=VS.85).aspx) is the supported API for verifying code signatures on Windows platforms.
  
  -	Certificate Validation (as used in restricted certificate validation for code signing or TLS/DTLS): CAPI2 API; for example, [CertGetCertificateChain](https://msdn.microsoft.com/library/windows/desktop/aa376078(v=vs.85).aspx) and [CertVerifyCertificateChainPolicy](https://msdn.microsoft.com/library/windows/desktop/aa377163(v=vs.85).aspx).

## Key Derivation Functions
Key derivation is the process of deriving cryptographic key material from a shared secret or an existing cryptographic key. Products should use recommended key derivation functions. Deriving keys from user-chosen passwords, or hashing passwords for storage in an authentication system is a special case not covered by this guidance; developers should consult an expert.

The following standards specify KDF functions recommended for use:

  - [NIST SP 800-108 (Revision 1)]https://csrc.nist.gov/pubs/sp/800/108/r1/upd1/final(): Recommendation For Key Derivation Using Pseudorandom Functions. In particular, the KDF in counter mode, with HMAC as a pseudorandom function

  - [NIST SP 800-56A (Revision 3)](https://csrc.nist.gov/pubs/sp/800/56/a/r3/final): Recommendation for Pair-Wise Key Establishment Schemes Using Discrete Logarithm Cryptography. 

To derive keys from existing keys, use the [BCryptKeyDerivation](https://msdn.microsoft.com/library/windows/desktop/hh448506(v=vs.85).aspx) API with one of the algorithms:

  - BCRYPT_SP800108_CTR_HMAC_ALGORITHM
    
  -	BCRYPT_SP80056A_CONCAT_ALGORITHM

To derive keys from a shared secret (the output of a key agreement), use the [BCryptDeriveKey](https://msdn.microsoft.com/library/windows/desktop/aa375393(v=vs.85).aspx) API with one of the following algorithms:

  - BCRYPT_KDF_SP80056A_CONCAT
  
  -	BCRYPT_KDF_HMAC

## Certificate validation
Products that use TLS, or DTLS should fully verify the X.509 certificates of the entities they connect to. This process includes verification of the following parts of the certificate:

  - Domain name.

  - Validity dates (both beginning and expiration dates).

  - Revocation status.

  - Usage (for example, “Server Authentication” for servers, “Client
    Authentication” for clients).

  - Trust chain. Certificates should chain to a root certification authority (CA) trusted by the platform or explicitly configured by the administrator.

If any of these verification tests fail, the product should terminate the connection with the entity.

Don't use "self-signed" certificates. Self-signed don't inherently convey trust, support revocation, or support key renewal.

## Cryptographic hash functions
Products should use the SHA-2 family of hash algorithms (SHA-256, SHA-384, and SHA-512). Truncation of cryptographic hashes for security purposes to less than 128 bits isn't permitted. While the usage of SHA-256 is the minimum, we recommend supporting SHA-384.

### MAC/HMAC/keyed hash algorithms
A message authentication code (MAC) is a piece of information attached to a message that allows its recipient to verify both the authenticity of the sender and the integrity of the message using a secret key.

The use of either a [hash-based MAC (HMAC)](https://csrc.nist.gov/publications/nistpubs/800-107-rev1/sp800-107-rev1.pdf) or [block-cipher-based MAC](https://csrc.nist.gov/publications/nistpubs/800-38B/SP_800-38B.pdf) is recommended as long as all underlying hash or symmetric encryption algorithms are also recommended for use; currently this includes the HMAC-SHA2 functions (HMAC-SHA256, HMAC-SHA384, and HMAC-SHA512). While the usage of HMAC-SHA256 is the minimum, we recommend supporting HMAC-SHA384.

Truncation of HMACs to less than 128 bits is not recommended.

## Design and operational considerations
  - You should provide a mechanism for replacing cryptographic keys as needed. Keys should be replaced once they reach the end of their active lifetime or the cryptographic key is compromised.
    
    - Whenever you renew a certificate, you should renew it with a new key (rekeying).
      
  -	Products using cryptographic algorithms to protect data should include enough metadata along with that content to support migrating to different algorithms in the future. This metadata should include the algorithm used, key sizes, and padding modes.
    
    - For more information on Cryptographic Agility, see the article [Cryptographic Agility](https://msdn.microsoft.com/magazine/ee321570.aspx).


  - Where available, products should use established, platform-provided cryptographic protocols rather than reimplementing them, including signing formats (for example, use a standard, existing format).
  
  - Don't report cryptographic operation failures to end-users. When returning an error to a remote caller (for example, web client, or client in a client-server scenario), use a generic error message only.
  
    - Avoid providing any unnecessary information, such as directly reporting out-of-range or invalid length errors. Log verbose errors on the server only, and only if verbose logging is enabled.

  - Extra security review is highly recommended for any design incorporating the following items:
 
    - A new protocol that is primarily focused on security (such as an authentication or authorization protocol)

    - A new protocol that uses cryptography in a novel or nonstandard way. Example considerations include:

      - Will a product that implements the protocol call any crypto APIs or methods as part of the protocol implementation?

      - Does the protocol depend on any other protocol used for authentication or authorization?

      -	Will the protocol define storage formats for cryptographic elements, such as keys?

  - Self-signed certificates aren't recommended. Use of a self-signed certificate, like use of a raw cryptographic key, doesn't inherently provide users or administrators any basis for making a trust decision.

    - In contrast, use of a certificate rooted in a trusted certificate authority makes clear the basis for relying on the associated private key and enables revocation and updates if there's a security failure.
