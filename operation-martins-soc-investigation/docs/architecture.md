# Architecture & Baseline

## Environment

The project report defines an isolated virtual testbed named `soc-sandbox` and presents a dual-adapter network architecture.

## Hosts

| Host | IP | Function |
|---|---|---|
| KDC1 / Domain Controller | `192.168.10.10` | Domain services / authentication |
| Windows workstation | `192.168.10.20` | Client endpoint |
| Kali Linux | `192.168.10.30` | Simulated red-team source |
| SIEM host | `192.168.56.1` | Splunk |

## Expected services

- DNS: `53`
- Kerberos: `88`
- LDAP: `389/TCP`
- SMB: `445/TCP`
- MSRPC: `135/TCP`
- Splunk ingestion: `9997/TCP`

## Baseline objective

The baseline establishes what normal domain and SIEM communication should look like. The report describes workstations requesting domain name resolution, obtaining authentication tickets, receiving Group Policy updates over SMB, and forwarding logs to Splunk.

## Evidence

The visual baseline is available at [`../evidence/01-baseline-topology.png`](../evidence/01-baseline-topology.png).
