# Passwords and File Permissions

First I would check the history of the commands run. So, just run the history command to see what has been typed in beforehand.

You will want to check [Payloads all the things](https://github.com/swisskyrepo/PayloadsAllTheThings) for more possible places to check for passwords and file permissions.

## Passwords:

Passwords are the most common form of authentication used to secure access to online accounts, applications, and devices. They are intended to prevent unauthorized access and protect sensitive information from being compromised. However, passwords are only effective if they are strong and kept confidential.

As a penetration tester, your goal is to identify vulnerabilities in an organization's security measures, including weak passwords. There are several ways to do this, including:

Password cracking: This involves using specialized tools and techniques to guess or crack passwords. This can be done through brute force attacks, which try every possible combination of characters until the correct password is found, or through dictionary attacks, which use a pre-built list of common passwords and variations.

Password spraying: This involves using a few common passwords and trying them across a large number of accounts. This technique can be effective if an organization has a large number of users with weak passwords.

Social engineering: This involves using psychological manipulation to trick users into revealing their passwords. This can be done through phishing attacks, where an attacker sends a fake email or website that looks like a legitimate one and asks for the user's password.

Password reuse: This involves using the same password across multiple accounts. If a user's password is compromised on one account, the attacker can use it to access other accounts.

To prevent these types of attacks, organizations should enforce strong password policies that require users to choose complex passwords and change them regularly. Multi-factor authentication can also be used to provide an additional layer of security.

## Port Forwarding:

Port forwarding is a technique used to allow external devices to access services running on a local network. It involves redirecting traffic from a specific port on the router to a specific port on a device on the network. This can be useful for running servers or accessing devices remotely.

As a penetration tester, port forwarding can be used to bypass firewalls and other security measures to access services that are not intended to be accessible from the internet. This can be done through:

Port scanning: This involves using tools to scan for open ports on a network. If a port is open and forwarding traffic to a device, the attacker can use that port to access the device.

Port forwarding exploitation: This involves exploiting vulnerabilities in the port forwarding configuration to gain access to devices on the network.

To prevent these types of attacks, organizations should only allow port forwarding for necessary services and should ensure that the configuration is secure. This includes using strong passwords for any devices that are accessible through port forwarding and monitoring network traffic for any suspicious activity.

## Step-by-Step Directions:

While providing a comprehensive guide on both passwords and port forwarding would require a significant amount of time and detail, here are some general steps that a penetration tester may follow to identify vulnerabilities in these areas:

+ Identify the target: Determine the scope of the test and identify the systems or applications that will be tested.

+ Gather information: Use tools such as Nmap or Recon-ng to gather information about the target network or application. This includes identifying open ports, services, and applications that are running.

+ Identify weak passwords: Use tools such as John the Ripper or Hashcat to crack or guess passwords. This can be done through brute force attacks, dictionary attacks, or password spraying.

+ Exploit port forwarding: Use tools such as Metasploit or Burp Suite to exploit vulnerabilities in the port forwarding configuration. This may involve scanning for open ports, identifying weak passwords on devices accessible through port forwarding, or exploiting known vulnerabilities in the software or firmware.

+ Report findings: Compile a report of the vulnerabilities identified and provide recommendations for remediation.

## Tools for Passwords
* [JackTheRipper](https://github.com/openwall/john) - A pretty complex and sophisisticated password cracking program that is open source.
* [Hydra](https://github.com/vanhauser-thc/thc-hydra) - One of the best tools for password cracking
* [Cain & Abel](https://github.com/xchwarze/Cain) - Password recovery tool 
* [Ophcrack](https://github.com/luisgg/ophcrack) - Password recovery tool
* [Hashcat](https://github.com/hashcat/hashcat) - Another good password cracking tool, can be complicated to use

## Tools for File Permissions
* [Linux Exploit Suggester 2](https://github.com/rebootuser/LinEnum) - A Next Generation Linux Kernel Exploit Suggester
* [LinPEAS](https://github.com/carlospolop/PEASS-ng/tree/master/linPEAS) - Linux Privilege Escalation Awesome Script
* [LinEnum](https://github.com/rebootuser/LinEnum) - A local linux enumeration and privilege escalation checks

