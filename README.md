# Creating and Managing Reports

In Splunk, reports can be created upon successful data extraction or can also be scheduled. 

**Creating Reports from Data Exctraction**

For this scenario, 7 consecutive failed login attempts have been purposely made on the Windows Server's Administrator account to trigger EventID 4625 – Failed logon.

Step 1: Data Exctraction
- Use the following SPL to querry the data from the Search Bar
- index=win_svr2_index EventCode=4625
| stats count by Account_Name, Source_Network_Address
| where count > 5

This SPL querry means "look for EventCode = 4625 on win_svr2 index and pipe it to display the account name and source IP address that made that failed login for more than 5 times".

<img width="1079" height="751" alt="image" src="https://github.com/user-attachments/assets/89b2179e-30cb-492f-bf5b-8a01d9bf080d" />


Step 2: Generate Report

- Go to the Save As menu and select "Report"

<img width="495" height="292" alt="image" src="https://github.com/user-attachments/assets/070744a4-621b-4c87-8dfb-9035c2ba06d5" />

- Give the report a title and click "Next"

<img width="553" height="365" alt="image" src="https://github.com/user-attachments/assets/5fbb06c9-f16f-4694-b1a3-0b09e9a7cea0" />

- Click "View"

<img width="555" height="352" alt="image" src="https://github.com/user-attachments/assets/3e72f954-9e95-49c0-9d78-b721451ea0f6" />

- We can see that the report displays according to the querry which shows the Account_Name that got the failed login, the Source IP address, and the failed login count which is > 5.

<img width="1905" height="295" alt="image" src="https://github.com/user-attachments/assets/0c859ab3-d7b5-45fd-9b65-9ee081e02996" />

**Edit and Delete Reports**

- From the Search App, go to the Reports sections
- Here you can find all existing reports.

- Select the report created a few minutes ago.
- 
- From here you can see information about your report.

- Select the Edit button
