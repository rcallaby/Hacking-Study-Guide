# System Enumeration

This is a part of more enumeration once you have a user shell.

First you want to maybe see what Kernel version you are using.
Use the following
```
    uname -a
```

This is for searching for Kernel exploits
Alternatively, you could use
```
    cat /proc/version
```
Or you could use:
```
    cat /etc/issue
```

To check what architecture the machine is running you would use the following:
```
    lscpu
```
This shows what processors are running, how many threads and what architecture this box may be running.

The reason why this is important is because when researching certain exploits you need to make sure that exploit would actually work.

So, if there is an exploit that only works on a two threaded system and you are only running one thread then that exploit won't work.

Again, it would be beneficial to take notes as you enumerate a box. These notes come in handy if you get stuck and later discover a potential exploit because you may have missed something while enumerating the box.

As well, you want to see what services are running by using the following command:
```
    ps aux
```
As well, you can narrow down the services by the user or service by using the following:
```
    ps aux | grep <username>

```

## Tools for Linux System Enumeration
* [LinEnum](https://github.com/rebootuser/LinEnum) - One of the most used tools for Linux Enumeration 
* [linux-smart-enumeration](https://github.com/diego-treitos/linux-smart-enumeration) - A robust Linux Enumeration tool
* [SUID3NUM](https://github.com/Anon-Exploiter/SUID3NUM) - A Linux Enumeration tool that is designed to find all the SUID binaries
* [uptux](https://github.com/initstring/uptux) - specialized escalation checks for Linux
* [SPARTA](https://github.com/SECFORCE/sparta) - A GUI tool for scanning computers on the network or remote
* [Linux Exploit Suggester](https://github.com/The-Z-Labs/linux-exploit-suggester) - A tool that will find potential exploits and suggests ways to use them

## Tutorials for Linux System Enumeration
* [Linux Operating System Enumeration - Hacking Tutorial](https://www.hacking-tutorial.com/hacking-tutorial/linux-operating-system-enumeration/) - A tutorial on Linux Enumeration 
* [Ethical Hacking - Enumeration](https://www.tutorialspoint.com/ethical_hacking/ethical_hacking_enumeration.htm) - A tutorial made by Tutorialspoint
* [Linux Enumeration Cheat Sheet](https://cyberlab.pacific.edu/resources/linux-enumeration-cheat-sheet) - A Cheat Sheet by the University of the Pacific
* [Basic Linux Privilege Escalation](https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/) - A good overview of how to perform Linux Privilege Escalation with enumeration aa a part of it


 