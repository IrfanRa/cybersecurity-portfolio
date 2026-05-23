# Cryptography Basics - Classes 1-3 Notes

**Focus:** Plaintext/Ciphertext, AES, RSA, ECC, MD5, SHA256, Hashing vs
Encryption vs Encoding, Salt concept, and Caesar Cipher.

## 2.5-Hour Plan

|           |                                          |
|-----------|------------------------------------------|
| **Time**  | **Task**                                 |
| 0:00-0:25 | Plaintext, ciphertext, and Caesar cipher |
| 0:25-0:55 | Encoding vs encryption vs hashing        |
| 0:55-1:30 | AES, RSA, and ECC                        |
| 1:30-2:00 | MD5, SHA256, hashing, and salt           |

## Plaintext and Ciphertext

**Plaintext** is the original readable data before encryption.
**Ciphertext** is the unreadable encrypted output generated after
applying an encryption algorithm and key.

> Plaintext: Hello World  
> Ciphertext: Khoor Zruog

In cybersecurity, encryption protects confidentiality by converting
readable data into unreadable form.

## Caesar Cipher

Caesar Cipher is a basic substitution cipher where each letter is
shifted by a fixed number of positions.

> Example with shift +3:  
> A -> D  
> B -> E  
> HELLO -> KHOOR

It is useful for understanding the basic concept of encryption, but it
is not secure for real-world use.

## Encoding vs Encryption vs Hashing

Encoding converts data from one format to another. It is reversible and
not designed for security.

Encryption converts plaintext into ciphertext using a key. It is
reversible only with the correct decryption key.

Hashing converts data into a fixed-length digest. It is one-way and
cannot be reversed to recover the original input.

|               |                |              |                                     |
|---------------|----------------|--------------|-------------------------------------|
| **Technique** | **Reversible** | **Uses Key** | **Main Purpose**                    |
| Encoding      | Yes            | No           | Data formatting                     |
| Encryption    | Yes            | Yes          | Confidentiality                     |
| Hashing       | No             | No           | Integrity and password verification |

## AES

AES stands for Advanced Encryption Standard. It is a symmetric
encryption algorithm, meaning the same secret key is used for encryption
and decryption.

> Encrypt: Plaintext + Secret Key -> Ciphertext  
> Decrypt: Ciphertext + Same Secret Key -> Plaintext

AES is fast and commonly used for encrypting files, disks, VPN traffic,
and secure communication sessions.

**Interview line:** AES is a symmetric encryption algorithm used to
protect data confidentiality. It is fast and commonly used for bulk data
encryption.

## RSA

RSA is an asymmetric encryption algorithm. It uses a public key and a
private key.

> Public Key -> Encrypt / verify  
> Private Key -> Decrypt / sign

The public key can be shared openly, while the private key must remain
secret. RSA is commonly used for secure key exchange, digital
signatures, and SSL/TLS certificates.

**Interview line:** RSA is an asymmetric encryption algorithm that uses
a public-private key pair. It is commonly used for secure key exchange
and digital signatures.

## ECC

ECC stands for Elliptic Curve Cryptography. It is also an asymmetric
cryptography method. ECC provides strong security with smaller key sizes
compared to RSA.

ECC is commonly used in mobile devices, IoT devices, modern TLS, and
digital signature systems.

**Interview line:** ECC provides strong asymmetric cryptography with
smaller key sizes, making it efficient for mobile, embedded, and modern
secure communication systems.

## MD5

MD5 is an old hashing algorithm. It is now considered insecure because
it is vulnerable to collision attacks.

A collision happens when two different inputs produce the same hash
output. Because of this weakness, MD5 should not be used for password
storage or security-sensitive integrity checks.

**Interview line:** MD5 is considered insecure because it is vulnerable
to collision attacks and should not be used for secure password storage
or integrity protection.

## SHA256

SHA256 is a secure cryptographic hash function from the SHA-2 family. It
produces a 256-bit fixed-length hash.

SHA256 is used for file integrity verification, password-related
security systems, digital signatures, malware identification, and
blockchain systems.

> macOS command:
> `shasum -a 256 file.txt`

This command generates the SHA256 hash of a file.

**Interview line:** SHA256 is a cryptographic hash function that
produces a fixed 256-bit hash and is commonly used for integrity
verification and security applications.

## Salt

A salt is a random value added to a password before hashing.

Without salt, the same password creates the same hash. With salt, even
if two users have the same password, their final hashes will be
different.

> password123 + salt1 -> hash1  
> password123 + salt2 -> hash2

Salt helps protect against rainbow table attacks and makes password
cracking harder.

**Interview line:** A salt is a random value added to a password before
hashing to ensure that identical passwords generate different hashes and
to defend against rainbow table attacks.

## Quick Self-Test Questions

1. What is the difference between plaintext and ciphertext?
2. Is encoding a security method?
3. Why is hashing not reversible?
4. Why is AES faster than RSA for large data?
5. Why is MD5 insecure?
6. What problem does salt solve?
7. Where is SHA256 used in cybersecurity?
8. What is the difference between symmetric and asymmetric encryption?

## Interview-Style Explanation

Cryptography is used to protect data. Plaintext is readable data, and
ciphertext is encrypted unreadable data. Encryption protects
confidentiality and is reversible with the correct key. Hashing is
one-way and is mainly used for integrity checks and password
verification. Encoding is only format conversion and should not be
considered security.

AES is symmetric and fast, so it is used for encrypting large amounts of
data. RSA and ECC are asymmetric algorithms that use public and private
keys. RSA is widely used, while ECC provides similar security with
smaller keys. MD5 is outdated and insecure due to collision attacks,
while SHA256 is stronger and commonly used today. Salt is used with
password hashing to make identical passwords produce different hashes
and reduce the effectiveness of rainbow table attacks.
