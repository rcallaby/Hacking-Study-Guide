# Fluxion

### Step 1: Setting Up Your Environment

#### Prerequisites
1. **A compatible wireless adapter**: Ensure you have a wireless adapter that supports monitoring and injection mode.
2. **Linux OS**: Fluxion is designed to run on Linux distributions. Kali Linux is highly recommended due to its pre-installed network security tools.

#### Installation
1. **Update your system**:
   ```bash
   sudo apt-get update && sudo apt-get upgrade
   ```
2. **Install dependencies**:
   ```bash
   sudo apt-get install git aircrack-ng isc-dhcp-server hostapd lighttpd mdk3 php-cgi
   ```
3. **Clone the Fluxion repository**:
   ```bash
   git clone https://github.com/FluxionNetwork/fluxion.git
   ```
4. **Navigate to the Fluxion directory**:
   ```bash
   cd fluxion
   ```
5. **Run the installer**:
   ```bash
   sudo ./fluxion.sh -i
   ```

### Step 2: Running Fluxion

1. **Start Fluxion**:
   ```bash
   sudo ./fluxion.sh
   ```
2. **Select your language**: Choose the preferred language for the interface.

### Step 3: Scanning for Targets

1. **Choose the wireless adapter**: Select the wireless adapter that you will use for the attack.
2. **Scan for networks**: Fluxion will start scanning for available Wi-Fi networks. This might take a few minutes.

### Step 4: Selecting the Target

1. **Choose your target network**: From the list of detected networks, select the one you want to attack.
2. **Choose the attack method**: Fluxion will provide several options, such as the Handshake Snooper, Captive Portal, and others. For this tutorial, we'll use the Captive Portal method.

### Step 5: Capturing the Handshake

1. **Handshake Capture**: Fluxion will try to capture the WPA handshake of the target network. This is essential for creating the fake AP.
2. **Deauthenticate clients**: To capture the handshake, Fluxion will deauthenticate connected clients, forcing them to reconnect and capture the handshake.

### Step 6: Creating the Fake Access Point

1. **Select an interface for the fake AP**: Choose the wireless interface that will be used to create the fake AP.
2. **Start the Fake AP**: Fluxion will create a fake AP with the same SSID as the target network.

### Step 7: Setting Up the Captive Portal

1. **Choose the attack vector**: Fluxion offers several templates for the captive portal (e.g., Social, Network Login). Choose one that fits your scenario.
2. **Configure the captive portal**: Set up the DHCP and web server settings. Fluxion automates most of this, but you may need to confirm configurations.

### Step 8: Waiting for Victim Interaction

1. **Monitor the fake AP**: Fluxion will display logs and information about connected clients.
2. **Capture credentials**: When a user connects to the fake AP, they will be redirected to a captive portal page asking for the Wi-Fi password. Once they enter the password, Fluxion captures it and displays it on the terminal.

### Step 9: Verifying Captured Credentials

1. **Validate the credentials**: Fluxion attempts to verify the captured credentials by using them to connect to the real network.
2. **Success confirmation**: If the credentials are correct, Fluxion will notify you of a successful capture.

### Example Scenario

#### Example 1: Capturing a Handshake and Using the Captive Portal
1. **Select the target**: You choose a network named "HomeWiFi".
2. **Capture the handshake**: Deauthenticate clients on "HomeWiFi" and capture the handshake.
3. **Fake AP setup**: Create a fake AP named "HomeWiFi".
4. **Portal setup**: Choose a social engineering template that looks like a router login page.
5. **Capture credentials**: A victim connects to the fake "HomeWiFi", enters the password on the captive portal, and Fluxion captures the password.

#### Example 2: Using Fluxion for an Enterprise Network
1. **Select the target**: You choose an enterprise network named "CorporateNet".
2. **Capture the handshake**: Deauthenticate clients on "CorporateNet" and capture the handshake.
3. **Fake AP setup**: Create a fake AP named "CorporateNet".
4. **Portal setup**: Choose a professional template mimicking an enterprise login.
5. **Capture credentials**: An employee connects to the fake "CorporateNet", enters their enterprise credentials, and Fluxion captures them.

### Ethical Considerations

Remember, using Fluxion without permission is illegal and unethical. Always have explicit authorization from the network owner before conducting any security testing.

### Conclusion

Fluxion is a powerful tool for Wi-Fi security testing, leveraging social engineering techniques to capture credentials. By following this step-by-step guide, you should be able to set up and use Fluxion effectively for authorized security assessments. If you have any questions or need further assistance, feel free to ask!