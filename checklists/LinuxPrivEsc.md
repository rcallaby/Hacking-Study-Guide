# Linux Privilege Escalation

### System Information
- **Kernel Version**: Identify potential kernel exploits.
  - Commands: `uname -a`, `cat /proc/version`, `cat /etc/issue`
- **Distribution and Version**: Know specific distribution vulnerabilities.
  - Commands: `cat /etc/*-release`, `lsb_release -a`
- **Architecture**: Determine if the system is 32-bit or 64-bit.
  - Commands: `uname -m`, `file /bin/bash`
- **Hostname**: Gather system name.
  - Command: `hostname`

### Drives
- **Mounted Drives**: Check for interesting mount points and their permissions.
  - Commands: `df -h`, `mount`, `lsblk`
- **FSTAB Configuration**: Review for noexec, nosuid, nodev options that restrict execution.
  - Command: `cat /etc/fstab`
- **Disk Usage**: Identify writable locations and potential data storage.
  - Commands: `du -ah /`, `find / -type d -writable 2>/dev/null`

### Installed Software
- **Installed Packages**: Check for vulnerable versions of software.
  - Commands: `dpkg -l`, `rpm -qa`
- **Development Tools**: Look for compilers or debuggers.
  - Commands: `which gcc`, `which gdb`
- **Custom Software**: Identify non-standard applications.
  - Command: `ls /usr/local/bin`, `ls /opt`

### Scheduled Cron Jobs
- **User Cron Jobs**: Inspect user-level scheduled tasks.
  - Commands: `crontab -l`, `ls -la /var/spool/cron/crontabs`
- **System Cron Jobs**: Check system-level scheduled tasks.
  - Commands: `cat /etc/crontab`, `ls -la /etc/cron.*`, `ls -la /etc/cron.d`
- **Anacron Jobs**: Review jobs run by anacron.
  - Commands: `cat /etc/anacrontab`

### Processes
- **Running Processes**: Identify all running processes and their privileges.
  - Commands: `ps aux`, `top`, `pgrep -u root`
- **Hidden Processes**: Look for unusual or hidden processes.
  - Commands: `ps -ef`, `pstree`
- **Processes with Elevated Privileges**: Identify processes running as root or with setuid.
  - Command: `ps -eo euser,ruser,suser,fuser,f,comm,label`

### Timers
- **Systemd Timers**: Check for systemd timer units.
  - Commands: `systemctl list-timers --all`, `cat /etc/systemd/system/*.timer`

### Services
- **Active Services**: Review running services for potential exploits.
  - Commands: `service --status-all`, `systemctl list-units --type=service --all`
- **Startup Services**: Check services set to start on boot.
  - Commands: `systemctl list-unit-files`, `ls /etc/init.d/`, `chkconfig --list`

### Sockets
- **Listening Ports**: Identify open ports and associated services.
  - Commands: `netstat -tuln`, `ss -tuln`
- **UNIX Domain Sockets**: Review active sockets.
  - Command: `ss -x`

### Users
- **Current User**: Details of the current user.
  - Commands: `id`, `whoami`
- **All Users**: List of all system users.
  - Command: `cat /etc/passwd`, `getent passwd`
- **User Privileges**: Check user group memberships.
  - Commands: `groups`, `id`
- **Password Hashes**: Access to hashed passwords.
  - Command: `cat /etc/shadow`

### D-Bus
- **D-Bus Services**: Identify available D-Bus services.
  - Commands: `busctl list`, `dbus-send --system --dest=org.freedesktop.DBus --type=method_call --print-reply /org/freedesktop/DBus org.freedesktop.DBus.ListNames`

### Network
- **Network Interfaces**: Check network configuration and interfaces.
  - Commands: `ifconfig -a`, `ip a`
- **Routing Table**: Review routing configuration.
  - Commands: `route`, `ip route`
- **DNS Configuration**: Check DNS servers.
  - Command: `cat /etc/resolv.conf`
- **Firewall Rules**: Inspect iptables rules.
  - Commands: `iptables -L`, `ufw status`

### SUDO and SUID Commands
- **Sudo Privileges**: Review sudo permissions for the current user.
  - Command: `sudo -l`
- **SUID/SGID Binaries**: Identify binaries with the setuid/setgid bit set.
  - Commands: `find / -perm -4000 2>/dev/null`, `find / -perm -2000 2>/dev/null`

### Capabilities
- **File Capabilities**: List files with special capabilities.
  - Command: `getcap -r / 2>/dev/null`
- **Process Capabilities**: Check capabilities of running processes.
  - Command: `pscap`

### Open Sessions
- **Logged In Users**: Identify active user sessions.
  - Commands: `who`, `w`
- **TTY/PTY Sessions**: Review terminal sessions.
  - Commands: `tty`, `ps -ef | grep tty`

### SSH
- **SSH Keys**: Locate SSH keys for users.
  - Commands: `ls -la ~/.ssh/`, `find / -name authorized_keys 2>/dev/null`
- **SSH Configuration**: Review SSH server configuration.
  - Command: `cat /etc/ssh/sshd_config`
- **Active SSH Sessions**: Identify active SSH connections.
  - Command: `ss -t | grep ssh`

### ACLs
- **Access Control Lists**: Review ACLs on files and directories.
  - Commands: `getfacl -R /`, `ls -la`

### Any Interesting Files
- **Configuration Files**: Check for misconfigurations or sensitive information.
  - Commands: `find /etc -type f -exec grep -i 'password\|user\|admin' {} +`
- **Backup Files**: Look for unprotected backup files.
  - Commands: `find / -name '*.bak' -o -name '*.old' -o -name '*.backup' 2>/dev/null`
- **Database Files**: Identify database files with sensitive information.
  - Commands: `find / -name '*.db' -o -name '*.sql' 2>/dev/null`
- **Logs**: Review logs for sensitive data.
  - Commands: `cat /var/log/auth.log`, `cat /var/log/syslog`

### Any Writable Files
- **Writable Directories and Files**: Check for world-writable files and directories.
  - Commands: `find / -writable ! -user $(whoami)`, `find / -perm -002 2>/dev/null`
- **User Home Directories**: Check for writable files in user home directories.
  - Command: `find /home -writable 2>/dev/null`

### Misc Tricks
- **Environmental Variables**: Review environment variables for sensitive information.
  - Command: `env`, `printenv`
- **Shell History**: Check command history for sensitive data.
  - Commands: `cat ~/.bash_history`, `cat ~/.zsh_history`
- **Unattended Upgrades**: Look for unattended package upgrades.
  - Command: `cat /etc/apt/apt.conf.d/20auto-upgrades`
- **Kernel Exploits**: Search for known kernel exploits.
  - Commands: `searchsploit linux kernel`, `exploitdb`

