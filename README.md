# Splunk-security-monitoring-portfolio
This repository demonstrates hands-on experience using **Splunk Enterprise** and **Universal Forwarder** to monitor and detect security events on a **Windows Server virtual machine** in an isolated lab environment.

## Lab Environment
- Splunk Enterprise (Windows Server 2022)
- Splunk Universal Forwarder
- Windows Event Logs
- Internal VM network (offline lab)
- Data forwarded via TCP port 9997

## Skills Demonstrated
- Basic Splunk installation and configuration of Universal Forwarder <a href="https://github.com/Kazu010101/Splunk-security-monitoring-portfolio.git">Splunk-Project|
- Uploading Data using Universal Forwarder and File Upload
- Creating and Managing Reports
- Log analysis using SPL
- Windows security event analysis
- Basic incident detection logic
- SOC Level 1 workflows

## Detection Scenarios
1. Failed login / brute-force detection
2. Successful login after multiple failures
3. Privilege escalation monitoring
4. Persistence via service creation
5. System shutdown and availability monitoring
