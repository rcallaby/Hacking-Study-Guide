# getsystem path

The getsystem escalation path is actually built into meterpreter and as such it is important to understand how to use it and how it works. Furthermore, understanding how all of these escalation techniques work is really important because from these you can gain an understanding on how to find and create new escalation paths from potential vulnerabilties in Windows or Linux, or even OS X, and so on.

Here is a link to how getsystem works on cobaltstrike:
https://www.cobaltstrike.com/blog/what-happens-when-i-type-getsystem/

The code to activate it is pretty obvious as you would just type getsystem in meterpreter such as:
```
    getsystem
```

As a penetration tester, one of the key goals is to identify and exploit vulnerabilities in a system to gain unauthorized access. One common technique used to achieve this is the "getsystem" path. This path involves escalating privileges on a system to gain administrative or system-level access. In this article, we will explore the steps involved in the getsystem path, including how and why it is used.

## What is the getsystem path?

The getsystem path is a technique used to escalate privileges on a Windows system to gain administrative or system-level access. The name comes from the fact that the end goal is to "get system" access. When a user logs into a Windows system, they are typically granted limited user-level access. This means that they can perform only certain actions and have limited control over the system. However, if a user can escalate their privileges to gain administrative or system-level access, they can perform a wider range of actions and have more control over the system.

## Why use the getsystem path?

The getsystem path is used by penetration testers and hackers to gain unauthorized access to a system. Once access has been gained, they can perform a range of malicious activities, including stealing data, installing malware, and conducting further attacks. By gaining administrative or system-level access, they can bypass many of the security measures that are in place to protect the system.

The getsystem path is particularly useful when a user has limited access to a system but needs to gain administrative or system-level access to perform a specific task. For example, if a penetration tester has discovered a vulnerability that can only be exploited with administrative access, they may use the getsystem path to escalate their privileges and exploit the vulnerability.

## Steps involved in the getsystem path

There are several steps involved in the getsystem path. These steps may vary depending on the specific system being targeted and the tools being used, but the general process is as follows:

Step 1: Reconnaissance
The first step in the getsystem path is reconnaissance. The penetration tester needs to gather as much information as possible about the system they are targeting. This includes information about the operating system, any installed software, network topology, and any known vulnerabilities.

Step 2: Exploitation
The second step is exploitation. The penetration tester needs to identify a vulnerability that can be exploited to gain elevated privileges on the system. This vulnerability may be a software vulnerability, a misconfiguration, or a weak password.

Step 3: Privilege escalation
The third step is privilege escalation. Once a vulnerability has been identified, the penetration tester needs to escalate their privileges on the system. This may involve running a privilege escalation exploit or using a tool such as Metasploit to escalate their privileges.

Step 4: Persistence
The fourth step is persistence. Once the penetration tester has gained administrative or system-level access, they need to ensure that they maintain access to the system even if they are detected. This may involve creating a backdoor, installing a rootkit, or modifying system settings.

Step 5: Covering tracks
The final step is covering tracks. The penetration tester needs to cover their tracks to ensure that their presence on the system is not detected. This may involve deleting logs, modifying timestamps, or obscuring their activity on the system.


The getsystem path is a powerful technique used by penetration testers and hackers to gain unauthorized access to a system. By escalating privileges, they can bypass many of the security measures that are in place to protect the system. The getsystem path involves several steps, including reconnaissance, exploitation, privilege escalation, persistence, and covering tracks. While the getsystem path can be a valuable tool for penetration testers, it is important to use it responsibly and with the proper authorization.
