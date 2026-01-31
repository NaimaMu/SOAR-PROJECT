#  User Login Anomaly Detection

## Overview
In this project, I create a simple SOAR automation that detects unusual user login activity. The project focuses on identifying logins from different countries within a short time frame to help detect possible account compromise. 

---

## Tools I used
- Wazuh
- Shuffle
- windows 11

## Explanation for Each
### wazuh
  - (will collect all the logs from my windows 11 and  monitors user login activity. Then I am going to create dashboards to actually helps me visualize where these activities is coming from.
### Shuffle
  - Shuffle receives alerts from wazuh and runs a simple automation. It flags the activity as suspicious and sends a notification to the analyst(which is me) in discord so that I can review it and take the correct action.

### Windows 11
  - This is my host machine that geenrates user login events. It has Wazuh agent is installed on already so I will see all the activities from this to my wazuh machine.

 ## Goal is:
   - To learn and practice basic SOAR automation and understand how alerts move from detection to response
