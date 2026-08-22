# Windows SOC Log Analysis & Threat Hunting Project

## Overview
This project focuses on analyzing Windows Event Logs and Sysmon logs to detect malicious activity, persistent threats, and command-and-control (C2) communications during a simulated cyber attack.

## Tools & Technologies Used
* Platform: TryHackMe (Windows Logging for SOC)
* Log Analyzer: Windows Event Viewer
* Monitoring Tool: System Monitor (Sysmon)

## Key Event IDs Monitored
* Event ID 1 (Sysmon): Process Creation (Used to detect browser and malware execution)
* Event ID 3 (Sysmon): Network Connections (Used to track C2 servers)
* Event ID 11 (Sysmon): File Creation (Used to identify dropped payloads)
* Event ID 15 (Sysmon): File Create Stream Hash / Downloads
* Event ID 4624 / 4625 (Security Log): Successful and Failed Logons
* Event ID 4720 / 4732 (Security Log): User Account Creation & Privilege Escalation

## Investigation Summary
1. Initial Access & Browser Identification: Analyzed Sysmon Event ID 1 to identify the browser used (`Google Chrome`) by the user.
2. Malware Payload Analysis: Tracked down the dropped malicious executable (`ckjg.exe`) via Event ID 11.
3. Persistence Mechanism: Located the startup directory placement used by the malware to maintain persistence on the host.
4. C2 Infrastructure Identification: Extracted the malicious IP address, port, and domain (`gettsveriff.com`) used for command and control communication via network event logs.

## Conclusion & Takeaways
Proper log configuration with Sysmon provides high-visibility insights into post-exploitation behavior, enabling SOC analysts to quickly contain and mitigate threats.
