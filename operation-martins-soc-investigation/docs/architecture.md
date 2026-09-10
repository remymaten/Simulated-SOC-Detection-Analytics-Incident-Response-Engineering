# Architecture & Baseline

## Environment

The project report defines an isolated virtual testbed named `soc-sandbox`.

## Hosts

| Host | IP | Function |
|---|---|---|
| KDC1 / Domain Controller | `192.168.10.10` | Authentication and domain services |
| Windows workstation | `192.168.10.20` | Endpoint |
| Kali Linux | `192.168.10.30` | Simulated attacker/red-team source |
| SIEM host | `192.168.56.1` | Splunk |

## Expected services

- DNS: 53
- Kerberos: 88
- LDAP: TCP 389
- SMB: TCP 445
- MSRPC: TCP 135
- Splunk ingestion: TCP 9997

## Design objective

The baseline establishes what normal domain and SIEM communication should look like so anomalous authentication activity can be distinguished during investigation.
