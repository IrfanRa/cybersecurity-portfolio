# Day 3 Revision Notes: SSL/TLS, CIA Triad, UAC, Linux vs Windows Privileges

## Topics Covered

- SSL/TLS Overview
- CIA Triad
- User Account Control
- Linux Privilege Model
- Windows Privilege Model
- Least Privilege Principle

---

## 1. SSL/TLS Overview

SSL/TLS is used to secure communication between a client and a server. Modern systems use TLS, while SSL is outdated and deprecated.

HTTPS means HTTP traffic is protected using TLS.

TLS provides:

- Confidentiality
- Integrity
- Authentication

### TLS Handshake Summary

1. Client sends a ClientHello message.
2. Server responds with ServerHello.
3. Server sends its digital certificate.
4. Client verifies the certificate.
5. Client and server agree on encryption keys.
6. Secure encrypted communication begins.

### Common TLS Issues

- Expired certificate
- Self-signed certificate
- Weak TLS version
- Weak cipher suite
- Certificate name mismatch
- Mixed content

---

## 2. CIA Triad

The CIA Triad is a core cybersecurity model.

### Confidentiality

Confidentiality ensures that only authorized users can access sensitive information.

Examples:

- Encryption
- Access control
- MFA
- Strong passwords
- File permissions

Failure examples:

- Data breach
- Password leak
- Unauthorized database access

### Integrity

Integrity ensures that data remains accurate and is not modified without authorization.

Examples:

- Hashing
- Digital signatures
- File integrity monitoring
- Audit logs

Failure examples:

- Website defacement
- File tampering
- Log modification

### Availability

Availability ensures that systems and data are accessible when needed.

Examples:

- Backups
- Redundancy
- Monitoring
- DDoS protection
- Disaster recovery

Failure examples:

- Server outage
- DDoS attack
- Ransomware
- Hardware failure

---

## 3. UAC - User Account Control

User Account Control is a Windows security feature that helps prevent unauthorized administrative changes.

UAC prompts the user when an application attempts to perform actions requiring elevated privileges.

UAC helps protect actions such as:

- Installing software
- Modifying system files
- Changing registry settings
- Installing drivers
- Changing firewall settings
- Creating services

UAC supports the principle of least privilege.

---

## 4. Linux Privilege Model

Linux uses:

- Users
- Groups
- Root account
- File ownership
- File permissions
- sudo

The root user has full control over the system.

Normal users have limited permissions.

`sudo` allows authorized users to run commands with elevated privileges.

Linux file permissions use:

- r = read
- w = write
- x = execute

Permissions apply to:

- Owner
- Group
- Others

Useful commands:

```bash
whoami
id
ls -l
sudo command
chmod 644 file.txt
sudo chown user:user file.txt

