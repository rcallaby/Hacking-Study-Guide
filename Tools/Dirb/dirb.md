# dirb

Here's a detailed guide to help you get started and make the most of `dirb`.

### Step 1: Installation

First, ensure `dirb` is installed on your system. It is available on most Linux distributions and can be installed via the package manager. For example, on a Debian-based system like Ubuntu, you can install it using:

```sh
sudo apt-get update
sudo apt-get install dirb
```

Verify the installation by typing:

```sh
dirb
```

You should see the `dirb` help and usage information if the installation was successful.

### Step 2: Basic Usage

The basic syntax for running `dirb` is:

```sh
dirb [TARGET_URL] [WORDLIST] [OPTIONS]
```

- **TARGET_URL**: The URL of the web application you want to scan.
- **WORDLIST**: The wordlist file containing directory and file names to brute-force.

#### Example 1: Basic Scan

Let's start with a basic scan using the default wordlist provided by `dirb`. Suppose we want to scan `http://example.com`.

```sh
dirb http://example.com
```

This command will use the default wordlist located in `/usr/share/dirb/wordlists/common.txt`.

### Step 3: Using Custom Wordlists

You might want to use a custom wordlist for more specific or comprehensive scans. You can find or create wordlists depending on your needs.

#### Example 2: Custom Wordlist

If you have a custom wordlist, say `custom_wordlist.txt`, located in your current directory, you can use it as follows:

```sh
dirb http://example.com ./custom_wordlist.txt
```

### Step 4: Advanced Options

`dirb` offers several options to customize your scans. Here are some useful ones:

- **-r**: Don't stop on an existing URL (useful for recursive scans).
- **-S**: Silent mode (only shows URLs with a response code different from 404).
- **-x**: Specify extensions to check for (e.g., `-x .php,.html`).
- **-o**: Output results to a file.

#### Example 3: Recursive Scan

To perform a recursive scan that digs deeper into discovered directories:

```sh
dirb http://example.com ./custom_wordlist.txt -r
```

#### Example 4: Silent Mode

To reduce noise and show only significant results:

```sh
dirb http://example.com ./custom_wordlist.txt -S
```

#### Example 5: Specific File Extensions

To check for specific file extensions like `.php` and `.html`:

```sh
dirb http://example.com ./custom_wordlist.txt -x .php,.html
```

#### Example 6: Save Output to a File

To save the scan results to a file named `scan_results.txt`:

```sh
dirb http://example.com ./custom_wordlist.txt -o scan_results.txt
```

### Step 5: Interpreting Results

When `dirb` runs, it lists out directories and files that exist on the target server. It shows the HTTP response codes next to each URL found. Here’s an example output snippet:

```
---- Scanning URL: http://example.com/ ----
+ http://example.com/index.php (CODE:200|SIZE:70346)
+ http://example.com/admin/ (CODE:403|SIZE:290)
+ http://example.com/uploads/ (CODE:200|SIZE:133)
```

- **CODE 200**: OK, the file/directory exists and is accessible.
- **CODE 403**: Forbidden, the file/directory exists but access is restricted.
- **CODE 404**: Not Found, which is typically not shown in default mode.

### Step 6: Practical Scenarios

#### Example 7: Identifying Hidden Admin Panels

To find hidden admin panels or login pages, you can use a targeted wordlist:

```sh
dirb http://example.com /usr/share/dirb/wordlists/admin.txt
```

#### Example 8: Finding Backup Files

Sometimes, backup files are left on the server unintentionally. Use a wordlist for common backup file extensions:

```sh
dirb http://example.com /usr/share/dirb/wordlists/extensions_common.txt -x .bak,.old,.backup
```

### Step 7: Combining with Other Tools

`dirb` can be combined with other tools for more comprehensive testing. For example, use `dirb` results to feed into `nikto` or `burpsuite` for deeper vulnerability scanning.

### Conclusion

`dirb` is a powerful tool for web content discovery and should be part of every penetration tester's toolkit. By following the steps and examples above, you can effectively use `dirb` to find hidden directories and files, enhancing your security assessments.
