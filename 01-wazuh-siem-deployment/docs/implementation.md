# Implementation

## 1. Deploy the Wazuh Appliance

The Wazuh OVA was imported into VMware and powered on as the central SIEM appliance.

After login, the server IP address was identified from the Linux interface so the dashboard and agents could reach the manager.

## 2. Access the Dashboard

The Wazuh dashboard was opened through the server IP over HTTPS.

The browser certificate warning was expected in the isolated lab because the appliance used its default/self-signed setup.

## 3. Enroll the Windows Endpoint

The Wazuh dashboard's agent-deployment workflow was used to generate the Windows installation steps. The manager address was supplied, the agent was installed, and its service was started.

## 4. Enroll the Linux Endpoint

The same workflow was repeated for a Linux endpoint using the appropriate package architecture.

## 5. Verify Connectivity

The dashboard was checked after deployment to confirm that the agents were reporting to the Wazuh manager.
