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
