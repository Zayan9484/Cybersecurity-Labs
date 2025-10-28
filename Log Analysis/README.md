
# Log Analysis
Log is an event or an action that is happened. 

The purpose of log is to give us information about the event – what has happened, when it happened, why it happened and how it happened.

e.g., Security log will tell you who logged in into OS, whether the login was successful or not and the time when it happened.

All we need is Windows operating system to understand logs. There is a tool in windows called Event Viewer through which we can see logs. It’s where all logs are stored.

### Ways to open Event Viewer:
- Search event viewer in start menu

OR

- Open cmd > Type eventvwr	(same command works in Run bar)

Suppose our windows get corrupted and we don’t have GUI access. So, it’s better to know how to open it using command prompt.
 
We have **Windows Log, Application and Service Logs**
 
- The left box is known as Navigation pane
- The middle box in Event Viewer is called Details pane where all the details are seen.
- The right box is called Action pane
 

## Logs Categories:
**Application:** Records problems or messages from apps you use (like Chrome, Notepad, or Office etc)

**System:** Shows issues or updates related to Windows itself (like starting/stopping services).

Suppose we download Splunk – when we start is, its log will be saved as service was started/closed.

**Security:** Tracks logins, logouts, and security-related actions (like failed passwords or new users).

**Forwarded Events:** Collects logs from other computers if one is set up to receive them.

Usually in an organization, one server is set up to receive logs from all other computers on the network. All these logs will come in forwarded events.

**Setup:** Keeps tracks of things that happen when Windows is being installed or updated.

**PowerShell Logs:** Shows what scripts or commands were run using PowerShell (good for spotting suspicious activity).

These are important because attackers normally compromise powershell to execute malicious commands.

**Sysmon (if enabled):** Gives detailed behind-the-scenes info like program launches, file changes or internet access – like CCTV for your computer.

It is a detailed version of your logs. Sysmon is not enabled by default. We have to enable it ourselves.

All the events happened in windows have Event_id such as login success, login failure, user create or delete. All of these events have specific ***event-id***.

**e.g., 4624 is event-id for successful login**
 

We can save the specific event. 

Click on the ***event > Click on actions tab > Save***
 
Extension of Windows event file is ***.evtx***

We can save events file in these formats:
 
We can find these logs navigation pane or all about this EventViewer in this path:

***C:/ > Windows > System32 > winevt > logs***
 
Each event has its own level id in Windows. It shows the severity of the event.
 
ID **60**, **70** and **90** are reserved for software developers to use.

Windows has its own Custom Views called Administrative Events.
 

It’s like you can create your own dashboard like which specific category logs you want to see. Like if I want to view the event logon success only, it will create a custom view for that log only.

## Benefits of Custom Views:
- Easy to understand
- Rather than forwarding all of the logs, companies can create specific custom views and forward that to SIEM tool

Administrative Events tab is a combination of all 5 tabs of Windows Log. But it will show only the view of Error, Critical and Warning events.

## How to create your own Custom View?
Click on ***Create Custom View > Select the level of Events you want there > Select Event log types which you want to see >*** If you want all event ids or only specific (if you want specific events to be shown there write their ids separating with comma or you can define a range like 4264-4625 > Select keywords
  
- Click OK
- Give it a name > OK

# Sysmon | System Monitor:
- Windows logs are like the regular CCTV, they show who came in and out. But attackers are smart they sneak in and hide their actions.
- Sysmon is like a high-definition security camera, it shows what program ran, what files were created, what network connection was made, every detail that regular Windows logs miss.
- Sysmon is powerful, but it can be noisy if we don't tell it what to watch and what to ignore. That's where the config file comes in.
- Think of it like setting up your CCTV rules you can say: only record people wearing red, ignore cats, focus on the door not the window.
- We do the same here, we tell Sysmon - watch for PowerShell, watch for rundll32, ignore Notepad or another legitimate/known Program.

It is not enabled by default. We can download it or enable it.

All of the Sysmon rules are in XML format.


## How to enable Sysmon?
Go to the web > Search Sysmon download > Download from the official Microsoft site
 

There is a file on GitHub which have pre-defined rules for Sysmon in XML format. We can download that too if we don’t want to make our own file in XML.
 
After unzipping the file, paste the rule file in the Sysmon directory which we’ve downloaded from Microsoft site, so we don’t have to give the path.

## Sysmon Event IDs:
 
You have to remember Sysmon Event ids. It’s very important in terms of interview and in general as well. If you know the id’s, you can configure Sysmon file accordingly and as per your need.

***Sysmon is the goldmine in Threat Hunting.***

### To set up or install Sysmon:
- Run cmd as an administrator
- Follow the guide given on GitHub (from where you download config file)

If you open Event Viewer, under Application and Services Logs > Windows, you can find Sysmon logs because Sysmon itself is an application and process.

# Open this [pdf](https://github.com/Zayan9484/Cybersecurity-Labs/blob/main/Log%20Analysis/Log%20Analysis.pdf) for detailed notes with screenshots of steps

