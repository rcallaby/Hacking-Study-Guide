# SSRF Service Side Request Forgery

As a penetration tester, it is important to be aware of the SSRF (Server-Side Request Forgery) vulnerability as it can allow attackers to perform malicious actions on behalf of a vulnerable application.

SSRF is a type of web vulnerability that occurs when an application makes a request to an external resource using user-supplied data, but fails to properly validate or sanitize the input. This can allow an attacker to craft a request that is not intended, such as sending requests to internal resources that are not meant to be accessible from the internet.

One common scenario of SSRF is when an application uses the user-supplied data to construct a URL and then fetches the content of that URL. If the application does not validate the input, an attacker can manipulate the URL to point to an internal resource, such as a local file, an internal network service, or even the application itself. This can result in information disclosure, data manipulation, or even remote code execution.

### Identifying SSRF Vulnerabilities

To identify SSRF vulnerabilities, a penetration tester needs to first understand how the application is processing user-supplied data, and then craft specific requests to test the validity of the input. This can involve sending requests to internal resources, such as localhost, and observing the application's behavior.

Once a SSRF vulnerability has been identified, the penetration tester should assess the severity of the issue and the potential impact to the organization. In some cases, SSRF can allow an attacker to gain access to sensitive information, such as server configuration files, or to execute malicious code on the target system.

### Preventing SSRF Vulnerabilities

To prevent SSRF vulnerabilities, it is important to properly validate and sanitize user-supplied data, and to restrict the use of untrusted data when making requests to external resources. Additionally, organizations should implement security controls, such as firewalls, to limit access to internal resources, and regularly monitor and test their applications for potential security issues.

SSRF is a serious vulnerability that can have significant impact to an organization's security. As a penetration tester, it is important to be aware of the potential for SSRF and to test for these vulnerabilities as part of a comprehensive security assessment.

## Top Tools used to detect and exploit SSRF

* [SSRFire](https://github.com/ksharinarayanan/SSRFire) - Automated SSRF Finder it can also find XSS and open redirects
* [httprebind](https://github.com/daeken/httprebind) - Automatic tool for DNS rebinding
* [ssrf-sheriff](https://github.com/teknogeek/ssrf-sheriff) - SSRF Testing written in Go
* [B-XSSRF](https://github.com/SpiderMate/B-XSSRF) - It can detect and keep track of blind XSS, XXE, and SSRF
* [ssrfDetector](https://github.com/JacobReynolds/ssrfDetector) - It does what it is named after it detects SSRF
* [sentrySSRF](https://github.com/xawdxawdx/sentrySSRF) - Searches sentry config to check blind SSRF
* [whonow](https://github.com/brannondorsey/whonow) - This is a malicious DNS server for executing DNS Rebinding attacks on the fly
* [dref](https://github.com/FSecureLABS/dref) - DNS Rebinding tool and framework
* [rbndr](https://github.com/taviso/rbndr) - It is a simple DNS Rebinding Tool
* [dnsFookup](https://github.com/makuga01/dnsFookup) - DNS Rebinding Toolkit

## Good Tutorials on SSRF
* [Server Side Request Forgery (SSRF)](https://portswigger.net/web-security/ssrf) - A tutorial and overview by PortSwigger
* [Server Side Request Forgery in Depth](https://www.geeksforgeeks.org/server-side-request-forgery-ssrf-in-depth/) - A pretty good tutorial by GeeksforGeeks
* [Beginner Guide To Exploit Server Sdie Request Forgery Vulnerability](https://infosecwriteups.com/exploiting-server-side-request-forgery-ssrf-vulnerability-faeb7ddf5d0e) - A pretty solid overview by inforsec write ups
* [Server Side Request Forgery - SSRF Security Testing](https://www.hackerone.com/application-security/how-server-side-request-forgery-ssrf) - A good tutorial by HackerOne

### Payloads for SSRF