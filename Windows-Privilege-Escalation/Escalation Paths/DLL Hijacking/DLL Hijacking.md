# DLL Hijacking

DLL hijacking is a technique used by attackers to execute malicious code by exploiting a vulnerability in the Windows operating system. An ethical hacker could use DLL hijacking as a means of escalating their privileges in a Windows environment.

In DLL hijacking, an attacker exploits the search order that Windows uses to load dynamic link libraries (DLLs) into memory. Windows first looks in the directory of the executable file, and then in directories listed in the PATH environment variable. An attacker can place a malicious DLL in a directory that is earlier in the search order than the directory where the legitimate DLL is located, such that Windows will load the malicious DLL instead of the legitimate one.

The attacker can use this technique to escalate their privileges by hijacking a process that runs with higher privileges and then executing malicious code. For example, the attacker might hijack a process running as an administrator and then use the elevated privileges to install malware or gain access to sensitive data.

An ethical hacker could use this technique as a means of testing the security of a system and determining the extent to which it is vulnerable to attack. By demonstrating how an attacker could use DLL hijacking to escalate their privileges, the ethical hacker could help organizations to understand the risks and take steps to reduce them.

## Tools for DLL Hijacking
* [JAWS - Just Another Windows Enum Script](https://github.com/411Hall/JAWS) - A powershell script
* [juicy-potato](https://github.com/ohpe/juicy-potato) - A sugared version of RottenPotatoNG with some extras
* [potato](https://github.com/foxglovesec/Potato) - Potato Privilege Escalation for Windows 7,8,19 and Server 2008 & 2012
* [PrivescCheck](https://github.com/itm4n/PrivescCheck) -This enumerates common Windows misconfigurations for privilege escalation
* [SessionGopher](https://github.com/Arvanaghi/SessionGopher) - This is a powershell scripts that finds saved session information for remote access tools
* [Sherlock](https://github.com/rasta-mouse/Sherlock/) - A Powershell script to find missing software patches for local privilege escalation
* [Spartacus](https://github.com/Accenture/Spartacus) - A tool to find DLL Hijacking targets on a local machine
* [Watson](https://github.com/rasta-mouse/Watson) - A .Net tool that finds missing KBs to find exploits for Privilege Escalation vulnerabilities


