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

<img width="940" height="396" alt="image" src="https://github.com/user-attachments/assets/82c00fa5-d30d-4d22-a2e9-26396cb75f27" />
