# Active Directory Checklist

### **Active Directory Security Checklist**

#### **1. Domain Enumeration**
   - **Gather basic domain information**: Domain name, domain controllers (DCs), trust relationships, domain functional levels.
   - **Identify domain controllers**:
     - Using `nslookup` to find DCs: `nslookup -type=SRV _ldap._tcp.dc._msdcs.<domain>`
     - Using `nltest`: `nltest /dclist:<domain>`
   - **Check for domain trust relationships**:
     - Using `nltest`: `nltest /domain_trusts`
     - Using PowerShell: `Get-ADTrust -Filter *`

#### **2. Using Powerview**
   - **Install PowerView**: Part of PowerSploit. Import the module: `Import-Module .\PowerView.ps1`
   - **Enumerate domain users**: `Get-NetUser`
   - **Enumerate domain groups**: `Get-NetGroup`
   - **Enumerate group memberships**: `Get-NetGroupMember -GroupName "Domain Admins"`
   - **Enumerate shares**: `Invoke-ShareFinder`
   - **Enumerate sessions**: `Get-NetSession`
   - **Enumerate logged-on users**: `Get-NetLoggedon`

#### **3. Using AD Module**
   - **Install Active Directory Module**: `Import-Module ActiveDirectory`
   - **Enumerate domain users**: `Get-ADUser -Filter *`
   - **Enumerate domain groups**: `Get-ADGroup -Filter *`
   - **Enumerate group memberships**: `Get-ADGroupMember -Identity "Domain Admins"`
   - **Enumerate organizational units (OUs)**: `Get-ADOrganizationalUnit -Filter *`
   - **Enumerate computers**: `Get-ADComputer -Filter *`

#### **4. Using Bloodhound**
   - **Remote Bloodhound**:
     - **Collect data**: Use `SharpHound` to collect data from the domain: `SharpHound.exe -c All`
     - **Upload data to Bloodhound**: Use the Bloodhound interface to upload the collected data and analyze.
   - **On-site Bloodhound**:
     - **Deploy collector**: Deploy `SharpHound` on a domain-connected system.
     - **Collect data and analyze**: Follow the same process as remote to collect and upload data for analysis.

#### **5. Using Adalanche**
   - **Remote Adalanche**:
     - **Deploy collector**: Similar to Bloodhound, use the Adalanche data collector.
     - **Upload and analyze**: Upload the collected data to the Adalanche server and analyze the AD environment.

#### **6. Useful Enumeration Tools**
   - **LDAP Enumeration**:
     - Use `ldapsearch` for Unix/Linux: `ldapsearch -x -H ldap://<dc_ip> -D "<bind_dn>" -w "<password>" -b "<search_base>" "(objectClass=*)"`
   - **Nmap**:
     - Scan for open ports and services: `nmap -p 88,135,139,389,445 <dc_ip>`
   - **CrackMapExec (CME)**:
     - General AD enumeration: `cme smb <dc_ip> -u <username> -p <password> --shares`
   - **Impacket**:
     - Use `GetUserSPNs.py` to find SPNs: `GetUserSPNs.py <domain>/<user>:<password>`
   - **ADRecon**:
     - Collect extensive AD information using `ADRecon.ps1`: `.\ADRecon.ps1 -All`

#### **7. Security Policies and Configurations**
   - **Check Group Policy Objects (GPOs)**:
     - List GPOs: `Get-GPO -All`
     - Check GPO links: `Get-GPLink -All`
   - **Audit Security Settings**:
     - Use `Secedit` to export security settings: `secedit /export /cfg <path\to\security\settings.cfg>`
   - **Review Password Policies**:
     - Check domain password policies: `Get-ADDefaultDomainPasswordPolicy`
   - **Review Account Lockout Policies**:
     - Check account lockout policies: `Get-ADDefaultDomainLockoutPolicy`

#### **8. Review Logs and Auditing**
   - **Check Event Logs**:
     - Review security-related event logs on DCs: `Get-WinEvent -LogName Security -MaxEvents 1000`
   - **Audit Logon Events**:
     - Check for suspicious logon events, failed logon attempts, and unusual access patterns.

### **Conclusion**
Regularly reviewing and updating this checklist ensures comprehensive security assessments of your Active Directory environment. It's important to stay updated with the latest tools and techniques as AD security evolves.