# Suricata IDS + Wazuh Integration

## Overview

This lab focused on deploying Suricata on an Ubuntu endpoint, forwarding Suricata alert data into Wazuh, and generating controlled network activity to verify that alerts were visible in the SIEM.

## What I Implemented

- Installed Suricata on Ubuntu.
- Added the Emerging Threats ruleset used in the lab.
- Configured `HOME_NET`, the active capture interface, and the Suricata rule path.
- Configured Wazuh to read Suricata's `eve.json` output.
- Restarted the relevant services after configuration changes.
- Generated an Nmap scan from the lab environment.
- Verified Suricata/Wazuh events containing source, rule, port, and log-location details.

## Data Flow

```text
Controlled Nmap Scan
        |
        v
Suricata on Ubuntu
        |
      eve.json
        |
        v
Wazuh Agent
        |
        v
Wazuh Dashboard / Threat Hunting
```

## Concepts Practiced

- Network IDS deployment
- Rule-based network detection
- JSON security telemetry
- SIEM log ingestion
- Alert validation
- Basic network-event investigation

## Evidence

- [Implementation notes](./docs/implementation.md)
- [Validation notes](./docs/validation.md)
- [Original lab notes](./docs/original-lab-notes.pdf)

## Historical Note

The original lab used the Suricata/rules versions current at the time. Current deployments should use supported packages and current rules rather than copying old version numbers blindly.

## Status

**Completed** — Suricata alerts were ingested and reviewed through Wazuh during controlled testing.
