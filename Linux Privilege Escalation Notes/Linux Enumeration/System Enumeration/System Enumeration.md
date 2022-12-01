<strong>System Enumeration</strong>

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



 