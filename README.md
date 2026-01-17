# Creating-Splunk-Dashboards 

The goals of visualizing using dashboards is to allow an analyst to see:

- Which accounts are being attacked
- Where the attempts are coming from
- How many failures occurred

## Step 1: Create the dashboard

```
index=win_svr2_index EventCode=4625
| stats count as failed_attempts by Account_Name, Source_Network_Address
| where failed_attempts >= 5
| sort - failed_attempts
```

- Run the SPL above in Search
- Click Save As → New Dashboard
  
<img width="940" height="184" alt="image" src="https://github.com/user-attachments/assets/4ee6be62-3a13-45eb-8ae1-3c0ec1b2894e" />

On the "Save Panel to New Dashboard":

- Give the dasboard a title: Windows Authentication Monitoring
- Give a description
- Permission: Private
- Select Dashboard Type: Classic
- Fill in the panel title field
- Click "Save to Dashboard" 

<img width="721" height="933" alt="image" src="https://github.com/user-attachments/assets/a6efd124-c260-44b8-83db-1d8de06f692e" />


## Step 2: Create Panel 1 – Bar Chart (Most Failed Logins)

Panel type: Bar Chart
Purpose: Identify targeted accounts

<img width="940" height="379" alt="image" src="https://github.com/user-attachments/assets/73e5f78e-6425-494e-8bf3-5f7368996e82" />

## Step 3: Create Panel 2 – Table (Source IP Analysis)

Panel type: Table
Purpose: Identify attacker source
Columns to display:
- Source_Network_Address
- Account_Name
- failed_attempts

<img width="940" height="337" alt="image" src="https://github.com/user-attachments/assets/fb3a0f03-33b6-4eb3-9959-8689e94c2d21" />

## Step 4: Create Panel 3 – Time Chart (Attack Trend)

Panel type: Line Chart
Purpose: Detect spikes over time

<img width="940" height="342" alt="image" src="https://github.com/user-attachments/assets/2338fd5c-44e4-43fc-9b58-201a629e4b41" />

## Result

<img width="940" height="416" alt="image" src="https://github.com/user-attachments/assets/d97ff8dd-1d69-4317-90f5-0ee1c6e62e4e" />
