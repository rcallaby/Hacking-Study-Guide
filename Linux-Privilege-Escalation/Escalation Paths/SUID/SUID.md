# SUID Escalation Path

SUID (Set User ID) is a permission bit in Linux that allows an executable file to run with the permissions of the file owner instead of the user who runs it. As a penetration tester, one of the objectives may be to escalate privileges by exploiting SUID bit.

### Here's a common SUID escalation path that can be used by a penetration tester:

Enumeration: The first step in SUID escalation is to enumerate the system and find any files with the SUID bit set. This can be done using tools such as "find" or "locate". For example, a command like "find / -perm -4000 -type f 2>/dev/null" can be used to find SUID files on the system.

Analysis: Once SUID files have been found, the next step is to analyze them and determine if they can be exploited. One common method is to use a tool such as "strings" to examine the binary for any hard-coded credentials or other sensitive information.

Exploitation: After identifying a vulnerable SUID binary, a penetration tester may attempt to exploit it to escalate privileges. One common method is to use a technique known as "DLL hijacking" where a malicious shared library is loaded by the vulnerable binary, allowing the attacker to execute arbitrary code with elevated privileges.

Post-exploitation: Once privileges have been escalated, the attacker can carry out additional attacks on the system, such as installing a backdoor or exfiltrating data.

It's worth noting that SUID escalation is not always possible or practical, as it requires finding a vulnerable SUID binary and successfully exploiting it. However, it is still an important technique to be aware of as a penetration tester, as it can provide a significant advantage in gaining access to a system.

## Tools for SUID Escalation in Linux
[GTFOBins](https://gtfobins.github.io/) - Not really a tool but a website where you can find many of the SUID escalation paths

## Tutorials for SUID Escalation in Linux
* [Linux Privilege Escalation - SUID Binaries](https://steflan-security.com/linux-privilege-escalation-suid-binaries/) - A fairly good overview of the entire process
* [Linux Privilege Escalation using the SUID bit](https://materials.rangeforce.com/tutorial/2019/11/07/Linux-PrivEsc-SUID-Bit/) - A good tutorial to gain a grasp on the whole SUID escalation path
* [Linux Privilege Escalation: SUID Blog](https://tryhackme.com/resources/blog/linux-privilege-escalation-suid) - A good blog post by TryHackMe that covers SUID Linux Privilege Escalation
* [Understanding Privilege Escalation by Abusing Linux Access Control](https://infosecwriteups.com/understand-privilege-escalation-by-abusing-linux-access-control-6cab107e7203) - Another good overview of how SUID and other escalation paths work in Linux