# Suricata IDS + Wazuh Integration

## Overview

This lab focused on deploying Suricata on an Ubuntu endpoint, forwarding Suricata alert data into Wazuh, and generating controlled network activity to verify that alerts were visible in the SIEM.

## Detection Flow

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

## Key Commands Used

Install Suricata:

```bash
sudo add-apt-repository ppa:oisf/suricata-stable
sudo apt-get update
sudo apt-get install suricata -y
```

Download the Emerging Threats ruleset used in the original lab:

```bash
cd /tmp/
curl -LO https://rules.emergingthreats.net/open/suricata-6.0.8/emerging.rules.tar.gz
sudo tar -xvzf emerging.rules.tar.gz
sudo mv rules/*.rules /etc/suricata/rules/
sudo chmod 640 /etc/suricata/rules/*.rules
```

Restart Suricata after configuration changes:

```bash
sudo systemctl restart suricata
```

Watch Suricata events in real time:

```bash
tail -f /var/log/suricata/eve.json
```

Generate controlled scan activity from the lab attacker machine:

```bash
nmap <ubuntu-target-ip>
```

## Wazuh Log Ingestion

Wazuh was configured to read Suricata's structured `eve.json` output:

```xml
<localfile>
  <log_format>json</log_format>
  <location>/var/log/suricata/eve.json</location>
</localfile>
```

## Suricata Configuration Areas

The lab configuration included:

```yaml
HOME_NET: "[<ubuntu-ip>]"
EXTERNAL_NET: "any"

default-rule-path: /etc/suricata/rules

rule-files:
  - "*.rules"
```

The active AF_PACKET interface was also configured for the Ubuntu endpoint.

## Validation

After the scan was generated, I reviewed Suricata/Wazuh events for details such as:

- source IP;
- destination/target information;
- Suricata rule ID;
- rule group;
- scanned ports; and
- log source.

## Evidence & Documentation

- [Implementation notes](./docs/implementation.md)
- [Validation notes](./docs/validation.md)
- [Original lab notes with screenshots](./docs/original-lab-notes.pdf)

## Historical Note

The ruleset/version above reflects the original lab. A current deployment should use supported Suricata packages and current rules rather than copying the old version number blindly.

## Status

**Completed** - Suricata alerts were ingested and reviewed through Wazuh during controlled testing.
