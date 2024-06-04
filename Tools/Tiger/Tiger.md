# Tiger

## Introduction to Tiger

Tiger is a Unix security auditing tool that checks various aspects of system security, including file permissions, configuration files, and potential vulnerabilities. It performs checks and provides reports on security status, helping to identify and mitigate security risks.

### Installation

Tiger can be installed on most Unix-based systems. Here’s how you can install it on a Debian-based system (like Ubuntu):

```bash
sudo apt-get update
sudo apt-get install tiger
```

For other distributions, you might need to download and compile it from source:

```bash
wget http://www.nongnu.org/tiger/tiger-3.2.3.tar.gz
tar -xzvf tiger-3.2.3.tar.gz
cd tiger-3.2.3
make
sudo make install
```

### Configuration

Tiger configuration files are typically found in `/usr/local/tiger` or `/etc/tiger`. The main configuration file is `tigerrc`.

To start, let's explore the `tigerrc` file:

```bash
sudo nano /etc/tiger/tigerrc
```

In this file, you can enable or disable specific checks, configure logging options, and set other parameters. For example, to enable all checks:

```bash
Tiger_Enable_All="Y"
```

And to specify a custom log file:

```bash
Tiger_LogFile="/var/log/tiger.log"
```

### Running Tiger

Running Tiger is straightforward. Simply execute:

```bash
sudo tiger
```

This command runs all enabled checks and produces a report. You can specify particular checks using the `-c` option:

```bash
sudo tiger -c check_accounts
```

##Understanding the Output

Tiger produces detailed reports on system security. Let’s look at an example output snippet:

```plaintext
# Checking accounts from /etc/passwd...
# Performing passwd file check...
--WARN-- [acc003w] Login (user) is disabled, but still has a valid shell.
--WARN-- [acc006w] Login (user) does not have a valid password.
```

Here, `acc003w` and `acc006w` are identifiers for specific checks. Each line provides a warning (`--WARN--`) or a pass (`--PASS--`) message, followed by details.

### Advanced Usage

Tiger can be customized for advanced usage. Here are some examples:

**Running Specific Checks:**

To run only specific checks:

```bash
sudo tiger -c check_accounts,check_files
```

**Running Tiger with Custom Configuration:**

You can run Tiger with a custom configuration file using the `-f` option:

```bash
sudo tiger -f /path/to/custom_tigerrc
```

**Generating HTML Reports:**

Tiger can produce reports in HTML format for better readability:

```bash
sudo tiger -H
```

### Automating Tiger

Automating Tiger checks using cron jobs can help maintain regular security auditing. Open the crontab editor:

```bash
sudo crontab -e
```

Add a job to run Tiger every day at midnight:

```plaintext
0 0 * * * /usr/sbin/tiger > /var/log/tiger.log 2>&1
```

## Conclusion

Tiger is a powerful tool for maintaining and improving system security. Regular audits with Tiger can help identify and mitigate vulnerabilities in your system. 

Keep in mind the importance of reviewing and updating configurations regularly to adapt to new security policies and system changes.