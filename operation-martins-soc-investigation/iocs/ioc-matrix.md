# Indicators of Compromise (IoCs) & Evidence Matrix

| Indicator | Value | Evidence / Significance |
|---|---|---|
| Suspicious source IP | `192.168.10.30` | Identified as the source of repeated failed authentication attempts |
| Windows Event ID | `4625` | Failed logon activity used for detection |
| Validation Event ID | `4624` | Used to check for successful authentication |
| Service-install Event ID | `7045` | Checked for rogue/persistence services |
| User-creation Event ID | `4720` | Checked for unexpected account creation |
| Target host | `192.168.10.10` / KDC1 | Domain Controller targeted by the activity |
| Dashboard headline | `12,500` | Failed-logon metric shown in the report dashboard |
| Dashboard source row | `79,665` | Failed-attempt value shown for source `192.168.10.30` in the report's table |

## Interpretation

The two dashboard numbers are preserved as separate displayed metrics. They should not be combined or treated as the same population without the underlying Splunk search/export.

![IoC Dashboard](../evidence/06-ioc-dashboard.png)
