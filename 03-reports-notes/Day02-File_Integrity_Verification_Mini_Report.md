# File Integrity Verification — Mini Report

**Author:** Irfan Rafiq  
**Track:** 45-Day Cybersecurity Mastery Plan  
**Phase:** Foundation  
**Topic:** Cryptography, Hashing, and File Integrity  
**Lab Environment:** Kali Linux VM  
**Tools Used:** `sha256sum`, `diff`, `GPG`, `Hashcat`, `hashid`

---

## 1. Executive Summary

This mini-report explains how file integrity verification works using cryptographic hashing. In the lab, a text file was created and hashed using SHA256. After modifying only one byte/character, the SHA256 hash changed completely. This confirmed that even a very small change in file content can be detected using a cryptographic hash.

The lab also included GPG encryption/decryption and basic hash type identification using Hashcat examples. These tasks helped reinforce the difference between hashing, encryption, and hash identification.

---

## 2. Objective

The objective of this lab was to:

- Generate a SHA256 hash of a file.
- Modify the file slightly and observe hash changes.
- Verify file integrity using checksum validation.
- Understand the avalanche effect in hashing.
- Encrypt and decrypt a file using GPG.
- Explore Hashcat example hashes and identify common hash types.

---

## 3. Background Concepts

### 3.1 Plaintext and Ciphertext

Plaintext is readable original data. Ciphertext is encrypted unreadable data produced after encryption.

Example:

```text
Plaintext:  This is a secret message.
Ciphertext: Unreadable encrypted output
```

### 3.2 Hashing

Hashing is a one-way process that converts input data into a fixed-length output called a hash or digest. A hash cannot be reversed to recover the original input.

SHA256 is commonly used for file integrity verification because the same file always produces the same hash, while any modification creates a different hash.

### 3.3 Encryption

Encryption protects confidentiality by converting readable data into unreadable ciphertext using a key or passphrase. Unlike hashing, encryption is reversible if the correct key/passphrase is available.

### 3.4 Encoding

Encoding is only data format conversion. It is reversible and should not be considered a security control.

---

## 4. Lab Environment

The lab was performed in Kali Linux using the terminal.

Recommended folder structure:

```text
cybersecurity-portfolio/
└── reports/
    └── notes/
        └── file-integrity-verification-mini-report.md
```

---

## 5. Procedure and Commands

### 5.1 Create a Lab Directory

```bash
mkdir -p ~/cyber-labs/day-crypto-lab
cd ~/cyber-labs/day-crypto-lab
```

**Purpose:**  
Creates a dedicated folder for the cryptography lab and moves into it.

---

### 5.2 Create a Sample File

```bash
echo "This is my first cryptography lab file." > message.txt
```

**Purpose:**  
Creates a simple text file that will be used for hashing and integrity verification.

---

### 5.3 Generate Original SHA256 Hash

```bash
sha256sum message.txt
sha256sum message.txt > original_hash.txt
```

**Purpose:**  
Generates the SHA256 hash of the original file and saves it as a baseline checksum.

---

### 5.4 Modify the File by One Character

```bash
printf "!" >> message.txt
```

**Purpose:**  
Adds a very small change to the file. This simulates a minor file modification or tampering attempt.

---

### 5.5 Generate Modified SHA256 Hash

```bash
sha256sum message.txt
sha256sum message.txt > modified_hash.txt
```

**Purpose:**  
Generates a new SHA256 hash after the file modification.

---

### 5.6 Compare Original and Modified Hashes

```bash
cat original_hash.txt
cat modified_hash.txt
diff original_hash.txt modified_hash.txt
```

**Purpose:**  
Displays both hashes and compares them. The output should show that the hashes are different.

---

### 5.7 Verify File Integrity Using Checksum

```bash
echo "This is my first cryptography lab file." > original_message.txt
sha256sum original_message.txt > original_message.sha256
sha256sum -c original_message.sha256
```

**Purpose:**  
Creates a checksum file and verifies that the file is unchanged.

Expected result:

```text
original_message.txt: OK
```

---

### 5.8 Modify the File and Verify Again

```bash
echo "modified" >> original_message.txt
sha256sum -c original_message.sha256
```

**Purpose:**  
Modifies the file and checks it against the original checksum.

Expected result:

```text
original_message.txt: FAILED
sha256sum: WARNING: 1 computed checksum did NOT match
```

---

## 6. GPG Encryption and Decryption

### 6.1 Create a Secret File

```bash
echo "This is a secret message for my cybersecurity lab." > secret.txt
```

**Purpose:**  
Creates a plaintext file for encryption testing.

---

### 6.2 Encrypt the File with GPG

```bash
gpg -c secret.txt
```

**Purpose:**  
Encrypts the file using symmetric encryption. GPG asks for a passphrase and creates an encrypted file named `secret.txt.gpg`.

---

### 6.3 Confirm Encrypted File Type

```bash
file secret.txt.gpg
```

**Purpose:**  
Confirms that the output file is GPG encrypted data.

---

### 6.4 Remove Plaintext File

```bash
rm secret.txt
```

**Purpose:**  
Deletes the original readable file so only the encrypted copy remains.

---

### 6.5 Decrypt the File

```bash
gpg -o decrypted_secret.txt -d secret.txt.gpg
cat decrypted_secret.txt
```

**Purpose:**  
Decrypts the encrypted file using the correct passphrase and verifies the recovered content.

---

## 7. Hashcat Example Hashes and Hash Identification

### 7.1 Run Hashcat Example Hashes

```bash
hashcat --example-hashes
```

**Purpose:**  
Displays many hash formats supported by Hashcat.

---

### 7.2 Save Hashcat Examples to a File

```bash
hashcat --example-hashes > hashcat_example_hashes.txt
```

**Purpose:**  
Saves the examples for later review and portfolio evidence.

---

### 7.3 Search Common Hash Types

```bash
grep -i "md5" hashcat_example_hashes.txt | head
grep -i "sha256" hashcat_example_hashes.txt | head
grep -i "bcrypt" hashcat_example_hashes.txt | head
grep -i "ntlm" hashcat_example_hashes.txt | head
```

**Purpose:**  
Filters the Hashcat examples to identify common hash families.

---

### 7.4 Generate and Identify Sample Hashes

```bash
echo -n "password123" | md5sum
echo -n "password123" | sha256sum
echo -n "password123" | sha512sum
```

**Purpose:**  
Generates sample hashes and helps identify them by length and pattern.

---

## 8. Observations

### 8.1 SHA256 Hash Change

After modifying only one character in the file, the SHA256 hash changed completely.

This proves that SHA256 is highly sensitive to input changes.

### 8.2 Integrity Verification

The command `sha256sum -c` successfully detected whether the file was unchanged or modified.

### 8.3 GPG Encryption

GPG converted a readable plaintext file into encrypted data. The encrypted file could not be read properly without decryption.

### 8.4 Hash Identification

Hash types can often be identified by length, format, prefix, and context.

Examples:

| Hash Type | Pattern |
|---|---|
| MD5 | 32 hexadecimal characters |
| SHA1 | 40 hexadecimal characters |
| SHA256 | 64 hexadecimal characters |
| SHA512 | 128 hexadecimal characters |
| bcrypt | Starts with `$2a$`, `$2b$`, or `$2y$` |
| Linux SHA512 crypt | Starts with `$6$` |
| NTLM | 32 hexadecimal characters, usually Windows context |

---

## 9. Key Findings

- SHA256 can detect even a one-byte file modification.
- File integrity verification is important for detecting tampering, corruption, and unauthorized changes.
- Hashing is one-way and is used for integrity verification.
- Encryption is reversible with the correct key/passphrase and is used for confidentiality.
- GPG can encrypt files securely using symmetric encryption.
- Hashcat example hashes are useful for understanding different hash formats.
- Hash identification is based on pattern, length, prefix, and real-world context.

---

## 10. Security Relevance

File integrity verification is important in cybersecurity operations. SOC analysts, system administrators, and incident responders use hashes to:

- Detect changed or tampered files.
- Verify downloaded files.
- Compare malware samples.
- Validate forensic evidence.
- Monitor critical system files.
- Confirm whether a file matches a known safe or malicious hash.

In a SOC environment, hash values are often used as Indicators of Compromise, also called IOCs.

---

## 11. Interview-Style Explanation

In this lab, I created a file and generated its SHA256 hash. Then I modified the file by adding only one character. After hashing the file again, the new hash was completely different from the original hash. This demonstrated the avalanche effect and showed how cryptographic hashes can detect even small changes in file content.

I also used `sha256sum -c` to verify file integrity. When the file was unchanged, the verification result was OK. After modifying the file, verification failed. This proves that hashing is useful for detecting file tampering.

I also used GPG to encrypt and decrypt a text file. This helped me understand the difference between hashing and encryption. Hashing is one-way and used for integrity, while encryption is reversible with the correct key or passphrase and used for confidentiality.

Finally, I reviewed Hashcat example hashes and practiced identifying hash types such as MD5, SHA256, SHA512, bcrypt, and NTLM based on format and length.

---

## 12. Conclusion

This lab demonstrated the practical use of SHA256 for file integrity verification. A small file modification caused the hash to change completely, proving that cryptographic hashing is effective for detecting file changes. GPG encryption demonstrated confidentiality protection, while Hashcat examples helped build familiarity with common hash formats.

This mini-report can be used as a beginner-friendly portfolio artifact for cybersecurity foundation skills, especially for junior SOC analyst, cybersecurity intern, and vulnerability assessment roles.

---

## 13. Portfolio Evidence to Add

Recommended files and screenshots:

```text
reports/notes/file-integrity-verification-mini-report.md
screenshots/sha256-before-after.png
screenshots/sha256-check-ok-failed.png
screenshots/gpg-encrypt-decrypt.png
screenshots/hashcat-example-hashes.png
```

---

## 14. Tracker Update

```text
Report completed: Yes
Portfolio completed: Yes
Lab completed: Yes
Status: Completed
Blocker / note: File Integrity Verification mini-report completed and ready for GitHub upload.
```
