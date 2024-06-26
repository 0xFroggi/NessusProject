# Nessus Vulnerability Scanner Project
### Nessus Vulnerability Scanner Implementation using Virtual Machines

**Project Overview:**

This project involved deploying a vulnerability scanner to learn how to identify and address security flaws, enhancing my expertise in securing systems.

**Project Details:**

I set up:

- **Windows 10 Virtual Machine**: Made intentionally vulnerable by stopping automatic updates, turning off the firewall, and installing outdated, insecure software.
- **Ubuntu Linux Virtual Machine**: Installed and configured with Nessus Vulnerability Scanner software to scan and detect security issues on the Windows machine.

### 1. Nessus Vulnerability Scanner Dashboard

- The Nessus dashboard is designed to provide an intuitive interface for security professionals to manage vulnerability scans effectively.
- Users can select from various predefined scan templates tailored to different types of vulnerabilities and scenarios, making it easier to identify and mitigate security risks in their networks.
- The sidebar offers easy access to scan policies, plugin configurations, and additional tools for comprehensive security management.
![Nessus Dashboard](https://github.com/0xFroggi/NessusProject/blob/main/images/nessus%20dashboard.png?raw=true)

### 2. Basic Network Scan 
- **Easy Setup**: Users can quickly name the scan, add a description, and select target systems (e.g., IP address `10.0.3.5` for a vulnerable Windows VM).
- **Organized Scans**: Save configurations in folders like "My Scans" for easy retrieval.
- **Detailed Settings**: Access detailed configurations through the sidebar categories (Basic, Discovery, Assessment, Report, Advanced).
- **Effective Management**: Schedule scans, set notifications, and configure policies to ensure thorough and timely scans.
![Basic Network Scan](https://github.com/0xFroggi/NessusProject/blob/main/images/initial%20scan%20-%20basic.png?raw=true)

**Results of the scan:**

- Shows the number of hosts scanned (1 in this case).
![Scan done](https://github.com/0xFroggi/NessusProject/blob/main/images/initial%20scan%20done.png?raw=true)

- Summarizes the vulnerabilities found, categorized by severity.
- Displays vulnerabilities categorized by severity: Medium, Low, Info.
![Scan Info](https://github.com/0xFroggi/NessusProject/blob/main/images/initial%20scan%20info.png?raw=true)

- Example Vulnerability: SMB signing is not required on the remote SMB server, which allows for man-in-the-middle attacks.
![SMB Signing](https://github.com/0xFroggi/NessusProject/blob/main/images/initial%20scan%20smb%20details.png?raw=true)

- Example Vulnerability: The remote host is listening on UDP port 137 or TCP port 445, and responds to NetBIOS or SMB requests.
![SMB NetBios](https://github.com/0xFroggi/NessusProject/blob/main/images/initial%20scan%20netbios%20details.png?raw=true)


### 3. Credential Scan and Configuration of the Windows Machine for the Scan
- At first, user for the Windows virtual machine privileges escalated by confugring Windows Registry to access administrator level resources. It will enhance the capability of the vulnerability scan.
- Location: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` provides the registry path to make necessary adjustments for access control.
- Key: `LocalAccountTokenFilterPolicy` set to `1`.
- This setting allows non-admin users to access administrative shares and resources, which is critical for enabling Nessus to perform a thorough credentialed scan.
![Windows Registry Config](https://github.com/0xFroggi/NessusProject/blob/main/images/allow%20non%20admins%20to%20access%20resources.png?raw=true)

- **Authentication Method**: Password-based authentication ensures secure access to the target system.
- **Credentials**: Administrator username and domain (`nessuswindows`) are specified for high-level access.
![Credential Scan Config](https://github.com/0xFroggi/NessusProject/blob/main/images/configure%20credentials.png?raw=true)

- The scan detected 43 vulnerabilities categorized by severity (Critical, High, Medium, Low, Info).
- It achieved higher level of findings than the initial “Basic Network Scan”.
- Each vulnerability is listed with its CVSS score, offering a standardized way to assess its impact and urgency.
![Credential Scan Overview](https://github.com/0xFroggi/NessusProject/blob/main/images/credential%20scan%20-%20overwiew.png?raw=true)

- Example Vulnerability: This vulnerability allows attackers to execute arbitrary code on the remote host's Microsoft 365 Office app.
- The vulnerability is detected based on the application's version number reported by the system.
![Credential Scan Detail](https://github.com/0xFroggi/NessusProject/blob/main/images/crendential%20scan%20-%20critical%20details.png?raw=true)


### 4. Testing Scanning Capabilities for Vulnerable Software
- Downloaded a vulnerable version of the Minecraft server known to include the Log4j vulnerability.
- Example path: `C:\Users\nessusadmin\Downloads\META-INF\libraries\org\apache\logging\log4j\log4j-core\2.14.1\log4j-core-2.14.1.jar`.
![Vuln Software](https://github.com/0xFroggi/NessusProject/blob/main/images/vuln%20minecraft.png?raw=true)

- Configured the scan to target the specific IP address of the machine hosting the vulnerable Minecraft server.
- The scan identified several critical vulnerabilities, including multiple issues related to Apache Log4j.
- Key vulnerabilities detected:
    - Apache Log4j < 2.15.0 Remote Code Execution (Windows)
    - Other vulnerabilities with varying CVSS scores and severity levels.
![Log4j Overview](https://github.com/0xFroggi/NessusProject/blob/main/images/log4j%20scan%20overwiew.png?raw=true)

- Critical Vulnerability: Apache Log4j < 2.15.0 Remote Code Execution
- The Log4j vulnerability, specifically identified as CVE-2021-44228, allows attackers to perform remote code execution by exploiting the JNDI lookup feature.
- An unauthenticated attacker can send a specially crafted request to a server running a vulnerable version of Log4j, leading to arbitrary code execution and potentially full system compromise.
![Log4j Details](https://github.com/0xFroggi/NessusProject/blob/main/images/log4j%20details.png?raw=true)

## Summary
In this project; 
I set up a homelab environment to test Nessus's capabilities in identifying and addressing security flaws. 
I configured a vulnerable Windows machine and used Nessus installed on an Ubuntu Linux machine to perform detailed scans. 
The scans successfully identified various vulnerabilities, including critical issues like the Log4j remote code execution. Through this project, I demonstrated the effectiveness of Nessus in detecting and mitigating security risks, enhancing my skills in vulnerability assessment and system security. 
This project provided valuable hands-on experience in using advanced security tools to protect systems from potential threats.












