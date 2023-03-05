# JackTheRipper

Jack the Ripper is a password cracking tool used by penetration testers and security professionals to crack passwords of remote systems. This tool is highly effective in breaking into password-protected systems, making it a popular choice among security professionals.

## What is Jack the Ripper?

Jack the Ripper is an open-source password cracking tool that can crack passwords for various operating systems and services, including Unix, Windows, and other platforms. It uses brute force methods to crack passwords, which means it tries different combinations of characters until it finds the correct one.

## How does Jack the Ripper work?

Jack the Ripper works by utilizing different modes to crack passwords. It includes several modes such as straight, combination, and incremental. In straight mode, Jack the Ripper tries every possible combination of characters until it finds the correct one. In combination mode, it tries combinations of characters from a given character set. In incremental mode, Jack the Ripper tries a specific character set with a variable password length.

The tool also uses wordlists to crack passwords, which are essentially lists of words that are commonly used in passwords. These wordlists are based on the dictionary words, common passwords, and leaked password databases. Jack the Ripper has a built-in wordlist, but users can also create their own or use custom ones available online.

## Examples of using Jack the Ripper

Here are some examples of how to use Jack the Ripper to crack passwords:

+ Cracking Windows Passwords: Jack the Ripper can be used to crack Windows passwords by creating a password hash dump file from a Windows machine using the pwdump tool. This file can then be imported into Jack the Ripper, which can use its different modes to crack the passwords.

+ Cracking Unix Passwords: Jack the Ripper can also be used to crack Unix passwords by using the "unshadow" command to create a password hash file from the /etc/passwd and /etc/shadow files on a Unix machine. The hash file can then be imported into Jack the Ripper, which can use its different modes to crack the passwords.

### Using Wordlists

Jack the Ripper can also use wordlists to crack passwords. Users can download custom wordlists or create their own. They can then import the wordlist into Jack the Ripper and use it to crack passwords.

* Sort a wordlist to use with wordlist rule mode

```
$tr A-Z a-z <SOURCE | sort -u > TARGET
```
* Use a POT file to generate a new wordlist
```
cut -d: -f2 john.pot | sort -u > pot.dic
```
* Generate candidate passwords for slow hashes
```
./john --wordlist=password.lst --stdout --rules: Jumbo | ./unique -mem=25 wordlist.uniq
```

### Using GPU Acceleration

 Jack the Ripper can be run on a computer with a powerful graphics processing unit (GPU) to accelerate password cracking. This method is significantly faster than using a CPU.

* List OpenCL deices and get the device id
```
 ./john --list=opencl-devices
```
* List formats supported by OpenCL
```
./john --list=formats --format=opencl
```
* Using JTR with Multiple GPU's
```
./john hashes -- format: <openclformat> --wordlist:<> --rules:<> --dev=0,1 --fork=2
```
* Using JTR with Multiple CPU's
```
./john hashes --wordlist:<> --rules:<> --dev=2 --fork=4
```


Jack the Ripper is an essential tool for any penetration tester or security professional looking to crack passwords on remote systems. With its various modes, wordlists, and GPU acceleration, it can quickly crack passwords and provide valuable insights into system vulnerabilities. However, it's important to use this tool ethically and only with proper authorization to avoid any legal consequences.