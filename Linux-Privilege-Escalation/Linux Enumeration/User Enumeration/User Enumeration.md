# User Enumeration

User enumeration helps to find out what permissions we may have and what we may not have. The idea is obviously try and get more permissions so that we can gain root access or super user access to the box.

To figure out who you are in the box you would just simply use the command whoami such as this:
```
    whoami
```
Alternatively, you can also use id to figure out what is your id and also what groups you may be a part of. If you are a part of the sudo group that would be listed here. If you are already part of the sudo group then it would be very easy to gain root access to the machine. That would be a easy win.

```
    id
```
You can run the command sudo -l to figure out what commands you can run as sudo. The more that you have access to as a sudo user the more likelyhood that you can gain a root access to the machine.
```
    sudo -l
```
Again, you will want to keep notes as to what you can use without password because you may become stuck and your notes will help save you in the end.

You could look at the /etc/passwd file to see what other users may be on the system. When there are more than one user on the system then you will need to enumerate them as well.

```
    cat /etc/passwd
```
You can get a listing of all the users without a complicated format by using the following Linux command. It should make things far easier to read:

```
    cat /etc/passwd | cut -d : -f 1
```
This eliminates all of the other data that all the users have in the passwd file. Again, this is helpful to keep notes on when hacking so that you can go back to it if you get stuck. Your notes may help you in the end because you may have missed something.

To check the passwords in a Linux box as a user you would use the following:
```
    cat etc/shadow
```
As well, you may want to see if you can enumerate the group file such as the following:
```
    cat etc/group
```
As well, if you gained access to a user then you may want to check the history of that user as that may show something interesting that you don't want to miss.
```
    history
```
It may also be helpful to grep through history if there is a lot there. A history of several thousand would mean that there is a high likelihood of interesting findings being present. Not clearing history of users is a potential security risk as well. So, that should be a finding in your report.

Finally, you may want to just see if you can sudo into a root privilege by typing the following:
```
    sudo su -
```



