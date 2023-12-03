# WPScan

WPScan is a popular open-source WordPress security scanner that helps identify vulnerabilities in WordPress installations. Here's a step-by-step tutorial on how to use WPScan:

### Prerequisites:

1. **Ruby Installation:**
   - Ensure that Ruby is installed on your system. You can download and install Ruby from [ruby-lang.org](https://www.ruby-lang.org/en/downloads/).

2. **Git Installation (Optional but recommended):**
   - WPScan can be cloned from its GitHub repository using Git. Install Git from [git-scm.com](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

### Step 1: Install WPScan

1. Open your terminal or command prompt.

2. Clone the WPScan repository from GitHub:
   ```bash
   git clone https://github.com/wpscanteam/wpscan.git
   ```

3. Navigate to the WPScan directory:
   ```bash
   cd wpscan
   ```

4. Install the required Ruby gems:
   ```bash
   gem install bundler && bundle install --without test
   ```

### Step 2: Update WPScan

WPScan is frequently updated with new vulnerabilities and features. It's crucial to keep it up to date.

```bash
cd wpscan
git pull
bundle install --without test
```

### Step 3: Perform a Simple Scan

Now, let's run a basic scan against a WordPress website. Replace `http://example.com` with the target WordPress site.

```bash
ruby wpscan.rb --url http://example.com
```

This command will perform a default scan, providing information about the WordPress version, installed themes, and plugins.

### Step 4: Enumerate Users

To list WordPress users, use the `--enumerate u` option. This information is valuable for potential attackers, so be cautious.

```bash
ruby wpscan.rb --url http://example.com --enumerate u
```

### Step 5: Enumerate Plugins and Themes

To enumerate installed plugins and themes, use the following commands:

```bash
# Enumerate Plugins
ruby wpscan.rb --url http://example.com --enumerate p

# Enumerate Themes
ruby wpscan.rb --url http://example.com --enumerate t
```

### Step 6: Perform a More Comprehensive Scan

For a more detailed scan, you can use the `--enumerate` option with multiple parameters:

```bash
ruby wpscan.rb --url http://example.com --enumerate u,t,p
```

### Step 7: Specify Timings and Threads

Adjust the scan intensity using the `--wp-content-dir` and `--wp-plugins-dir` options. You can also control the timing and threads for a more efficient scan:

```bash
ruby wpscan.rb --url http://example.com --enumerate u,t,p --wp-content-dir custom-content --wp-plugins-dir custom-plugins --batch --max-threads 50
```

### Step 8: Save Output to a File

Save the scan results to a file for later analysis:

```bash
ruby wpscan.rb --url http://example.com --output-file wpscan_results.txt
```

These steps cover the basics of using WPScan. Remember to use this tool responsibly and only on websites you have permission to scan. Unauthorized scanning can be illegal and unethical.