# ffuf

ffuf (Fuzz Faster U Fool) is an open-source web fuzzer used primarily in cybersecurity to identify vulnerabilities in web applications. Developed by hackers and security researchers, this tool automates the process of testing various inputs to uncover hidden resources, directories, files, and potential security flaws. Its flexibility and speed make it a preferred choice among penetration testers and bug bounty hunters who aim to secure web applications by finding and exploiting vulnerabilities before malicious actors can.

ffuf is utilized for a range of purposes within the cybersecurity domain, including directory discovery, parameter fuzzing, and virtual host discovery. By sending numerous HTTP requests with various payloads, ffuf helps security professionals identify hidden paths, sensitive files, and unprotected resources that could be exploited. The tool's ability to handle large wordlists and execute multiple requests simultaneously makes it particularly effective for comprehensive security assessments of web applications. Additionally, its compatibility with various input sources and output formats allows users to customize their fuzzing operations and integrate ffuf into broader security workflows.

To get the most out of ffuf, users should follow a structured approach:

1. **Preparation**: Gather and prepare relevant wordlists that include potential directory names, parameter values, and other inputs specific to the target application. High-quality wordlists are crucial for thorough testing.
   
2. **Configuration**: Customize ffuf's settings to match the testing requirements. This includes specifying the target URL, setting the request method (GET or POST), and adjusting the number of concurrent requests to optimize performance without overwhelming the target server.

3. **Execution and Analysis**: Run ffuf with the prepared configurations and monitor the results. Analyze the output to identify any discovered paths or resources, paying close attention to HTTP status codes and response sizes. Use the findings to investigate further and validate potential vulnerabilities.

By following these steps, security professionals can effectively leverage ffuf to enhance their web application security assessments and uncover critical vulnerabilities.

## Step 1: Installation

Before using FFUF, you need to install it. Here’s how you can do it:

#### On Linux:

1. **Install Go (if not already installed):**
    ```bash
    sudo apt update
    sudo apt install golang-go
    ```

2. **Install FFUF:**
    ```bash
    go install github.com/ffuf/ffuf@latest
    ```

#### On macOS:

1. **Install Homebrew (if not already installed):**
    ```bash
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    ```

2. **Install FFUF:**
    ```bash
    brew install ffuf
    ```

## Step 2: Basic Usage

#### Directory Fuzzing

Let's start with a basic example of directory fuzzing on a target website. 

1. **Prepare a wordlist:**
    FFUF requires a wordlist to perform fuzzing. You can use the SecLists repository or create your own wordlist.

    ```bash
    git clone https://github.com/danielmiessler/SecLists.git
    ```

    Assuming you have your wordlist ready at `~/SecLists/Discovery/Web-Content/common.txt`, you can proceed.

2. **Run FFUF:**
    ```bash
    ffuf -u http://example.com/FUZZ -w ~/SecLists/Discovery/Web-Content/common.txt
    ```

    - `-u` specifies the URL with the `FUZZ` keyword where the wordlist entries will be substituted.
    - `-w` specifies the path to the wordlist.

#### Example Output:

```
/admin                  [Status: 200, Size: 512]
/login                  [Status: 200, Size: 789]
/test                   [Status: 200, Size: 1024]
```

## Step 3: Advanced Usage

#### Fuzzing with Multiple Wordlists

You can use multiple wordlists simultaneously to target different parts of the URL.

1. **Run FFUF with two wordlists:**
    ```bash
    ffuf -u http://example.com/FUZZ/FUZZ2 -w ~/SecLists/Discovery/Web-Content/common.txt -w ~/SecLists/Discovery/DNS/subdomains-top1million-20000.txt:FUZZ2
    ```

    - Here, `FUZZ` will be substituted by the first wordlist and `FUZZ2` by the second wordlist.

#### Using Headers

To include headers in your request, use the `-H` option.

1. **Run FFUF with headers:**
    ```bash
    ffuf -u http://example.com/FUZZ -w ~/SecLists/Discovery/Web-Content/common.txt -H "Authorization: Bearer <your_token>"
    ```

#### POST Data Fuzzing

You can also fuzz POST data by using the `-d` option.

1. **Run FFUF with POST data:**
    ```bash
    ffuf -u http://example.com/login -w ~/SecLists/Discovery/Web-Content/common.txt -X POST -d "username=FUZZ&password=password123"
    ```

#### Filtering and Matching

FFUF offers various options to filter and match results based on status codes, response size, words, lines, etc.

1. **Filter by status code:**
    ```bash
    ffuf -u http://example.com/FUZZ -w ~/SecLists/Discovery/Web-Content/common.txt -fc 404
    ```

    - `-fc` filters out the results with status code 404.

2. **Match by status code:**
    ```bash
    ffuf -u http://example.com/FUZZ -w ~/SecLists/Discovery/Web-Content/common.txt -mc 200,301
    ```

    - `-mc` matches only the results with status codes 200 and 301.

## Step 4: Real-World Examples

#### Fuzzing for Hidden Directories

```bash
ffuf -u http://example.com/FUZZ -w ~/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt
```

#### Fuzzing for Subdomains

```bash
ffuf -u http://FUZZ.example.com -w ~/SecLists/Discovery/DNS/subdomains-top1million-5000.txt -H "Host: FUZZ.example.com"
```

#### Fuzzing for File Extensions

```bash
ffuf -u http://example.com/index.FUZZ -w ~/SecLists/Discovery/Web-Content/big.txt -e php,html,txt,js
```

- `-e` specifies the file extensions to append.

## Step 5: Tips and Best Practices

1. **Optimize Wordlists:**
   - Use wordlists that are specific to your target for better results.
   - Remove redundant or unlikely words to speed up the fuzzing process.

2. **Rate Limiting:**
   - Be mindful of rate limits on the target server to avoid being blocked. Use the `-rate` option to control the number of requests per second.

    ```bash
    ffuf -u http://example.com/FUZZ -w ~/SecLists/Discovery/Web-Content/common.txt -rate 50
    ```

3. **Output to a File:**
   - Save your results to a file for further analysis.

    ```bash
    ffuf -u http://example.com/FUZZ -w ~/SecLists/Discovery/Web-Content/common.txt -o results.json -of json
    ```

    - `-o` specifies the output file and `-of` specifies the format (e.g., json, html, md, csv).

## Conclusion

FFUF is a versatile tool for web fuzzing, and with these steps and examples, you should be able to use it effectively for your cybersecurity tasks. Always ensure you have permission to test the target systems and comply with ethical guidelines.

Feel free to ask if you have any questions or need further assistance!