# OVERVIEW:
- In this section, I integrate the ELK Stack with Shuffle SOAR. My goal is to detect suspicious Windows login activity in ELK firs, then later send those alerts to SHuffle so Shuffle can start an automation workflow.



# Step 1: Confirm ELK is receiving Windows Login Logs

### 1.1 Check failed login events (Event ID 4625)
First I want to confirm if ELK is receiving failed login attempts. 
     1. Open "Kibana"  
     2. Navigate "Discover"
     3. Select the data view "winlogbeat-*"
     4. Now I am going to run a querry to see if my ELKstack is detecting failed login attempts. 
           Querry: event.code: "4625"    
<img width="746" height="623" alt="image" src="https://github.com/user-attachments/assets/ad3dfe15-d5bf-4bcb-8f04-89b186ca51c7" />

At this time, no results are returned, which indicates there were no failed login attempts within the selected time range. 
____________________________________________________________________________________________________

### 1.2 Verify successful login events (Event ID 4624) 

To confirm log ingestion is working correctly, I search for successful logins 
           querry: event.code:"4624"
This query shows results, which confirms that Winlogbeat is sending Windows login logs to ELK

<img width="966" height="584" alt="image" src="https://github.com/user-attachments/assets/32748502-a770-427c-954e-51e3e177cd90" />

____________________________________________________________________________________________________

# Step 2: Create a Detection Rule for Failed Logins
### 2.1 Open Detection Rule and Create a new rule
- Now that I have confirmed logs are coming into ELK, I create a detection rule for failed login attempts.

     1. in Kibana, go to Security
     2. Click Rules (or Detection rules) 
<img width="744" height="622" alt="image" src="https://github.com/user-attachments/assets/f9eeae19-3451-43ab-b4b3-9e929021bcae" />

### 2.2 Select "Threshold" rule type
On the "Create new rule" screen, I select "Threshold" because I want an alert to trigger only when failed logins happen multiple times within a short time period 

<img width="743" height="619" alt="image" src="https://github.com/user-attachments/assets/b9bcaaef-7cc6-463b-ac17-2cfa5b2298ea" /> 
<img width="1082" height="700" alt="image" src="https://github.com/user-attachments/assets/b3e5ec40-e436-45eb-8f62-76937025c804" />

# Configure the Threshold rule (failed logins)
I configure the threshold rule using these settings:

     - Index patterns: winlogbeat-* ,  logs-*
     - query:  event.code: "4625"
     - Group by : source.Ip, @timestamp, and agent.name
     - Threshold: 1 
     - Time window: 5 minutes

This means the alert will trigger if there are 3 faild login attempts within 5 minutes (per source IP a, timestamp, and agent.name) after I finish, I click "Continue" to move to the next step. 

<img width="543" height="376" alt="image" src="https://github.com/user-attachments/assets/7ad05ecb-8bbd-4351-93cc-ad9418d1e648" />

<img width="825" height="403" alt="image" src="https://github.com/user-attachments/assets/7d1266b3-8503-407d-8065-946333f8d863" />

 # Finishing the Detection Rule
 Now I complete the rule details by adding by adding a name, description, severity, risk score, and tags

 - Rule name: Windows Failed Login Attempts
 - Description: This rule detects multiple failed login attempts on a Windows 11 system, which may indicate brute-force or unauthorized access activity.
 - Severity: Medium
 - Risk Score: 47
 - Tags: failed-login, windows, bruteforce

After I finish entering the details, I click "Continue" 
<img width="865" height="589" alt="image" src="https://github.com/user-attachments/assets/722f72fd-c4e4-426f-9fcd-002bbc5d05fc" />
<img width="1031" height="671" alt="image" src="https://github.com/user-attachments/assets/26a5ba69-a619-42a3-89a6-a09aec572f5f" />


# Schedule the rule
Next, I set how often the rule should run. 
- Runs every: 5 minutes
- Additional look-back time: 1 minute

This means Elastic will check for failed logins every 5 minutes, and it will also look back an extral 1 minute to help avoid missing events. 

After setting the schedule, I click "COntinue" 
<img width="904" height="325" alt="image" src="https://github.com/user-attachments/assets/29233ebb-803c-44c3-b31e-0d9a19d2d751" />

# Rule Actions
At this step, I do not add any actions yet, I leave the actions section empty because I want to confirm the rule works correctly before connecting it to SHuffle(SOAR). 
Then I click "Create rule and Enable" 
<img width="625" height="508" alt="image" src="https://github.com/user-attachments/assets/98345787-2c89-47c5-9c90-00b62d8f9ae4" />

# Finishing
As we can see here, the rule has been created. I am going to log my windows several times in order to check if the rule is working or now. 
<img width="825" height="507" alt="image" src="https://github.com/user-attachments/assets/c2c5ed2c-52c5-4ff8-98fe-eca843349d1d" />

I locked my windows and logedin incorect password. And this
<img width="1268" height="659" alt="image" src="https://github.com/user-attachments/assets/f312e4b1-eee2-49d9-8b02-69cb45940f4e" />
<img width="1263" height="568" alt="image" src="https://github.com/user-attachments/assets/bad2831c-6a07-4056-8d38-b9328febae97" />

# Let's click "Take an action " and then click "Investigate in timeline"  to see if it gives us more detail about this alert 
<img width="493" height="617" alt="image" src="https://github.com/user-attachments/assets/57d30a47-8c44-4da3-a7a4-a8713ee373ca" />

This is what I am seeing: 
<img width="572" height="475" alt="image" src="https://github.com/user-attachments/assets/47cb71d5-9415-4711-8868-a45abf0e732e" />
<img width="1778" height="662" alt="image" src="https://github.com/user-attachments/assets/9a67ede3-f486-4129-b165-82fdb19f4b37" />
<img width="1103" height="571" alt="image" src="https://github.com/user-attachments/assets/172fd3a4-6675-41d1-a478-2313a1aafdb3" />
<img width="477" height="572" alt="image" src="https://github.com/user-attachments/assets/4781a84c-f219-4116-99f0-3a51adfd551c" />

# Additional Step
Checking if I can see this failed login attemps in kibana
<img width="995" height="516" alt="image" src="https://github.com/user-attachments/assets/1ffea94f-2710-4629-9909-9eda4d22c9d1" />

now, as we can see here, it detectes and I am able to see Event.code:4625 here


Now Moving to the Next step which is "Integrating ELK stack with SHUFFLE"  
