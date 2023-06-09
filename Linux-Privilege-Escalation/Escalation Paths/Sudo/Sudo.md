# Sudo Escalation Path

Penetration testers commonly use the sudo escalation path to gain elevated privileges on a target system. The following steps provide a general overview of how a penetration tester might perform this process:

Reconnaissance: The first step is to gather information about the target system, including the operating system, installed software, and user accounts.

Exploit vulnerabilities: The penetration tester would attempt to exploit any known vulnerabilities or misconfigurations to gain initial access to the target system. This could involve techniques such as phishing, social engineering, or exploiting software vulnerabilities.

Enumeration: Once the tester has access to the target system, they would perform enumeration to identify what permissions and privileges they currently have. This may involve running commands like whoami and id to determine their current user and group memberships.

To identify sudo access you would perform the following command to see what sudo privileges you have using the following command:
```
    sudo -l
```

Identifying sudo access: The tester would search for any user accounts that have sudo access, either by reviewing the /etc/sudoers file or by running the command sudo -l to identify what commands can be executed with elevated privileges.

Exploiting sudo access: If the tester has identified a user with sudo access, they can attempt to exploit this access to escalate privileges further. This could involve exploiting a vulnerability in one of the allowed commands or using a tool like sudoedit to spawn a shell with root privileges.

Covering tracks: Once the tester has achieved elevated privileges, they would typically attempt to cover their tracks by removing any evidence of their presence on the target system, such as deleting log files or modifying timestamps.

It's important to note that this process can vary depending on the target system and the specific vulnerabilities or misconfigurations present, and that ethical considerations and legal requirements must be taken into account when conducting a penetration test.

## Tools to test sudo escalation path in Linux
[sudo_killer](https://github.com/TH3xACE/SUDO_KILLER) - A tool to identify and exploit sudo rules misconfiguration

## Tutorials for SUDO Privilege Escalation
* [A Guide to Linux Privilege Escalation](https://payatu.com/blog/a-guide-to-linux-privilege-escalation/) - A pretty overview of privilege escalation, it also includes sudo as a path
* [Introduction to Linux Privelege Escalation](https://academy.hackthebox.com/course/preview/linux-privilege-escalation/introduction-to-linux-privilege-escalation) - A pretty good tutorial on Linux Privelege Escalation by Hack the Box
* [Linux Privilege Escalation exploiting Sudo rights](https://medium.com/schkn/linux-privilege-escalation-using-text-editors-and-files-part-1-a8373396708d) - A good step by step tutorial on how to escalate privileges in Linux using SUDO
* [Linux Privilege Escalation using Sudo Rights](https://www.linode.com/docs/guides/linux-red-team-privilege-escalation-techniques/) - A good tutorial by Linode
