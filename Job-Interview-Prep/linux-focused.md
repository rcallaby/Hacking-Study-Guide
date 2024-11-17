# Linux Administration Questions

## File System and Permissions:
---

#### **1. How does the Linux file permission model work (e.g., rwx notation)?**

The Linux file permission model is based on three main components:
1. **File Types and Ownership:**
   - Each file has three types of ownership:
     - **Owner:** The user who owns the file.
     - **Group:** The group associated with the file.
     - **Others:** Anyone who is not the owner or in the group.

2. **Permission Classes:**
   - **Read (r):** Allows reading the contents of a file or listing the contents of a directory.
   - **Write (w):** Allows modifying the contents of a file or creating/deleting files in a directory.
   - **Execute (x):** Allows executing a file (if it’s a script or binary) or accessing a directory.

3. **Notation and Representation:**
   - Permissions are represented as a string, e.g., `-rw-r--r--`.
     - The first character indicates the file type (`-` for regular file, `d` for directory, etc.).
     - The next nine characters are grouped into three sets: owner, group, and others.
     - Example: `-rw-r--r--`
       - Owner: `rw-` (read and write).
       - Group: `r--` (read only).
       - Others: `r--` (read only).

4. **Numeric (Octal) Representation:**
   - Permissions can also be represented numerically:
     - `r` = 4, `w` = 2, `x` = 1.
     - Combine the values for each class (e.g., `rw-` = 6, `r--` = 4).
     - Example: `chmod 644 file.txt` sets `rw-r--r--`.

---

#### **2. How would you recursively change ownership and permissions on a directory?**

To recursively change ownership and permissions, use the following commands:

1. **Change Ownership:**
   ```bash
   sudo chown -R <owner>:<group> <directory>
   ```
   - The `-R` flag ensures the command applies to all files and subdirectories within the specified directory.
   - Example:
     ```bash
     sudo chown -R user:group /path/to/directory
     ```

2. **Change Permissions:**
   ```bash
   chmod -R <permissions> <directory>
   ```
   - Example:
     ```bash
     chmod -R 755 /path/to/directory
     ```
   - This sets the directory and all its contents to be readable, writable, and executable by the owner, and readable and executable by the group and others.

---

### **Additional Questions**

#### **3. What are Setuid, Setgid, and Sticky Bit permissions, and why are they important?**

1. **Setuid (Set User ID):**
   - When set on an executable file, this bit allows the file to run with the permissions of its owner.
   - Represented as `s` in the owner’s execute field (e.g., `-rwsr-xr-x`).
   - Example: `/usr/bin/passwd` uses setuid to allow users to change their passwords securely.

2. **Setgid (Set Group ID):**
   - When set on an executable, it allows the file to run with the group permissions of the file.
   - When set on a directory, new files and subdirectories inherit the group ID of the parent directory.
   - Represented as `s` in the group’s execute field (e.g., `drwxrwsr-x`).

3. **Sticky Bit:**
   - Used on directories to restrict file deletion.
   - Only the file owner, directory owner, or root can delete files in the directory.
   - Represented as `t` in the others' execute field (e.g., `drwxrwxrwt`).
   - Example: `/tmp` directory.

**Importance:**
- These special permissions enhance security and usability, but misconfiguration can lead to privilege escalation vulnerabilities.

---

#### **4. How can you find files with specific permissions, such as setuid or setgid, on a Linux system?**

Use the `find` command:
```bash
find / -perm /4000 2>/dev/null
```
- The `/4000` flag searches for files with the setuid bit.
- Replace `/4000` with `/2000` to search for setgid files.
- `2>/dev/null` suppresses permission-denied errors.

**Why important for penetration testing?**
- Identifying files with these permissions can uncover potential privilege escalation paths.

---

#### **5. How would you secure sensitive files in a Linux environment?**

1. **Use Strict Permissions:**
   - Example:
     ```bash
     chmod 600 sensitive_file.txt
     ```
     Ensures only the owner can read/write the file.

2. **Restrict Access:**
   - Use `chown` to assign appropriate ownership.
   - Example:
     ```bash
     chown root:root sensitive_file.txt
     ```

3. **Encrypt Files:**
   - Example with `gpg`:
     ```bash
     gpg -c sensitive_file.txt
     ```

4. **Use ACLs for Granular Permissions:**
   - Example:
     ```bash
     setfacl -m u:username:r-- sensitive_file.txt
     ```

5. **Monitor and Audit:**
   - Use tools like `auditd` to log access to sensitive files.

---

#### **6. How can misconfigured file permissions lead to security vulnerabilities?**

1. **Privilege Escalation:**
   - Files with excessive permissions (e.g., `chmod 777`) allow unauthorized users to modify or execute files, leading to exploitation.

2. **Information Disclosure:**
   - Sensitive files with world-readable permissions may expose critical data (e.g., `/etc/shadow`).

3. **Code Injection:**
   - Writable scripts or binaries can be modified by attackers to execute malicious code.

4. **Denial of Service (DoS):**
   - Writable directories can be abused to fill disk space with junk data.

**Mitigation:**
- Regularly audit permissions using tools like `find` and ensure adherence to the principle of least privilege.

---

#### **7. What tools can be used to automate file system permission audits?**

1. **Lynis:**
   - A security auditing tool that includes checks for file permissions.
   - Example:
     ```bash
     lynis audit system
     ```

2. **chkrootkit:**
   - Searches for common rootkits and misconfigurations.

3. **Custom Scripts:**
   - Use bash scripts with `find` and `ls` commands to scan for specific permission issues.

---

#### **8. During a penetration test, how would you identify and exploit writable directories?**

1. **Identify Writable Directories:**
   ```bash
   find / -type d -perm -o+w 2>/dev/null
   ```

2. **Exploit:**
   - **Privilege Escalation:** Modify scripts executed by privileged users.
   - **Persistence:** Drop malicious payloads into writable locations.

3. **Mitigation Recommendations:**
   - Remove world-writable permissions unless explicitly required.
   - Secure sensitive directories with sticky bits.

---

### **Preparation Tips for Interviews**

1. **Understand Practical Scenarios:**
   - Be ready to explain how improper file permissions can lead to exploitation during penetration testing engagements.
   - Be prepared to discuss real-world examples of vulnerabilities caused by misconfigured permissions.

2. **Demonstrate Command Proficiency:**
   - Be able to write and explain `find`, `chmod`, `chown`, and `acl` commands fluently.

3. **Highlight Mitigation Strategies:**
   - Discuss how you would identify and fix misconfigurations.

By focusing on these areas, you will be well-prepared to answer advanced technical questions in a penetration testing interview.

Here’s a detailed exploration of the topic *Processes and Services* in Linux, expanding on the provided questions and adding new ones. Detailed answers are given to demonstrate technical expertise in managing and analyzing processes and services, particularly in the context of a penetration testing or system administration role.

---

#### **1. How can you list all running processes in Linux?**

You can list all running processes using several commands, depending on the level of detail required:

1. **Using `ps`:**
   ```bash
   ps -aux
   ```
   - `a`: Lists processes of all users.
   - `u`: Displays user-oriented output.
   - `x`: Includes processes not associated with a terminal (background processes).

2. **Using `top`:**
   - Interactive, real-time display of processes.
   - Press `q` to exit.
   - Example:
     ```bash
     top
     ```

3. **Using `htop`:**
   - Enhanced version of `top` with a user-friendly interface.
   - Requires installation:
     ```bash
     sudo apt install htop
     htop
     ```

4. **Using `pidof`:**
   - Retrieves the process ID (PID) of a specific process.
   - Example:
     ```bash
     pidof apache2
     ```

5. **Using `pgrep`:**
   - Searches for processes by name.
   - Example:
     ```bash
     pgrep sshd
     ```

6. **Using `systemctl` (for services):**
   ```bash
   systemctl list-units --type=service
   ```
   - Lists active services managed by `systemd`.

**Relevance for Penetration Testing:**
- These commands help identify misbehaving or unauthorized processes, which could indicate malicious activity.

---

#### **2. What are systemd and init, and how do they differ?**

1. **init (SysVinit):**
   - The traditional init system for Unix-like operating systems.
   - Operates through a series of runlevels (`0-6`), where each runlevel corresponds to a specific system state.
   - Uses shell scripts in `/etc/rc.d/` or `/etc/init.d/` to start and stop services.

2. **systemd:**
   - A modern replacement for init, designed to overcome its limitations.
   - Uses units (e.g., `.service`, `.socket`, `.target`) to manage services and dependencies.
   - Benefits:
     - **Parallelization:** Starts services simultaneously for faster boot times.
     - **On-demand loading:** Starts services only when needed.
     - **Integrated logging:** Works with `journald` for centralized log management.
   - Config files are located in `/lib/systemd/system/` or `/etc/systemd/system/`.

**Differences:**
| Feature             | init                   | systemd              |
|---------------------|------------------------|----------------------|
| **Parallelization** | No                     | Yes                  |
| **Configuration**   | Scripts in `/etc/init.d/` | Unit files in `/etc/systemd/system/` |
| **Dependency Mgmt** | Limited                | Dependency-aware     |
| **Logging**         | Syslog                 | journald             |
| **Runlevels**       | Defined (`0-6`)        | Targets (e.g., `multi-user.target`) |

**Relevance for Penetration Testing:**
- Knowing these systems aids in identifying and exploiting misconfigured services or pivoting through processes.

---

### **Additional Questions**

#### **3. How can you kill a process in Linux?**

1. **Using `kill`:**
   ```bash
   kill -SIGTERM <PID>
   ```
   - `SIGTERM` (15): Gracefully stops a process.
   - Replace with `SIGKILL` (9) to forcibly terminate.
   - Example:
     ```bash
     kill -9 1234
     ```

2. **Using `killall`:**
   - Stops processes by name.
   - Example:
     ```bash
     killall apache2
     ```

3. **Using `pkill`:**
   - Searches and terminates processes by name.
   - Example:
     ```bash
     pkill -f my_script.py
     ```

**Relevance:**
- Killing unauthorized or resource-intensive processes is critical for system stability and security.

---

#### **4. How do you identify which service or process is using a specific port?**

1. **Using `lsof`:**
   ```bash
   lsof -i :<port>
   ```
   - Example:
     ```bash
     lsof -i :22
     ```

2. **Using `netstat`:**
   ```bash
   netstat -tuln | grep <port>
   ```
   - `-t`: TCP, `-u`: UDP, `-l`: Listening, `-n`: Numeric addresses.

3. **Using `ss`:**
   ```bash
   ss -tuln | grep <port>
   ```

4. **Using `fuser`:**
   ```bash
   fuser <port>/tcp
   ```

**Relevance for Penetration Testing:**
- Identifying services tied to open ports can reveal vulnerable software or misconfigurations.

---

#### **5. How would you start, stop, and restart a service in Linux?**

1. **Using `systemctl` (systemd):**
   ```bash
   systemctl start <service>
   systemctl stop <service>
   systemctl restart <service>
   systemctl status <service>
   ```
   - Example:
     ```bash
     systemctl restart sshd
     ```

2. **Using `service` (init):**
   ```bash
   service <service> start
   service <service> stop
   service <service> restart
   ```
   - Example:
     ```bash
     service apache2 restart
     ```

---

#### **6. How can you ensure a service starts automatically on boot?**

1. **Using `systemctl` (systemd):**
   ```bash
   systemctl enable <service>
   ```
   - To disable:
     ```bash
     systemctl disable <service>
     ```

2. **Using `chkconfig` (init):**
   ```bash
   chkconfig <service> on
   ```

**Relevance for Penetration Testing:**
- Persistent malware may use these methods to ensure execution after reboot.

---

#### **7. How would you investigate a suspicious process?**

1. **Get detailed information using `ps`:**
   ```bash
   ps -p <PID> -o pid,ppid,cmd,%cpu,%mem
   ```

2. **Check the executable path using `readlink`:**
   ```bash
   readlink -f /proc/<PID>/exe
   ```

3. **View open files using `lsof`:**
   ```bash
   lsof -p <PID>
   ```

4. **Check network activity using `netstat` or `ss`:**
   ```bash
   netstat -anp | grep <PID>
   ```

5. **Inspect process memory:**
   ```bash
   cat /proc/<PID>/maps
   ```

6. **Kill or isolate the process if necessary.**

**Relevance:**
- Essential for identifying malicious processes during incident response.

---

#### **8. What tools can you use to monitor and analyze Linux processes and services?**

1. **`strace`:** Traces system calls and signals.
   ```bash
   strace -p <PID>
   ```

2. **`lsof`:** Lists open files for processes.

3. **`auditd`:** Monitors and logs events on the system.

4. **`top`/`htop`:** Provides real-time process monitoring.

5. **`journald` Logs:** View logs using:
   ```bash
   journalctl -u <service>
   ```

---

### **Preparation Tips for Interviews**

1. **Understand Key Concepts:**
   - Be prepared to explain how Linux manages processes and services under different init systems (`init` vs. `systemd`).
   - Discuss how you would identify, analyze, and mitigate malicious processes.

2. **Command Proficiency:**
   - Demonstrate expertise with `ps`, `top`, `htop`, `systemctl`, `kill`, and other process management commands.

3. **Scenario-Based Questions:**
   - Be ready to answer hypothetical questions, such as how to stop a runaway process or investigate a suspicious service running on an open port.

By mastering these questions and answers, you'll be well-prepared to handle technical interview questions related to processes and services.

Networking:
    What commands would you use to check open ports and active network connections?
    How do you configure a static IP on a Linux machine?

Security:
    How do you harden an SSH server?
    What is SELinux/AppArmor, and how do they enhance Linux security?

Logs and Monitoring:
    How would you analyze logs in /var/log/ for potential issues?
    What tools can you use to monitor Linux server performance?