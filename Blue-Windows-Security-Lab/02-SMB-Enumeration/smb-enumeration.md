# 2. SMB Enumeration

## Objective

Enumerate SMB services and determine whether anonymous access or exposed shares were available.

## Share Enumeration

```bash
smbclient -L //TARGET_IP -N
```

The following shares were reported:

| Share | Type | Comment |
|---|---|---|
| ADMIN$ | Disk | Remote Admin |
| C$ | Disk | Default share |
| IPC$ | IPC | Remote IPC |

The command also attempted SMB1 workgroup listing and returned a resource-name error. No useful workgroup listing was obtained.

## IPC$ Connection

```bash
smbclient //TARGET_IP/IPC$
```

A password prompt appeared. The SMB client entered an interactive session, where `help` displayed available SMB client commands.

Running:

```text
ls
```

returned:

```text
NT_STATUS_INVALID_PARAMETER listing *
```

## ADMIN$ Access Attempt

```bash
smbclient //TARGET_IP/ADMIN$
```

Result:

```text
tree connect failed: NT_STATUS_ACCESS_DENIED
```

This demonstrated that the administrative share could not be accessed with the attempted credentials.

## SMB Protocol Enumeration

An initial script syntax attempt was incorrect:

```bash
nmap -p445 --script smb-os-discovery.smb-protocols TARGET_IP
```

Nmap reported that the script specification did not match a valid category, filename, or directory.

The corrected command was:

```bash
nmap -p445 --script smb-os-discovery,smb-protocols TARGET_IP
```

The scan identified:

- Windows 7 Ultimate SP1
- SMBv1 / NT LM 0.12
- SMB 2.0.2
- SMB 2.1

## Enumeration Conclusion

SMB was confirmed as a significant attack surface. SMBv1 was present, which was an important security observation for the vulnerability-assessment phase.
