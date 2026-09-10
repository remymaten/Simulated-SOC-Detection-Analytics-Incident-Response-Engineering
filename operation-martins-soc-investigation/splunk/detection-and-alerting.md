# Splunk Detection & Alert Engineering

## Telemetry

The lab forwards Windows and Linux logs into Splunk.

## Primary investigation signal

The report states that the investigation queried:

```text
index=* EventCode=4625
```

EventCode `4625` was used to isolate failed logon attempts. The activity was traced to the Kali host at `192.168.10.30`.

## Validation

The response process also checked EventCode `4624`, Event `7045`, and Event `4720` to investigate successful access and potential persistence.

## Evidence

![Detection Alert](../evidence/05-detection-alert.png)
