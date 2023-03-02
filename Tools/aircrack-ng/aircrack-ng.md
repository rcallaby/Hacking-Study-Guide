# aircrack-ng

Aircrack-ng is a popular open-source tool used for penetration testing, specifically for cracking wireless networks. It is widely used by security professionals to assess the security of wireless networks and identify vulnerabilities that can be exploited by attackers. This article provides an overview of Aircrack-ng and how it can be used by penetration testers.

## What is Aircrack-ng?

Aircrack-ng is a set of tools for auditing wireless networks. It includes a packet sniffer, a WEP and WPA/WPA2-PSK key cracker, and an analysis tool for 802.11 wireless LANs. It can be used to capture packets transmitted over a wireless network, monitor network traffic, and perform various attacks to crack the encryption keys used to secure the network.

## How to Install Aircrack-ng?

Aircrack-ng can be installed on various operating systems, including Linux, Windows, and macOS. The installation process varies depending on the operating system being used. The following are the general steps to install Aircrack-ng on a Linux operating system.

+ Step 1: Install dependencies
Aircrack-ng requires certain dependencies to be installed on the system, including libssl-dev, libnl-3-dev, libnl-genl-3-dev, and ethtool. To install these dependencies, run the following command:

```
sudo apt-get update
sudo apt-get install libssl-dev libnl-3-dev libnl-genl-3-dev ethtool

```
+ Step 2: Download Aircrack-ng
Download the Aircrack-ng package from the official website using the following command:

```
wget https://download.aircrack-ng.org/aircrack-ng-1.6.tar.gz

```
+ Step 3: Extract the Package
Extract the downloaded package using the following command:

```
tar -xvf aircrack-ng-1.6.tar.gz

```
+ Step 4: Compile Aircrack-ng
Change the directory to the extracted package and run the following commands to compile and install Aircrack-ng:

```
cd aircrack-ng-1.6
make
sudo make install

```
Once the installation process is complete, Aircrack-ng is ready to use.

How to Use Aircrack-ng?

Aircrack-ng can be used to perform a variety of attacks on wireless networks, including capturing packets, monitoring network traffic, and cracking encryption keys. The following are the steps to use Aircrack-ng for cracking WEP and WPA/WPA2-PSK encryption keys.

+ Step 1: Enable Monitor Mode
Before capturing packets, it is necessary to enable monitor mode on the wireless network interface card (NIC). Run the following command to enable monitor mode:

```
sudo airmon-ng start wlan0

```
+ Step 2: Capture Packets
Use the following command to capture packets transmitted over the wireless network:

This command will start capturing packets and display various details about the wireless network, including the BSSID, ESSID, and channel number.

+ Step 3: Target a Network
Identify the network that needs to be cracked based on the BSSID and channel number displayed in the previous step. Run the following command to capture packets for a specific network:

```
sudo airodump-ng --bssid <BSSID> -c <channel> -w capture wlan0mon

```
Replace <BSSID> and <channel> with the BSSID and channel number of the network, respectively. This command will capture packets specifically for the target network and save them in a file called "capture".

+ Step 4: Deauthenticate Clients
Deauthenticate the clients connected to the target network using the following command:

```
sudo aireplay-ng --deauth 0 -a <BSSID> wlan0mon

```
This command will send deauthentication packets to the clients connected to the target network, causing them to disconnect and reconnect to the network. This step is necessary to generate traffic that can be used to crack the encryption key.

+ Step 5: Crack WEP Encryption
If the target network uses WEP encryption, use the following command to crack the encryption key:

```
sudo aircrack-ng capture-01.cap

```
This command will use the captured packets to perform a brute-force attack and crack the WEP key. The key will be displayed in the output if the attack is successful.

+ Step 6: Crack WPA/WPA2-PSK Encryption
If the target network uses WPA/WPA2-PSK encryption, use the following command to crack the encryption key:

```
sudo aircrack-ng capture-01.cap -w wordlist.txt

```
This command will use the captured packets and a wordlist to perform a dictionary attack and crack the WPA/WPA2-PSK key. Replace "wordlist.txt" with the path to the wordlist file. The key will be displayed in the output if the attack is successful.

Aircrack-ng is a powerful tool that can be used by penetration testers to identify vulnerabilities in wireless networks and crack encryption keys. It is essential to use this tool ethically and with the permission of the network owner. The above steps provide a basic overview of how Aircrack-ng can be used for WEP and WPA/WPA2-PSK key cracking. However, it is important to note that there are various other parameters and options that can be used with Aircrack-ng to customize the attacks and achieve better results.



