# Nikto

### Step 1: Installation

#### On Debian-based systems (e.g., Ubuntu)
```sh
sudo apt update
sudo apt install nikto
```

#### On Red Hat-based systems (e.g., CentOS)
```sh
sudo yum install epel-release
sudo yum install nikto
```

#### From source (for any Unix-like system)
1. Download the latest version from [Nikto's GitHub page](https://github.com/sullo/nikto).
```sh
git clone https://github.com/sullo/nikto
```
2. Navigate to the Nikto directory:
```sh
cd nikto/program
```
3. Make the nikto.pl script executable:
```sh
chmod +x nikto.pl
```
4. Run Nikto:
```sh
./nikto.pl
```

### Step 2: Basic Usage

The basic syntax for running Nikto is:
```sh
nikto -h <hostname or IP>
```

#### Example:
```sh
nikto -h http://example.com
```

### Step 3: Common Options

- **Specify a port**: If the web server is running on a non-standard port:
  ```sh
  nikto -h http://example.com -p 8080
  ```

- **Save output to a file**: You can save the results in various formats such as HTML, CSV, or XML.
  ```sh
  nikto -h http://example.com -o output.html -Format html
  ```

- **Use a proxy**: If you need to route your scan through a proxy:
  ```sh
  nikto -h http://example.com -useproxy http://proxyserver:port
  ```

- **Specify scan type**: You can specify different types of scans (e.g., SSL, headers only).
  ```sh
  nikto -h http://example.com -ssl
  ```

- **Update Nikto**: Ensure your Nikto has the latest plugins and databases.
  ```sh
  nikto -update
  ```

### Step 4: Advanced Usage

#### Scanning multiple targets
Create a text file with a list of hosts and use the `-h` flag with the file path:
```sh
nikto -h targets.txt
```

#### Specifying a specific plugin
Use the `-plugins` option to specify a particular plugin:
```sh
nikto -h http://example.com -plugins <plugin_name>
```

#### Using authentication
If the web application requires authentication, you can use:
```sh
nikto -h http://example.com -id username:password
```

### Step 5: Interpreting Results

Nikto provides a list of potential vulnerabilities, including descriptions and recommendations. Here’s a sample of what you might see:
```
+ Server: Apache/2.4.18 (Ubuntu)
+ The X-XSS-Protection header is not defined. This header can hint to the user-agent to protect against some forms of XSS
+ Allowed HTTP Methods: GET, POST, OPTIONS, HEAD 
+ OSVDB-3092: /test/: This might be interesting...
```

### Step 6: Troubleshooting Common Issues

1. **Permission Denied**: If you encounter a "permission denied" error, try running Nikto with `sudo`.
   ```sh
   sudo nikto -h http://example.com
   ```

2. **SSL Errors**: For sites using SSL/TLS, if you encounter SSL certificate errors, you can use the `-ssl` flag or ignore SSL checks:
   ```sh
   nikto -h https://example.com -ssl
   ```

3. **Slow Scans**: Nikto scans can be slow for large sites or those with many endpoints. Ensure you have a stable network connection and consider running scans during off-peak hours.

4. **Firewall Blocking**: Some firewalls may block Nikto scans. Ensure you have permission to scan the target and consider using stealthier scan methods if appropriate.

5. **Updating Issues**: If Nikto fails to update, check your internet connection and verify that you have the necessary permissions to write to Nikto's directory.

### Step 7: Ethical Considerations

Always ensure you have explicit permission to scan any target. Unauthorized scanning is illegal and unethical. Stick to targets you own or have been given permission to test.

### Conclusion

Nikto is a powerful tool for identifying vulnerabilities in web applications, but it should be used responsibly and as part of a comprehensive security testing strategy. By following these steps, you should be able to effectively use Nikto to help secure web applications.