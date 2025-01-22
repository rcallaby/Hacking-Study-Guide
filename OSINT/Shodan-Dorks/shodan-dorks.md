# A list of Shodan Dorks

### General Queries

| **Query**                         | **Description**                                                                                           | **Example**                                                                                      |
|-----------------------------------|-----------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
| `city:"[city name]"`              | Find devices located in a specific city.                                                                 | `city:"Chicago"` searches for devices in Chicago.                                         |
| `country:"[country code]"`        | Search for devices in a specific country using the ISO country code.                                     | `country:"US"` finds devices in the United States.                                              |
| `geo:"[latitude],[longitude]"`    | Search for devices at a specific geographical location using latitude and longitude.                     | `geo:"51.5072,0.1276"` searches around New York City’s coordinates.                           |
| `hostname:"[hostname]"`           | Look for devices with a specific hostname.                                                               | `hostname:"example.com"` returns devices hosted under example.com.                              |
| `net:"[IP range]"`                | Find devices within a specific IP range.                                                                 | `net:"192.168.1.0/24"` finds devices in the IP range 192.168.1.0–192.168.1.255.                 |
| `os:"[operating system]"`         | Search for devices running a specific operating system.                                                   | `os:"Windows"` returns devices running Windows.                                                 |
| `port:"[port number]"`            | Find devices with a specific open port.                                                                  | `port:22` returns devices with SSH running on port 22.                                          |
| `org:"[organization name]"`       | Search for devices associated with a specific organization.                                               | `org:"Google"` finds devices owned by Google.                                                   |
| `isp:"[ISP name]"`                | Search for devices using a specific ISP (Internet Service Provider).                                     | `isp:"Comcast"` finds devices using Comcast as their ISP.                                       |
| `product:"[product name]"`        | Find devices running a specific software product.                                                        | `product:"Apache"` returns devices running the Apache web server.                               |
| `version:"[version number]"`      | Search for devices running a specific software version.                                                   | `version:"5.7"` finds devices running MySQL version 5.7.                                        |
| `has_screenshot:"true"`           | Find devices with available screenshots.                                                                 | `has_screenshot:true` returns devices that include a screenshot.                                |
| `ssl.cert.subject.cn:"[name]"`    | Search for SSL certificates with a specific common name (CN).                                            | `ssl.cert.subject.cn:"example.com"` finds certificates for example.com.                         |
| `http.title:"[title text]"`       | Find web pages with a specific title.                                                                    | `http.title:"Welcome"` returns web pages with the title "Welcome".                              |
| `http.status_code:[code]`         | Search for devices returning a specific HTTP status code.                                                | `http.status_code:404` finds devices showing a 404 Not Found page.                              |
| `ssl:"[SSL keyword]"`             | Find devices with specific SSL configurations or details.                                                | `ssl:"SHA256"` returns devices using SHA256 encryption in their SSL configuration.              |
| `before:"[date]" / after:"[date]"`| Search for devices indexed before or after a certain date.                                               | `before:"2021-01-01"` finds devices indexed before January 1, 2021                             |

---

### Applications and Services

| **Query**                              | **Description**                                                                                   | **Example**                                                                                 |
|----------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|
| `product:"[product name]"`             | Locate devices running a specific product.                                                       | `product:"Apache"` finds servers running the Apache web server.                            |
| `version:"[version]"`                  | Find devices running a specific software version.                                                | `version:"2.4.41"` returns devices running Apache version 2.4.41.                          |
| `"default password"`                   | Find devices still using their default credentials, which is a major security risk.              | `"default password"` reveals devices with default login credentials.                       |
| `webcam`                               | Search for internet-connected webcams.                                                           | `webcam` returns exposed webcams connected to the internet.                                |
| `ftp`                                  | Find devices running FTP (File Transfer Protocol) services.                                      | `ftp` returns devices with FTP servers, which may be misconfigured or vulnerable.          |
| `"X-Powered-By: PHP/[version]"`        | Locate servers running specific PHP versions.                                                    | `"X-Powered-By: PHP/5.6"` finds servers running PHP version 5.6.                           |
| `iis:[version number]`                 | Search for servers running a specific version of Microsoft IIS (Internet Information Services).  | `iis:8.5` finds servers running IIS version 8.5.                                           |
| `"MongoDB Server Information" port:27017`| Identify exposed MongoDB databases on the default port.                                         | `"MongoDB Server Information" port:27017` finds unsecured MongoDB servers.                 |

---

### Security Vulnerabilities and Weaknesses

| **Query**                         | **Description**                                                                                  | **Example**                                                                               |
|-----------------------------------|--------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| `vuln:"[CVE-ID]"`                 | Search for devices affected by a specific CVE (Common Vulnerabilities and Exposures) ID.        | `vuln:"CVE-2021-26855"` finds devices vulnerable to a Microsoft Exchange Server exploit. |
| `ssl.cert.expired:"true"`         | Find devices using expired SSL certificates.                                                    | `ssl.cert.expired:true` returns systems with expired SSL certificates.                   |
| `"heartbleed" vuln`               | Search for devices vulnerable to the Heartbleed bug, a critical SSL/TLS vulnerability.          | `"heartbleed" vuln` identifies devices affected by Heartbleed.                           |
| `"Authentication: disabled"`      | Find devices where authentication mechanisms are disabled.                                      | `"Authentication: disabled"` returns systems with no authentication in place.           |
| `ssl:"TLSv1"`                     | Locate devices using the outdated and insecure TLSv1 protocol.                                  | `ssl:"TLSv1"` finds devices using the vulnerable TLSv1 protocol.                         |
| `http.component:"Drupal" vuln:"CVE-2018-7600"`| Search for Drupal websites vulnerable to the Drupalgeddon2 vulnerability.             | `http.component:"Drupal" vuln:"CVE-2018-7600"` finds Drupal sites vulnerable to CVE-2018-7600. |

---

### Complex Queries

| **Query**                                           | **Description**                                                                                           |
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| `os:"Linux" port:"22" "SSH" country:"DE"`           | Find Linux devices in Germany running SSH on port 22.                                                      |
| `product:"Apache" version:"2.3" -"200 OK"`        | Identify Apache servers running version 2.3 that do not return a 200 OK status.                        |
| `city:"Los Angeles" os:"Windows" port:"3389"`          | Find Windows devices with RDP (Remote Desktop Protocol) enabled in Los Angeles.                        |
| `net:"192.168.1.0/24" webcam`                       | Locate webcams within the specified IP range.                                                            |
| `org:"Google" ssl.cert.expired:"true"`              | Search for devices owned by Google with expired SSL certificates.                                        |
| `country:"DE" product:"MySQL" version:"5.5" "default password"` | Find MySQL databases in Germany using default credentials.                                    |
