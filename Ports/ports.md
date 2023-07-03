# Ports

Below is a listing of all the most important ports to check when doing any type of penetration tests

* 21 - FTP
* 22 - SSH
* 25 - SMTP

* 111 - RPCbind (maps rpc services to listening ports)
* 139 - SMB or Samba
* 161 - SNMP (check if default community string in use)
* 445 - SMB or Samba

* 512 - R-services
* 513 - R-services
* 514 - R-services

* 1524 - ingreslock backdoor (connect with netcat)
* 2049 - Network File System (NFS)
* 2049 - NFS (try to mount the remote file system)
* 3632 - distccd (Distributed code compilation)
* 3690 - SVN (Check anonymous svn repo access)

* 1099 - RMI (use exploit/multi/misc/java_rmi_server)
* 3306 - mysql database (mysql -h 192.168.14.129)

* 5432 - Postgres database
* 5900 - VNC (vncviewer 192.168.14.129:5900)

* 6667 - IRC Daemon (could be unrealRCD having backdoor)
* 6697 - IRC Daemon (could be unrealRCD having backdoor)

* 8080 - UPnP (windows IoT webserver "Device Portal")
* 8787 - dRuby (Distributed Ruby)

* 37215 - UpnP (check for CVE-2020-12695)

