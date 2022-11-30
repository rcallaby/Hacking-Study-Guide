<strong>Network Enumeration</strong>

Doing a network enumeration is necessary as you can determine what other systems or networks this computer may be connected to. By doing a enumeration you can determine if you should be able to pivot to a different machine or to see if there may be more vulnerablities on the network.

The first command to enumerate the network would be ipconfig.
```
    ipconfig
```
As well, you can get more information by using the /all switch on that command such as:
```
    ipconfig /all
```
As well, it is important to check out the arp tables by using the following command:
```
    arp -a
```
As well you may want to look at the routing table by using route print command such as:
```
    route print
```
You can also determine who this computer is talking to by using the netstat command such as the following:
```
    netstat -ano
```
The netstat command also provides who may be listening and what ports may be open. The more ports that are open the bigger the threat surface and the more vulnerabilities the machine and the entire network may be subject to.

Internal services are also very important.
