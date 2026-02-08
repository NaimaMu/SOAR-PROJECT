#  User Login Anomaly Detection

## Overview
In this project, I am building a simple SOAR automation to detect unusual user login activity. I am using a homelab environment to show how security alerts move from detection to automated response.

## Diagram for this Project
This shows the overall flow of my SOAR project and what I am trying to achieve. I am using Windows 11 to generate user login events, which are sent to the ELK Stack for analysis. When the ELK Stack detects suspicious login activity, it sends an alert to Shuffle, which runs an automation and sends a notification to Discord so I can review the alert and take the proper action.
<img width="812" height="595" alt="image" src="https://github.com/user-attachments/assets/e031ebfe-85de-4ccd-a907-d02a68334bf4" />

## Tools I used
- Shuffle(SOAR)
- ELKStack(SIEM)
- windows 11
- Discord(Notification)
- Virtualbox(HOMELAB)

## Explanation Of Each Tool
### ELKStack
- The ELK Stack collects and analyzes login logs from my Windows 11 system. It is used to monitor user login activity and detect suspicious behavior. Dashboards and detection rules help visualize where login activity is coming from and identify potential security issues.

### Shuffle
- I am using Shuffle as my SOAR platform.
- Shuffle receives alerts from the ELK Stack when suspicious activity is detected.
- Shuffle runs an automation and sends a notification to Discord so I can review the alert.
- 
### Windows 11
- Windows 11 is the host system that generates user login events. It has the ELK agent installed, which allows login activity to be sent to the ELK Stack for monitoring and analysis.
 ## Goal is:
   - To learn and practice basic SOAR automation
   - to understand how security alerts move from detection to automated response
   - To gain hands-on experience using SEIM and SOAR tools in my homelab environment
