# Wazuh File Integrity Monitoring

## Overview

This lab tested Wazuh File Integrity Monitoring (FIM) on both Ubuntu and Windows endpoints.

The goal was to define test directories, create or modify files inside them, and verify that Wazuh recorded the resulting file-integrity events.

## Ubuntu Implementation

Create the test directory and file:

```bash
sudo mkdir -p /opt/fim-demo
echo "start" | sudo tee /opt/fim-demo/watchme.txt
```

Open the Wazuh agent configuration:

```bash
sudo nano /var/ossec/etc/ossec.conf
```

Add the monitored directory inside the `<syscheck>` block:

```xml
<directories realtime="yes" report_changes="yes">/opt/fim-demo</directories>
```



![Ubuntu syscheck configuration monitoring /opt/fim-demo](./screenshots/02-ubuntu-fim-directory-config.png)

Restart the agent:

```bash
sudo systemctl restart wazuh-agent
```

Generate a file change:

```bash
echo "changed $(date)" | sudo tee -a /opt/fim-demo/watchme.txt
```

The resulting event was then reviewed under Wazuh File Integrity Monitoring.



![Ubuntu file modification detected in Wazuh](./screenshots/03-ubuntu-fim-event.png)


![Ubuntu integrity-change event details](./screenshots/04-ubuntu-fim-event-details.png)

## Windows Implementation

The Windows test path was:

```text
C:\fim-demo\watchme.txt
```

The Wazuh agent configuration included:

```xml
<directories realtime="yes" report_changes="yes">C:\fim-demo</directories>
```



![Windows syscheck configuration monitoring C:\fim-demo](./screenshots/05-windows-fim-directory-config.png)

Restart the Wazuh service from an elevated PowerShell session:

```powershell
Restart-Service -Name WazuhSvc
```

After modifying the test file, I verified the resulting event in the Wazuh dashboard.



![Windows file modification detected in Wazuh](./screenshots/07-windows-fim-event.png)


![Windows integrity-change event details](./screenshots/08-windows-fim-event-details.png)

## What I Validated

- monitored file path;
- file modification event;
- event timestamp;
- change details reported by Wazuh; and
- FIM operation on both Linux and Windows endpoints.

## Evidence & Documentation

- [All screenshots](./screenshots/README.md)

- [Configuration notes](./docs/configuration.md)
- [Validation notes](./docs/validation.md)
- [Original lab notes with screenshots](./docs/original-lab-notes.pdf)

## Status

**Completed** - file changes on both Windows and Ubuntu were detected in the lab.

