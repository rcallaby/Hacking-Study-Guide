# MetaSploit

## What is Metasploit?

Metasploit is an open-source penetration testing tool that is designed to make it easier for security professionals to find and exploit vulnerabilities in networks, applications, and operating systems. The tool is widely used by penetration testers, ethical hackers, and security researchers around the world to identify and exploit security weaknesses in various systems.

## Metasploit Framework Architecture:

The Metasploit Framework is based on a client-server architecture, where the client is a console interface that interacts with the backend server, which is responsible for managing and executing the various exploits and payloads. The client provides a wide range of features that can be used to perform various tasks, such as creating and configuring payloads, selecting exploits, and launching attacks.

The Metasploit Framework is divided into three main components:

Exploits: These are the scripts or codes that take advantage of a vulnerability in a system or application.

Payloads: These are the codes or scripts that provide a way for the attacker to gain control over the compromised system.

Auxiliary: These are the scripts or codes that provide additional functionality, such as network scanning, fingerprinting, and brute-force attacks.

## How Penetration Testers Use Metasploit:

Penetration testers use Metasploit in various ways to identify and exploit security vulnerabilities. Some of the common use cases of Metasploit are:

Vulnerability Scanning: Metasploit can be used to scan for vulnerabilities in networks, applications, and operating systems. It can scan for various types of vulnerabilities, such as SQL injection, buffer overflows, and remote code execution.
For example, to scan for vulnerabilities in a web application, a penetration tester can use the following command:

```
msfconsole
use auxiliary/scanner/http/dir_scanner
set RHOSTS <target IP>
set THREADS 10
run
```

Exploiting Vulnerabilities: Once a vulnerability is identified, Metasploit can be used to exploit it and gain access to the system or application.
For example, to exploit a known vulnerability in an operating system, a penetration tester can use the following command:

```
msfconsole
use exploit/<exploit name>
set RHOST <target IP>
set PAYLOAD <payload>
set LHOST <attacker IP>
run
```

Payload Creation: Metasploit can be used to create custom payloads that can be used to gain access to a compromised system or application. These payloads can be customized to suit the specific requirements of the penetration test.
For example, to create a custom payload for a specific exploit, a penetration tester can use the following command:
```
msfvenom
-p <payload>
--platform <target OS>
--arch <target architecture>
-e <encoder>
-f <output format>
-o <output file>
```

Post-Exploitation: Metasploit can be used to perform post-exploitation activities, such as privilege escalation, data exfiltration, and lateral movement.
For example, to perform privilege escalation on a compromised system, a penetration tester can use the following command:
```
msfconsole
use post/multi/recon/local_exploit_suggester
set SESSION <session ID>
run
```
Reporting: Metasploit can be used to generate detailed reports on the vulnerabilities identified and the exploits used during the penetration testing.
For example, to generate a report on the vulnerabilities identified and the exploits used during a penetration testing, a penetration tester can use the following command:
```
msfconsole
use reporting/<reporting module
```
Social Engineering: Metasploit can be used to test the effectiveness of social engineering attacks, such as phishing, spear-phishing, and vishing.
For example, to test the effectiveness of a phishing attack, a penetration tester can use the following command:
```
msfconsole
use auxiliary/phishing/smtp_spoof
set TO <victim email>
set SUBJECT <email subject>
set BODY <email body>
set FROM <spoofed sender>
set SMTP_SERVER <SMTP server>
run
```
Password Cracking: Metasploit can be used to test the strength of passwords used in various systems and applications.
For example, to crack a password using Metasploit, a penetration tester can use the following command:
```
msfconsole
use auxiliary/scanner/ssh/ssh_login
set RHOSTS <target IP>
set USERNAME <username>
set PASS_FILE <password file>
run
```
Metasploit is a powerful tool that provides penetration testers with a wide range of features to identify and exploit vulnerabilities in various systems and applications. With its client-server architecture and modular design, it allows penetration testers to customize their attacks and payloads to suit their specific requirements. However, it is important to note that Metasploit should only be used by authorized security professionals for ethical and legal penetration testing purposes. Unauthorized use of Metasploit or any other hacking tool is strictly prohibited and can result in serious legal consequences.

### MetaSploit CheatSheet