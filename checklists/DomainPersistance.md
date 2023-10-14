# Domain Persistance

When it comes to domain persistence in penetration testing, it's important to thoroughly assess a network's security posture to identify potential vulnerabilities that could allow an attacker to maintain access even after initial compromise. Here's a checklist to help you with domain persistence testing:

1. **Reconnaissance and Information Gathering:**
   - [ ]Enumerate all subdomains associated with the target domain.
   - [ ]Identify DNS records (A, AAAA, CNAME, MX, TXT, etc.).
   - [ ]Perform WHOIS lookup to gather registration information.
   - [ ]Look for expired or unused subdomains.

2. **Vulnerability Scanning:**
   - [ ]Conduct vulnerability scans (using tools like Nmap, Nessus, or OpenVAS) to identify potential vulnerabilities on the target systems.
   - [ ]Focus on services, ports, and applications that could be exploited for persistence.

3. **Password Cracking and Brute Force Attacks:**
   - [ ]Perform password cracking attempts on identified services (e.g., SSH, FTP, HTTP basic authentication).
   - [ ]Utilize tools like Hydra, Medusa, or John the Ripper for this purpose.

4. **Service Exploitation:**
   - [ ]Exploit known vulnerabilities in services, especially those with a history of providing persistent access (e.g., MS17-010 for EternalBlue).

5. **Client-side Attacks:**
   - [ ]Consider phishing campaigns to target employees or users with privileges that could provide access to the domain.

6. **Client-side Exploits:**
   - [ ]Exploit vulnerable client applications (e.g., Adobe Reader, Flash, Java) to gain a foothold on a target system.

7. **Steganography and Data Exfiltration:**
   - [ ]Look for hidden information in images, documents, or other files on the compromised system that may contain sensitive data or further instructions.

8. **Post-exploitation Frameworks:**
   - [ ]Utilize post-exploitation frameworks (e.g., Metasploit, PowerShell Empire, Covenant) to establish a persistent foothold.

9. **Privilege Escalation:**
   - [ ]Identify and exploit vulnerabilities that allow for privilege escalation on the compromised system.

10. **Rootkit Installation:**
    - [ ]Consider deploying a rootkit to hide the attacker's presence on the system.

11. **Backdooring:**
    - [ ]Install a backdoor that allows for remote access even after the initial compromise is detected and mitigated.

12. **Persistence Mechanisms:**
    - [ ] Set up mechanisms for persistence, such as creating scheduled tasks, modifying startup scripts, or installing services.

13. **Data Exfiltration and Exfiltration Channels:**
    - [ ] Identify methods to exfiltrate sensitive data from the compromised system without detection.

14. **Cleanup and Covering Tracks:**
    - [ ]Remove traces of the attack, such as logs, temporary files, and other artifacts.
    - [ ]Modify or delete event logs to hide evidence of the compromise.

15. **Monitoring and Detection:**
    - [ ]Implement monitoring solutions and intrusion detection systems (IDS) to detect any unusual activities or connections.

16. **Documentation and Reporting:**
    - [ ]Document all findings, techniques used, and potential vulnerabilities discovered.
    - [ ]Provide recommendations for mitigation and improvement.
