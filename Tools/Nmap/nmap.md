# Nmap

Nmap is a powerful open-source network scanner tool used for network exploration, security auditing, and network reconnaissance. It is one of the most popular tools used by penetration testers and network administrators for identifying open ports, services running on those ports, and other important network information.

In this article, we will cover what Nmap is, how it works, and provide a step-by-step guide on how to use it effectively.

## What is Nmap?

Nmap (Network Mapper) is an open-source tool designed to scan and map networks. It can be used to identify hosts and services on a network, as well as detect vulnerabilities and security issues. It was first released in 1997 and has since become a standard tool for network security professionals.

## How does Nmap work?

Nmap works by sending packets to a target network and analyzing the responses received. It uses a variety of scanning techniques such as TCP, UDP, SYN, and FIN scans to identify hosts, services, and open ports.

The tool also has a number of advanced features, such as OS fingerprinting, service version detection, and scripting capabilities, which can be used to obtain even more information about the target network.

Step-by-step guide to using Nmap:

+ Install Nmap:
Nmap can be installed on a variety of operating systems, including Windows, Linux, and macOS. To install Nmap, simply download the appropriate package for your operating system from the official website (https://nmap.org/download.html) and follow the installation instructions.

+ Determine your target:
Before you can start using Nmap, you need to determine the target network that you want to scan. This can be done by identifying the IP address range that corresponds to the network you are interested in.

+ Basic scan:
Once you have identified your target network, you can perform a basic scan by running the following command:

```
nmap [target IP address or range]

```
This will perform a simple scan of the target network, identifying hosts and open ports.

+ Scan for specific ports:
If you want to scan for specific ports, you can use the -p option followed by a comma-separated list of ports. For example, to scan for ports 80, 443, and 8080, you would use the following command:

```
nmap -p 80,443,8080 [target IP address or range]

```
+ Scan for all ports:
To scan for all ports, you can use the -p- option. For example:

```
nmap -p- [target IP address or range]

```
Note that scanning all ports can be time-consuming and may generate a large amount of network traffic.

+ OS fingerprinting:
Nmap can be used to identify the operating system running on a target system. This is done using the -O option. For example:

```
nmap -O [target IP address or range]
```

+ Service detection:
Nmap can also be used to detect the services running on a target system. This is done using the -sV option. For example:

```
nmap -sV [target IP address or range]
```
+ Scripting:
Nmap also has a number of built-in scripts that can be used to automate certain tasks, such as detecting vulnerabilities or performing brute-force attacks. These scripts can be accessed using the --script option. For example:

```
nmap --script [script name] [target IP address or range]
```

Nmap is a powerful network scanning tool that can be used by penetration testers and network administrators to identify hosts, open ports, services, and vulnerabilities on a target network.

## NMAP Scripting Engine (NSE)
Nmap Scripting Engine (NSE) is a powerful tool that comes with Nmap, a widely used open-source network scanner. NSE allows penetration testers to automate and customize their network reconnaissance and vulnerability scanning tasks. In this article, we will discuss NSE from the perspective of a penetration tester and provide examples of how to use it.

## What is Nmap Scripting Engine (NSE)?

NSE is a framework built into Nmap that allows users to write and execute scripts in order to automate and customize their network scanning tasks. These scripts can perform a variety of tasks, including vulnerability scanning, service enumeration, host discovery, and more. NSE is written in the Lua programming language, which is a lightweight and fast scripting language.

## Why use Nmap Scripting Engine (NSE)?

Penetration testers often use Nmap as a basic tool for network scanning, but its default scanning options may not be enough to thoroughly assess a network. NSE allows penetration testers to customize their scans and perform additional tests that are not available with the default Nmap options. Additionally, NSE provides a way to automate repetitive tasks, which can save time and increase efficiency.

## How to use Nmap Scripting Engine (NSE)

NSE scripts are located in the /usr/share/nmap/scripts directory (on Linux systems), and there are over 600 scripts available for use. To run an NSE script, simply specify the script name with the -sC or -sV option when running Nmap. For example, to run the default set of NSE scripts, use the following command:

```
nmap -sC <target>
```
To run a specific script, use the -script option followed by the script name. For example, to run the http-headers script, use the following command:

```
nmap -sV --script http-headers <target>
```
NSE scripts can also be combined with other Nmap options to perform more specific scans. For example, to perform a scan of all ports and run the http-headers script on any ports with HTTP services, use the following command:

```
nmap -p- -sV --script http-headers <target>

```
NSE scripts can also be used with the Nmap Scripting Engine Arguments (-script-args) option to provide additional input to the script. For example, to run the http-sql-injection script with a specific payload, use the following command:

```
nmap -sV --script http-sql-injection --script-args http-sql-injection.payload="SELECT 1" <target>

```
## Examples of using Nmap Scripting Engine (NSE)

Service Enumeration
NSE can be used to identify the services running on a target system. The following command will run the default set of NSE scripts to identify services running on a target:

```
nmap -sC <target>

```
Vulnerability Scanning
NSE can be used to scan for vulnerabilities in a target system. The following command will run the vuln script to identify vulnerabilities on a target:

```
nmap -sV --script vuln <target>

```
Network Discovery
NSE can be used to discover hosts and subnets on a network. The following command will run the broadcast-avahi-dos script to discover hosts on the local network using the Avahi service:

```
nmap --script broadcast-avahi-dos

```
Web Application Scanning
NSE can be used to scan web applications for vulnerabilities. The following command will run the http-sql-injection script to scan for SQL injection vulnerabilities on a target web application:

```
nmap -sV --script http-sql-injection <target>

```
NSE is a powerful tool that can greatly enhance the capabilities of Nmap for penetration testing. It allows for automation and customization of network scanning tasks, and provides a way to perform additional tests that are not available with the default Nmap options. With over 600 scripts available, NSE provides a wide range of capabilities for network reconnaissance and vulnerability scanning.

It is important to note that NSE scripts can be very powerful and can potentially cause damage to systems if not used properly. It is important for penetration testers to understand the scripts they are running and to use them responsibly. Additionally, it is recommended to run NSE scripts with caution and permission from the target system owner.

NSE is a valuable tool for penetration testers and network administrators to assess and secure their networks. Its flexibility and customization options make it a must-have for any security professional's toolkit.

