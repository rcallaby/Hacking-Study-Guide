# Kismet Wireless

### What is Kismet?

Kismet is a wireless network detector, sniffer, and intrusion detection system. It can work with any wireless card that supports raw monitoring mode (rfmon) and can sniff 802.11a, 802.11b, 802.11g, and 802.11n traffic.

### Installing Kismet

#### On Debian-based Systems (e.g., Ubuntu)

```bash
sudo apt update
sudo apt install kismet
```

#### On Red Hat-based Systems (e.g., Fedora)

```bash
sudo dnf install kismet
```

### Setting Up Kismet

Before you can use Kismet, you'll need to make sure your wireless network card is in monitor mode. This allows Kismet to listen to all wireless traffic, rather than just traffic intended for your device.

#### Putting Your Wireless Card in Monitor Mode

1. **Identify your wireless network interface:**

```bash
sudo iwconfig
```

This will list all the network interfaces and their current modes.

2. **Put the interface into monitor mode:**

```bash
sudo ip link set wlan0 down
sudo iw dev wlan0 set type monitor
sudo ip link set wlan0 up
```

Replace `wlan0` with your network interface name.

### Configuring Kismet

The configuration file for Kismet is located at `/etc/kismet/kismet.conf`. Open this file in your favorite text editor:

```bash
sudo nano /etc/kismet/kismet.conf
```

You need to specify the source of your wireless data. Add or modify the following lines:

```bash
ncsource=wlan0
```

Again, replace `wlan0` with your wireless interface name.

### Running Kismet

With your wireless card in monitor mode and your configuration file set up, you can start Kismet:

```bash
sudo kismet
```

Kismet will start, and you should see the Kismet interface. It may ask you to create a new user if you're running it for the first time. Follow the on-screen prompts to do so.

### Using Kismet

When Kismet is running, it will start capturing wireless traffic. Here's a basic guide to using the Kismet interface:

- **Networks Tab:** Shows all the networks Kismet has detected.
- **Clients Tab:** Shows all the clients connected to those networks.
- **Alerts Tab:** Displays any security alerts, such as detected attacks.
- **Status Tab:** Displays the current status of Kismet, including the number of packets captured.

You can navigate between these tabs using the arrow keys on your keyboard.

### Filtering Results

Kismet allows you to apply filters to narrow down the results. For example, you can filter by SSID, MAC address, or signal strength. This can be done through the interface or by using command-line options.

### Saving Captured Data

Kismet can save the captured data to files for later analysis. By default, it will save to the `Kismet` directory in your home directory. You can configure this in the `kismet.conf` file:

```bash
logprefix=/path/to/logfiles/
```

### Analyzing Captured Data

The captured data can be analyzed using tools like Wireshark. To open a Kismet capture file in Wireshark:

1. Start Wireshark.
2. Open the capture file (`.pcap` or `.pcapng` format).

### Example Commands

- **Starting Kismet with a specific log prefix:**

```bash
sudo kismet -f /etc/kismet/kismet.conf --log_prefix=/path/to/logfiles/
```

- **Filtering networks by SSID:**

```bash
sudo kismet -f /etc/kismet/kismet.conf --ssid_filter "YourSSID"
```

- **Filtering by MAC address:**

```bash
sudo kismet -f /etc/kismet/kismet.conf --bssid_filter "00:11:22:33:44:55"
```

### Stopping Kismet

To stop Kismet, simply press `Shift + q` in the Kismet interface. This will safely terminate the program and close any open files.

### Conclusion

Kismet is a robust tool for wireless network monitoring and security assessments. This tutorial covers the basics, but Kismet offers many advanced features that you can explore as you become more familiar with the tool. For more detailed information, refer to the [Kismet documentation](https://kismetwireless.net/docs/readme/).

Remember, always use Kismet responsibly and ensure you have permission to monitor any networks you are working with. Unauthorized network monitoring is illegal and unethical. Happy sniffing!