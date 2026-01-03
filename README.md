# Adding Data to Splunk

Splunk can add data in different ways. This lab demonstrates adding data in 2 ways:

a. Using Universal Forwarder installed on Windows Server host

b. Uploading a log file

**a. Add Data using Universal Forwarder**

- Go to Settings > Add Data

<img width="771" height="748" alt="image" src="https://github.com/user-attachments/assets/6c9224f4-55a3-482e-a081-9ddedad62e5c" />

- Choose Forward

<img width="940" height="387" alt="image" src="https://github.com/user-attachments/assets/38f0c468-8651-4a8a-8835-5c9c9fe77192" />

- Add the Windows Server to the selected host and give it a Server Class Name
- Click "Next"

<img width="940" height="386" alt="image" src="https://github.com/user-attachments/assets/24aee045-7022-42f2-9d84-c19e92451fec" />

- Select the Local Event Logs to monitor data from the Windows Server host.
- Select which Event Logs we want to monitor, in this case all are chosen.
- Click "Next"

<img width="940" height="497" alt="image" src="https://github.com/user-attachments/assets/92eb3ddb-b8f1-40cb-add6-4b044f455c74" />

- Create a new index where the logs need to be put.
- Give it an index name
- Click "Next"

<img width="940" height="836" alt="image" src="https://github.com/user-attachments/assets/30463797-7874-42d3-8ca0-eb6e8fb4ced1" />

- Review the configuration
- Click "Submit"

<img width="940" height="494" alt="image" src="https://github.com/user-attachments/assets/8c56a7e1-3420-4d5f-b110-009b9b60dbcf" />

- Click "start searching" to start searching for data

<img width="940" height="400" alt="image" src="https://github.com/user-attachments/assets/b3da0485-83fe-4b58-bcac-ac74631ba9f7" />

- Go to Setting > Forwarding and receiving to check if Port 9997 is in the receiving list

<img width="781" height="756" alt="image" src="https://github.com/user-attachments/assets/16bd28d4-108b-400c-a70d-cee8e7e9bfe5" />

- Verify that Port 9997 is listening to receive data

<img width="940" height="166" alt="image" src="https://github.com/user-attachments/assets/6f0d3655-4101-42d8-af4f-459c3b96cc35" />

- Go to the search field and try searching data using index="win_svr2_index"
- Verified that Event data from the Windows Server are displayed

<img width="940" height="691" alt="image" src="https://github.com/user-attachments/assets/cf444577-0e53-4fe1-a3cc-6a2fdd4c8453" />

This is where all data request are querried using a combination of wildcard character ("*") and operators. For example:
- To search for a username with "Ad" on it, input "Username=Ad*" to make usernames like Admin, Adrian, etc. to be populated.
- Use operators AND to search for connection on the computer named SVR2 with an event ID using the input "eventid=4624 AND computername=svr2"
- Search for every connection on the computer except the domain controller: "eventid=4624 NOT computername=domaincontroller"
- We can also use from "Search History"




**b. Add Data by uploading a log file**

- Go to Settings > Add Data
- Select "Upload" 

<img width="1180" height="547" alt="image" src="https://github.com/user-attachments/assets/1f4fa33f-480e-4568-81ca-8d88a6848247" />

- Click "Select File" > Choose the file > Click "Open"
<img width="1373" height="816" alt="image" src="https://github.com/user-attachments/assets/98c57380-cc65-46cd-a55b-bbbc4e6f22a5" />

- Confirm that the file is uploaded successfully, and click "Next"

<img width="933" height="705" alt="image" src="https://github.com/user-attachments/assets/8af24cb9-fb60-4727-9e50-9b99f0e5e32d" />

- Choose how Splunk will read your file (in this lab, we use Default) then press "Next"

<img width="1345" height="863" alt="image" src="https://github.com/user-attachments/assets/124c1e91-9a25-42eb-b388-c54a891150b7" />

- Give it a name, and click "Save"

<img width="645" height="418" alt="image" src="https://github.com/user-attachments/assets/25a81628-52d5-4f4d-9882-a3d84ad655ab" />

- Click "Review" and "Submit"

<img width="1012" height="757" alt="image" src="https://github.com/user-attachments/assets/2957f384-9bd4-4dd5-a5f6-46d9fbdc3fc6" />
<img width="1067" height="378" alt="image" src="https://github.com/user-attachments/assets/f7ddd58b-7d5e-4b34-ab51-601fa782380e" />

- Click "Start Searching"

<img width="1147" height="525" alt="image" src="https://github.com/user-attachments/assets/0f5074e6-d3dc-4c08-83a2-41faf546a59c" />

- Data is now populated and we can start searching

<img width="1345" height="832" alt="image" src="https://github.com/user-attachments/assets/ffbabfea-7829-46ab-9f5e-a0f2cbf129a5" />


The next lab is about creating and managing report in Splunk.






