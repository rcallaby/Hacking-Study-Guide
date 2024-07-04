# Splunk

### Step 1: Installation and Setup
1. **Download Splunk**: Go to the [Splunk website](https://www.splunk.com) and download the Splunk Enterprise or Splunk Free depending on your requirements.
2. **Install Splunk**: Follow the installation instructions for your operating system.
   - For Windows, run the installer and follow the prompts.
   - For macOS, use the `.dmg` file.
   - For Linux, use the package manager or download the `.tar` file and follow the instructions.

### Step 2: Getting Started with Splunk
1. **Open Splunk**: Once installed, open the Splunk web interface. Typically, it's at `http://localhost:8000`.
2. **Login**: Use the default credentials (`admin/changeme` for the first login, then change the password).

### Step 3: Adding Data to Splunk
1. **Add Data**:
   - Go to the Splunk home page and click on "Add Data".
   - Choose a data source type (Upload, Monitor, Forward).
     - **Upload**: For static files like logs (`.log` files).
     - **Monitor**: For continuously updating files or directories.
     - **Forward**: For data from other servers.
   - Follow the prompts to upload your data.
   - Select a source type (e.g., `syslog` for system logs).
   - Assign the data to an index (create a new one or use `main`).

### Step 4: Searching and Investigating Data
1. **Search Interface**:
   - Go to the Search & Reporting app.
   - Use the search bar to query your data.

2. **Basic Searches**:
   - `index=main`: Search all data in the main index.
   - `index=main error`: Search for the keyword "error" in the main index.
   - `index=main sourcetype=syslog`: Search all syslog entries.

3. **Example Searches**:
   - Find failed login attempts: `index=main sourcetype=secure "failed password"`
   - Find successful logins: `index=main sourcetype=secure "Accepted password"`

### Step 5: Using Fields and Stats
1. **Extract Fields**:
   - Splunk automatically extracts fields, but you can also manually extract them.
   - Use the `Field Extractor` tool to define new fields.

2. **Basic Stats**:
   - `stats count by source`: Count events grouped by source.
   - `stats avg(response_time) by host`: Average response time grouped by host.

3. **Example Stats**:
   - Find the number of login attempts per user: `index=main sourcetype=secure | stats count by user`
   - Find the average duration of sessions: `index=main sourcetype=web | stats avg(session_duration)`

### Step 6: Creating Alerts
1. **Set up Alerts**:
   - Go to the Alerts section.
   - Click on "Create Alert".
   - Define a search query for the alert condition.
   - Set the trigger conditions (e.g., if more than 10 failed login attempts in 5 minutes).

2. **Example Alert**:
   - Alert for multiple failed logins: `index=main sourcetype=secure "failed password" | stats count by user | where count > 5`
   - Configure to trigger when the condition is met and set notification options (email, webhook, etc.).

### Step 7: Creating Dashboards
1. **Create a Dashboard**:
   - Go to the Dashboards section.
   - Click on "Create New Dashboard".
   - Add panels using saved searches or new queries.

2. **Example Panels**:
   - Panel for login attempts: `index=main sourcetype=secure | timechart count by user`
   - Panel for error rates: `index=main "error" | timechart count by sourcetype`

### Step 8: Advanced Features
1. **Use Splunk Apps**:
   - Explore and install apps from Splunkbase (e.g., Splunk Security Essentials).
   - Follow app-specific instructions for additional functionality.

2. **Advanced Search Commands**:
   - `eval`: Create new fields or modify existing ones.
     - Example: `eval status=if(status_code==200, "OK", "FAIL")`
   - `transaction`: Group events into transactions.
     - Example: `transaction startswith="login" endswith="logout"`

### Practical Examples

#### Example 1: Investigating Failed SSH Logins
1. **Search Query**: `index=main sourcetype=secure "failed password"`
2. **Extract Fields**:
   - Identify the `user` and `source_ip` fields if not automatically extracted.
3. **Stats and Alerts**:
   - Count of failed logins by user: `index=main sourcetype=secure "failed password" | stats count by user`
   - Alert for suspicious activity: Create an alert if a user has more than 10 failed login attempts in an hour.

#### Example 2: Monitoring Web Server Logs
1. **Search Query**: `index=main sourcetype=access_combined`
2. **Stats**:
   - Count of HTTP 404 errors: `index=main sourcetype=access_combined status=404 | stats count by uri`
3. **Dashboard Panels**:
   - Panel for top requested pages: `index=main sourcetype=access_combined | top uri`
   - Panel for status codes over time: `index=main sourcetype=access_combined | timechart count by status`

### Conclusion
Splunk is a powerful tool for cybersecurity, offering real-time monitoring, alerting, and analysis capabilities. By following these steps and practicing with real data, you can effectively leverage Splunk to enhance your security posture.
