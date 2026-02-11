# OVERVIEW:
- In this secion, I am integrating the ELK Stack with Shuffle.My goal is to send security alerts from ELK to Shuffle so that Shuffle can start an automation when suspicious login activity is detected.

     
SO Let's Get start!

# Let's confirm if ELK is receiving Windows Login Logs by doing the following:
     a. Open Kibana  
     b. Go to Discover
     c. Selecting my dat view which is winlogbeat-*
     d. Now I am going to search if I have a failed logins or successful logins by searching this querry : 
          event.code: "4625"    
<img width="746" height="623" alt="image" src="https://github.com/user-attachments/assets/ad3dfe15-d5bf-4bcb-8f04-89b186ca51c7" />
- Did not return any result which means there is no unsuccessfull login attempt

Now lets check if there are any successful login attemp:
querry: event.code:"4624"

<img width="966" height="584" alt="image" src="https://github.com/user-attachments/assets/32748502-a770-427c-954e-51e3e177cd90" />
- We can see that that querry worked and now returns a successful login attempts.


# Now Lets create a detection rule
     a. in Kibana, go to Security
     b. Then go to Rules (Or Detection rules)
<img width="744" height="622" alt="image" src="https://github.com/user-attachments/assets/f9eeae19-3451-43ab-b4b3-9e929021bcae" />

     c. now click Create new rule
<img width="743" height="619" alt="image" src="https://github.com/user-attachments/assets/b9bcaaef-7cc6-463b-ac17-2cfa5b2298ea" /> 

     d. Now I am going to click on where it says "Threshold"
<img width="1082" height="700" alt="image" src="https://github.com/user-attachments/assets/b3e5ec40-e436-45eb-8f62-76937025c804" />

# Configure the Threshold rule (failed logins)
I set the rule like this:
     - Index patterns: winlogbeat-* ,  logs-*
     - query:  event.code: "4625"
     - Threshold: 5
     - Time window: 5 minutes
This means the alert will trigger if there are 5 failed login attempts within 5 minutes. 
<img width="785" height="542" alt="image" src="https://github.com/user-attachments/assets/54f65968-c0e3-4276-8e21-84de71a779d6" />

### After that click "Continue" to proceed to the next step 
<img width="825" height="403" alt="image" src="https://github.com/user-attachments/assets/7d1266b3-8503-407d-8065-946333f8d863" />

 # Finishing the Detection Rule
 Now, I am going to name my rule, add description, severity, and risk score. and click "continue". 
<img width="865" height="589" alt="image" src="https://github.com/user-attachments/assets/722f72fd-c4e4-426f-9fcd-002bbc5d05fc" />
<img width="1031" height="671" alt="image" src="https://github.com/user-attachments/assets/26a5ba69-a619-42a3-89a6-a09aec572f5f" />

# Schedule the rule
<img width="904" height="325" alt="image" src="https://github.com/user-attachments/assets/29233ebb-803c-44c3-b31e-0d9a19d2d751" />
     - This means Elastic Checks for fialed login every 5 minutes and also checks the last 1 minute just in case it missed something. 
     
Click "Continue"

# Rule Actions
At this step, I did not add any actionns. I left everything empty and clicked create rule. his is because I want to first make sure the rule works before connecting it to Shuffle.

<img width="625" height="508" alt="image" src="https://github.com/user-attachments/assets/98345787-2c89-47c5-9c90-00b62d8f9ae4" />

# Finishing
As we can see here, the rule has been created and now I can move on the the next step
<img width="1036" height="487" alt="image" src="https://github.com/user-attachments/assets/698d8765-f448-45c6-ae76-0e2e347b1f4f" />

