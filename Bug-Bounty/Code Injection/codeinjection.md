# Code Injection

Code injection is a common attack technique used by attackers to exploit vulnerabilities in software applications. In this technique, an attacker injects malicious code into a vulnerable application to gain unauthorized access or to execute arbitrary code on the target system.

In penetration testing, code injection is often used to test the security of an application and to identify any vulnerabilities that could be exploited by attackers. The purpose of this type of testing is to identify and remediate any security weaknesses before they can be exploited by malicious actors.

Here are some common examples of code injection techniques:

SQL Injection: SQL injection is a common code injection technique that targets web applications that use a backend database. The attacker injects malicious SQL commands into the input fields of the web application to gain unauthorized access to the database or to execute arbitrary code on the target system.
For example, if a web application uses an SQL query to retrieve data from a database, an attacker can inject a command into the input field to retrieve data from other tables, delete data, or execute arbitrary commands on the database.

Command Injection: Command injection is a code injection technique that targets applications that execute system commands. The attacker injects malicious commands into the input fields of the application to execute arbitrary commands on the target system.
For example, if a web application allows users to execute system commands, an attacker can inject a command to retrieve sensitive information from the system, delete files, or execute arbitrary commands on the system.

Code Injection: Code injection is a technique where the attacker injects malicious code into a target application to gain unauthorized access or to execute arbitrary code on the target system.
For example, an attacker can inject a malicious code into a web application to steal sensitive information or to execute arbitrary code on the target system.

Overall, code injection is a powerful technique used by attackers to exploit vulnerabilities in software applications. It is important for developers to build secure applications that are resistant to code injection attacks, and for organizations to perform regular penetration testing to identify and remediate any security weaknesses.

## Tools for Code Injection
[commix](https://github.com/commixproject/commix) - An all in one command injection penetration testing tool
[Burp Suite](https://portswigger.net/burp) - You can use the popular website penetration testing tool for command injection as well 
[SQLMap](https://github.com/sqlmapproject/sqlmap) - A Automatic SQL Injection and Database takeover tool
[jSQL Injection](https://github.com/ron190/jsql-injection) - A java application for automatic SQL Database injection
[BBQSQL](https://manpages.ubuntu.com/manpages/focal/en/man1/bbqsql.1.html) - This is a blind SQL injection framework written in Python
[NoSQLMap](https://github.com/codingo/NoSQLMap) - An automated NoSQL database enumeration and web exploitation tool
[DSSS](https://github.com/stamparm/DSSS) - Darn Small SQLi Scanner
[Explo] - A human readable and machine readable web vulnarability testing format
[Blind-SQL-Bitshifting](https://github.com/awnumar/blind-sql-bitshifting) - A module that performs blind SQL injection by using the bitshifting method

## Tutorials for Code Injection
[Code Injection](https://learn.snyk.io/lessons/malicious-code-injection/javascript/) - A pretty good overview of code injection by synkLearn
[A Pentesters Guide to Code Injection](https://www.cobalt.io/blog/a-pentesters-guide-to-code-injection) - A fairly good overview to Code Injection tutorial by Cobalt.io
[Code Injection: An Easy Guide in 5 Points](https://u-next.com/blogs/cyber-security/code-injection/) - A fairly good overview by Jigsaw Academy
[Code Injection in Brief: Types, Examples, and Mitigation](https://brightsec.com/blog/code-injection/)
