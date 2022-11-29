<strong>Windows System Enumeration</strong>

To start you would like at system archeitecture, the hostname, the drives, and so on. The more information you can obtain the better.

The first command you can type in is systeminfo
'''
    systeminfo
'''
Or to get a more succint version of this you would type the following:
'''
    systeminfo | findstr /B /C:"OS Name" /C:"OS Version" /C:"System Type"
'''
This is very similar to using grep in Linux where findstr is similar but not the same as grep.

This can help you determine if you can use a kernel exploit or a Windows System exploit. The more systeminfo you get the more refined you can be in what exploit to use.

As well, you can use hostname to determine the hostname of the machine to see if that is useful informtion.
'''
    hostname
'''
You can also determien what patches have been applied to the system. If you know a system may be vulnerable if no patches were applied for a certain exploit then you should be able to exploit that vulnerability and gain system access.

You can determine if something is patched by using the following command:
'''
    wmic qfe
'''
Alternatively, you can use the following command to get a more succint version of the displayed patches on your system
'''
    wmic qfe get Caption,Description,HotfixID,InstalledOn
'''
You can also see what drives may be on your system using a variation of the above command such as:
'''
    wmic localdisk get caption,description,providername
'''
The more drives available means more potential information available on how to escalate the machine.
