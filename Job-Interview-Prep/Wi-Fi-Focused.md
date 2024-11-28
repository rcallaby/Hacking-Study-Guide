# Wi-Fi Focused Interview Questions

### 1. **WPA/WPA2 Cracking:**
   - **Question:** Describe the process of cracking a WPA2 password using the dictionary attack method. What tools would you use, and how would you capture the handshake?
   - **Expected Answer:** The tester should explain using tools like **Aircrack-ng** or **Hashcat**. They should detail the steps: capturing the WPA2 handshake using **Airodump-ng**, filtering the target AP, and using **Aircrack-ng** or **Hashcat** for cracking with a wordlist or brute force.

### 2. **WEP Cracking:**
   - **Question:** How would you crack a WEP key using a tool like Aircrack-ng? What makes WEP vulnerable to these attacks, and how can you accelerate the process?
   - **Expected Answer:** The tester should mention **Aircrack-ng** and the use of tools like **Aireplay-ng** to inject packets and generate enough IVs (Initialization Vectors). The vulnerability of WEP lies in weak IVs and poor encryption. Cracking is accelerated by capturing a high number of IVs.

### 3. **Deauthentication Attack:**
   - **Question:** How does a deauthentication attack work in a Wi-Fi network, and how would you perform this attack using a tool like **Aircrack-ng** or **MDK3**?
   - **Expected Answer:** The tester should explain how a deauthentication attack sends fake deauthentication frames to disconnect clients from the AP, forcing them to reauthenticate. This attack is useful for capturing WPA/WPA2 handshakes. Tools like **Aircrack-ng** or **MDK3** can be used to send these frames.

### 4. **Evil Twin Attack:**
   - **Question:** What is an Evil Twin attack, and how do you perform it in a Wi-Fi network environment? What tools would you use for this?
   - **Expected Answer:** The tester should describe setting up a rogue access point with the same SSID as the target network to trick users into connecting to it. The attacker can use tools like **Airbase-ng**, **Hostapd**, or **Fluxion**. The answer should also mention potential man-in-the-middle (MITM) attacks using this technique.

### 5. **WPS Cracking:**
   - **Question:** Explain how a WPS PIN brute force attack works. What are the vulnerabilities in WPS that make this attack feasible, and what tools can be used to exploit this?
   - **Expected Answer:** The tester should describe WPS’s use of an 8-digit PIN, where the first 4 digits are susceptible to a brute force attack due to a weak checksum, making the attack feasible. Tools like **Reaver** or **Bully** are commonly used for this purpose.

### 6. **WPA3 Vulnerabilities (if applicable):**
   - **Question:** What is the difference between WPA2 and WPA3 in terms of security, and are there any known vulnerabilities in WPA3?
   - **Expected Answer:** The tester should explain the improvements in WPA3, such as **Simultaneous Authentication of Equals (SAE)**, which replaces the Pre-Shared Key (PSK) method to improve password protection. They should also mention potential vulnerabilities in WPA3, such as the **Dragonblood** attack, which targets the SAE handshake.

### 7. **Wi-Fi Sniffing:**
   - **Question:** What tools and techniques can you use to sniff Wi-Fi traffic? How would you differentiate between legitimate traffic and attack traffic?
   - **Expected Answer:** The tester should mention tools like **Wireshark**, **Kismet**, and **Airodump-ng**. They should explain capturing packets, filtering for specific protocols (e.g., 802.11 management frames, DNS, HTTP), and identifying suspicious activity, such as spoofed APs or unusual traffic patterns.

### 8. **Man-in-the-Middle (MITM) with Wi-Fi:**
   - **Question:** How would you set up a MITM attack on a Wi-Fi network? What tools would you use to intercept and manipulate traffic, and what risks are involved for the attacker?
   - **Expected Answer:** The tester should discuss tools like **Ettercap**, **Bettercap**, or **MITMf** for intercepting and manipulating traffic. They should mention techniques like DNS spoofing, ARP poisoning, and SSL stripping. The risks involved would include detection through network traffic analysis or security measures like HTTPS.

### 9. **Rogue DHCP Server Attack:**
   - **Question:** What is a rogue DHCP server attack, and how does it affect a Wi-Fi network? How would you exploit this vulnerability?
   - **Expected Answer:** The tester should explain that in a rogue DHCP attack, an attacker sets up a fake DHCP server to provide incorrect network configuration (e.g., incorrect DNS servers, gateways) to clients. This can be used for MITM attacks. Tools like **Yersinia** or **dhcpstarv** can be used to carry out the attack.

### 10. **Wi-Fi Password Cracking using PMKID:**
   - **Question:** What is PMKID, and how does it relate to WPA2 password cracking? How would you use it to crack a Wi-Fi password?
   - **Expected Answer:** The tester should explain that PMKID is a method for capturing the Pairwise Master Key Identifier during the 4-way handshake, which can be used to crack the WPA2 password without capturing the full handshake. Tools like **hashcat** or **aircrack-ng** can be used to crack the PMKID hash.

### 11. **SSID Hiding and its Weaknesses:**
   - **Question:** What is SSID hiding in Wi-Fi networks, and what are the limitations or vulnerabilities associated with it?
   - **Expected Answer:** The tester should explain that SSID hiding involves the AP not broadcasting its SSID, which is intended to make the network less visible. However, the SSID is still discoverable by capturing beacon frames or by querying the AP directly using tools like **Airodump-ng**. Hiding SSID does not provide real security.

### 12. **Wi-Fi Channel Hopping:**
   - **Question:** How does Wi-Fi channel hopping work in an attack scenario, and what is its purpose?
   - **Expected Answer:** The tester should explain how an attacker uses **channel hopping** to avoid detection by switching between different Wi-Fi channels, making it harder for defenders to monitor or block their activity. This technique is useful during sniffing or deauthentication attacks.

### 13. **Captive Portal Bypassing:**
   - **Question:** Describe how you would attempt to bypass a captive portal on a public Wi-Fi network. What techniques or tools could you use?
   - **Expected Answer:** The tester should mention techniques such as DNS manipulation, using tools like **Bettercap** to spoof DNS requests, or using VPNs to bypass the portal. They should also mention using **Proxychains** or **Tor** to mask traffic.

### 14. **Wi-Fi DoS Attacks:**
   - **Question:** What is a Denial-of-Service (DoS) attack on a Wi-Fi network, and how can it be executed effectively?
   - **Expected Answer:** The tester should explain DoS attacks like jamming (using a **jammer** to flood the frequency with noise) or flooding the AP with deauthentication packets to prevent legitimate clients from connecting. Tools like **MDK3** or **Aireplay-ng** are often used for such attacks.

### 15. **Identifying Weak Encryption:**
   - **Question:** How would you identify a Wi-Fi network that is using weak or outdated encryption (e.g., WEP or WPA)?
   - **Expected Answer:** The tester should explain that **Airodump-ng** can be used to capture packets and inspect the encryption used by the AP (WEP, WPA, WPA2). They should also mention that tools like **Wireshark** can help identify weak encryption protocols by inspecting the handshake.

