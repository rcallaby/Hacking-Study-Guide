<strong>Password Hunting</strong>

Finding passwords is obviously fairly important in order to escalate privileges on a system. There are many ways to do this and as I discover more ways to find passwords I will list them here.

Passwords are typically stored in files. This means a lot of vulnerablities could be found just by searching for these passwords.

Passwords can also be stored in the registry.

You can use findstr to help you find passwords such as the following:
```
    findstr /si password *.txt
```
You can also search for more file types by using the following such as:
```
    findstr /si password *.txt *.ini *.config *.xml
```
Of course, you will want to find a directory where these files may exist. You probably won't find passwords in the /MyDocuments directory of your system or the system you are enumerating. But that could be possible, so don't discount it.

You can find a lot of methods for this from GTFOBins. So you should definitely use that for a reference.