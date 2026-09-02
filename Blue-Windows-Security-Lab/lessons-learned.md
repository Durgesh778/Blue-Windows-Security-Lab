# Lessons Learned

## Technical Lessons

1. `-p-` can be used when a full TCP port scan is required.
2. Ports 135, 139 and 445 are important Windows network-service ports.
3. SMB enumeration can reveal shares and protocol information.
4. SMBv1 is an important security finding on older Windows systems.
5. Metasploit's `check` function can help verify whether a known vulnerability appears exploitable.
6. Successful exploitation can lead to a Meterpreter session and significant system access.
7. Post-exploitation data such as credential hashes must be handled as sensitive information.

## Defensive Lessons

- Keep Windows systems and SMB components patched.
- Disable SMBv1 where it is not required.
- Restrict SMB exposure using firewalls and network segmentation.
- Monitor unusual SMB activity.
- Use strong authentication and least privilege.
- Protect credential material and never publish password hashes.

## Reporting Lesson

A good security write-up should document the methodology, commands, observations, impact, and lessons learned while removing sensitive information such as IP addresses, MAC addresses, credentials and password hashes.
