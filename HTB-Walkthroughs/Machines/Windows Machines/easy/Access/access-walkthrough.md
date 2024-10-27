# Access Walkthrough HTB Walkthrough

"Access" is a challenging machine on the Hack The Box platform that offers a real-world-like penetration testing scenario. The primary objective of this machine is to gain unauthorized access to a remote server and escalate privileges to achieve full control. This box is categorized as an Active Directory-focused machine, making it a valuable learning experience for those looking to hone their skills in Windows-based environments.

The vulnerability that allows exploitation on the "Access" machine is centered around a misconfigured Active Directory setup. The initial foothold is obtained through a user account enumeration technique, where an attacker identifies a weak password policy that allows for brute-force attacks. With a low-privilege user account, the attacker can perform a Kerberos ticket attack to escalate privileges and gain access to a higher-privilege user's credentials. The final privilege escalation involves exploiting a misconfigured group policy object (GPO) that grants the attacker the ability to execute code with SYSTEM-level privileges, thereby granting full control over the system.

"Access" on Hack The Box provides a realistic demonstration of how misconfigurations and weaknesses in Active Directory environments can lead to significant security breaches. It highlights the importance of proper password policies, user account management, and GPO configuration to prevent unauthorized access and privilege escalation in Windows-based networks. This machine serves as an invaluable learning opportunity for cybersecurity professionals seeking to enhance their skills in securing Active Directory environments and understanding the implications of common vulnerabilities.

Here's a detailed breakdown of the Hack The Box machine "Access":

### Initial Assessment

- **IP Address:** Identify the IP address provided for the target machine from the HTB VPN connection.
- **Nmap Scan:** Perform an Nmap scan to identify open ports and services:
  ```bash
  nmap -sC -sV -oN access_initial <IP_ADDRESS>
  ```
  - **-sC**: Runs default scripts.
  - **-sV**: Version detection.
  - **-oN**: Outputs results to a file called `access_initial`.
- The scan should reveal the following open ports:
  - **Port 21**: FTP service (vsftpd)
  - **Port 80**: HTTP service
  - **Port 139 and 445**: SMB services

### Gaining a Foothold

#### Obtaining User

1. **Anonymous FTP Access:**
   - Connect to the FTP server using anonymous login:
     ```bash
     ftp <IP_ADDRESS>
     ```
   - If successful, list available files and directories.
   - Download any accessible files and analyze them locally.
   - One important file to check for is **`backup.mdb`**, a Microsoft Access Database file.

2. **Analyzing `backup.mdb`:**
   - Use **`mdb-tools`** to extract information from `backup.mdb`:
     ```bash
     mdb-tables backup.mdb
     ```
   - Look for tables containing potential credentials or sensitive information.
   - Extract data from tables that might include usernames or passwords:
     ```bash
     mdb-export backup.mdb <TABLE_NAME>
     ```
   - Use any credentials found to attempt further access via SMB or other services.

### Escalating Privileges from User to Root

1. **SMB Enumeration:**
   - Use **`smbclient`** or **`enum4linux`** to gather information on available SMB shares and potential credentials for escalation:
     ```bash
     smbclient -L //<IP_ADDRESS> -U <username>
     ```
   - If there are writable shares, consider uploading files or scripts for privilege escalation.
   
2. **Obtaining Shell Access:**
   - If credentials are valid, log in using SMB:
     ```bash
     smbclient //<IP_ADDRESS>/Share -U <username>
     ```
   - Explore files for potential privilege escalation vectors, like vulnerable executables, scripts, or configuration files.

3. **Privilege Escalation:**
   - Look for common privilege escalation methods, such as weak permissions on sensitive files or services.
   - Use **WinPEAS** or **PowerUp.ps1** to automate privilege escalation checks:
     - Transfer the script to the machine using SMB or another method, and execute it to identify misconfigurations.
   - If successful, obtain access to `NT Authority\System` or other high-privileged accounts.

### Concluding Thoughts

- **Enumeration** is the key to this machine, with multiple layers of information gathering needed to progress.
- The **backup.mdb** file was the critical point for gaining user access.
- **SMB** was essential for lateral movement and privilege escalation.
- Proper use of tools like **mdb-tools**, **smbclient**, and Windows enumeration scripts was vital for both foothold and privilege escalation.

