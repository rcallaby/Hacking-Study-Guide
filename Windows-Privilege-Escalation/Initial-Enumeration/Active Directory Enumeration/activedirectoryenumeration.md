# Active Directory Enumeration

As a penetration tester, there are various methods and tools that can be used to enumerate an Active Directory (AD) during an assessment. Here are some of the possible commands and tools that can be used:

Nmap: Nmap is a popular network scanning tool that can be used to discover hosts, ports, and services. It can be used to scan the AD network and identify the hosts and their open ports.

```
nmap -p 1-65535 -sV -O -oA ad_scan <AD IP range>

```
Netdiscover: Netdiscover is a tool used for passive network discovery. It sends ARP requests and listens for responses to identify live hosts on the network.

```
netdiscover -i eth0 -r <AD IP range>

```
BloodHound: BloodHound is a tool used to identify the trust relationships in an AD environment. It can be used to identify the domain admins, high-privilege users, and potential attack paths.

PowerView: PowerView is a PowerShell tool used for AD enumeration. It can be used to retrieve information about AD objects, including users, groups, computers, and trusts.

```
Import-Module .\PowerView.ps1
Get-NetDomainController -Domain <domainname>
Get-NetUser -Domain <domainname>
Get-NetComputer -Domain <domainname>

```
ADInfo: ADInfo is a tool used to extract information about AD objects. It can be used to extract information about users, groups, computers, and trust relationships.

```
adinfo -u -c -g -t <domainname>

```
LDAP Enumeration: Lightweight Directory Access Protocol (LDAP) can be used to extract information about AD objects. Tools like ldapsearch can be used to extract information about users, groups, computers, and trust relationships

```
ldapsearch -h <AD IP> -x -s base namingcontexts
ldapsearch -h <AD IP> -x -b "dc=<domainname>,dc=<tld>" -s sub "(&(objectClass=user)(objectCategory=person))"

```
These are some of the commands and tools that can be used to enumerate an AD during an assessment. It is important to note that different tools may provide different results, and the results should be correlated to identify potential attack paths and vulnerabilities.