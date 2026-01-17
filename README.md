# Configuring Alert on Splunk

Alerts on Splunk are saved searches that can be triggered when certain pre-determined conditions are met. They can be scheduled or in real-time. 

Step 1: Creating the Brute-Force Alert in Splunk
- We will use the querry from the previous brute force attack detection.

  index=win_svr2_index EventCode=4625
  
  | stats count as failed_attempts by Account_Name, Source_Network_Address
  
  | where failed_attempts >= 5

<img width="418" height="106" alt="image" src="https://github.com/user-attachments/assets/84910dee-87b1-4801-ae50-c3eb91a44f68" />

- Run the querry and confirm the result

<img width="940" height="367" alt="image" src="https://github.com/user-attachments/assets/a6a5c55b-67df-43f3-8e3d-7feb499850ae" />

Step 2: Create the alert
- After querring the request as in the report section, save it as an alert.
  
<img width="1676" height="452" alt="image" src="https://github.com/user-attachments/assets/91460aee-2059-4ddf-8760-9057d40dd22b" />

Step 3: Alert configuration

We will need to select the type of alert (scheduled or in real-time), when it must be run (if there are more than 5 login failure for example), and the action.

For this lab example, the alert configuration is as follows:
- Permissions: Private
- Alert Type: Scheduled, Run on Cron Schedule
- Time Range: Last for 15 minutes
- Cron Expression : */5 * * * * (This means: */5 → every 5 minutes, * * * * → every hour, every day)
- Expires: 1 hour
- Trigger Condition: Number of result (i.e. failed login is bigger than 5)
- Trigger : Once

<img width="798" height="725" alt="image" src="https://github.com/user-attachments/assets/f8beb2a0-b933-44b8-a4c5-8722b7c890ec" />

- Triggered Actions: "Add to Triggered Alerts" and "Log Event".

<img width="405" height="346" alt="image" src="https://github.com/user-attachments/assets/b91f5a95-9581-4ef2-9a2c-e16231811d82" />

- For the "Add to Triggered Alerts", set the severity to "Medium".

<img width="707" height="170" alt="image" src="https://github.com/user-attachments/assets/23e087f4-dec9-44aa-9263-adf45dec8667" />

- For the "Log Event", fill in the fields as follows: 

<img width="765" height="652" alt="image" src="https://github.com/user-attachments/assets/b6f58ad5-a4d6-4189-8ea6-0adc32259b18" />

- Click "Save" after finish configuring
- After alert has been saved, click "View Alert"

<img width="800" height="312" alt="image" src="https://github.com/user-attachments/assets/6001386e-efd2-4047-8221-a49fdd1c7ad2" />


Rationale for the configuration:
- The alert runs every 5 minutes and looks back over the last 15 minutes to detect bursts of failed logins, ensuring timely detection without excessive alerting.
- Scheduled alerts using cron expressions allow fine-grained control such as running detections every 5 minutes.
- The alert logs a clear, single-line event into the main index using a generic sourcetype, making it easier to review and investigate the alert activity.
