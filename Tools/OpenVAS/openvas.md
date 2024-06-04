# OpenVAS

## OpenVAS - A Quick Start Guide

### Introduction

OpenVAS is a comprehensive open-source vulnerability scanning tool that helps identify security issues in systems, applications, and networks. It is widely used by penetration testers to perform detailed vulnerability assessments. OpenVAS is part of the Greenbone Vulnerability Management (GVM) framework, which offers a range of services for vulnerability scanning and management.

### Installation

OpenVAS can be installed on various operating systems, but the most common and straightforward installation is on a Linux-based system, such as Ubuntu. Here’s how you can install OpenVAS on Ubuntu:

1. **Update your system**:
    ```bash
    sudo apt update && sudo apt upgrade -y
    ```

2. **Install OpenVAS**:
    ```bash
    sudo apt install openvas -y
    ```

3. **Initialize OpenVAS**:
    ```bash
    sudo gvm-setup
    ```

4. **Start OpenVAS services**:
    ```bash
    sudo gvm-start
    ```

5. **Check the status**:
    ```bash
    sudo gvm-check-setup
    ```

After the setup, OpenVAS will be available through a web interface, typically at `https://<your-server-ip>:9392`.

### Configuring OpenVAS

#### Accessing the Web Interface

1. Open a web browser and navigate to `https://<your-server-ip>:9392`.
2. Log in using the default admin credentials generated during setup. It's recommended to change the default password immediately for security reasons.

#### Updating the Feeds

OpenVAS relies on up-to-date vulnerability databases to perform effective scans. Make sure your feeds are current:

1. In the web interface, go to `Administration` > `Feed Status`.
2. Click on the `Update` button to download the latest vulnerability definitions and data.

### Performing a Basic Scan

#### Creating a Target

1. **Define the target**:
    - Navigate to `Configuration` > `Targets`.
    - Click on `+` to create a new target.
    - Enter a name for the target and specify the IP address or hostname.
    - Save the target.

#### Creating a Task

1. **Create a new task**:
    - Go to `Scans` > `Tasks`.
    - Click on `+` to create a new task.
    - Name the task and select the target you created.
    - Choose a scan configuration (e.g., Full and Fast) from the drop-down menu.
    - Save the task.

2. **Start the scan**:
    - After creating the task, you will see it listed under `Scans` > `Tasks`.
    - Select the task and click on the `Start` button.

### Analyzing Scan Results

Once the scan is complete, OpenVAS will provide detailed results that you can analyze to identify vulnerabilities.

1. **View the results**:
    - Go to `Scans` > `Reports`.
    - Find your scan task in the list and click on it to view the report.

2. **Interpret the findings**:
    - The report will list discovered vulnerabilities, their severity, and details.
    - Focus on high and medium severity vulnerabilities first.
    - Each vulnerability entry provides information about the issue, potential impact, and remediation steps.

### Examples of Common Vulnerabilities

Here are some examples of common vulnerabilities you might encounter:

1. **Unpatched Software**:
    - **Description**: Software that is not updated may have known vulnerabilities.
    - **Example**: An outdated Apache server might have known exploits.
    - **Remediation**: Update the software to the latest version.

2. **Weak Passwords**:
    - **Description**: Accounts with weak passwords are susceptible to brute-force attacks.
    - **Example**: The admin account using "admin123" as a password.
    - **Remediation**: Implement strong password policies.

3. **Open Ports**:
    - **Description**: Unnecessary open ports can be entry points for attackers.
    - **Example**: An open port 23 (Telnet) which is not needed.
    - **Remediation**: Close unnecessary ports and services.

### Advanced Features

#### Creating Custom Scan Configurations

1. **Go to** `Configuration` > `Scan Configs`.
2. Click on `+` to create a new scan configuration.
3. Define the settings as per your requirements (e.g., specific ports, types of checks).
4. Save the configuration and use it for your tasks.

#### Scheduling Regular Scans

1. **Create a schedule**:
    - Navigate to `Configuration` > `Schedules`.
    - Click on `+` to create a new schedule.
    - Define the frequency (e.g., daily, weekly) and save it.

2. **Apply the schedule to a task**:
    - When creating or editing a task, assign the schedule under the `Schedule` section.
    - The task will now run automatically as per the defined schedule.

### Best Practices

1. **Regular Updates**: Keep your OpenVAS and its feeds updated to ensure you have the latest vulnerability information.
2. **Comprehensive Scans**: Perform comprehensive scans periodically, not just on-demand.
3. **Prioritize Findings**: Focus on fixing high and medium severity vulnerabilities first.
4. **Documentation**: Keep detailed records of scans, findings, and remediation steps.
5. **Continuous Learning**: Stay updated with the latest security trends and vulnerabilities.

### Conclusion

OpenVAS is a robust tool for penetration testers, providing a wide array of features for identifying and managing vulnerabilities. By following this tutorial, junior penetration testers can effectively use OpenVAS to enhance their security assessments. Remember, the key to effective penetration testing is not just finding vulnerabilities but also understanding their impact and how to remediate them.