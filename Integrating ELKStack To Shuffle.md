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
     c. now click Create new rule

<img width="744" height="622" alt="image" src="https://github.com/user-attachments/assets/f9eeae19-3451-43ab-b4b3-9e929021bcae" />











































## STEP1: Creating a webhook tirigger in shuffle
     a. Logging in to Shuffle.
<img width="1067" height="677" alt="image" src="https://github.com/user-attachments/assets/050feaf0-be43-46c0-8338-eea95fc995d4" />
<img width="629" height="496" alt="image" src="https://github.com/user-attachments/assets/6bdd148e-8535-48e2-9d1d-e3327a7f711a" />
<img width="982" height="600" alt="image" src="https://github.com/user-attachments/assets/b47aaeb3-cd84-47ae-97cc-0485a6b1a388" />
<img width="1069" height="679" alt="image" src="https://github.com/user-attachments/assets/5d287d30-5eb9-4984-a81f-5691e27d5798" />


