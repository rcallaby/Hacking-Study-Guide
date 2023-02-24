# User Enumeration

When gaining a foothold on a machine it is very important to enumerate the users that you can find on the machine. You can determine who may have admin privileges and those who don't. Before attempting to escalate it is important to figure out who is there and what roles they may have.

The first command would be to determine who you are the time you gain a foothold and that is accomplished with the whoami command.
```
    whoami
```
You can also see what privileges you may have with the /priv switch such as the following:
```
    whoami /priv
```
You can determine what groups you currently belong to by using the /groups switch such as the following:
```
    whoami /groups
```

The command net user shows how many users are on the machine you are logged into. Now, this doesn't determine how many users or what users may be on the network. However, if you have higher admin rights users on the machine then that could be a potential avenue of attack.
```
    net user
```

You can look into what these users have in terms of pivileges and so on by using the network name along with the net user command such as the following:
```
    net user [username]
```

You can also look at the local groups such as the following:
```
    net localgroup
```

If you know a group has admin privileges such as the group administrators then you can look into that to find what may be there such as the following:
```
    net localgroup administrators
```



