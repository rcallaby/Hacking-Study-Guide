# jaws-enum

JAWS-ENUM is a network penetration testing tool designed to perform information gathering tasks against a target network or host. It is specifically built to extract information such as domain names, usernames, IP addresses, and other details that can be useful in further stages of penetration testing.

In this article, we'll take a closer look at JAWS-ENUM and discuss what it does, how it works, and provide some examples of how to use it.

## What is JAWS-ENUM?

JAWS-ENUM is an open-source tool developed in Python that is used for reconnaissance and information gathering. It is designed to extract valuable information about a target network or host, which can be used in further stages of penetration testing.

The tool is based on the DNS enumeration technique, which involves querying different DNS servers to extract domain names, subdomains, IP addresses, and other related information. JAWS-ENUM uses a combination of techniques such as brute-forcing, dictionary attacks, and zone transfers to extract information from the DNS servers.

## How does JAWS-ENUM work?

JAWS-ENUM works by performing the following steps:

DNS enumeration: JAWS-ENUM queries different DNS servers to extract information about the target network or host. It tries to extract information such as domain names, subdomains, IP addresses, and other related information.

Zone transfers: If the target DNS server allows zone transfers, JAWS-ENUM performs zone transfers to extract more detailed information about the target network or host.

Brute-forcing: JAWS-ENUM performs brute-force attacks to extract information such as usernames and passwords.

Dictionary attacks: JAWS-ENUM also performs dictionary attacks to extract information such as usernames, passwords, and email addresses.

Port scanning: JAWS-ENUM can also perform port scanning to identify open ports and services running on the target network or host.

Examples of how to use JAWS-ENUM

Let's take a look at some examples of how to use JAWS-ENUM:

Example 1: Extracting subdomains

The following command can be used to extract subdomains of a target domain:

```
jaws-enum.py --domain example.com --subdomains

```
This command will query different DNS servers to extract subdomains of the example.com domain.

Example 2: Performing zone transfers

The following command can be used to perform zone transfers of a target domain:

```
jaws-enum.py --domain example.com --zonetransfer

```
This command will perform zone transfers of the example.com domain to extract more detailed information about the target network or host.

Example 3: Performing brute-force attacks

The following command can be used to perform brute-force attacks to extract information such as usernames and passwords:

```
jaws-enum.py --domain example.com --brute

```
This command will perform brute-force attacks to extract information such as usernames and passwords from the target network or host.

Example 4: Performing dictionary attacks

The following command can be used to perform dictionary attacks to extract information such as usernames, passwords, and email addresses:

```
jaws-enum.py --domain example.com --dictionary

```
This command will perform dictionary attacks to extract information such as usernames, passwords, and email addresses from the target network or host.

JAWS-ENUM is a useful tool for reconnaissance and information gathering during a penetration testing engagement. It can be used to extract valuable information such as domain names, subdomains, IP addresses, and other related details. It is a versatile tool that can perform brute-force attacks, dictionary attacks, and zone transfers to extract information about the target network or host.