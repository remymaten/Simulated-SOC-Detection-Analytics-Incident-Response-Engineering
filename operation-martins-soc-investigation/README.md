# OPERATION MARTINS
## Simulated Breach Investigation & SOC Defense Architecture

![Project](https://img.shields.io/badge/Project-SOC%20Investigation-blue)
![SIEM](https://img.shields.io/badge/SIEM-Splunk-orange)
![Network%20Analysis](https://img.shields.io/badge/Network-Wireshark-blue)
![Environment](https://img.shields.io/badge/Environment-Isolated%20Lab-lightgrey)

> **Cybersecurity portfolio project by Martins Jesurobo**

## Overview

**Operation Martins** is a simulated breach investigation and SOC defense project performed inside an isolated virtual testbed (`soc-sandbox`).

The project demonstrates an end-to-end defensive workflow:

1. Establish a network baseline
2. Inspect network traffic
3. Build a log-ingestion/SIEM pipeline
4. Engineer detection analytics and alerts
5. Conduct threat hunting
6. Identify Indicators of Compromise (IoCs)
7. Build an incident timeline
8. Execute incident response and recovery

The submitted project report identifies the target environment as **MartinsPay Technologies / Martins Logistics** and names Martins Jesurobo as the lead security investigator / defense presenter.

## Lab Architecture

| Asset | Address | Role |
|---|---|---|
| Domain Controller (KDC1) | `192.168.10.10` | Domain services / authentication |
| Windows workstation | `192.168.10.20` | Client endpoint |
| Kali Linux | `192.168.10.30` | Simulated red-team source |
| SIEM host | `192.168.56.1` | Splunk ingestion |

The report describes a dual-adapter architecture with a host-only path used for SIEM ingestion.

## Network & Traffic Analysis

The baseline identifies expected services including:

- DNS `53`
- Kerberos `88`
- LDAP `389/TCP`
- SMB `445/TCP`
- MSRPC `135/TCP`
- Splunk ingestion `9997/TCP`

Normal traffic is described as workstation/domain-controller authentication, name resolution, Group Policy activity, and log forwarding to Splunk.

See [`network/baseline-topology.png`](network/baseline-topology.png) and [`wireshark/traffic-analysis.md`](wireshark/traffic-analysis.md).

## SIEM & Detection

The project uses Splunk to ingest Windows and Linux telemetry.

A key investigation queried Windows **EventCode 4625** to isolate repeated failed logon activity. The report states that the source was traced to the Kali host at `192.168.10.30`.

The project also uses EventCode 4624 during validation and checks Event IDs 7045 and 4720 when investigating possible persistence.

See [`splunk/detection-and-alerting.md`](splunk/detection-and-alerting.md).

## Threat Hunting & IoCs

The evidence demonstrates repeated authentication failures targeting the environment. The report's SIEM dashboard records:

- **12,500** total failed logins in the displayed dashboard view
- A prominent attacking source of `192.168.10.30`
- Targeted activity against the Domain Controller

See [`iocs/ioc-matrix.md`](iocs/ioc-matrix.md).

## Incident Response

The response follows four phases:

### 1. Identification & Detection
Repeated failed authentication activity was identified through Splunk.

### 2. Containment
The reported response blocked the Kali source IP at the network boundary and disabled the targeted Administrator account in Active Directory.

### 3. Eradication
Active SMB connections were terminated. Splunk and Event Viewer were checked for successful authentication, rogue services, and unexpected user creation.

### 4. Recovery
The affected account was reset, re-enabled, and an Account Lockout Policy was enforced through Group Policy.

See [`incident-response/incident-response-report.md`](incident-response/incident-response-report.md).

## Evidence

The repository includes rendered evidence from the submitted project report, including:

- Baseline topology
- Traffic-analysis evidence
- SIEM/log-ingestion pipeline
- Threat-hunting evidence
- Detection alert
- IoC dashboard
- Incident-response workflow

The complete original report is available in [`docs/Operation-Martins-Project-Report.pdf`](docs/Operation-Martins-Project-Report.pdf).

## Security & Scope

This repository documents a **simulated, isolated lab environment**. The material is intended for authorized cybersecurity training, detection engineering, SOC analysis, and defensive incident-response practice.

No real credentials are published in this repository. Any credential-like values visible in source screenshots should be treated as lab-only artifacts and must not be reused outside the authorized test environment.

## Author

**Martins Jesurobo**

Cybersecurity | SOC | GRC | Security Operations
