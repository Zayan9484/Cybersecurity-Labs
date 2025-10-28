### In this LAB, I have installed Suricata IDS on Ubuntu server to detect and visualize network-based threats in real time. This is a step-by-step comprehensive and beginner friendly guide.


# Installing Suricata IDS on Ubuntu Server:
The goal of setting up a Suricata home-lab is to gain practical experience in deploying and configuring an Intrusion Detection System (IDS) for network security monitoring. Suricata is an open-source IDS capable of detecting and preventing various network-based threats. This home-lab provides individuals with hands-on experience in setting up, configuring, and utilizing Suricata to enhance network security.

### What we’ll do?
We will set up a Suricata IDS and install it on our Ubuntu server. Then we will launch some network probes or network-based attacks to see if Suricata IDS is able to detect that or not.

## Steps to configure & install Suricata:
You can find complete commands and guide here:

*https://github.com/0xrajneesh/Suricata-IDS-Home-Lab/blob/main/installing-suricata.md*

1.	Install Suricata on the Ubuntu endpoint.

        - sudo add-apt-repository ppa:oisf/suricata-stable
  	    - sudo apt-get update
  	    - sudo apt-get install suricata -y
 
We can confirm if it is installed or not by navigating to ***/etc/suricata***
 
2.	Download and extract the Emerging Threats Suricata ruleset:

        - cd /tmp/ && curl -LO https://rules.emergingthreats.net/open/suricata-6.0.8/emerging.rules.tar.gz
        - sudo tar -xvzf emerging.rules.tar.gz && sudo mv rules/*.rules /etc/suricata/rules/
        - sudo chmod 640 /etc/suricata/rules/*.rules
 
After installing the rules, we can confirm if they are installed or not
 
3.	Modify Suricata settings in the /etc/suricata/suricata.yaml file and set the following variables:
 
         HOME_NET: "[your ubuntu machine IP]"
        EXTERNAL_NET: "any"
        default-rule-path: /etc/suricata/rules
        rule-files:
        - "*.rules"
 
 

# Global stats configuration
    stats:
    enabled: Yes
 

# Linux high speed capture support
    af-packet:
    - interface: ens33  (you can check your network interface by running ip a or ifconfig command)
 
 - Save the file

4.	Restart the Suricata service:

         sudo systemctl restart suricata
 
- Now, edit the **ossec.conf** which is in ***/var/ossec/etc/ossec.conf***
- Go to the bottom of the file and add this block before ***</ossec_config>***
- Whatever log file we need to monitor, we have to add it here. Save and exit

We have added this block so that Wazuh can read Suricata’s security alerts from eve.json, because it’s the file where Suricata stores all structured alert data.

Why this line is needed?

### Purpose:
It tells Wazuh Agent → “Hey, also read and analyze this log file from Suricata.”

Without this line, Wazuh does not know Suricata’s logs exist, so no alerts would be visible in Wazuh.

### Why specifically eve.json:
- Suricata produces different log files (like stats.log, fast.log, eve.json etc.).
- Out of these, eve.json is the main detailed log file that contains all Suricata alerts, events, and metadata in JSON format.
- Other files (like fast.log) are smaller or only summaries. But eve.json is standard and recommended because Wazuh already knows how to parse Suricata JSON events.
- Restart the agent to take effect of this change
 
To see logs in real time in CLI, we can use this command:

    tail -f filename
 

### Nmap Scan:
Now, we will send some probes to our Ubuntu machine and see if we can see any alerts on Wazuh dashboard.
- Go to your kali machine
- Initiate Nmap scan (use your ubuntu machine IP here)
  
- Now go to the **Wazuh dashboard > Ubuntu agent > Threat Hunting > Events**
 

We can see all the alerts here like:

***Source IP, Agent IP, Rule Id, Rule Group***, which ***ports*** were scanned, ***location of the logs*** and many more.

We can also these logs in our Ubuntu machine by using the 

    tail -f eve.json command

For detailed steps with screenshot, open this [pdf](https://github.com/Zayan9484/Cybersecurity-Labs/blob/main/Intrusion%20Detection%20in%20Wazuh/Suricata%20IDS%20on%20Ubuntu.pdf)

