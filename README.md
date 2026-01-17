# Installing Splunk Universal Forwarders

After installation of Splunk Enterprise, the universal forwarder in the default configuration is installed. The goal is to send Windows Server logs to Splunk.

Prerequisites: 
- splunkforwarder setup file downloaded 

## Step 1: Universal Forwarder Setup
- Accept the Licence Agreement
- Select "an on-premises Splunk Enterprise instance" to install Splunk on an on-premise Windows Server VM.

<img width="843" height="546" alt="image" src="https://github.com/user-attachments/assets/5fa182cc-b967-4125-93ca-0298e94bcf1b" />

- Use the default configuration
- Provide a username to Universal Forwarder.
<img width="645" height="503" alt="image" src="https://github.com/user-attachments/assets/f7252f06-f17b-4c6a-84c3-5d0f10dd9449" />

- Provide the server IP or Hostname and the port to the receiving indexer. Since this lab setup has no DNS, IP is used.
- Use default configuration for the deployment server port (8089) and Receiving Indexer port (9997)
<img width="639" height="498" alt="image" src="https://github.com/user-attachments/assets/6d69daef-183e-4991-8a18-3b693eaff1b3" />
<img width="621" height="490" alt="image" src="https://github.com/user-attachments/assets/e83e5956-ec31-4acd-85d9-3491ffd79d84" />

- Click Next and Launch the installation

## Step 2: Check Universal Forwarder Installation on Windows

- Go to services.msc
- Verify if "SplunkForwarder Service" is up.

<img width="940" height="439" alt="image" src="https://github.com/user-attachments/assets/b5f05201-8ac6-4cb4-beb1-1ce80eaa6bdd" />

## Step 3: Verify if Splunk listens on port 9997 via PowerShell

- Open PowerShell and input `cd "C:\Program Files\Splunk\bin"`
- Run `.\splunk enable listen 9997`
- Enter Splunk username and password
- The prompt should display `Listening for Splunk data on TCP port 9997`.
- Restart Splunk using command `.\splunk restart` (Splunk will disconnect. Relogin after the restart)

<img width="940" height="344" alt="image" src="https://github.com/user-attachments/assets/cf3f5987-0d83-4f36-8bcf-246c2cb3be31" />

- After logging in to Splunk, open PowerShell and verify Splunk is listening using `netstat -an | findstr 9997`
- We should see expected result : `TCP    0.0.0.0:9997    LISTENING`

<img width="695" height="209" alt="image" src="https://github.com/user-attachments/assets/fe7a48ce-9dc9-401a-a866-e1475db0a3af" />


## Step 4: Verify Windows Server is displayed on Splunk

- Go to your Splunk Server
- Go to Settings > Agent management

<img width="940" height="444" alt="image" src="https://github.com/user-attachments/assets/983a673a-7f67-4edd-ae35-341abf345c8b" />

- Verify that Windows Server is listed on this page

<img width="940" height="599" alt="image" src="https://github.com/user-attachments/assets/badc1614-eb52-491f-b9d6-38225e0c0678" />

## Conclusion

- Splunk Universal Forwarder is communicating with Splunk Enterprise using port 9997 and ready to send Windows Server logs to Splunk.
- This lab builds an isolated environment to experiment with basic SOC activities. 

Next Lab: Adding Data to Splunk
