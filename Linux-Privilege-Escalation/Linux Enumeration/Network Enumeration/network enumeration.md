# Network Enumeration

This is really important. It helps us understaand what open ports that are open internally, and some other tools or programs that may be available to us to allow us to enumerate more.

The first command would be ifconfig or iwconfig if you want to know of any wireless connections that may be available.
```
    ifconfig or iwconfig
```
Alternatively, you could use the new version of this command that is ip or in this case it would be the command ip a which basically does the same thing but since ifconfig has been deprecated it may be best to use the updated command.
```
    ip a
```

Sometimes you may have a computer that has two nics and therefore may have two home ip addresses.

You will also want to check to see what is included in your local network by using the following:
```
    ip route
```

Alternatively, you can use the command ip neigh to see what are your neighbors or what is in your network.

```
    ip neigh
```

Another good network enumeration command to know would be netstat which shows what services or ports may be open. Again, this is to see what esclation paths you may have available. Taking good notes is crucial to your success and also for creating detailed reports which is what is required as a Penetration Tester.

You would use the following command to help you enumerate a network using netstat:
```
    netstat -ano
```



