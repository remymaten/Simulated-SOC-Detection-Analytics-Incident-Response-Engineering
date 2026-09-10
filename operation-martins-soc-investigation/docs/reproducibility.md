# Technical Reproducibility Guide

## Purpose

This guide documents the parts of Operation Martins that can be reconstructed from the submitted project evidence without inventing configuration details that were not included in the source report.

## 1. Build the documented lab topology

Create an isolated virtual testbed containing the following documented systems:

| System | Address | Documented role |
|---|---|---|
| KDC1 / Domain Controller | `192.168.10.10` | Domain controller / authentication |
| Windows workstation | `192.168.10.20` | Endpoint |
| Kali Linux | `192.168.10.30` | Simulated red-team source |
| Splunk host | `192.168.56.1` | SIEM |

The source report depicts a dual-adapter architecture and identifies the host-only adapter as the SIEM communication path.

## 2. Establish the service baseline

The documented baseline includes:

- DNS `53`
- Kerberos `88`
- LDAP `389/TCP`
- SMB `445/TCP`
- MSRPC `135/TCP`
- Splunk ingestion `9997/TCP`

Use the baseline to distinguish expected domain traffic from anomalous traffic during the investigation.

## 3. Perform the documented reconnaissance step

The evidence screenshot shows an Nmap service-discovery command against the Windows workstation:

```text
nmap -Pn -sV 192.168.10.20
```

The report records SMB/MSRPC exposure as part of the observed environment.

## 4. Inspect SMB/authentication activity

The evidence includes NetExec SMB activity against the Domain Controller. The screenshot contains a credential-like lab value, so it is intentionally **not reproduced here**.

The important reproducibility points are the target (`192.168.10.10`), SMB service (`445`), the Administrator account context, and the resulting authentication activity.

## 5. Configure SIEM visibility

The source report states that Universal Forwarders on the server, Kali system, and workstation stream Windows Event Logs and Linux logs to Splunk over TCP `9997` through the host-only path.

The exact Splunk configuration files were not included in the submitted report, so this repository does not fabricate them.

## 6. Execute the documented detection query

The report explicitly states that the investigator queried:

```text
index=* EventCode=4625
```

Use the query to isolate failed Windows logons and pivot on the source IP.

## 7. Validate and scope

The documented response uses:

```text
EventCode=4624   # successful logon validation
Event 7045       # rogue service check
Event 4720       # unexpected account creation check
```

These checks help determine whether the activity progressed beyond failed authentication and whether persistence was established.

## 8. Execute the documented response

The report records these response actions:

- Block the Kali source IP at the network boundary.
- Disable the targeted Administrator account.
- Terminate active SMB connections.
- Check for successful logons.
- Check for rogue services.
- Check for unexpected user creation.
- Reset the affected account credential.
- Re-enable the account.
- Enforce Account Lockout Policy through Group Policy.

## Reproducibility boundary

The report does not provide all implementation-level details required for a one-click rebuild, such as exact VM resource allocations, Windows installation/build steps, Active Directory provisioning commands, Splunk configuration files, raw PCAP files, or exported dashboards/searches. These are intentionally identified as missing rather than guessed.
