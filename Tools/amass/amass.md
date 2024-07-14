# amass

### Step 1: Installation

To use `amass`, you need to install it. You can install `amass` using various methods, but the easiest way is through package managers like `apt` (on Debian-based systems) or `brew` (on macOS).

#### Using APT (Debian-based systems)
```bash
sudo apt-get update
sudo apt-get install amass
```

#### Using Brew (macOS)
```bash
brew install amass
```

#### Using Go
If you have Go installed, you can also install `amass` using the following command:
```bash
go install -v github.com/owasp-amass/amass/v3/...@master
```

### Step 2: Basic Usage

Once installed, you can start using `amass` for domain enumeration. Here's a basic command to get started:

```bash
amass enum -d example.com
```

This command will enumerate subdomains for `example.com`.

### Step 3: Output Options

You can specify different output formats. For example, to save the output in a text file, use:

```bash
amass enum -d example.com -o output.txt
```

For JSON output, which can be useful for further processing, use:

```bash
amass enum -d example.com -json output.json
```

### Step 4: Using Different Modes

`amass` has several modes that you can use depending on your needs:

- **Passive Mode**: Only uses public sources and does not send any direct queries to the target.
- **Active Mode**: Performs direct queries to the target along with using public sources.

To use passive mode:
```bash
amass enum -passive -d example.com
```

To use active mode:
```bash
amass enum -active -d example.com
```

### Step 5: Using Configuration Files

You can configure `amass` using a configuration file. This allows you to specify API keys, different data sources, and other settings.

Here's a basic example of a configuration file (`config.ini`):

```ini
[resolvers]
  1.1.1.1
  8.8.8.8

[sources]
  AlienVault = true
  Cloudflare = true

[output]
  directory = /path/to/output
```

To use the configuration file:
```bash
amass enum -d example.com -config config.ini
```

### Step 6: Using Amass with Other Tools

`amass` can be integrated with other tools for more comprehensive reconnaissance. For example, you can use `amass` with `nmap` to scan discovered subdomains:

```bash
amass enum -d example.com -o subdomains.txt
nmap -iL subdomains.txt
```

### Step 7: Advanced Enumeration

For more advanced enumeration, you can use the `-brute` flag to perform DNS brute forcing:

```bash
amass enum -d example.com -brute
```

You can also specify a custom wordlist for brute forcing:

```bash
amass enum -d example.com -brute -w wordlist.txt
```

### Step 8: Visualizing Results

`amass` can generate graphs to visualize the relationships between domains. This can be done using the `viz` command:

```bash
amass viz -d example.com -o graph.png
```

### Step 9: Monitoring and Automation

You can set up `amass` to run periodically and monitor changes in subdomains over time. This can be useful for ongoing security monitoring.

For example, using a cron job:

```bash
crontab -e
```

Add the following line to run `amass` every day at midnight:

```bash
0 0 * * * amass enum -d example.com -o /path/to/output/$(date +\%F).txt
```

### Step 10: Reviewing Results

After running `amass`, review the results carefully. Look for interesting subdomains, potential vulnerabilities, and other useful information that can help in your security assessment.

---
