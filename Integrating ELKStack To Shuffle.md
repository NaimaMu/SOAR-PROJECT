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

