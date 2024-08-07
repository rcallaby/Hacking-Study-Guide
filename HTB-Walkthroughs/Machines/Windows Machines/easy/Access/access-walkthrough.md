# Access Walkthrough HTB Walkthrough

"Access" is a challenging machine on the Hack The Box platform that offers a real-world-like penetration testing scenario. The primary objective of this machine is to gain unauthorized access to a remote server and escalate privileges to achieve full control. This box is categorized as an Active Directory-focused machine, making it a valuable learning experience for those looking to hone their skills in Windows-based environments.

The vulnerability that allows exploitation on the "Access" machine is centered around a misconfigured Active Directory setup. The initial foothold is obtained through a user account enumeration technique, where an attacker identifies a weak password policy that allows for brute-force attacks. With a low-privilege user account, the attacker can perform a Kerberos ticket attack to escalate privileges and gain access to a higher-privilege user's credentials. The final privilege escalation involves exploiting a misconfigured group policy object (GPO) that grants the attacker the ability to execute code with SYSTEM-level privileges, thereby granting full control over the system.

"Access" on Hack The Box provides a realistic demonstration of how misconfigurations and weaknesses in Active Directory environments can lead to significant security breaches. It highlights the importance of proper password policies, user account management, and GPO configuration to prevent unauthorized access and privilege escalation in Windows-based networks. This machine serves as an invaluable learning opportunity for cybersecurity professionals seeking to enhance their skills in securing Active Directory environments and understanding the implications of common vulnerabilities.

## Initial Assessment

## Intial Assesment


## Initial Assesment


## Gaining a Foothold

### Obtaining User

### Escalating Privileges from User to Root


## Concluding Thoughts