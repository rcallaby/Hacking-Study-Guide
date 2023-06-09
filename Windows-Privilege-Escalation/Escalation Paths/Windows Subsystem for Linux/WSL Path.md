# WSL Path

The Windows Subsystem for Linux is a escalation path that unfortunately came into light because Microsoft decided to add Linux as a subsystem to Windows.That means some of the Linux vulnerabilities could also become Windows vulnerabilties. That means we should test those vulnerabilities if they are present.

Windows Subsystem for Linux (WSL) is a feature in Windows 10 that allows users to run Linux applications directly on their Windows machines. This feature has been increasingly popular among developers and system administrators who want to use Linux command-line tools on their Windows systems.

However, as with any feature that allows users to run commands with elevated privileges, there is always a risk of potential exploitation by attackers. Penetration testers need to understand the escalation path of WSL to identify potential security weaknesses and assess the overall security posture of the system.

## WSL Escalation Path

The WSL escalation path is a set of techniques that can be used to escalate privileges from a low-privileged user account to a higher-privileged account with administrative access. The escalation path includes the following steps:

+ Identify the version of WSL running on the system
+ Identify the version of the Windows kernel running on the system
+ Identify the current user account and privileges
+ Identify potential vulnerabilities in the WSL environment
+ Exploit the vulnerabilities to escalate privileges
+ Gain administrative access to the system

## Step-by-Step Directions

### Identify the version of WSL running on the system
To identify the version of WSL running on the system, a penetration tester can use the command "wsl -l -v" in a Command Prompt or PowerShell session. This command will display a list of all installed WSL distributions along with their version numbers.

### Identify the version of the Windows kernel running on the system
To identify the version of the Windows kernel running on the system, a penetration tester can use the command "systeminfo" in a Command Prompt or PowerShell session. This command will display system information including the version of the Windows kernel.

### Identify the current user account and privileges
To identify the current user account and privileges, a penetration tester can use the command "whoami /priv" in a Command

Prompt or PowerShell session. This command will display the current user account name along with a list of their privileges.

### Identify potential vulnerabilities in the WSL environment
To identify potential vulnerabilities in the WSL environment, a penetration tester can use a variety of techniques including vulnerability scanners, manual testing, and fuzzing. Some potential vulnerabilities that can be exploited to escalate privileges in the WSL environment include:

### Misconfigured file permissions that allow non-privileged users to modify sensitive files
Vulnerable Linux applications that can be exploited to execute arbitrary code
Exploitable kernel vulnerabilities that can be used to gain elevated privileges
Exploit the vulnerabilities to escalate privileges
Once potential vulnerabilities have been identified, a penetration tester can attempt to exploit them to escalate privileges. Depending on the specific vulnerability, different techniques may be used. Some common techniques that can be used to escalate privileges in the WSL environment include:

### Exploiting vulnerable Linux applications to execute arbitrary code with elevated privileges
Using symbolic links to modify sensitive files that are writable by non-privileged users
Exploiting kernel vulnerabilities to gain elevated privileges
Gain administrative access to the system
Once privileges have been escalated, a penetration tester can attempt to gain administrative access to the system. This can be done by using the escalated privileges to create a new administrative user account or by modifying existing administrative accounts.

## Conclusion

The WSL escalation path is an important concept for penetration testers to understand. By identifying potential vulnerabilities in the WSL environment and exploiting them to escalate privileges, attackers can gain elevated access to a Windows system. Penetration testers can use the techniques outlined above to assess the security posture of WSL installations and identify potential vulnerabilities that could be exploited by attackers.

## Tools Used for WSL Path


