# medusa

### Medusa: A Comprehensive Guide for Penetration Testers

Medusa is a versatile, fast, and parallel brute-forcer which is often used in penetration testing to test the strength of passwords for various services. This guide will cover the essentials of using Medusa, including installation, basic commands, and advanced tips.

#### Installation

Medusa can be installed on most Linux distributions using package managers or by compiling from source.

**On Debian-based systems (e.g., Ubuntu):**
```bash
sudo apt-get update
sudo apt-get install medusa
```

**On Red Hat-based systems (e.g., Fedora, CentOS):**
```bash
sudo dnf install medusa
```

**Compiling from source:**
1. Download the latest release from the [Medusa GitHub repository](https://github.com/jmk-foofus/medusa).
2. Extract the tarball:
   ```bash
   tar -zxvf medusa-x.x.tar.gz
   ```
3. Navigate to the directory:
   ```bash
   cd medusa-x.x
   ```
4. Compile and install:
   ```bash
   ./configure
   make
   sudo make install
   ```

#### Basic Usage

Medusa operates by attempting to log in to a service using a list of usernames and passwords. The basic syntax for Medusa is:
```bash
medusa -h <target-ip> -u <username> -p <password> -M <module>
```

**Example:**
```bash
medusa -h 192.168.1.10 -u admin -p password123 -M ssh
```

This command attempts to log into the SSH service on the target IP using the username `admin` and password `password123`.

#### Common Modules

Medusa supports a variety of services (modules). Some common ones include:
- `ssh`: Secure Shell
- `ftp`: File Transfer Protocol
- `telnet`: Telnet
- `http`: HTTP Basic Authentication
- `mysql`: MySQL Database
- `rlogin`: Remote Login

#### Using Password and Username Lists

In real-world scenarios, using lists of usernames and passwords is more effective. 

**Example with password list:**
```bash
medusa -h 192.168.1.10 -u admin -P /path/to/password_list.txt -M ssh
```

**Example with username and password lists:**
```bash
medusa -h 192.168.1.10 -U /path/to/username_list.txt -P /path/to/password_list.txt -M ssh
```

#### Advanced Usage

##### Target Multiple Hosts
You can specify multiple targets in a file:
```bash
medusa -H /path/to/hosts_list.txt -u admin -P /path/to/password_list.txt -M ssh
```

##### Output Results to a File
```bash
medusa -h 192.168.1.10 -u admin -p password123 -M ssh -O results.txt
```

##### Specify Number of Threads
To increase the speed of your brute force attack, you can specify the number of parallel threads:
```bash
medusa -h 192.168.1.10 -u admin -P /path/to/password_list.txt -M ssh -t 10
```

##### Verbose Output
For more detailed output, use the `-v` flag. For even more detail, use `-v 6`:
```bash
medusa -h 192.168.1.10 -u admin -P /path/to/password_list.txt -M ssh -v 6
```

#### Pro-Tips for Beginners

1. **Know Your Limits**: Brute force attacks can generate a lot of traffic and may be considered illegal without permission. Always ensure you have authorization before testing.
   
2. **Use Validated Lists**: Ensure your username and password lists are well-curated. Lists from repositories like SecLists are usually reliable.
   
3. **Optimize Threads**: Adjust the number of threads according to the target system's capacity. Too many threads can cause the system to slow down or detect the attack.
   
4. **Understand the Service**: Each service (e.g., SSH, FTP) may have different lockout policies and response times. Customize your attack parameters accordingly.

5. **Save Your Results**: Always use the `-O` flag to save your results. This helps in reporting and analyzing your findings later.

6. **Stay Updated**: Regularly check for updates to Medusa and its modules. Security tools are constantly evolving, and staying updated ensures you have the latest features and fixes.

7. **Combine with Other Tools**: Use Medusa in conjunction with other tools like Nmap for comprehensive penetration testing. Nmap can help identify open ports and running services, which can then be targeted using Medusa.

#### Example Scenario

Let's say we want to brute-force SSH logins on multiple hosts with a list of usernames and passwords.

1. **Create Your Lists**:
   - `hosts.txt`:
     ```
     192.168.1.10
     192.168.1.11
     192.168.1.12
     ```

   - `usernames.txt`:
     ```
     root
     admin
     user
     ```

   - `passwords.txt`:
     ```
     password123
     admin123
     letmein
     ```

2. **Run Medusa**:
   ```bash
   medusa -H hosts.txt -U usernames.txt -P passwords.txt -M ssh -t 5 -O results.txt -v 6
   ```

In this scenario:
- `-H hosts.txt` specifies the file with target IPs.
- `-U usernames.txt` specifies the file with usernames.
- `-P passwords.txt` specifies the file with passwords.
- `-t 5` sets the number of parallel threads to 5.
- `-O results.txt` saves the output to `results.txt`.
- `-v 6` enables verbose output.

By following this guide, you should be well-equipped to start using Medusa for your penetration testing tasks. Remember, ethical considerations are paramount; always ensure you have explicit permission to test the systems you target.