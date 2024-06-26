# Inveigh

Inveigh is a PowerShell-based tool designed for conducting man-in-the-middle (MITM) attacks within Windows environments, particularly exploiting the NetBIOS Name Service (NBT-NS) and Link-Local Multicast Name Resolution (LLMNR) vulnerabilities. It functions by impersonating services like NBT-NS and LLMNR to intercept and manipulate network traffic, allowing cybersecurity professionals to demonstrate how attackers can exploit these protocols to intercept network communications. Inveigh can also be extended to capture SMB and HTTP traffic, making it a versatile tool for network security testing and demonstrating the potential for credential interception.

In the realm of cybersecurity, Inveigh is primarily used in penetration testing and red team exercises to assess the security of network protocols and configurations. By simulating attacks, security teams can identify and mitigate vulnerabilities before they can be exploited by actual attackers. The tool provides real-time data and has features for customizing the scope and nature of attacks, including specifying target IP addresses, enabling packet capture, and logging traffic for further analysis. Importantly, like all penetration testing tools, Inveigh should be used ethically and legally, with explicit permission from network administrators, to ensure that security testing strengthens cybersecurity measures without crossing legal boundaries.

### Step 1: Environment Setup

Before using Inveigh, ensure you have a Windows environment with PowerShell. It’s recommended to run PowerShell as an administrator to avoid any permission issues.

### Step 2: Importing Inveigh

Open PowerShell and navigate to the directory containing the Inveigh script. Import the script with the following command:

```powershell
Import-Module .\Inveigh.ps1
```

### Step 3: Basic Usage

To start Inveigh with default settings, simply run:

```powershell
Invoke-Inveigh
```

This command initiates Inveigh with default settings, listening for LLMNR/NBT-NS requests on the network.

### Step 4: Customizing Parameters

Inveigh has numerous parameters you can customize. For example, to specify a particular network interface and enable packet capture, you can use:

```powershell
Invoke-Inveigh -IP 192.168.1.100 -PCAPEnabled $true
```

Here, `-IP` specifies the local IP address to bind, and `-PCAPEnabled` enables packet capture.

### Step 5: Analyzing Output

Inveigh displays real-time results in the PowerShell window. It shows details like the type of request, the requesting IP, and the spoofed response.

### Step 6: Utilizing Advanced Features

Inveigh supports more sophisticated features like SMB and HTTP capture. To enable HTTP capture, use:

```powershell
Invoke-Inveigh -HTTP $true
```

This feature will allow Inveigh to respond to HTTP requests and potentially capture credentials.

### Step 7: Logging and Output

To save Inveigh’s output for later analysis, you can redirect it to a file:

```powershell
Invoke-Inveigh > output.txt
```

### Step 8: Stopping Inveigh

To stop Inveigh, simply press `Ctrl+C` in the PowerShell window. This will terminate the session and stop all listeners.

### Example Scenario

Imagine you're testing the security of your network. You've set up Inveigh on a machine with IP address 192.168.1.100 and started listening. A coworker unknowingly sends a request for a server name that doesn't exist in DNS but is captured by LLMNR. Inveigh responds, directing the request to a malicious IP where you can further interact with the request, demonstrating how an attacker could exploit LLMNR/NBT-NS vulnerabilities.

### Caution and Ethics

Using Inveigh to intercept and manipulate network traffic can be considered a form of attack. Always ensure you have explicit permission to use these tools in any network environment. Unauthorized use of Inveigh can be illegal and unethical.

This tutorial assumes you have a fundamental understanding of network protocols and PowerShell. Using Inveigh effectively requires good knowledge of network security principles and the ethical guidelines governing penetration testing.