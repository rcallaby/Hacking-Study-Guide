# Fierce

Fierce is a domain scanner and reconnaissance tool used in penetration testing to gather information about domain names. It helps in identifying potential vulnerabilities and weaknesses in a network's infrastructure. Below is a detailed tutorial on how to use Fierce for penetration testing:

### Installing Fierce:

1. **Prerequisites:**
- Fierce is a Perl script, so you need to have Perl installed on your system.
- Ensure that you have the required dependencies. You can install them using the following command:
 ```bash
cpan install Net::DNS Net::Netmask Net::IP Net::CIDR::Lite
 ```

2. **Download Fierce:**
- Clone the Fierce repository from GitHub using the following command:
```bash
git clone https://github.com/mschwager/fierce.git
```

3. **Change Directory:**
   - Navigate to the Fierce directory:
     ```bash
     cd fierce
     ```

4. **Make Fierce Executable:**
   - Make the `fierce.pl` script executable:
     ```bash
     chmod +x fierce.pl
     ```

### Using Fierce:

#### Basic Usage:

```bash
./fierce.pl -dns example.com
```

Replace `example.com` with the target domain you want to scan.

#### Options and Examples:

1. **Brute Force Subdomains:**
   - Fierce can perform a brute-force scan for subdomains using the `-dns` option. This can be useful for discovering hidden or unlinked subdomains:
     ```bash
     ./fierce.pl -dns example.com
     ```

2. **Output to a File:**
   - Save the results to a file for later analysis:
     ```bash
     ./fierce.pl -dns example.com -file output.txt
     ```

3. **Specify DNS Server:**
   - You can use a specific DNS server for the scan with the `-dnsserv` option:
     ```bash
     ./fierce.pl -dns example.com -dnsserv 8.8.8.8
     ```

4. **Include Wildcard Subdomains:**
   - Include wildcard subdomains in the scan with the `-wn` option:
     ```bash
     ./fierce.pl -dns example.com -wn
     ```

5. **Aggressive Mode:**
   - Aggressive mode increases the number of threads and may provide more comprehensive results:
     ```bash
     ./fierce.pl -dns example.com -threads 10
     ```

6. **Output in XML Format:**
   - Save the results in XML format for integration with other tools:
     ```bash
     ./fierce.pl -dns example.com -xml output.xml
     ```

### Interpreting Results:

- Fierce will provide a list of subdomains along with their associated IP addresses.
- Look for misconfigurations, open ports, or any other information that may be useful for penetration testing.
- Use the results to identify potential targets for further analysis and exploitation.

### Additional Tips:

- **Stay Ethical:**
  Always ensure that you have permission to conduct penetration testing on a network. Unauthorized testing is illegal and can result in severe consequences.

- **Stay Updated:**
  Periodically check for updates to Fierce and install them to benefit from the latest features and improvements.

- **Explore Additional Options:**
  Fierce has additional options that allow you to customize the scan further. Review the help menu (`./fierce.pl -h`) to explore these options.
