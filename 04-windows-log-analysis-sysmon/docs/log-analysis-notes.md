# Log Analysis Notes

## Windows Event Viewer

The lab covered the main Windows log categories and how Event Viewer can be opened both through the GUI and from the command line.

A key focus was the **Security** log, where authentication and other security-relevant actions are recorded.

## Event IDs

Windows events are identified by Event IDs. For example, Event ID **4624** represents a successful logon.

Understanding Event IDs is useful when building filters, SIEM searches, and detection logic.

## Custom Views

Custom Views were created to narrow large event sets to particular severities, log sources, or Event IDs.

## Sysmon

Sysmon was studied as an additional telemetry source that can record richer process, file, and network activity than default Windows logging.

This foundation was later applied in my separate SOC Detection Engineering project, where Sysmon process telemetry was collected and investigated through Wazuh.
