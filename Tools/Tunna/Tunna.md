# Tunna - A web socks proxy

# Introduction:
In the world of ethical hacking, having the right tools at your disposal is crucial. One such tool that can greatly enhance your capabilities is Tunna, a web Socks proxy. Tunna allows you to route your network traffic through a proxy server, providing you with anonymity and the ability to bypass certain restrictions. In this tutorial, we will explore the features of Tunna and guide you through the process of setting up and using it effectively for ethical hacking purposes.

## What is Tunna?
Tunna is a powerful web Socks proxy designed specifically for ethical hacking purposes. It allows you to route your network traffic through a proxy server, which can be useful in scenarios where you need to hide your identity or bypass certain network restrictions. Tunna supports both HTTP and HTTPS protocols, making it versatile for various hacking activities.

## Prerequisites:
Before we begin, ensure you have the following prerequisites:

A Linux-based operating system (e.g., Ubuntu, Kali Linux)
Python 3 installed on your system
Basic knowledge of networking concepts and ethical hacking techniques
Installation:
To install Tunna, follow these steps:
a. Open a terminal on your Linux system.
b. Clone the Tunna repository from GitHub using the command: git clone https://github.com/SECFORCE/Tunna.git
c. Navigate to the Tunna directory: cd Tunna
d. Install the required Python dependencies using pip: pip install -r requirements.txt

## Configuration:
Tunna requires some configuration before you can start using it. Follow these steps:
a. Open the config.json file located in the Tunna directory using a text editor.
b. Review and modify the default settings as per your requirements. Pay attention to options such as proxy listening port, proxy server timeouts, and encryption settings.
c. Save the changes to config.json.

## Setting Up the Proxy Server:
To set up the proxy server using Tunna, execute the following steps:
a. In the Tunna directory, run the command: python3 tunna.py
b. Tunna will start listening on the specified port, and the proxy server will be ready to accept connections.
c. Take note of the IP address and port on which Tunna is listening. This information will be required to configure your web browser or other tools to use Tunna as a proxy.

## Proxying Traffic:
To route your traffic through Tunna, perform the following steps:
a. Configure your web browser to use the Tunna proxy server. Refer to your browser's settings and set the proxy server address as the IP address and port obtained in the previous step.
b. Test the proxy configuration by visiting a website. If everything is set up correctly, the traffic should be routed through Tunna, and you will see the requests and responses in the Tunna terminal window.

## Handling Encrypted Traffic:
Tunna is capable of handling encrypted traffic by leveraging the power of Man-in-the-Middle (MitM) attacks. To intercept and decrypt HTTPS traffic, follow these steps:
a. In the Tunna directory, locate the certs directory and open it.
b. Extract the ca.pem file and install it as a trusted root certificate authority on the system where you intend to intercept HTTPS traffic.
c. Configure your target device to trust the certificate authority installed in the previous step.
d. Restart the target device and initiate HTTPS connections. Tunna will intercept and decrypt the traffic, allowing you to analyze it.

## Advanced Usage and Customization:
Tunna offers several advanced features and customization options. Some notable features include:

Support for SOCKS4, SOCKS4a, and SOCKS5 protocols.
Configuration of blacklist and whitelist rules.
Customization of proxy server timeouts, response modification, and request tampering.
Refer to the official Tunna documentation and explore the available options to further enhance your ethical hacking capabilities.

### Best Practices for Ethical Hacking with Tunna:
While using Tunna for ethical hacking, it is essential to adhere to best practices to ensure responsible and legal usage:
Obtain proper authorization before conducting any hacking activities.
Use Tunna only on systems and networks you have permission to test.
Respect the privacy and security of others during your testing.
Keep yourself updated with the latest ethical hacking techniques and follow the legal frameworks and guidelines of your jurisdiction.

# Conclusion:
Tunna is a powerful tool that empowers ethical hackers to perform various network-related activities with anonymity and flexibility. By following this step-by-step tutorial, you have learned how to install, configure, and use Tunna as a web Socks proxy. Remember to use Tunna responsibly and within legal boundaries to ensure the security of yourself and others.
Disclaimer: The tutorial provided is intended for educational and ethical hacking purposes only. The usage of Tunna or any other hacking tool for illegal activities is strictly prohibited and can lead to severe consequences under the law.

Remember to always act ethically and responsibly when conducting any hacking-related activities.