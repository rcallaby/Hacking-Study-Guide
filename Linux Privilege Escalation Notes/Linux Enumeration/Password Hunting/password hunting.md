# Password Hunting

Obviously finding passwords is crucial to actually gaining additional privileges in Linux. The following is some techniques for finding passwords using Linux. Of course, not all of these techniques work all the time but I would get into the habit of at least trying these techniques with each penetration test to make sure that these vulnerabilities aren't present.

You can use the grep command and the --color=auto to highlight the results. Since this is going to give you a lot of results it is helpful to actually see the results by using --color=auto to make it more apparent.

The full command is as follows to help you find passwords on a Linux machine:
```
    grep --color=auto -rnw '/' -ie "PASSWORD=" --color=always 2> /dev/null
```
You can also try and find the passwords through filenames that may be stored on the system. For this we would use the locate command such as:
```
    locate password | more
```
You could also use the following:
```
    locate pass | more
```
or even the following:
```
    locate pwd | more
```
There are many variations of this so use your imagination and try and figure out what may be readily available.

You could also find passwords in ssh files such as the authorized_keys file by using the following:
```
    find / -name authorized_keys
```
or by using the following:
```
    find / -name id_rsa
```
