# Improper Authentication 

Improper authentication is a common vulnerability that is often found during penetration testing. Improper authentication occurs when a system fails to properly authenticate users or authenticate them in a secure manner. This can allow attackers to gain unauthorized access to the system or data. Here are a few examples of improper authentication vulnerabilities:

Weak passwords: If a system allows users to choose weak passwords, such as "password" or "123456," it can be easily hacked through brute force attacks. Attackers can use automated tools to try a large number of passwords until they find the right one.

Lack of multi-factor authentication: When a system does not require a second form of authentication, such as a token or biometric scan, it is vulnerable to attacks that bypass the password-based authentication. For example, if a user's password is compromised, a hacker can easily gain access to the system without any additional challenge.

Authentication bypass: Some systems have vulnerabilities that allow attackers to bypass the authentication process entirely, such as by manipulating the URL or cookie values.

Default or weak credentials: Many devices and software applications come with default usernames and passwords, which are often publicly available. Attackers can exploit these vulnerabilities to gain access to the system.

Session hijacking: When a system does not properly protect user sessions, an attacker can steal the user's session cookie and use it to impersonate the user and gain access to their account.

Insecure password recovery: If a system allows users to recover their passwords through an insecure method, such as by answering security questions that can be easily guessed or found online, it can be vulnerable to attacks.

During a penetration testing engagement, testers will attempt to exploit these types of vulnerabilities to determine if the system can be easily compromised. The goal is to identify these issues before attackers can find and exploit them.

## Tools for Improper Authentication
* [BruteX](https://github.com/1N3/BruteX) - brute force services on a target
* [patator](https://github.com/lanjelot/patator) - Multi brute forcer with a flexble usage
* [thc-hydra](https://github.com/vanhauser-thc/thc-hydra) - a login cracker that can support numerous protocols
* [DefaultCreds-cheat-sheet](https://github.com/ihebski/DefaultCreds-cheat-sheet) - This is as you can imagine it a cheatsheet for various programs and devices
* [changeme](https://github.com/ztgrace/changeme) - A default credential scanner
* [Burp Suite](https://portswigger.net/burp) - One of the most comphrensive tools you can use, it incorporates many features you will need in just one tool

## Tutorials for Improper Authentication