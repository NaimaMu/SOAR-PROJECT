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

As we can see, Shuffle is now listening for incoming alerts from ELK.

# Step 2: Configure The Webhook Action in Kibana
For this step it sends alerts from ELK to Shuffle

1. Open Kibana and go to "Security" then click "Rules"

<img width="335" height="469" alt="image" src="https://github.com/user-attachments/assets/1fc7f612-c5af-4af0-b990-34e0bf39834a" />

2. click the rule that I created already that named "Windows Failed Login Attempts"
<img width="688" height="485" alt="image" src="https://github.com/user-attachments/assets/52fad69e-d4c2-4acc-b1ca-e28bede67daa" />

<img width="833" height="257" alt="image" src="https://github.com/user-attachments/assets/82d41900-8ca6-4320-9efb-a453b8250b78" />

3. click "Edit Rule" and scroll down to "Actions" and then click "Add action"
<img width="838" height="553" alt="image" src="https://github.com/user-attachments/assets/af4e055c-bbd9-4e1c-9d1b-4130bb3054a0" />
<img width="600" height="543" alt="image" src="https://github.com/user-attachments/assets/4d6d0593-7ffa-4fb0-9f58-9691285bfa7c" />

4. Now select "Webhook" and then create a new "Webhook Connector"
<img width="789" height="587" alt="image" src="https://github.com/user-attachments/assets/6ce36ef2-0278-4ec9-8d12-31ee5bcf6bb1" />

IMPORTANT NOTE ABOUT ELASTIC LICENSING:
- Using a webhook action in Kibana requires an Elastic Gold License.
<img width="503" height="517" alt="image" src="https://github.com/user-attachments/assets/30a6afc6-aa83-454b-ab2a-87041282f681" />
Since I'm using the free Elastic license, I cannot send alerts directly from Kibana to Shuffle using a webhook.  Because of this, I need to use a different approach.

# Step 3: Use Index Action as a Workaround
- To work around the license limitation, I configure Kibana to store alerts in an Elasticsearch index instead of sending them directly. 
