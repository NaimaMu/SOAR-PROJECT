Overview: 
  - I am integrating ELKStack with Shuffle SOAR to automate the response to failed login alerts, ELK is responsible for detecting failed login events, and Shuffle receives these alerts through a webhook and prepares them for automated actions. 

# Already Done The Following:
    a. ELKStack installed and running
    a detection rule already created in Kibana(failed login rule)
    SHuffle SOAR installed and runnin
  

# Step 1: Create the Shuffle Webhook  
  1. Log in to Shuffle
  2. Go to "Workflows"  and click "New Workflow"
<img width="791" height="617" alt="image" src="https://github.com/user-attachments/assets/0fb78dcf-ea8c-4410-bc87-955fa84425d6" />

  3. I am going to name it "ELK - Failed Login Alerts" and add a description as well. then click "create from scratch"
<img width="949" height="687" alt="image" src="https://github.com/user-attachments/assets/f7f63251-ac41-4c83-aa24-ae900a10c9fa" />

  4. Click "Add trigger"
  5. Now select "Webhook"
<img width="586" height="524" alt="image" src="https://github.com/user-attachments/assets/f7bd6c0b-4b95-49fe-9859-8a21f2268740" />

  
  6. Click "Start" to initialize the webhook
<img width="878" height="645" alt="image" src="https://github.com/user-attachments/assets/89f4f848-2cd4-48c4-80e7-d1bc2efba40b" />
<img width="902" height="650" alt="image" src="https://github.com/user-attachments/assets/65396ed8-5b4a-4e03-a27f-a953b125faa3" />

As we can see this, Shuffle is now listening for incoming alerts from ELK.



# Step 2: Configure The Webhook Action in Kibana
For this step it sends alerts from ELK to Shuffle

1. Open Kibana and go to "Security" then click "Rules"
