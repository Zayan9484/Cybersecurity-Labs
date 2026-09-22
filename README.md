# Cybersecurity Labs

Hands-on cybersecurity labs from my training and self-study, reorganized as portfolio documentation.

These are learning labs completed in controlled environments. They show what I configured, tested, observed, and documented; they are not presented as production deployments.

## Labs

| Lab | Focus | Tools / Technologies |
|---|---|---|
| [Wazuh SIEM Deployment](./01-wazuh-siem-deployment/) | Deploying Wazuh and enrolling endpoints | Wazuh, VMware, Windows, Ubuntu/Kali |
| [Suricata IDS + Wazuh](./02-suricata-wazuh-intrusion-detection/) | Network IDS deployment and SIEM integration | Suricata, Wazuh, Ubuntu, Nmap |
| [Wazuh File Integrity Monitoring](./03-wazuh-file-integrity-monitoring/) | Detecting file creation/modification activity | Wazuh FIM, Windows, Ubuntu |
| [Windows Log Analysis & Sysmon](./04-windows-log-analysis-sysmon/) | Understanding Windows security telemetry | Event Viewer, Windows Security Logs, Sysmon |
| [OSINT & Packet Analysis](./05-osint-packet-analysis/) | Public-source reconnaissance and traffic inspection | Wireshark, Subfinder, Shodan, Kali Linux |
| [Malware Analysis Lab](./06-malware-analysis/) | Static and dynamic malware-analysis workflow | FlareVM, PEStudio, FLOSS, Regshot, FakeNet |

## More Advanced Detection Engineering Work

My later [SOC Detection Engineering project](https://github.com/Zayan9484/SOC-Detection-Engineering) builds on these foundations with custom detections, correlation rules, investigation notes, MITRE ATT&CK mapping, and end-to-end validation.

## Repository Structure

Each lab keeps the original notes for evidence, while the main README explains the objective, environment, implementation, validation, and limitations in a cleaner format.
