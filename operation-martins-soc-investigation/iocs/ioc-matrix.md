# Indicators of Compromise (IoCs) & Evidence Matrix

| Indicator | Value | Evidence / Significance |
|---|---|---|
| Suspicious source IP | `192.168.10.30` | Identified as the source of repeated failed authentication attempts |
| Windows Event ID | `4625` | Failed logon activity used for detection |
| Validation Event ID | `4624` | Used to check for successful authentication |
| Service-install Event ID | `7045` | Checked for rogue/persistence services |
| User-creation Event ID | `4720` | Checked for unexpected account creation |
| Target host | `192.168.10.10` / KDC1 | Domain Controller targeted by the activity |
| Dashboard metric | `12,500` | Total failed logins shown in the report's dashboard view |

## Interpretation

The IoCs are strongest when correlated rather than viewed individually. The source IP, failed-logon events, targeted host, and subsequent validation checks together support the investigation narrative.

![IoC Dashboard](ioc-dashboard-evidence.png)
