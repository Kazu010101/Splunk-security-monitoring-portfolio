# Detection Scenario 2 – Successful Login After Multiple Failures

Detect when a user successfully logs in after several failed login attempts, which may indicate:
- Brute-force attempts / password guessing that eventually succeeded

## SPL Querry
```
index=win_svr2_index (EventCode=4625 OR EventCode=4624)
| stats 
    count(eval(EventCode=4625)) AS failed_attempts,
    count(eval(EventCode=4624)) AS successful_logins
    BY Account_Name, Source_Network_Address
| where failed_attempts >= 5 AND successful_logins >= 1
```
SPL's Logic:
1. Search within the win_svr2 index for Event ID (4625)	for Failed login or Event ID (4624) for Successful login
2. Count failed logins (4625) per user + source IP
3. Count a successful login (4624) from the same user and source IP
4. Trigger if successful login happens after ≥ 5 failures

This SPL ensures that:
1. No alert for normal logins
2. No alert for failures only
3. Alert only occurs when successful login follows multiple failures (in this case >=5)

## Step 1: Creating the Alert for Successful Login After Multiple Failures Scenario

- Run the SPL Querry.
<img width="598" height="280" alt="image" src="https://github.com/user-attachments/assets/cebd4a84-bd90-4ba3-aac5-4967c4b3cd60" />

- After querring the request, save it as an alert.
<img width="1721" height="217" alt="image" src="https://github.com/user-attachments/assets/5edf4e9b-1be4-42e2-a67e-5019ef4bf627" />

## Step 2: Alert Configuration:
- Permissions: Private
- Alert Type: Scheduled, Run on Cron Schedule
- Time Range: Last for 15 minutes
- Cron Expression : */5 * * * * (This means: */5 → every 5 minutes, * * * * → every hour, every day)
- Expires: 1 hour
- Trigger Condition: > 0 (The alert only appears when the system has already confirmed that multiple failed logins were followed by a successful one, so any result (i.e. > 0) means suspicious activity was detected.)
- Trigger : Once
<img width="797" height="725" alt="image" src="https://github.com/user-attachments/assets/a918e463-9854-4939-8705-7213a92116e9" />

Triggered Actions: Select "Add to Triggered Alerts" and "Log Event".
<img width="707" height="171" alt="image" src="https://github.com/user-attachments/assets/612ed31a-577c-4960-9920-16f4da93f5d2" />

For the "Add to Triggered Alerts", set the severity to "Critical".
<img width="700" height="185" alt="image" src="https://github.com/user-attachments/assets/02e1de5e-b8bc-4bc2-bb87-1562014b51c2" />

For the "Log Event", fill in the fields as follows:
<img width="695" height="575" alt="image" src="https://github.com/user-attachments/assets/584d818d-f1c5-4d06-bb32-0bdae582e30c" />

Click "Save" after finish configuring
After alert has been saved, click "View Alert"
<img width="800" height="312" alt="image" src="https://github.com/user-attachments/assets/64c84ab7-f9b6-45c2-b29a-cd2ac24e52d3" />

Confirmed that the Alert is listed and enabled
<img width="1892" height="316" alt="image" src="https://github.com/user-attachments/assets/83929549-4b71-46b7-a1c2-3a930efce7fc" />

## Step 3: Verify the Alert Configuration

- Relog and generate > 5 failed logins on Windows Server host
- Login Successfully
- Wait up to 5 minutes
- Go to Activity → Triggered Alerts
- The triggered alert is listed
<img width="1385" height="286" alt="image" src="https://github.com/user-attachments/assets/65853611-cc69-414a-879c-b4815c3ab862" />

- Click "View Results" to see the details (Account Name, Source IP, failed attempts, and successful logins)
<img width="1898" height="408" alt="image" src="https://github.com/user-attachments/assets/e4ea02d2-58a8-4d87-b1b8-71005d21a598" />


## Lab Outcome and Conclusion
This lab demonstrated the detection of suspicious login behaviour where a successful authentication occurs after multiple failed login attempts.
By correlating Windows Security Event IDs 4625 (failed login) and 4624 (successful login), the alert accurately identified potential brute-force or credential-guessing activity that resulted in account compromise.
The scenario also validates the importance of correlating multiple security events rather than relying on single-event detection.
This approach improves detection accuracy by identifying attack patterns that indicate a higher risk to account security.

By enabling early identification of compromised credentials, and supporting timely investigation and response, the succesful detection aligns with MITRE ATT&CK and the NIST Cybersecurity Framework.
