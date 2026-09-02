# Blue Windows Security Lab

## Overview

This repository documents a controlled Windows security lab performed in an isolated environment. The objective was to practice reconnaissance, SMB enumeration, vulnerability assessment, exploitation, and basic post-exploitation analysis.

> **Disclaimer:** This work was performed only against a deliberately configured lab system that I was authorized to test. It is intended for educational purposes.

## Methodology

1. Reconnaissance
2. SMB Enumeration
3. Vulnerability Assessment
4. Exploitation
5. Post-Exploitation
6. Lessons Learned

## Key Findings

- TCP 135, 139 and 445 were exposed.
- SMB services were identified on the Windows target.
- SMBv1 was detected.
- The target was identified as Windows 7 Ultimate SP1.
- Metasploit's MS17-010 check reported the target as vulnerable.
- The EternalBlue lab exploit successfully established a Meterpreter session.
- Credential hashes were obtained during post-exploitation; actual hashes are intentionally excluded from this repository.

## Privacy / Redaction

All target and attacker IP addresses have been replaced with `TARGET_IP` and `ATTACKER_IP`.

MAC addresses, credential hashes, and other unnecessary lab-specific identifiers are also excluded.

## Documents

- [Reconnaissance](01-Reconnaissance/nmap.md)
- [SMB Enumeration](02-SMB-Enumeration/smb-enumeration.md)
- [Vulnerability Assessment](03-Vulnerability-Assessment/ms17-010.md)
- [Exploitation](04-Exploitation/eternalblue.md)
- [Post-Exploitation](05-Post-Exploitation/meterpreter.md)
- [Lessons Learned](lessons-learned.md)
