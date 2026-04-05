#  SOAR Project

## Overview
In this project, I am building a simple SOAR automation to detect unusual user login activity. I am using a homelab environment to show how security alerts move from detection to automated response.

## Diagram for this Project
This diagram shows how my SOAR(Security Orchestration Automation and Response) project works. Windows 11 generates login events, and the ELK Stack checks for failed login attempts. when an alert is triggered, a python script frowards it to Shuffle, which automates the process and sends a notification to Discord so I can review it in real time. This helps me practcie responding to security alerts automatically in my homelab. 
<img width="978" height="681" alt="image" src="https://github.com/user-attachments/assets/88ca67f7-26a6-4e6e-a503-ecf0b026d720" />

## What I use In this Project
- Shuffle(SOAR)
- ELK Stack(SIEM)
- windows 11
- Python(forwarding ELK logs to Shuffle)
- Discord(Notification)
- Virtualbox(HOMELAB)

## Explanation Of Each Tool
### ELKStack
- The ELK Stack collects and analyzes login logs from my Windows 11 system. It is used to monitor user login activity and detect suspicious behavior.

### Python Script
  - Baisc Python script thta forwars ELK logs to Shuffle for failed login attempts.
  - The script is set up to run automatically using "Task Scheduler" on my windows 11 whenever I log in.
    
### Shuffle
- I am using Shuffle as my SOAR platform.
- Shuffle receives alerts from the ELK Stack when suspicious activity is detected.
- Shuffle runs an automation and sends a notification to Discord so I can review the alert.

### Windows 11
- Windows 11 is the host system that generates user login events. It has the ELK agent installed, which allows login activity to be sent to the ELK Stack for monitoring and
analysis.

 ### Goal is:
   - To learn and practice basic SOAR automation
   - Understand how security alerts move from detection to automated response.
   - To gain hands-on experience using SEIM and SOAR tools in my homelab environment
