# smbclient

`smbclient` is a command-line tool that allows users to access and interact with SMB/CIFS shares on a network. It operates similarly to an FTP client but for SMB protocols, enabling users to connect to shared resources, list directory contents, download and upload files, and execute commands on the remote system. Part of the Samba suite, `smbclient` is commonly used in both administrative and security contexts due to its powerful capabilities and flexibility in managing network shares.

Penetration testers use `smbclient` primarily for its ability to enumerate shares on target systems, access sensitive files, and potentially exploit misconfigurations in SMB shares. During a penetration test, an attacker might use `smbclient` to list all available shares on a network, access those shares with valid or guessed credentials, and exfiltrate data. Its scripting capabilities also allow for automated tasks, making it a versatile tool for thorough security assessments. By leveraging `smbclient`, penetration testers can identify security weaknesses related to SMB shares, helping organizations to strengthen their defenses against unauthorized access.

For both novices and experts, `smbclient` offers a user-friendly yet powerful interface to interact with SMB shares. Beginners can start with basic commands to list shares and download files, gradually learning more advanced features like scripting for automation. Experts, on the other hand, can utilize its full potential by integrating `smbclient` into complex security testing frameworks, performing detailed enumeration, and conducting sophisticated attacks on SMB shares. By understanding and effectively using `smbclient`, users at any skill level can enhance their ability to manage and secure SMB/CIFS resources.


## What is `smbclient`?

`smbclient` is a command-line tool that functions like an FTP client but operates over SMB/CIFS protocols. It's part of the Samba suite and is commonly used in penetration testing and security assessments to interact with SMB shares.

### Step 1: Installation

First, ensure `smbclient` is installed on your system. On most Linux distributions, you can install it via the package manager.

**For Debian-based systems (e.g., Ubuntu):**
```sh
sudo apt-get update
sudo apt-get install smbclient
```

**For Red Hat-based systems (e.g., CentOS):**
```sh
sudo yum install samba-client
```

**Verify installation:**
```sh
smbclient --version
```

### Step 2: Basic Usage

The basic syntax for using `smbclient` is:
```sh
smbclient //server/share -U username
```
- `//server/share`: The SMB share you want to access.
- `-U username`: The username to authenticate with.

**Example:**
```sh
smbclient //192.168.1.10/shared -U john
```

You will be prompted for the password. Once authenticated, you will enter an interactive shell similar to FTP.

### Step 3: Listing Shares on a Server

To list available shares on a server, use the `-L` option:
```sh
smbclient -L //192.168.1.10 -U john
```

**Output Example:**
```
Sharename       Type      Comment
---------       ----      -------
shared          Disk
IPC$            IPC       IPC Service (server)
```

### Step 4: Connecting to a Share

To connect to a specific share, use the command as shown earlier:
```sh
smbclient //192.168.1.10/shared -U john
```

Once connected, you can use various commands within the interactive shell.

### Step 5: Navigating the Share

Within the interactive shell, you can use commands similar to Unix commands:

- `ls`: List files and directories.
- `cd`: Change directory.
- `pwd`: Print current directory.
- `mkdir`: Create a directory.
- `rmdir`: Remove a directory.

**Example:**
```sh
smb: \> ls
  .                       D        0  Mon Jun  7 09:30:00 2021
  ..                      D        0  Mon Jun  7 09:30:00 2021
  file.txt                A     2048  Mon Jun  7 09:31:00 2021

smb: \> cd folder
smb: \folder\> ls
  .                       D        0  Mon Jun  7 09:32:00 2021
  ..                      D        0  Mon Jun  7 09:32:00 2021
```

### Step 6: Downloading Files

To download files, use the `get` command.

**Example:**
```sh
smb: \> get file.txt
getting file \file.txt of size 2048 as file.txt (2.0 kb/s) (average 2.0 kb/s)
```

### Step 7: Uploading Files

To upload files, use the `put` command.

**Example:**
```sh
smb: \> put localfile.txt remotefile.txt
putting file localfile.txt as \remotefile.txt (2.0 kb/s) (average 2.0 kb/s)
```

### Step 8: Scripting with `smbclient`

You can also script `smbclient` commands for automated tasks. Use the `-c` option to pass commands.

**Example Script:**
```sh
#!/bin/bash

smbclient //192.168.1.10/shared -U john%password -c "ls; get file.txt; exit"
```

### Step 9: Passwordless Authentication

For scripting and automation, you can store credentials in a file and use it with the `-A` option.

**Credentials File (`smbcreds`):**
```
username = john
password = password
domain   = WORKGROUP
```

**Command:**
```sh
smbclient //192.168.1.10/shared -A smbcreds -c "ls"
```

### Step 10: Advanced Usage

#### Mounting SMB Shares

You can mount SMB shares directly into your file system using `mount.cifs`.

**Example:**
```sh
sudo mount.cifs //192.168.1.10/shared /mnt/smb -o username=john,password=password
```

#### Enum4linux

For more advanced enumeration, you can use tools like `enum4linux` which leverages `smbclient` for detailed information gathering.

**Example:**
```sh
enum4linux -a 192.168.1.10
```

# Conclusion

`smbclient` is a powerful tool for accessing and managing SMB shares in a network, especially useful in cybersecurity for both offensive and defensive operations. By mastering `smbclient`, you can efficiently enumerate shares, download/upload files, and script these operations for automation.