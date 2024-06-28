# Domain Escalation

### Domain Escalation Checklist

#### 1. Reconnaissance
- **Network Scanning**
  - Identify active hosts and open ports (Nmap, Masscan).
- **Service Enumeration**
  - Enumerate services on open ports (SMB, LDAP, RDP, HTTP).
- **Domain Enumeration**
  - Gather domain information (nslookup, dig, ldapsearch).
  - Identify domain controllers (AD Discovery Tools).
  
#### 2. Credential Gathering
- **Password Spraying**
  - Test common passwords across multiple accounts.
- **Brute Forcing**
  - Use tools like Hydra, Medusa for brute force attacks.
- **Phishing**
  - Conduct phishing campaigns to collect credentials.
- **Credential Dumping**
  - Extract credentials from memory (Mimikatz, ProcDump).

#### 3. Vulnerability Assessment
- **Patch Levels**
  - Identify unpatched systems (Nessus, OpenVAS).
- **Misconfigurations**
  - Look for weak or default configurations (e.g., SMB signing not required).

#### 4. Initial Access
- **Kerberoasting**
  - Extract service account tickets and crack them offline.
- **AS-REP Roasting**
  - Extract AS-REP responses for accounts without pre-authentication.
- **Pass-the-Hash**
  - Use extracted NTLM hashes to authenticate.
- **Pass-the-Ticket**
  - Use Kerberos tickets for lateral movement.

#### 5. Post-Exploitation
- **Privilege Escalation**
  - Exploit local vulnerabilities (e.g., kernel exploits, privilege escalation scripts).
- **Persistence**
  - Create backdoors (scheduled tasks, startup items).
- **Data Exfiltration**
  - Identify and extract sensitive data.

#### 6. Lateral Movement
- **Remote Execution**
  - Use tools like PsExec, WMIC, WinRM.
- **Admin Shares**
  - Access administrative shares (C$, ADMIN$).
- **RDP**
  - Use Remote Desktop Protocol for movement.
- **DLL Injection**
  - Inject malicious DLLs into processes.

#### 7. Domain Dominance
- **Domain Admin Privileges**
  - Obtain Domain Admin credentials.
- **Golden Ticket Attack**
  - Create Kerberos tickets with elevated privileges.
- **Silver Ticket Attack**
  - Create Kerberos tickets for specific services.
- **DCShadow**
  - Simulate a rogue Domain Controller.

### Tools and Techniques
- **Cracking Tools**: Hashcat, John the Ripper
- **Enumeration Tools**: BloodHound, ADRecon
- **Exploitation Frameworks**: Metasploit, Cobalt Strike
- **Scripting Languages**: PowerShell, Python
- **Log Analysis**: Splunk, ELK Stack

This checklist should be adapted to the specific context and environment of the engagement. Always ensure to have proper authorization before conducting any penetration testing activities.
