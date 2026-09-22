# Configuration Notes

The lab used Wazuh's `syscheck` feature to monitor dedicated test directories.

Ubuntu example:

```xml
<directories realtime="yes" report_changes="yes">/opt/fim-demo</directories>
```

Windows example:

```xml
<directories realtime="yes" report_changes="yes">C:\fim-demo</directories>
```

After changing the agent configuration, the Wazuh agent/service was restarted before testing file changes.
