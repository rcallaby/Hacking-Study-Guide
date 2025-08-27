# AV and Firewall Enumeration

When doing CTF's or any type of real world penetratino testing finding and enumerating the various anti-virus and firewalls that may be present should be a good idea. You will want to learn this not only for the harder machines but also for real world penetration testing.

You will want to look at the service control or sc to query what services are enabled. For instance, Windows Defender is typically a service and you can figure out if it is running by using the following command:

```
sc query windefend
```
There may be oher antivirus or firewalls running and you can check it by using the following:

```
sc queryex type=service
```
This gives you a list of all the services running on your machine.

To check firewalls you can run netsh advfirewall firewall dump which may or may not return anything depending upon your machine.
```
netsh advfirewall firewall dump
```
Or alternatively, you can use the more up to date command such as the following:
```
netsh firewall show state
```
As well you can show the configuration of your firewall by using the following:
```
netsh firewall show config
```

