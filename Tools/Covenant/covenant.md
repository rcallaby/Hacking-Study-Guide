# Covenant

### **Step 1: Setting Up Covenant**

#### **1.1 Prerequisites**
Before setting up Covenant, ensure that your system meets the following prerequisites:
- **Operating System**: Covenant runs on Windows, Linux, or macOS, though it is commonly deployed on a Linux system (e.g., Ubuntu).
- **.NET Core SDK**: Covenant requires the .NET Core SDK 3.1 or later. You can install it by running the following commands on a Linux machine:
  ```bash
  wget https://dot.net/v1/dotnet-install.sh
  chmod +x dotnet-install.sh
  ./dotnet-install.sh -c 3.1
  ```
  You can verify the installation by checking the .NET version:
  ```bash
  dotnet --version
  ```
- **Docker (Optional)**: If you prefer containerization, you can use Docker to run Covenant.

#### **1.2 Cloning the Covenant Repository**
Clone the Covenant GitHub repository to your local machine:
```bash
git clone --recurse-submodules https://github.com/cobbr/Covenant
cd Covenant/Covenant
```

#### **1.3 Building the Covenant Project**
Next, build the Covenant project using the .NET Core SDK:
```bash
dotnet build
```
After the build is complete, you’ll have the Covenant application ready to run.

### **Step 2: Running Covenant**

#### **2.1 Starting Covenant**
To start Covenant, run the following command:
```bash
dotnet run
```
By default, Covenant will start a web server on `http://localhost:7443`. You can access the Covenant web interface through your browser by navigating to this address.

#### **2.2 Creating an Account**
When you access Covenant for the first time, you’ll need to create an administrative account. This account will be used to log into the Covenant web interface. Simply follow the prompts on the screen to set up your credentials.

### **Step 3: Configuring Covenant**

#### **3.1 Creating a Listener**
A Listener is a server-side component that waits for connections from Grunts (the Covenant agents). To create a Listener:
1. Go to the **Listeners** section in the Covenant interface.
2. Click on **Create Listener**.
3. Choose the listener type (HTTP, HTTPS, SMB, etc.). The most common is **HTTP**.
4. Set the **BindAddress** to the IP address of the machine running Covenant.
5. Set the **BindPort** to the port you want to listen on (e.g., 80, 443).
6. Optionally, configure other parameters like **UseSSL** (recommended for HTTPS listeners).
7. Click **Create Listener** to finalize the setup.

#### **3.2 Generating a Launcher**
A Launcher is the code that you’ll execute on the target machine to establish a connection back to your Covenant listener. To generate a launcher:
1. Go to the **Launchers** section.
2. Click on **Generate Launcher**.
3. Select the **Listener** you created earlier.
4. Choose a **Launcher Type** (e.g., `PowerShell`, `Binary`, `MSBuild`).
5. Customize any additional options if needed (e.g., obfuscation, delay).
6. Click **Generate** to create the launcher.

The generated launcher will be displayed on the screen. This is the command or script you’ll execute on the target machine.

### **Step 4: Deploying the Launcher on the Target**

Deploy the launcher on the target system by any means available (e.g., phishing, exploitation, physical access). Once executed, the target will attempt to connect back to the Covenant listener you set up earlier.

### **Step 5: Managing Grunts**

Once a target connects to your listener, it will appear in the **Grunts** section of Covenant. Here’s how you can manage them:

#### **5.1 Interacting with Grunts**
1. Select the Grunt from the list.
2. You can now run commands, scripts, and modules against the target.
3. To execute a command:
   - Click on **Task**.
   - Choose the **Command** from the dropdown (e.g., `ipconfig`, `whoami`).
   - Optionally, enter arguments for the command.
   - Click **Task** to execute the command.

#### **5.2 Running Modules**
Covenant comes with built-in modules that allow you to perform various post-exploitation tasks:
1. Go to the **Modules** section.
2. Select a module (e.g., `Dump LSASS`, `Keylogger`, `Mimikatz`).
3. Configure the module’s options if needed.
4. Click **Task** to run the module on the selected Grunt.

### **Step 6: Data Exfiltration and Persistence**

#### **6.1 Data Exfiltration**
Use Covenant’s capabilities to exfiltrate data from the compromised machine:
1. Use built-in commands to search for sensitive data.
2. Use the `Download` command to exfiltrate files back to the Covenant server.

#### **6.2 Establishing Persistence**
To maintain access to the target system, you can use Covenant’s persistence mechanisms:
1. Deploy persistence modules (e.g., registry-based persistence, scheduled tasks).
2. Ensure that the Grunt will reconnect automatically on reboot or at regular intervals.

### **Step 7: Cleaning Up**

After your red team engagement is complete, it’s important to clean up all traces of your activities:
1. **Terminate Grunts**: In the Grunts section, terminate all active Grunts.
2. **Delete Listeners**: Go to the Listeners section and delete any listeners you’ve set up.
3. **Delete Launchers**: Ensure that all generated launchers and payloads are removed from the target systems.
4. **Logs and Data**: Clean up any logs, files, or data stored on the Covenant server.

### **Step 8: Advanced Usage**

#### **8.1 Custom Grunt Development**
For advanced users, Covenant allows the development of custom Grunts using the .NET framework. This requires knowledge of C# and .NET.

#### **8.2 API Integration**
Covenant provides a RESTful API that can be integrated into automated workflows. This allows for the automation of tasks like launching new Grunts, running commands, and retrieving data.

#### **8.3 Docker Deployment**
To run Covenant in a Docker container:
```bash
docker pull covenantproject/covenant
docker run -it -p 7443:7443 covenantproject/covenant
```
This approach simplifies deployment and ensures that Covenant runs in an isolated environment.

### **Conclusion**

Covenant is a highly versatile and powerful C2 framework that can be tailored to a wide range of red team operations. This tutorial covered the essential steps to get you started with Covenant, from setup to advanced usage. Whether you’re using it for a penetration test, a red team engagement, or as part of a CTF, Covenant provides the tools and flexibility you need to manage and control compromised systems effectively.

Always remember to use Covenant responsibly and within the bounds of legal and ethical guidelines.