# Evidence Index

This folder contains the visual evidence rendered from the submitted **Operation Martins** project report. Credential-like lab values visible in the source evidence have been redacted for public-portfolio hygiene. Each image maps to a documented project phase; no unrelated screenshots have been added.

| Evidence | Report page | What it supports |
|---|---:|---|
| `01-baseline-topology.png` | 2 | Dual-adapter architecture and documented host/IP layout |
| `02-traffic-analysis.png` | 3 | Traffic-analysis baseline, expected protocols and ports |
| `03-splunk-log-ingestion-pipeline.png` | 4 | Log-ingestion/SIEM pipeline and simulated attack workflow |
| `04-threat-hunting.png` | 5 | SMB/threat-hunting evidence against the Domain Controller |
| `05-detection-alert.png` | 6 | Splunk EventCode 4625 detection evidence |
| `06-ioc-dashboard.png` | 7 | IoC dashboard, failed-logon metrics and source IP |
| `07-incident-response.png` | 8 | Identification, containment, eradication and recovery workflow |

## Evidence limitations

The submitted report provides screenshots and a final written response narrative. It does not include a raw PCAP, Splunk export, dashboard definition, or full VM configuration export. Those artifacts are therefore not represented as available in this repository.

## Public-repository hygiene

The repository documentation intentionally does not reproduce credential-like values visible in lab screenshots. Before making the repository public, review every image for any accidental real secret or personal information.
