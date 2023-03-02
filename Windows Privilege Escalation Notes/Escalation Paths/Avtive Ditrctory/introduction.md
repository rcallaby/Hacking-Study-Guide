# Active Directory

As a penetration tester, one of the most critical tasks is to escalate privileges once you have gained access to a network or system. Active Directory (AD) is a vital component of most corporate networks, and it provides a central point for managing and controlling access to resources. In this article, we will explore various techniques for escalating privileges using Active Directory, including RottenPotato attacks and PrivExchange attacks.

## What is Active Directory?

Active Directory is a directory service developed by Microsoft for Windows domain networks. It provides authentication and authorization services, as well as centralized management of users, computers, and other network resources. Active Directory is a critical component of most corporate networks, and it is often targeted by attackers seeking to escalate privileges.

## Privilege Escalation Techniques

Privilege escalation refers to the process of obtaining higher levels of access than originally granted by exploiting vulnerabilities in a system or network. There are several techniques that can be used to escalate privileges in an Active Directory environment, including the following:

+ RottenPotato Attack
The RottenPotato attack is a technique that exploits the Windows authentication process to escalate privileges to SYSTEM-level access. This attack works by exploiting a feature called NTLM authentication, which allows users to authenticate with a server without providing their credentials repeatedly.

To carry out a RottenPotato attack, the attacker needs to first gain access to a low-privileged user account on the target system. The attacker then uses the Metasploit Framework to create a rogue SMB server that appears to be a legitimate Windows domain controller. The attacker then exploits the NTLM authentication process to obtain a token with SYSTEM-level privileges.

+ PrivExchange Attack
The PrivExchange attack is another technique used to escalate privileges in an Active Directory environment. This attack exploits a vulnerability in Microsoft Exchange that allows an attacker to impersonate an Exchange server and gain elevated privileges.

To carry out a PrivExchange attack, the attacker needs to first gain access to a low-privileged user account on the target system. The attacker then uses the Exchange Web Services (EWS) to create a fake Exchange server and trick the victim into authenticating to it. Once the victim has authenticated, the attacker can use the EWS to obtain an authentication token with elevated privileges.

+ Kerberoasting
Kerberoasting is a technique that exploits a weakness in the way that Windows handles Kerberos authentication. This attack can be used to obtain the password hash of a domain user, which can be cracked to obtain the user's plaintext password.

To carry out a Kerberoasting attack, the attacker needs to first identify a user with a service account that has a Kerberos Service Principal Name (SPN) set. The attacker can then use a tool like PowerView to request a Kerberos ticket-granting ticket (TGT) for the user. The attacker can then use the TGT to request a service ticket for the user's SPN, which will contain the user's password hash.

+ Pass-the-Hash
Pass-the-Hash is a technique that allows an attacker to use the password hash of a domain user to authenticate to other systems on the network. This technique can be used to escalate privileges by authenticating to systems with higher levels of access.

To carry out a Pass-the-Hash attack, the attacker needs to first obtain the password hash of a domain user. The attacker can then use a tool like Mimikatz to inject the password hash into the memory of a process running on the target system. The attacker can then use the injected password hash to authenticate to other systems on the network.


Escalating privileges in an Active Directory environment is a critical component of penetration testing. There are several techniques that can be used to escalate privileges, including the RottenPotato attack, PrivExchange attack, Kerberoasting