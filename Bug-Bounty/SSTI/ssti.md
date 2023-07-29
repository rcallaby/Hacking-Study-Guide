# Server Side Template Injection

# Introduction:
As the field of bug bounty hunting and ethical hacking continues to gain prominence, new vulnerabilities and attack vectors are constantly being discovered. One such vulnerability is Server Side Template Injection (SSTI), a technique that allows an attacker to inject malicious code into a server-side template, leading to remote code execution and potential compromise of the target system. In this article, we will explore the concept of SSTI, its implications, and provide examples to illustrate its significance in bug bounty hunting and ethical hacking.

### Understanding Server Side Template Injection (SSTI):
Server Side Template Injection occurs when an application incorporates user input into a server-side template without proper validation or sanitization. Typically, templates are used to dynamically generate web pages or other content by embedding variables or expressions within the template file. However, if an application blindly evaluates user-supplied input within these templates, it opens up the possibility for an attacker to inject malicious code.

#### Implications of SSTI:
Exploiting SSTI can have severe consequences, including:

Remote Code Execution (RCE): By injecting malicious code into the template, an attacker can execute arbitrary commands on the server, gaining full control over it.
Information Disclosure: SSTI vulnerabilities may reveal sensitive information such as database credentials, internal system details, or source code, exposing the system to further attacks.

Server-Side Request Forgery (SSRF): Attackers can abuse SSTI to forge requests from the server to internal resources, potentially bypassing network restrictions and attacking internal systems.

### Examples of SSTI:
Let's examine a couple of examples to understand the mechanics of SSTI and how it can be leveraged in real-world scenarios:

#### Example 1: 

Python/Jinja2 Template Injection:
Consider a web application that uses the Python-based Jinja2 template engine. The application allows users to create blog posts with titles and content. However, a lack of proper input validation makes it vulnerable to SSTI.

An attacker could exploit this vulnerability by injecting malicious code into the title field, such as:
```
{{ 7 * 7 }}
```
The template engine will evaluate the expression and display the result, 49, on the page. However, an attacker could go further and execute arbitrary code, such as:
```
{{ ''.__class__.__mro__[1].__subclasses__()[216]('cat /etc/passwd', shell=True, stdout=-1).communicate()[0].strip() }}
```
This code exploits the subprocess module to execute a shell command and retrieve the contents of the /etc/passwd file, leaking sensitive system information.

#### Example 2: 

Ruby/ERB Template Injection:
Suppose an application uses the Ruby programming language with the ERB templating engine. Users can submit feedback, which is rendered in an HTML email template.

An attacker can inject code into the feedback form, such as:

```
<%= 7 * 7 %>
```
Similar to the previous example, the injected expression is evaluated, and the result, 49, is included in the email. However, the attacker can escalate the attack by executing arbitrary code, for instance:

```
<%= %x(cat /etc/passwd) %>
```
This code uses the backticks to execute a shell command, reading the contents of the /etc/passwd file and potentially exposing user credentials and other sensitive data.

## Bug Bounty Hunting and Ethical Hacking:
When engaging in bug bounty hunting or ethical hacking, SSTI vulnerabilities present an excellent opportunity for discovering critical flaws in web applications. Here are some tips for identifying and exploiting SSTI vulnerabilities:

### Reconnaissance:

Conduct thorough reconnaissance to identify the technologies and frameworks employed by the target application2. Identify Template Engines: Determine the template engine used by the application, as different engines have varying syntax and behaviors.
Input Validation: Look for user input being directly incorporated into templates without proper validation or sanitization.
Test Template Injection: Inject payloads and expressions to test if they are being evaluated by the template engine. Start with basic payloads like {{ 7 * 7 }} and observe the output for potential injection points.

### Exploit and Escalate: 

If successful, escalate the attack by executing arbitrary code. Explore the capabilities of the template engine and leverage its functionalities to achieve remote code execution or information disclosure.
Reporting and Responsible Disclosure: Document your findings and report them to the organization or platform through responsible disclosure channels, ensuring that the vulnerabilities are addressed and patched.

# Conclusion:
Server Side Template Injection is a critical vulnerability that can lead to remote code execution and compromise of web applications. In bug bounty hunting and ethical hacking, discovering and exploiting SSTI vulnerabilities can be rewarding, as they often expose serious flaws in the target systems. By understanding the mechanics of SSTI, employing proper reconnaissance, and following responsible disclosure practices, security researchers play a vital role in helping organizations fortify their defenses and protect user data from potential attacks.

### Tutorials for SSTI

### Payloads for SSTI