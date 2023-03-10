# Bug Bounty Checklist

Below is a checklist that I am in the process of making, if you have anything meaningful to add to it please feel free to create a feature request issue and explain how you could improve it. If I agree then please feel to improve it and issue a pull request

## Recon on Wildcard Domains
* [ ] run amass
* [ ] run subfinder
* [ ] run dnsgen
* [ ] run massdns 
* [ ] run httprobe
* Ideally, put all the output of the programs above into a single file and then eliminate duplicates

## Run automated tools below to check for vulnerabilities
* [ ] Nmap
* [ ] Burp Crawler
* [ ] ffuf
* [ ] Linkfinder

## Manually check to find other sensitive information you may have missed
* [ ] Google Dorks
* [ ] OSINT
* [ ] Shodan
* [ ] Github
* [ ] Pastebin
* [ ] Censys
* [ ] LeakIX

## Gather as much information as possible using various methods
* [ ] Spider/Crawl for missing content
* [ ] Check the robots.txt, sitemap.xml
* [ ] Perform Web Application finger printing
* [ ] Identify users and the roles in place
* [ ] Identify the entry points for applications
* [ ] Identify any Debug Parameters found
* [ ] Identify client side code
* [ ] Be sure to also manually explore the website and the metadata and source code

## Checking for configuration errors
* [ ] Check for any old backups and any unreferenced files
* [ ] Test file extension handling
* [ ] Test for policies
* [ ] Test for non-production data where it shouldn't be (live production)
* [ ] Look for sensitive data in client side (such as API keys, credentials)

