# Windows Privilege Escalation


### Initial Enumeration
1. **System Information Gathering:**
   - Identify the Windows version and architecture (32-bit or 64-bit).
   - Check for system patches and vulnerabilities.

2. **User Information:**
   - List users and their privileges (e.g., admin, user).
   - Enumerate user groups and memberships (e.g., Administrators, Remote Desktop Users).

3. **Running Processes and Services:**
   - List running processes and services.
   - Identify services running with elevated privileges (e.g., SYSTEM).

4. **Network Configuration:**
   - Check for open ports and connections.
   - Identify network shares and permissions.

### Exploitation and Privilege Escalation Techniques
5. **Exploiting Misconfigurations:**
   - Look for misconfigured services (e.g., weak permissions, unquoted service paths).
   - Exploit weak registry permissions (e.g., HKLM registry keys).

6. **Exploiting Vulnerabilities:**
   - Search for known vulnerabilities (e.g., CVEs) related to the Windows version and installed software.
   - Exploit vulnerable services (e.g., outdated software with known exploits).

7. **Password Attacks:**
   - Attempt password spraying or brute-force attacks against user accounts.
   - Exploit weak or default credentials.

8. **File and Directory Permissions:**
   - Check for sensitive files (e.g., configuration files, backups) with weak permissions.
   - Identify writable directories and files accessible by low-privileged users.

9. **Scheduled Tasks:**
   - List scheduled tasks and identify those running with elevated privileges.
   - Modify or create scheduled tasks to execute malicious payloads.

### Post-Exploitation
10. **Maintaining Access:**
    - Establish persistence mechanisms (e.g., backdoors, scheduled tasks, registry keys).
    - Use rootkits or stealth techniques to avoid detection.

11. **Covering Tracks:**
    - Clear event logs (e.g., Security, System) to remove traces of the attack.
    - Modify timestamps of files and directories accessed during the attack.

### Documentation and Reporting
12. **Documentation:**
    - Document all findings, including exploited vulnerabilities and escalation techniques.
    - Prepare a detailed report outlining the attack vectors and recommended mitigations.

### Tools and Resources
- Use relevant tools for enumeration (e.g., `PowerSploit`, `Metasploit`).
- Refer to vulnerability databases (e.g., CVE, Exploit-DB) for the latest exploits and vulnerabilities.

