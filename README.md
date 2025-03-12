# Sysmon-Threat-Detection
Detecting unauthorized activity using Sysmon and Windows Event Viewer
Objective:
	This project demonstrates how Sysmon can help detect unauthorized user activity particularly network connections and process executiona tracking. By leveraging Sysmon’s detailed logging capabilities, security teams can identify suspicious activity before it escalates into a security incident.

Tools Used: 
  -Sysmon (configured with the SwitftOnSecurity Sysmon config)
  -Windows Event Viewer

Project Steps and Findings:
  -Sysmon Installation and Configuration
  -Installed Sysmon and applied the SwiftOnSecurity config to expand event tracking beyond basic process creation and termination.
  -Process Execution and Network Monitoring
    -Ran the following commands to generate logs
      -Curl (to test outbound network requests)
      -Whoami (to check user identity)
      -Ping (to simulate network activity)
    -Observed Sysmon Event Logs
      -Event ID 1 (Process Create): Captured PowerShell executions, including full command-line arguments.
      ![Sysmon Process Creation Detection](https://github.com/user-attachments/assets/d4822452-52a1-4293-9d83-4b70fb076ef8)
      -Event ID 3 (Network Connection Detection): Logged outbound network connections initiated by executed processes.
      ![Sysmon Network Connection Detection](https://github.com/user-attachments/assets/eb4d6bdd-7396-4889-924d-aad1f0865976)

File Creation Monitoring
  -Created test files to observe file activity tracking
    -Event ID 11 (FileCreate): Logged new file creations, helping detect unauthorized file modifications.
    ![Sysmon File Creation Detection](https://github.com/user-attachments/assets/6ce19a31-0eb7-48ad-875e-b9a1ae2e4370)

Registry Modification Monitoring
  -Modified the Window registry to test detection.
    -Event ID 13 (Registry Value Set): Captured changes to registry keys: a common attack vector for persistence tactics.
    ![Sysmon Widnows Registry Modification Detection](https://github.com/user-attachments/assets/09b02b6d-811d-4b73-938d-acc43993c3f9)

Key Takeaways and Next Steps
  -Sysmon effectively tracks process execution, network connections, file creation, and registry changes, making it a powerful tool for malware detection, unauthorized access monitoring, and insider threat identification.
  -Next Step:
    -The next step for a Security team would be to forward the Sysmon logs to Microsoft Sentinel for a real time alerting and correlation, improving security visibility through a single-pane-of-glass. This is what's known as a SIEM or Security Information and Event Management System.
