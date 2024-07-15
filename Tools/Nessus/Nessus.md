# Nessus


### Step 1: Install Nessus

1. **Download Nessus**:
   - Visit the [Tenable Downloads page](https://www.tenable.com/downloads/nessus) and select the appropriate version for your operating system.

2. **Install Nessus**:
   - For Windows:
     - Run the downloaded `.exe` file and follow the installation wizard.
   - For Linux:
     - Use the following commands (example for Debian-based systems):
       ```bash
       sudo dpkg -i Nessus-<version>.deb
       sudo systemctl start nessusd.service
       ```

3. **Start Nessus**:
   - Open a web browser and go to `https://localhost:8834`.

### Step 2: Set Up Nessus

1. **Create an Account**:
   - When you first launch Nessus, you’ll be prompted to create an administrative account. Fill in the required details.

2. **Enter Activation Code**:
   - After creating an account, enter the activation code you received from Tenable. You can get a free home use license or a professional one.

3. **Update Plugins**:
   - Nessus will then update its plugins. This may take some time, so be patient.

### Step 3: Configuring a Scan

1. **Log In**:
   - Log in to Nessus using the account credentials you created.

2. **Create a New Scan**:
   - Click on the “New Scan” button on the dashboard.

3. **Choose a Scan Template**:
   - Select a scan template based on your needs. Common templates include:
     - **Basic Network Scan**: For general network vulnerability scanning.
     - **Advanced Scan**: For customized scan configurations.
     - **Host Discovery**: To identify live hosts on the network.
     - **Web Application Tests**: For web application security testing.

4. **Configure Scan Settings**:
   - **Name**: Give your scan a descriptive name.
   - **Targets**: Enter the IP addresses or hostname of the targets you want to scan.
   - **Schedule**: (Optional) Schedule the scan to run at specific times.

5. **Advanced Settings** (Optional):
   - Customize the scan settings such as port range, scan performance, credentials, and plugins.

### Step 4: Running the Scan

1. **Launch the Scan**:
   - Click on the “Save” button to save your scan configuration.
   - On the scans page, click on the “Launch” button next to your configured scan.

2. **Monitor the Scan**:
   - You can monitor the progress of the scan in real-time. The scan time will vary based on the number of targets and the depth of the scan.

### Step 5: Analyzing Scan Results

1. **View Results**:
   - Once the scan is complete, click on the completed scan to view the results.

2. **Interpreting Results**:
   - Nessus provides a detailed report of all the vulnerabilities found.
   - **Severity Levels**: Results are categorized by severity levels (Critical, High, Medium, Low, Informational).
   - **Details**: Click on individual vulnerabilities to see detailed information, including a description, solution, and references.

3. **Exporting Reports**:
   - You can export the scan results in various formats (PDF, HTML, CSV) by clicking the export button.

### Step 6: Remediation

1. **Prioritize Vulnerabilities**:
   - Focus on critical and high-severity vulnerabilities first.
   - Consider the exploitability and impact of each vulnerability.

2. **Apply Fixes**:
   - Follow the remediation steps provided by Nessus for each vulnerability.
   - This may involve patching software, changing configurations, or other corrective actions.

3. **Rescan**:
   - After applying fixes, it’s a good practice to rescan the targets to ensure that vulnerabilities have been addressed.

### Additional Tips

- **Credentialed Scans**: For more comprehensive results, use credentialed scans by providing Nessus with SSH or Windows credentials.
- **Scan Policies**: Create and save scan policies for different environments and needs.
- **Continuous Scanning**: Schedule regular scans to maintain up-to-date security assessments.

