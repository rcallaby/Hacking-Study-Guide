# Google Dorking

Google Dorking, also known as Google Hacking or Google-fu, is a technique used by hackers, security professionals, and investigators to search for sensitive information that is not normally accessible through conventional search methods. It involves using advanced search operators or queries to find information that is not readily available to the public.

Google Dorking is not an illegal activity, but it can be used for malicious purposes if not used ethically. It is important to use this technique responsibly and legally, and with the intention of improving security measures rather than exploiting vulnerabilities.

Google Dorking can be used to find a variety of information, including but not limited to:

+ Sensitive documents and files (e.g., password files, configuration files, source code, etc.)
+ Vulnerable servers and web applications
+ Open network devices (e.g., cameras, routers, switches, etc.)
+ Personal information (e.g., email addresses, phone numbers, usernames, etc.)
+ Online services with known vulnerabilities

## Examples of Google Dorks

There are countless Google Dorks that can be used to find specific information. Here are some examples of commonly used dorks:

+ Filetype Dorks
A "filetype" dork can be used to search for a specific type of file on a website or server. For example, if you want to find all PDF files related to a particular topic, you can use the following dork:

```
filetype:pdf site:example.com "your query"

```
+ Intitle Dorks

The "intitle" operator can be used to search for websites or pages that have specific keywords in their title. For example, if you want to find all websites related to a particular topic, you can use the following dork:

```
intitle:"your query"

```
+ Link Dorks

The "link" operator can be used to find pages that link to a specific website or page. For example, if you want to find all websites that link to a particular website, you can use the following dork:

```
link:example.com

```
+ Cache Dorks

The "cache" operator can be used to find the cached version of a specific website or page. For example, if you want to find the cached version of a website that has been removed, you can use the following dork:

```
cache:example.com

```
+ Site Dorks

The "site" operator can be used to search for specific keywords or phrases on a specific website or domain. For example, if you want to find all pages on a specific website that contain a certain keyword, you can use the following dork:

```
site:example.com "your query"

```
+ Password Dorks

Password dorks are used to find pages that contain password information, such as usernames and passwords, configuration files, etc. For example, if you want to find all pages that contain passwords related to a particular website, you can use the following dork:

```
site:example.com intext:password

```
+ Vulnerability Dorks

Vulnerability dorks are used to find websites or servers that have known vulnerabilities that can be exploited. For example, if you want to find websites or servers that are vulnerable to a specific exploit, you can use the following dork:

```
site:example.com inurl:exploit

```
+ Filetype Dorks

Filetype dorks are used to find specific file types on websites or servers. For example, if you want to find all PHP files on a website, you can use the following dork:

```
site:example.com filetype:php

```
+ Directory Dorks

Directory dorks are used to find specific directories on websites or servers. For example, if you want to find all directories related to a particular topic on a website

```
site:example.com inurl:/directory/

```
* Related Dork

This will list webpages that are similar to a specified web page
```
related: www.amazon.com
```
* All in Text Dork

This will search for occurances of the keywords given
```
allintext: "keyword"
```


## Large List of Google Dorks

```

filetype:SWF SWF
filetype:TXT TXT
filetype:XLS XLS
filetype:asp   DBQ=" * Server.MapPath("*.mdb")
filetype:asp "Custom Error Message" Category Source
filetype:asp + "[ODBC SQL"
filetype:asp DBQ=" * Server.MapPath("*.mdb")
filetype:asp DBQ=\" * Server.MapPath(\"*.mdb\") 
filetype:asp “Custom Error Message” Category Source
filetype:bak createobject sa
filetype:bak inurl:"htaccess|passwd|shadow|htusers"
filetype:bak inurl:\"htaccess|passwd|shadow|htusers\" 
filetype:conf inurl:firewall -intitle:cvs 
filetype:conf inurl:proftpd. PROFTP FTP server configuration file reveals
filetype:dat "password.dat
filetype:dat \"password.dat\" 
filetype:eml eml +intext:"Subject" +intext:"From" +intext:"To"
filetype:eml eml +intext:\"Subject\" +intext:\"From\" +intext:\"To\" 
filetype:eml eml +intext:”Subject” +intext:”From” +intext:”To”
filetype:inc dbconn 
filetype:inc intext:mysql_connect
filetype:inc mysql_connect OR mysql_pconnect 
filetype:log inurl:"password.log"
filetype:log username putty PUTTY SSH client logs can reveal usernames
filetype:log “PHP Parse error” | “PHP Warning” | “PHP Error”
filetype:mdb inurl:users.mdb


intext:" -FrontPage-" ext:pwd inurl:(service | authors | administrators | users)
intext:""BiTBOARD v2.0" BiTSHiFTERS Bulletin Board"
intext:"# -FrontPage-" ext:pwd inurl:(service | authors | administrators | users) "# -FrontPage-" inurl:service.pwd
intext:"#mysql dump" filetype:sql
intext:"#mysql dump" filetype:sql 21232f297a57a5a743894a0e4a801fc3
intext:"A syntax error has occurred" filetype:ihtml
intext:"ASP.NET_SessionId" "data source="
intext:"About Mac OS Personal Web Sharing"
intext:"An illegal character has been found in the statement" -"previous message"
intext:"AutoCreate=TRUE password=*"
intext:"Can't connect to local" intitle:warning
intext:"Certificate Practice Statement" filetype:PDF | DOC
intext:"Certificate Practice Statement" inurl:(PDF | DOC)
intext:"Copyright (c) Tektronix, Inc." "printer status"
intext:"Copyright © Tektronix, Inc." "printer status"
intext:"Emergisoft web applications are a part of our"
intext:"Error Diagnostic Information" intitle:"Error Occurred While"
intext:"Error Message : Error loading required libraries."
intext:"Establishing a secure Integrated Lights Out session with" OR intitle:"Data Frame - Browser not HTTP 1.1 compatible" OR intitle:"HP Integrated Lights-
intext:"Fatal error: Call to undefined function" -reply -the -next
intext:"Fill out the form below completely to change your password and user name. If new username is left blank, your old one will be assumed." -edu
intext:"Generated   by phpSystem"
intext:"Generated by phpSystem"

Use these to find potential vulnerable websites:


inurl:php?=id1
inurl:index.php?id=
inurl:trainers.php?id=
inurl:buy.php?category=
inurl:article.php?ID=
inurl:play_old.php?id=
inurl:declaration_more.php?decl_id=
inurl:pageid=
inurl:games.php?id=
inurl:page.php?file=
inurl:newsDetail.php?id=
inurl:gallery.php?id=
inurl:article.php?id=
inurl:show.php?id=
inurl:staff_id=
inurl:newsitem.php?num= andinurl:index.php?id=
inurl:trainers.php?id=
inurl:buy.php?category=
inurl:article.php?ID=
inurl:play_old.php?id=
inurl:declaration_more.php?decl_id=
inurl:pageid=
inurl:games.php?id=
inurl:page.php?file=
inurl:newsDetail.php?id=
inurl:gallery.php?id=
inurl:article.php?id=
inurl:show.php?id=
inurl:staff_id=
inurl:newsitem.php?num=

```