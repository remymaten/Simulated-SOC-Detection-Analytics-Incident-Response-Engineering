# Threat Hunt Findings

## Investigation focus

The threat-hunting phase examined authentication and SMB-related activity associated with the simulated breach.

## Key finding

The evidence identifies the Kali host at `192.168.10.30` as the suspicious source associated with repeated authentication activity against the Domain Controller.

## Hunt progression

The investigation moved from network observation to centralized authentication telemetry, source correlation, validation for successful access, and persistence checks.

![Threat Hunt Evidence](../evidence/04-threat-hunting.png)
