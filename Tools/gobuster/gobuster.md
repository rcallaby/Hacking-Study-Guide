# Gobuster

Gobuster is an essential tool in the cybersecurity professional’s arsenal, specifically designed for brute-forcing URIs (directories and files) and DNS subdomains on web servers. Leveraging a fast and efficient method of enumerating directories, files, and subdomains, Gobuster is particularly valuable during the reconnaissance phase of penetration testing and security assessments. Its ability to quickly identify hidden or obscure paths and subdomains that might otherwise go unnoticed can reveal significant vulnerabilities or misconfigurations within a web application. With support for a variety of wordlists and the capability to handle multiple file extensions, Gobuster provides extensive flexibility, making it a go-to tool for thorough web content discovery.

Using Gobuster is highly advantageous when you need to map out the structure of a target web server, identify sensitive directories, or uncover hidden endpoints that could be exploited. For instance, discovering forgotten administrative interfaces, unprotected directories containing sensitive information, or even finding backup files inadvertently left accessible can significantly impact the security posture of a web application. Moreover, Gobuster’s speed and efficiency, driven by its use of Go, make it capable of handling large wordlists and processing extensive brute-force tasks with minimal performance overhead. This capability ensures comprehensive coverage without significant delays, crucial for timely vulnerability assessments.

However, while Gobuster is powerful, it must be used with caution and a clear understanding of ethical and legal implications. Unauthorized scanning of web servers can lead to legal consequences, and it is imperative to have explicit permission from the target organization before conducting any tests. Additionally, aggressive scanning can generate substantial traffic and potentially disrupt services, so it is essential to configure Gobuster's rate limits and other parameters to avoid impacting the target's operations negatively. Security professionals must also be aware of the potential for false positives or missed findings, necessitating corroboration with other tools and manual verification to ensure accurate results. By adhering to these precautions, Gobuster can be effectively and responsibly utilized in the pursuit of securing web applications.

### Step 1: Install Gobuster

Gobuster is written in Go, so you need to have Go installed on your system. You can install Gobuster via package managers like `apt` on Debian-based systems, or you can compile it from the source.

#### Using `apt` on Debian-based systems:
```bash
sudo apt-get update
sudo apt-get install gobuster
```

#### Compiling from source:
1. Install Go from the [official Go website](https://golang.org/doc/install).
2. Clone the Gobuster repository:
    ```bash
    git clone https://github.com/OJ/gobuster.git
    cd gobuster
    ```
3. Build Gobuster:
    ```bash
    go build
    ```

### Step 2: Basic Usage of Gobuster

Gobuster can be used to brute-force directories, files, and DNS subdomains. Let's start with brute-forcing directories and files.

#### Brute-Forcing Directories and Files
To brute-force directories and files on a target web server, you need a wordlist. A commonly used wordlist is `directory-list-2.3-medium.txt` from the SecLists repository.

Example command:
```bash
gobuster dir -u http://example.com -w /path/to/wordlist/directory-list-2.3-medium.txt
```

**Parameters:**
- `dir`: Indicates the directory/file brute-forcing mode.
- `-u`: Specifies the URL of the target.
- `-w`: Specifies the path to the wordlist.

**Example:**
```bash
gobuster dir -u http://testphp.vulnweb.com -w /usr/share/wordlists/dirb/common.txt
```

This will output directories and files discovered on the target server.

### Step 3: Advanced Options

Gobuster provides several advanced options to customize your scan.

#### Setting Extensions
To search for specific file extensions, use the `-x` flag.

**Example:**
```bash
gobuster dir -u http://testphp.vulnweb.com -w /usr/share/wordlists/dirb/common.txt -x php,txt,html
```

#### Recursive Scanning
To perform a recursive scan, where Gobuster will continue scanning discovered directories, use the `-r` flag.

**Example:**
```bash
gobuster dir -u http://testphp.vulnweb.com -w /usr/share/wordlists/dirb/common.txt -r
```

#### Specifying Status Codes
You can filter the results by HTTP status codes using the `-s` flag.

**Example:**
```bash
gobuster dir -u http://testphp.vulnweb.com -w /usr/share/wordlists/dirb/common.txt -s "200,204,301,302,307,403,500"
```

### Step 4: Brute-Forcing DNS Subdomains

Gobuster can also be used to brute-force DNS subdomains. You'll need a subdomain wordlist for this.

**Example Command:**
```bash
gobuster dns -d example.com -w /path/to/wordlist/subdomains.txt
```

**Parameters:**
- `dns`: Indicates the DNS subdomain brute-forcing mode.
- `-d`: Specifies the domain name of the target.
- `-w`: Specifies the path to the wordlist.

**Example:**
```bash
gobuster dns -d example.com -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-20000.txt
```

### Step 5: Outputting Results to a File

You can save the results of your scan to a file using the `-o` flag.

**Example:**
```bash
gobuster dir -u http://testphp.vulnweb.com -w /usr/share/wordlists/dirb/common.txt -o results.txt
```

### Step 6: Using a Proxy

If you need to route your requests through a proxy, use the `-p` flag.

**Example:**
```bash
gobuster dir -u http://testphp.vulnweb.com -w /usr/share/wordlists/dirb/common.txt -p http://127.0.0.1:8080
```

### Step 7: Ignoring SSL Certificate Errors

If you're scanning an HTTPS site with a self-signed certificate, you might need to ignore SSL certificate errors using the `-k` flag.

**Example:**
```bash
gobuster dir -u https://testphp.vulnweb.com -w /usr/share/wordlists/dirb/common.txt -k
```

### Step 8: Example Scenarios

#### Scenario 1: Brute-forcing directories on a web server
```bash
gobuster dir -u http://example.com -w /usr/share/wordlists/dirb/common.txt -x php,html,js -o dir_results.txt
```

#### Scenario 2: Brute-forcing DNS subdomains
```bash
gobuster dns -d example.com -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-20000.txt -o dns_results.txt
```

#### Scenario 3: Recursive brute-forcing with specific status codes
```bash
gobuster dir -u http://example.com -w /usr/share/wordlists/dirb/common.txt -r -s "200,204,301,302" -o recursive_results.txt
```

### Conclusion

Gobuster is a powerful and versatile tool for discovering hidden content on web servers. By understanding and utilizing its various options, you can effectively map out the structure of a target server and uncover potentially sensitive information. Remember to always have permission to test the target and adhere to ethical guidelines in cybersecurity.