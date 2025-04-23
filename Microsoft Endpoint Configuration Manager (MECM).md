## Microsoft Endpoint Configuration Manager (MECM)

![MECM](https://www.itta.net/wp-content/uploads/2023/02/Microsoft-Endpoint-Manager-e1721405318658.png)

#### Microsoft Endpoint Configuration Manager (MECM) is a comprehensive management solution designed to help IT manage PCs and servers effectively. It enables organizations to keep software up-to-date, set configuration and security policies, and monitor system status while providing employees access to corporate applications on their chosen devices. MECM supports management for various operating systems, including Windows, Linux, and Mac OS, making it versatile for diverse IT environments.

### Requirements
1. SQL
2. SQL ODBC
3. Windows ADK
4. Windows ADK PE
5. .NET Framework 4.8 Update

### Update Software Center Packages

##### Manual (Control Panel > View By: Icon > Configuration Manager > Actions)
![MECM](https://www.prajwaldesai.com/wp-content/uploads/2022/03/Trigger-SCCM-Machine-Policy-Retrieval-Evaluation-Cycle-Snap1.jpg)

##### PowerShell
```powershell
# Trigger Machine Policy Retrieval & Evaluation Cycle in Config Manager
(Get-WmiObject -Namespace "ROOT\ccm" -Class "SMS_Client").TriggerSchedule("{00000000-0000-0000-0000-000000000021}")
```
