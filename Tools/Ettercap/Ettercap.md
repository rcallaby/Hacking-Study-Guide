# Ettercap

## How to Use Ettercap for Network Security Testing

Ettercap is a comprehensive suite for man-in-the-middle attacks on LAN. It features sniffing of live connections, content filtering on the fly, and many other interesting tricks. This guide will help you get started with Ettercap.

#### Prerequisites
- A computer running a Linux distribution (preferably Kali Linux).
- Root privileges on the system.

### Step-by-Step Tutorial

#### Step 1: Install Ettercap
1. **Open a terminal**.
2. **Update your package list**:
   ```sh
   sudo apt update
   ```
3. **Install Ettercap**:
   ```sh
   sudo apt install ettercap-graphical
   ```

#### Step 2: Start Ettercap
1. **Launch Ettercap in graphical mode**:
   ```sh
   sudo ettercap -G
   ```

#### Step 3: Configure Network Interface
1. **Select your network interface**: Go to `Sniff` > `Unified Sniffing`.
2. **Choose the appropriate network interface** (e.g., `eth0` for wired, `wlan0` for wireless).

#### Step 4: Scan for Hosts
1. **Scan for hosts on the network**: Go to `Hosts` > `Scan for hosts`.
2. **View the hosts list**: After the scan completes, go to `Hosts` > `Hosts list`. This will show all the devices connected to the network.

#### Step 5: Select Targets
1. **Add the target**: In the `Hosts list` window, select the target(s) you want to perform the attack on.
   - **Target 1 (usually the victim)**: Click on the IP address and add it to Target 1.
   - **Target 2 (usually the gateway)**: Click on the gateway IP address and add it to Target 2.

#### Step 6: Start the Man-in-the-Middle Attack
1. **Start ARP poisoning**: Go to `Mitm` > `ARP poisoning`.
2. **Enable sniffing of remote connections**: Check the option `Sniff remote connections`.
3. **Click OK** to start the ARP poisoning attack.

#### Step 7: Capture Data
1. **View captured data**: Go to `View` > `Connections` to see the active connections and data being captured.
2. **Filters and Plugins**: Use filters and plugins to manipulate the data flow.
   - **Filters**: Create custom filters to manipulate traffic.
   - **Plugins**: Go to `Plugins` > `Manage the plugins` to see available plugins.

#### Step 8: Analyze Data
1. **View sniffed data**: Go to `View` > `Profiles` to create profiles for different types of traffic.
2. **Use Wireshark**: For deeper analysis, you can save the captured data and open it with Wireshark.

#### Step 9: Stop the Attack
1. **Stop the attack**: Go to `Mitm` > `Stop mitm attack`.
2. **Stop sniffing**: Go to `Sniff` > `Stop sniffing`.

### Advanced Usage

#### Using Ettercap Filters
1. **Create a filter script**: Write a filter script to manipulate packets.
   ```sh
   if (ip.proto == TCP && tcp.dst == 80) {
       replace("Accept-Encoding", "Accept-foo");
       msg("HTTP Request modified\n");
   }
   ```
2. **Compile the filter**:
   ```sh
   etterfilter your_filter.ef
   ```
3. **Apply the filter**: Go to `Filters` > `Load a filter`.

#### Using Plugins
1. **Load plugins**: Go to `Plugins` > `Manage the plugins`.
2. **Enable plugins**: Select and enable plugins to extend Ettercap’s functionality.

### Safety and Ethics
- **Permission**: Always ensure you have permission to perform penetration testing on the network.
- **Legal compliance**: Follow all legal guidelines and ethical practices.

By following these steps, you can effectively use Ettercap to perform network security tests and sniff traffic. Always remember to use these tools responsibly and ethically.