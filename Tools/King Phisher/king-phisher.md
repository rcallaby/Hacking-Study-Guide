# King Phisher

King Phisher is a robust open-source tool designed for spear phishing campaigns, primarily used in the field of cybersecurity. It facilitates the creation, management, and monitoring of phishing attacks to test and train employees on recognizing phishing attempts. The tool is widely utilized by penetration testers, security consultants, and organizations' internal security teams to simulate real-world phishing scenarios. By using King Phisher, these professionals can evaluate the susceptibility of their employees to phishing attacks and enhance overall security awareness within the organization.

The tool's functionality includes crafting customized phishing emails, creating fake landing pages, and tracking user interactions. Users can set up King Phisher on a server and use its client interface to manage phishing campaigns. The process involves configuring email templates, specifying recipient lists, and monitoring the success of the campaigns through detailed reports. These features make King Phisher an essential component in a comprehensive security training and awareness program, allowing organizations to identify weak points and address them proactively.

However, several precautions must be taken when using King Phisher. It is crucial to obtain explicit permission from the organization being tested to avoid legal repercussions. Users must ensure compliance with all relevant laws and regulations governing phishing simulations and data privacy. Ethical considerations are paramount; the tool should be used responsibly to educate and protect, rather than exploit. Properly informing and gaining consent from all stakeholders involved is necessary to maintain trust and transparency throughout the phishing simulation process.


### Step 1: Installation

King Phisher can be installed on various operating systems, but we'll focus on an Ubuntu-based system.

1. **Update System Packages**:
    ```bash
    sudo apt update
    sudo apt upgrade -y
    ```

2. **Install Dependencies**:
    ```bash
    sudo apt install git python3 python3-pip python3-dev libpq-dev postgresql postgresql-contrib build-essential
    ```

3. **Clone the King Phisher Repository**:
    ```bash
    git clone https://github.com/securestate/king-phisher.git
    cd king-phisher
    ```

4. **Install Python Dependencies**:
    ```bash
    sudo pip3 install -r requirements.txt
    ```

### Step 2: Setting Up the Database

King Phisher uses PostgreSQL for its database.

1. **Create a PostgreSQL User and Database**:
    ```bash
    sudo -u postgres createuser king_phisher --createdb --login --pwprompt
    sudo -u postgres createdb king_phisher --owner=king_phisher
    ```

2. **Configure PostgreSQL**:
    Edit the PostgreSQL configuration file (usually found at `/etc/postgresql/[version]/main/pg_hba.conf`):
    ```plaintext
    local   king_phisher   king_phisher                               md5
    host    king_phisher   king_phisher   127.0.0.1/32    md5
    ```
    Restart PostgreSQL:
    ```bash
    sudo service postgresql restart
    ```

### Step 3: Configuring King Phisher

1. **Edit the Configuration File**:
    The main configuration file is `server_config.yml`. Example configuration:
    ```yaml
    server:
      address: 0.0.0.0
      port: 80
      ssl: false
      server_header: "Apache"
      user: nobody
      group: nogroup
      web_root: "/var/www"
      database:
        connection: postgresql+psycopg2://king_phisher:[password]@localhost/king_phisher
    ```

2. **Setup SSL (Optional but recommended)**:
    If you want to use SSL, set up your certificates and adjust the configuration:
    ```yaml
    ssl:
      certificate: "/path/to/cert.pem"
      key: "/path/to/key.pem"
      enabled: true
    ```

### Step 4: Starting the King Phisher Server

1. **Run the Server**:
    ```bash
    sudo ./KingPhisherServer
    ```

2. **Check for Successful Startup**:
    The server should start without errors, listening on the configured port.

### Step 5: Configuring the King Phisher Client

1. **Install the Client**:
    The client can be installed on the same or a different machine. Repeat the installation steps but only clone the repository and install dependencies.

2. **Run the Client**:
    ```bash
    sudo ./KingPhisher
    ```

3. **Connect to the Server**:
    Use the client interface to connect to your server. You will need to provide the server address and port configured earlier.

### Step 6: Creating a Phishing Campaign

1. **Login to King Phisher Client**:
    Use the credentials set during the PostgreSQL setup.

2. **Create a New Campaign**:
    Navigate to `Campaigns` -> `New Campaign`.

3. **Configure Campaign Details**:
    - **Campaign Name**: Give it a descriptive name.
    - **URL**: The URL where the phishing page will be hosted.
    - **Landing Page**: Select a landing page template.
    - **Expiration Date**: Set a campaign expiration date.
    - **Company Name**: Target company's name for the campaign context.
    - **Tracking Images**: Enable if you want to track email openings.

### Step 7: Crafting the Phishing Email

1. **Email Template**:
    Navigate to `Templates` -> `Email Templates` and create a new template. Example:
    ```html
    <html>
    <body>
    <p>Hello,</p>
    <p>We noticed unusual activity in your account. Please <a href="{{url}}">click here</a> to verify your details.</p>
    <p>Thank you.</p>
    </body>
    </html>
    ```

2. **Sending Emails**:
    Go to `Campaigns` -> `Send Messages`. Fill in the details:
    - **Recipients**: List of email addresses.
    - **Email Subject**: Subject line for the phishing email.
    - **Template**: Select the crafted email template.

### Step 8: Monitoring the Campaign

1. **View Campaign Results**:
    Navigate to `Campaigns` -> `View Campaigns` and select your campaign to view statistics like email opens, clicks, and credentials entered.

### Step 9: Post-Campaign Analysis

1. **Generate Reports**:
    Use the `Reports` section to generate comprehensive reports on the campaign's success, identifying which users fell for the phishing attempt.

### Examples and Best Practices

1. **Example Email Subject Lines**:
    - "Urgent: Verify Your Account"
    - "Security Alert: Unusual Login Attempt"
    - "Important: Update Your Password"

2. **Landing Page Examples**:
    - Clone of a bank login page.
    - Corporate intranet login page.
    - Fake Microsoft 365 login.

3. **Phishing Scenarios**:
    - **Credential Harvesting**: Users are prompted to enter their credentials on a fake login page.
    - **Malware Delivery**: Links or attachments in the email deliver malware when clicked.

4. **Legal and Ethical Considerations**:
    Always obtain explicit permission from the organization you're testing. Ensure all activities comply with relevant laws and regulations.

By following these steps, you can effectively use King Phisher to conduct phishing simulations, helping improve your organization's cybersecurity posture.