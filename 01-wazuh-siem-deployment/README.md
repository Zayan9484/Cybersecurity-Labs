# Wazuh SIEM Deployment & Agent Enrollment

## Overview

This lab documents my initial Wazuh deployment in a VMware environment. I imported the Wazuh virtual appliance, accessed the dashboard, enrolled Windows and Linux endpoints, and verified that the agents were connected.

## What I Implemented

- Imported and powered on the Wazuh OVA in VMware.
- Identified the Wazuh server IP and accessed the web dashboard.
- Deployed a Wazuh agent to a Windows endpoint.
- Deployed a Wazuh agent to a Linux endpoint.
- Verified that the enrolled endpoints appeared as active agents.

## Architecture

```text
Windows Endpoint ----\
                      \
                       > Wazuh Manager / Dashboard
                      /
Linux Endpoint ------/
        |
     VMware Lab
```

## Concepts Practiced

- SIEM deployment
- Endpoint agent enrollment
- Centralized monitoring
- Windows and Linux endpoint onboarding
- Basic troubleshooting of agent/server connectivity

## Evidence

- [Implementation notes](./docs/implementation.md)
- [Validation notes](./docs/validation.md)
- [Screenshot evidence](./screenshots/README.md)
- [Original lab notes](./docs/original-lab-notes.pdf)

## Security Note

The original lab notes contain default appliance credentials used in the training environment. Default credentials should be changed immediately in any real deployment.

## Status

**Completed** — Wazuh was deployed and both endpoint agents were verified as active in the lab.
