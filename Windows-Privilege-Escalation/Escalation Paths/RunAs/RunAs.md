# RunAs Escalation Path

You should be checking this as you log on as a low level user. You can run as an administrator as a low level user if you are given such privileges.

A command to enumerate to view what privileges you may have is listed below:

```
    cmdkey /list
```

As a penetration tester, one of the important techniques you need to be familiar with is Runas escalation on Windows. This technique is used to escalate privileges from a lower-privileged user account to a higher-privileged account. In this article, we will discuss how Runas escalation works, and provide a step-by-step guide on how to perform this technique.

## What is Runas?

Runas is a command-line tool in Windows that allows users to run a program as a different user account. The tool is useful for performing administrative tasks that require elevated privileges. By default, Runas will prompt the user for the password of the account they want to run the program as.

## How does Runas escalation work?

Runas escalation works by abusing the way Windows handles user accounts and privileges. When a user runs a program using Runas, Windows creates a new process that runs as the specified user account. This new process inherits the privileges of the user account, including any elevated privileges that the user may have.

If a lower-privileged user account has the ability to run a program as a higher-privileged user account, then the user can escalate their privileges to gain access to resources that they would not normally have access to. This is because the new process created by Runas will have the privileges of the higher-privileged user account, which can be used to access sensitive data or perform administrative tasks.

## Step-by-step guide for performing Runas escalation

Now that we understand how Runas escalation works, let's take a look at how to perform this technique. Here is a step-by-step guide for performing Runas escalation on Windows:

### Identify a vulnerable program
The first step in performing Runas escalation is to identify a vulnerable program that can be run with elevated privileges. This program should be one that can be run by a lower-privileged user account, but also has the ability to execute commands as a higher-privileged user account.

Some common examples of vulnerable programs include:

+ Scheduled tasks: These are tasks that are scheduled to run at specific times or intervals. They can be configured to run as a higher-privileged user account, but can be created and managed by lower-privileged user accounts.
+ Service executables: These are programs that run in the background as a service. They can be configured to run as a higher-privileged user account, but can be started and stopped by lower-privileged user accounts.
+ Control panel applets: These are programs that allow users to configure system settings. They can be configured to run as a higher-privileged user account, but can be launched by lower-privileged user accounts.
+ Create a payload
The next step is to create a payload that will be executed with elevated privileges. This payload can be any command or script that will run with the privileges of the higher-privileged user account.

For example, if the vulnerable program is a scheduled task, you can create a payload that will be executed when the task runs. This payload can be a command that will create a new user account with administrative privileges, or a script that will download and execute a malicious payload.

## Use Runas to run the vulnerable program
Once you have identified a vulnerable program and created a payload, you can use Runas to run the program as the higher-privileged user account. To do this, open a command prompt and enter the following command:

```
runas /user:<higher-privileged user account> <vulnerable program>

```
Replace <higher-privileged user account> with the name of the higher-privileged user account, and <vulnerable program> with the path to the vulnerable program.

When you run this command, you will be prompted to enter the password for the higher-privileged user account. After entering the password, the vulnerable program will run with elevated privileges