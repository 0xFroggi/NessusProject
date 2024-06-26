# Nessus Vulnerability Scanner Project
### Nessus Vulnerability Scanner Implementation using Virtual Machines

**Project Overview:**

This project involved deploying a vulnerability scanner to learn how to identify and address security flaws, enhancing my expertise in securing systems.

**Project Details:**

I set up:

- **Windows 10 Virtual Machine**: Made intentionally vulnerable by stopping automatic updates, turning off the firewall, and installing outdated, insecure software.
- **Ubuntu Linux Virtual Machine**: Installed and configured with Nessus Vulnerability Scanner software to scan and detect security issues on the Windows machine.

1. Nessus Vulnerability Scanner Dashboard
- The Nessus dashboard is designed to provide an intuitive interface for security professionals to manage vulnerability scans effectively.
- Users can select from various predefined scan templates tailored to different types of vulnerabilities and scenarios, making it easier to identify and mitigate security risks in their networks.
- The sidebar offers easy access to scan policies, plugin configurations, and additional tools for comprehensive security management.

![Nessus Dashboard](https://github.com/0xFroggi/NessusProject/blob/main/images/nessus%20dashboard.png?raw=true)

2. Basic Network Scan 
- **Easy Setup**: Users can quickly name the scan, add a description, and select target systems (e.g., IP address `10.0.3.5` for a vulnerable Windows VM).
- **Organized Scans**: Save configurations in folders like "My Scans" for easy retrieval.
- **Detailed Settings**: Access detailed configurations through the sidebar categories (Basic, Discovery, Assessment, Report, Advanced).
- **Effective Management**: Schedule scans, set notifications, and configure policies to ensure thorough and timely scans.

![Basic Network Scan](https://github.com/0xFroggi/NessusProject/blob/main/images/initial%20scan%20-%20basic.png?raw=true)

Results of the scan:

- Shows the number of hosts scanned (1 in this case).
![Scan done](https://github.com/0xFroggi/NessusProject/blob/main/images/initial%20scan%20done.png?raw=true)

- Summarizes the vulnerabilities found, categorized by severity.
- Displays vulnerabilities categorized by severity: Medium, Low, Info.
![Scan Info](https://github.com/0xFroggi/NessusProject/blob/main/images/initial%20scan%20info.png?raw=true)

- Example Vulnerability: SMB signing is not required on the remote SMB server, which allows for man-in-the-middle attacks.
![SMB Signing](https://github.com/0xFroggi/NessusProject/blob/main/images/initial%20scan%20smb%20details.png?raw=true)

- Example Vulnerability: The remote host is listening on UDP port 137 or TCP port 445, and responds to NetBIOS or SMB requests.
![SMB NetBios](https://github.com/0xFroggi/NessusProject/blob/main/images/initial%20scan%20netbios%20details.png?raw=true)
