#  SOAR Project

## Overview
In this project, I am building a simple SOAR automation to detect unusual user login activity. I am using a homelab environment to show how security alerts move from detection to automated response.

## Diagram for this Project
This shows the overall flow of my SOAR project and what I am trying to achieve. I am using Windows 11 to generate user login events, which are sent to the ELK Stack for analysis. When the ELK Stack detects suspicious login activity, it sends an alert to Shuffle, which runs an automation and sends a notification to Discord so I can review the alert and take the proper action.

<img width="795" height="533" alt="image" src="https://github.com/user-attachments/assets/2ddbaac6-6a51-45e9-9c8d-d5bf6e82d490" />

## Tools I used
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
