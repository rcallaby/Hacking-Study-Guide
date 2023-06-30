# Sshuttle 

## Tutorial on Using Sshuttle:

### Step 1: Install sshuttle

Make sure you have Python installed on your system.
Open a terminal or command prompt.
Run the following command to install sshuttle using pip:

```
pip install sshuttle
```

### Step 2: Understand the basics of sshuttle

sshuttle is a powerful tool that allows you to create transparent VPN-like tunnels using SSH.
It works by setting up a remote server as a proxy and forwarding traffic through it, enabling you to pivot and tunnel your connections through intermediate hosts.

### Step 3: Establish a SSH connection to a remote host

Identify the target host that you want to pivot or tunnel through.
Open a terminal or command prompt.
Run the following command to initiate a SSH connection:

```
ssh username@remote_host
```

Replace username with the appropriate username and remote_host with the IP address or domain name of the target host.
Enter the password or passphrase if prompted.
Step 4: Basic usage of sshuttle

Once you are connected to the remote host via SSH, you can use sshuttle to create the tunnel.
Run the following command to tunnel all traffic through the remote host:

```
sshuttle -r username@remote_host 0.0.0.0/0
```
Replace username and remote_host with the appropriate values.
The 0.0.0.0/0 specifies that all traffic should be tunneled through the remote host. You can modify this IP range as per your requirements.

### Step 5: Tunnel specific subnets or ports

If you only want to tunnel specific subnets or ports, you can modify the sshuttle command accordingly.
For example, to tunnel traffic only from a specific subnet, use:

```
sshuttle -r username@remote_host subnet_cidr
```
Replace subnet_cidr with the appropriate subnet in CIDR notation.
To tunnel specific ports, use the --ssh-cmd option:

```
sshuttle -r username@remote_host --ssh-cmd "ssh -p port_number" subnet_cidr
```
Replace port_number with the SSH port number used by the remote host.

### Step 6: Verify the tunneling

Once sshuttle is running, it will create the tunnel and start forwarding traffic.
Open another terminal or command prompt and test the tunnel by accessing resources or services that are only accessible through the remote host.
Verify that you can access those resources successfully.

### Step 7: Terminate the tunnel

To terminate the sshuttle tunnel, go back to the terminal or command prompt where sshuttle is running.
Press Ctrl+C to stop the tunneling.
Remember to use sshuttle responsibly and ethically, ensuring that you have the necessary permissions and legal authorization before conducting any penetration testing or ethical hacking activities.