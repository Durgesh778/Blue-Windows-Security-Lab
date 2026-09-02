# 1. Reconnaissance

## Objective

Identify reachable TCP services, service versions, and operating-system information on the lab target.

## Initial Attempt


```bash
nmap -T4 -p- -A TARGET_IP
```

### Options

- `-T4` — faster scan timing.
- `-p-` — scan all TCP ports.
- `-A` — enable OS detection, version detection, default NSE scripts and traceroute.

## Results

The target was reachable. The scan identified:

| Port | State | Service |
|---:|---|---|
| 135 | open | MSRPC |
| 139 | open | NetBIOS-SSN |
| 445 | open | Microsoft-DS / SMB |
| 49152 | open | MSRPC |
| 49153 | open | MSRPC |
| 49154 | open | MSRPC |
| 49155 | open | MSRPC |
| 49157 | open | MSRPC |

The target was identified as **Windows 7 Ultimate Service Pack 1**. The SMB host script also reported the `WORKGROUP` workgroup.

## Additional Service Scan

```bash
nmap -sV -p 135,139,445 TARGET_IP
```

This confirmed the services on ports 135, 139 and 445.

## Nikto Attempt

```bash
nikto -h TARGET_IP
```

The recorded attempt returned:

```text
0 host(s) tested
```

Therefore, no useful Nikto findings were recorded from this attempt.

## SSH Check

```bash
nmap -p22 -sV TARGET_IP
```

Result:

```text
22/tcp closed ssh
```

This indicated that SSH was not available on the target.

## Reconnaissance Conclusion

SMB on TCP 445 was the most important service to investigate further because it was exposed and the target was an older Windows system.
