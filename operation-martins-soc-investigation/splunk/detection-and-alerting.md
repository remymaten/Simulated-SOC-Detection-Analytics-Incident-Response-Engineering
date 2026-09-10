# Splunk Detection & Alert Engineering

## Telemetry

The lab forwards Windows and Linux logs into Splunk.

## Primary investigation signal

The report states that the investigation queried:

`index=* EventCode=4625`

EventCode 4625 was used to isolate failed logon attempts.

## Correlation

The failed authentication activity was traced to the Kali host:

`192.168.10.30`

The report also describes validation using EventCode 4624 and checks for:

- Event 7045 — unexpected service installation
- Event 4720 — unexpected user creation

## Detection objective

The goal is to turn repeated authentication failures into actionable SOC telemetry, correlate the source host, validate whether successful access occurred, and investigate possible persistence.

![Detection Alert](detection-alert-evidence.png)
