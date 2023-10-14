# Network Penetration Testing Checklist

This is a work in progress at the moment, meaning that I may be missing something. If you know of what I could be missing and want to add to this file then please create a feature request detailing what you want to add and then add it via a pull request.

## Host Discovery
DNS Footprinting to Enumerate DNS Records

- [ ] A - A record is used to point to the domain name
- [ ] MX - Records reponsible for email exchange
- [ ] NS - Identify DNS servers responsible for DNS records
- [ ] SRV - Records to distinguish the service hosted on specific servers
- [ ] PTR - Reverse DNS Lookup
- [ ] SOA - Start of Record
- [ ] CNAME - CNAME maps a domain name to another domain name
## Port Scanning
Port Scanning using the following tools: Nmap, Netscan tools, and Network Monitor

- [ ] Nmap Scan for open ports - such as nmap -open google.com
- [ ] Nmap Scan for a specific port - nmap -p 80 10.10.123.92

## Banner Grabbing/OS Fingerprinting

- [ ] Perform Banner Grabbing with tools such as:
    - [ ] Telnet
    - [ ] IDServe
    - [ ] Nmap

## Scan for possible vulnerabilities
- [ ] GFILanguard
- [ ] Nessus


## Prepare Proxies
- [ ] Proxifier
- [ ] SSL Proxy
- [ ] Proxy Finder

## Document Findings
- Document all findings as per the rules and the scope of the penetration test