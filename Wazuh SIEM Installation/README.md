# Hands-On Wazuh – Wazuh SIEM Deployment and Agent Installation on Windows & Ubuntu

In this guide, I have deployed Wazuh SIEM using the pre-built Virtual Machine (OVA) format.

I have installed Wazuh Agents on Windows & Ubuntu for monitoring purpose like it is in SOC environment. This is a step-by-step comprehensive and beginner friendly guide.


## Installing Wazuh in Virtual Machine:
- Go to Wazuh official website “Wazuh.com”.
- Click on Documentation and go to Installation alternatives.
- You can install it in a Virtual Machine by clicking on Virtual Machine and then install
- Download the ova file by clicking on virtual appliance (OVA).
- Open the VMware > Click on file > Open
- Power on the VM.
 
It will open the Wazuh virtual machine.

- The default login credentials are:
  - **Username:** Wazuh-user
  - **Password:** Wazuh
    
*It will look like this after login*
 
- Find the IP address of VM by typing this command:
  - ip a
 
## Accessing Wazuh dashboard:
We can access the Wazuh dashboard from the web interface by using the following credentials:

- **URL:** https://<wazuh_server_ip> (write your machine ip here)
  - If pop-up window appears, click on advance and accept risk and continue.
    
- **user:** admin
- **password:** admin
 
 
## Installing Wazuh Agents:
**Installing Windows Agent:**

- Click on Deploy new agent
- Select windows > Write the Wazuh machine IP address in server address.

In my case it’s 192.168.149.110

- Follow the steps and run the commands given there in windows powershell to download, install and start the agent in windows machine.

After running these commands in windows powershell, we can see our windows agent on dashboard.
 
### Now, we will install Wazuh agent in Kali/Ubuntu machine.
- Click on Deploy new agent
- Select the Linux > DEB amd64 (you can choose it according to your machine architecture)
  
*You can check architecture of your machine by running command in terminal:
**uname -m***
 
- Run these commands on your Kali/Ubuntu machine to install Wazuh agent
 

 

 

We can see both of our agents are active.
PS: I have switched to another network so the IP of the server is changed.


# Open this [pdf](https://github.com/Zayan9484/Cybersecurity-Labs/blob/main/Wazuh%20SIEM%20Installation/Installing%20Wazuh%20in%20Virtual%20Machine.pdf) for detailed notes with screenshots

