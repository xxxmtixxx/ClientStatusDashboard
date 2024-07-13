# Client Status Dashboard

## Description
The Client Status Dashboard is a PowerShell-based tool designed to monitor the status of multiple clients. It continuously checks the status of clients listed in a CSV file and updates an HTML dashboard accordingly. The dashboard is shared via SMB, allowing it to be accessed from other Windows machines on the same network. This design makes the tool lightweight and easy to deploy.

## Features
- **Continuous Monitoring**: The tool continuously pings each client listed in a CSV file and updates their status on the dashboard.
- **HTML Dashboard**: The status of each client is displayed on an HTML dashboard, which is automatically updated every 30 seconds.
- **SMB Share**: The HTML dashboard is shared via SMB, making it accessible from other Windows machines on the same network.
- **Shortcut Creation**: A shortcut to the dashboard is created on the Public Desktop for easy access.
- **Installer and Uninstaller Scripts**: The tool comes with PowerShell scripts to install and uninstall the tool. Both scripts create a log file at `C:\Temp\console.log` for troubleshooting purposes.

## CSV File
The CSV file (`clients.csv`) is located in the `C:\Temp\MonitorClients` directory. This file contains a list of clients to be monitored. Each client should be represented by a row in the CSV file with the following columns:
- `Company`: The name of the company.
- `IPOrDomain`: The IP address or domain name of the client.

You can modify the CSV file to add, remove, or change clients. The changes will be reflected on the dashboard the next time it is updated.

## Installation
To install the Client Status Dashboard, run the installer script with administrative privileges. The installer script performs the following actions:
- Downloads a ZIP file from a specified URL and extracts it to a specified directory.
- Checks if Chocolatey and NSSM are installed, and installs them if they are not.
- Creates a service to run the monitoring script.
- Shares the directory containing the HTML dashboard via SMB.
- Creates a shortcut to the dashboard on the Public Desktop.
- Logs all actions to `C:\Temp\console.log`.

## Uninstallation
To uninstall the Client Status Dashboard, run the uninstaller script with administrative privileges. The uninstaller script performs the following actions:
- Stops the service created by the installer script.
- Deletes the service.
- Removes the SMB share.
- Deletes the directory containing the HTML dashboard and the monitoring script.
- Deletes the shortcut from the Public Desktop.
- Logs all actions to `C:\Temp\console.log`.
