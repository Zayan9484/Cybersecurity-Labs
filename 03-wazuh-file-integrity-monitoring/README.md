# Wazuh File Integrity Monitoring

## Overview

This lab tested Wazuh File Integrity Monitoring (FIM) on both Ubuntu and Windows endpoints.

The goal was to define test directories, create or modify files inside them, and verify that Wazuh recorded the resulting file-integrity events.

## What I Implemented

### Ubuntu
- Created `/opt/fim-demo` and a test file.
- Added the directory to the Wazuh agent's `syscheck` configuration with real-time monitoring and change reporting.
- Restarted the Wazuh agent.
- Modified the monitored file and reviewed the resulting FIM event.

### Windows
- Created `C:\fim-demo\watchme.txt`.
- Added the directory to the Windows Wazuh agent's FIM configuration.
- Restarted the Wazuh service.
- Modified the file and reviewed the event in the Wazuh dashboard.

## Concepts Practiced

- File Integrity Monitoring
- Wazuh `syscheck`
- Real-time file monitoring
- Windows and Linux endpoint configuration
- Event validation

## Evidence

- [Configuration notes](./docs/configuration.md)
- [Validation notes](./docs/validation.md)
- [Original lab notes](./docs/original-lab-notes.pdf)

## Status

**Completed** — file changes on both Windows and Ubuntu were detected in the lab.
