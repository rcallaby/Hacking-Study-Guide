# Windows Build

### Windows Build Penetration Testing Checklist

1. **System Info**
   - Obtain system information (OS version, architecture, hardware details).
   - Check system configuration (firewall settings, installed software).

2. **Kernel Exploits**
   - Search for kernel exploits using scripts (check for known vulnerabilities).

3. **Logging/AV Enumeration**
   - Identify logging mechanisms and configure accordingly.
   - Enumerate antivirus (AV) software and bypass techniques if applicable.

4. **Network**
   - Scan for open ports and services (use tools like Nmap).
   - Check for network vulnerabilities (misconfigurations, weak protocols).

5. **Running Processes**
   - List running processes and identify potentially exploitable ones.
   - Look for suspicious or unauthorized processes.

6. **Services**
   - Enumerate services and their configurations (check for weak permissions).
   - Test for service exploitation (buffer overflows, privilege escalation).

7. **Applications**
   - Identify installed applications and their versions.
   - Test applications for known vulnerabilities (exploit databases).

8. **DLL Hijacking**
   - Search for DLL hijacking opportunities (misconfigured application paths).
   - Test and exploit DLL vulnerabilities in running applications.

9. **Windows Credentials**
   - Enumerate cached and stored credentials (use tools like Mimikatz).
   - Test for pass-the-hash and pass-the-ticket attacks.

10. **Files and Registry (Credentials)**
    - Search for sensitive files (passwords, configuration files).
    - Check registry entries for stored credentials and sensitive information.

11. **Leaked Handlers**
    - Look for exposed or misconfigured file and object handlers.
    - Exploit handler vulnerabilities (file type association exploits).

12. **Pipe Client Impersonation**
    - Identify named pipes and potential for client impersonation.
    - Test for unauthorized access via named pipes (privilege escalation).

This checklist covers essential steps and considerations for conducting penetration testing on a Windows system build. Each section involves thorough enumeration, vulnerability assessment, and exploitation where applicable to ensure comprehensive security testing.