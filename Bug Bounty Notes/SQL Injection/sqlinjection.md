# SQL Injection

As a bug bounty hunter, SQL injection vulnerabilities are a high-priority target because they can allow attackers to gain unauthorized access to sensitive information or even take control of a website or application.

SQL injection occurs when an attacker is able to inject malicious SQL code into a vulnerable web application, which is then executed by the database. This can happen when an application does not properly sanitize user input, allowing an attacker to insert their own SQL statements.

To find SQL injection vulnerabilities, a bug bounty hunter can use a variety of methods, including:

Manual testing: By using tools like Burp Suite or OWASP ZAP, a tester can manually inject SQL code into web forms and other input fields to see if the application is vulnerable. This method is time-consuming and requires a high degree of technical knowledge.

Automated testing: There are many automated vulnerability scanners that can detect SQL injection vulnerabilities, such as SQLMap or Netsparker. These tools can scan an entire application and report any vulnerabilities they find, which can save time for the tester.

Fuzzing: Fuzzing involves generating large amounts of random or semi-random input to see how the application responds. By fuzzing an application's input fields, a tester can sometimes trigger unexpected behavior that reveals a SQL injection vulnerability.

Once a SQL injection vulnerability has been identified, a bug bounty hunter can typically exploit it to gain unauthorized access to the application or database. This might involve using SQL commands to extract data, modify data, or even execute code on the server.

It's important to note that SQL injection vulnerabilities can be prevented by properly sanitizing user input and using prepared statements with parameterized queries. However, many applications still contain these vulnerabilities, which is why they are a popular target for bug bounty hunters.

## Tools to help find SQL Injection Vulnerabilities
* [sqlmap](https://github.com/sqlmapproject/sqlmap) - Automatic SQL Injection and Database takeover tool
* [NoSQLMap](https://github.com/codingo/NoSQLMap) - Automated NoSQL database enumeration and web app exploit tool
* [SQLiScanner](https://github.com/0xbug/SQLiScanner) - This is an automatic SQL Injection with sqlmap api
* [sqli-hunter](https://github.com/zt2/sqli-hunter) - It is a simple HTTP/HTTPS proxy server that helps in finding SQL Injections
* [waybacksqlscanner](https://github.com/ghostlulzhacks/waybackSqliScanner) - This gathers urls from the wayback machine then tests for sql injection using the GET parameter
* [burp-to-sqlmap](https://github.com/Miladkhoshdel/burp-to-sqlmap) - This performs SQLInjection test on Burp Suite Bulk Requests using SQLMap
* [andor](https://github.com/sadicann/andor) - Blind SQL Injection tool written in Golang
* [nosqli](https://github.com/Charlie-belmer/nosqli) - NoSql Injection Command Line Tool that finds websites using MongoDB