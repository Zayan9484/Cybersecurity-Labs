# Implementation

## Suricata Setup

Suricata was installed on the Ubuntu endpoint and configured to monitor the lab network interface.

The lab configuration included:
- a defined `HOME_NET`;
- the active AF_PACKET interface;
- the Suricata rules directory; and
- the Emerging Threats rules available at the time.

## Wazuh Integration

Suricata writes structured security events to `eve.json`.

The Ubuntu Wazuh agent configuration was updated so Wazuh would read this JSON log source. After the configuration change, the services were restarted.

## Controlled Test

An Nmap scan was generated from another lab machine against the monitored Ubuntu endpoint.

The resulting events were reviewed in Wazuh Threat Hunting and in Suricata's local logs.
