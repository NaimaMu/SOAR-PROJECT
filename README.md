#  User Login Anomaly Detection

## Overview
In this project, I created a simple SOAR automation to detect unusual user login activity on a Windows 11 system. The project focuses on identifying suspicious login behavior and demonstrating how security alerts can move from detection in a SIEM to automated response using a SOAR platform in a homelab environment.
## Objective
The objective of this project is to detect suspicious login activity on a Windows 11 system and automate a response using Shuffle. This project helps demonstrate how security alerts flow from detection to response.
---

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
Shuffle receives alerts from the ELK Stack and runs a simple automation workflow. When suspicious activity is detected, Shuffle flags the event and sends a notification to the analyst (me) through Discord so I can review the alert and take the appropriate action.

### Windows 11
- Windows 11 is the host system that generates user login events. It has the ELK agent installed, which allows login activity to be sent to the ELK Stack for monitoring and analysis.
 ## Goal is:
   - To learn and practice basic SOAR automation
   - to understand how security alerts move from detection to automated response
   - To gain hands-on experience using SEIM and SOAR tools in my homelab environment
