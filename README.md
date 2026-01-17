# Creating and Managing Reports

In Splunk, reports can be created upon successful data extraction or can also be scheduled. 

## Creating Reports from Data Extraction

For this scenario, 7 consecutive failed login attempts have been purposely made on the Windows Server's Administrator account to trigger EventID 4625 – Failed logon.

## Step 1: Data Extraction
- Use the following SPL to querry the data from the Search Bar
```
index=win_svr2_index EventCode=4625
| stats count by Account_Name, Source_Network_Address
| where count > 5
```

This SPL querry means "look for EventCode = 4625 on win_svr2 index and pipe it to display the account name and source IP address that made that failed login for more than 5 times".

<img width="1079" height="751" alt="image" src="https://github.com/user-attachments/assets/89b2179e-30cb-492f-bf5b-8a01d9bf080d" />


## Step 2: Generate Report

- Go to the Save As menu and select "Report"

<img width="495" height="292" alt="image" src="https://github.com/user-attachments/assets/070744a4-621b-4c87-8dfb-9035c2ba06d5" />

- Give the report a title and click "Next"

<img width="553" height="365" alt="image" src="https://github.com/user-attachments/assets/5fbb06c9-f16f-4694-b1a3-0b09e9a7cea0" />

- Click "View"

<img width="555" height="352" alt="image" src="https://github.com/user-attachments/assets/3e72f954-9e95-49c0-9d78-b721451ea0f6" />

- We can see that the report displays according to the querry which shows the Account_Name that got the failed login, the Source IP address, and the failed login count which is > 5.

<img width="1905" height="295" alt="image" src="https://github.com/user-attachments/assets/0c859ab3-d7b5-45fd-9b65-9ee081e02996" />

## Edit and Delete Reports

- From the Search App, go to the Reports sections

<img width="725" height="302" alt="image" src="https://github.com/user-attachments/assets/05b5980a-c4cf-4d85-a2a0-dc852ed83e88" />

- Here you can find all existing reports.
- Select the report created a few minutes ago.

<img width="1898" height="582" alt="image" src="https://github.com/user-attachments/assets/a11f14aa-6dde-4127-9c38-db841b01ffa5" />

- From here you can see information about your report and Edit the information

<img width="1346" height="372" alt="image" src="https://github.com/user-attachments/assets/a7e0fd78-a3f0-4cf4-b788-89e0dfe728ea" />

## Scheduled Report 

Now let's schedule the report we created before to occur for every day at 08:00 AM to show the failed login yesterday.

- Select "Edit Schedule" 

<img width="1348" height="358" alt="image" src="https://github.com/user-attachments/assets/986831b9-a536-4a38-abbf-db85d7fd6321" />

- Check "Schedule Report for (name of your report)"
  
<img width="673" height="338" alt="image" src="https://github.com/user-attachments/assets/80394df7-a2cd-4411-9179-7ebe6ffb751e" />

- Configure the report settings accordingly and click "Save"
  
<img width="667" height="577" alt="image" src="https://github.com/user-attachments/assets/2d4c1b9d-4a38-47ed-80ef-95c7ee0c16e2" />

- Review the information in the report

<img width="1507" height="367" alt="image" src="https://github.com/user-attachments/assets/64598390-bc34-4ca8-976e-feced18cffd9" />


The next lab is <a href="https://github.com/Kazu010101/Splunk-security-monitoring-portfolio/tree/Configuring-Alert-on-Splunk">Configuring Alert on Splunk
