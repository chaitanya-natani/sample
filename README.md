# Runbook for Initial Cluster Configuration on Cloud oneFS

Below are the steps that need to be performed manually in order to provide the minimal configuration needed to access the cluster and proceed. These steps can be followed exclusively on the console.

Upon successful installation of Isilon OneFS, the user will receive a sequence of prompts as shown below: 
```sh
Welcome to the Isilon IQ configuration wizard.
Copyright (c) 2001-2020 Dell Inc. All Rights Reserved.
Enter 'help' at any prompt for additional information on that step.
Enter 'back' at any prompt to return to previous step.
Enter 'quit' at any prompt to discard all changes.
Enter 'manual' at any prompt to switch to manual mode (console).

	Node build: Isilon OneFS 9.1.0.14 B_9_1_0_003(RELEASE) 
	Node serial number: SV200-153267-4182

Select an option:
	[ 1] Create a new cluster
	[ 2] Join an existing cluster
	[ 3] Exit wizard and configure manually
	[ 4] Reboot into SmartLock Compliance mode
Wizard >>>
```
Type in `1`, and press `enter` to continue creating a new cluster. Next,

```sh
*** IMPORTANT INFORMATION - PLEASE READ CAREFULLY ***

Congratulations on your new Dell EMC purchase!

Your purchase and use of this Dell EMC product is subject to and governed
by the Dell EMC Commercial Terms of Sale, unless you have a separate written agreement with Dell EMC that specifically applies to your order, and the End User License Agreement (E-EULA), which are each presented below in the following order:

*       Commercial Terms of Sale
*       End User License Agreement (E-EULA)

The Commercial Terms of Sale for the United States are presented below and
are also available online at the website below that corresponds to the country in which this product was purchased.

By the act of clicking "I accept," you agree (or re-affirm your agreement to) the foregoing terms and conditions.  To the extent that Dell Inc. or any Dell Inc. direct or indirect subsidiary ("Dell") is deemed under applicable law to have accepted an offer by you: (a) Dell hereby objects to and rejects all additional or inconsistent terms that may be contained in any purchase order or other documentation submitted by you in connection with your order; and (b)
--More--(2%)



Do you accept the EULA? [no]
```

Type in `yes` and press `enter` to continue.

```sh
Please change the root password from the default.
Please enter new password for root:
```

Type in appropriate new password, and press `enter` to continue.

```sh
Please re-enter password for root: 
```

Re-type the password, and press `enter` to continue.

```sh
Password changed.

Please change the UI admin password from the default.
Please enter new password for admin:
```

Type in appropriate new password for UI admin, and press `enter` to continue.

```sh
Please re-enter password for admin:
```

Re-type the password, and press `enter` to continue.

```sh
Password changed.


Enter a new name for the cluster:
Configure name >>>
```

Type in the appropriate cluster name, (note: in this example runbook we are using cluster name as `vonefs-black-canary`). Press `enter` to continue.

```sh
!! WARNING: Limit cluster name to 11 characters or less when the
!! NetBIOS Name Service is enabled to avoid name truncation. Isilon
!! uses up to 4 characters for individual node names.

Proceed with cluster name vonefs-black-canary? [yes]
```

Type in `yes` and press `enter` to continue.

```sh
Cluster name set to vonefs-black-canary

Cluster encoding:
	[ 1] Windows-SJIS
	[ 2] Windows-949
	[ 3] Windows-1252
	[ 4] EUC-KR
	[ 5] EUC-JP
	[ 6] EUC-JP-MS
	[ 7] UTF-8-MAC
	[ 8] UTF-8
	[ 9] ISO-8859-1 (Latin-1)
	[10] ISO-8859-2 (Latin-2)
	[11] ISO-8859-3 (Latin-3)
	[12] ISO-8859-4 (Latin-4)
	[13] ISO-8859-5 (Cyrillic)
	[14] ISO-8859-6 (Arabic)
	[15] ISO-8859-7 (Greek)
	[16] ISO-8859-8 (Hebrew)
	[17] ISO-8859-9 (Latin-5)
	[18] ISO-8859-10 (Latin-6)
	[19] ISO-8859-13 (Latin-7)
	[20] ISO-8859-14 (Latin-8)
	[21] ISO-8859-15 (Latin-9)
	[22] ISO-8859-16 (Latin-10)
	[Enter] Use current encoding: utf-8
Configure encoding >>>
```

Type in `8` and press `enter` to continue.

```sh
Encoding set to utf-8

Configure interface int-a:
	[ 1] Configure netmask
	[ 2] Configure MTU
	[ 3] Configure int-a IP ranges
	[Enter] Keep the current configuration:
	           Netmask: (not set)
	               MTU: 1460 (shared)
	         IP ranges: (not set)
Configure interface int-a >>>
```

Type in `1`, and press `enter` to continue.

```sh
Enter a new netmask
Configure int-a netmask >>>
```

Type in the appropriate netmask, (note: in this example runbook we are using netmask as `255.255.248.0`), and press `enter` to continue.

```sh
Configure interface int-a:
	[ 1] Configure netmask
	[ 2] Configure MTU
	[ 3] Configure int-a IP ranges
	[Enter] Keep the current configuration:
	           Netmask: 255.255.248.0
	               MTU: 1460 (shared)
	         IP ranges: (not set)
Configure interface int-a >>>
```

Type in `3`, and press `enter` to continue.

```sh
Configure int-a IP ranges
	[ 1] Add an IP range
	[ 2] Delete an IP range
	[Enter] Keep the current IP ranges:
	         IP ranges: (not set)
Configure int-a IP ranges >>>
```

Type in `1`, and press `enter` to continue.

```sh
Enter the low IP address of the range to add:
Low IP address (add) >>>
```

Type in appropriate low IP address, (note: in this example runbook we are using low IP address as: `10.3.104.2`), and press `enter` to continue.

```sh
Enter the high IP address of the range:
High IP address (add) >>>
```

Press `enter` to continue.

```sh
Configure int-a IP ranges
	[ 1] Add an IP range
	[ 2] Delete an IP range
	[Enter] Keep the current IP ranges:
	         IP ranges: 10.3.104.2-10.3.104.2
Configure int-a IP ranges >>>
```

Press `enter` to continue.

```sh
Configure interface int-a:
	[ 1] Configure netmask
	[ 2] Configure MTU
	[ 3] Configure int-a IP ranges
	[Enter] Keep the current configuration:
	           Netmask: 255.255.248.0
	               MTU: 1460 (shared)
	         IP ranges: 10.3.104.2-10.3.104.2
Configure interface int-a >>>
```

Press `enter` to continue.

```sh
Configure external subnet
	[ 1] ext-1 - External interface
	[ 2] Use internal interface for external subnet
	[Enter] Exit configuring external network.
Configure external subnet >>>
```

Type in `1`, and press `enter` to continue.

```sh
Configure interface ext-1:
	[ 1] Configure netmask
	[ 2] Configure MTU
	[ 3] Configure ext-1 IP ranges
	[Enter] Keep the current configuration:
	           Netmask: (not set)
	               MTU: 1500
	         IP ranges: (not set)
Configure interface ext-1 >>>
```
Type in `1`, and press `enter` to continue.

```sh
Enter a new netmask
Configure ext-1 netmask >>>
```

Type in appropriate netmask, (note: in this example runbook we are using netmask as: `255.255.248.0`), and press enter to continue.

```sh
Configure interface ext-1:
	[ 1] Configure netmask
	[ 2] Configure MTU
	[ 3] Configure ext-1 IP ranges
	[Enter] Keep the current configuration:
	           Netmask: 255.255.248.0
	               MTU: 1500
	         IP ranges: (not set)
Configure interface ext-1 >>>
```

Type in `3`, and press `enter` to continue.

```sh
Configure external IP ranges
	[ 1] Add an IP range
	[ 2] Delete an IP range
	[Enter] Keep the current IP ranges:
	         IP ranges: (not set)
Configure ext-1 IP ranges >>>
```

Type in `1`, and press `enter` to continue.

```sh
Enter the low IP address of the range to add:
Low IP address (add) >>>
```

Type in appropriate low IP address, (note: in this example runbook we are using low IP address as: `10.3.96.2`), and press `enter` to continue.

```sh
Enter the high IP address of the range:
High IP address (add) >>>
```

Press `enter` to continue.

```sh
Configure external IP ranges
	[ 1] Add an IP range
	[ 2] Delete an IP range
	[Enter] Keep the current IP ranges:
	         IP ranges: 10.3.96.2-10.3.96.2
Configure ext-1 IP ranges >>>
```

Press `enter` to continue.

```sh
Configure interface ext-1:
	[ 1] Configure netmask
	[ 2] Configure MTU
	[ 3] Configure ext-1 IP ranges
	[Enter] Keep the current configuration:
	           Netmask: 255.255.248.0
	               MTU: 1500
	         IP ranges: 10.3.96.2-10.3.96.2
Configure interface ext-1 >>>
```

Press `enter` to continue.

```sh
Enter default gateway:
Configure default gateway >>>
```

Type in appropriate default gateway, (note: in this example runbook we are using gateway as `10.3.96.1`), and press `enter` to continue.

```sh
Configure SmartConnect settings
	[ 1] SmartConnect zone name
	[ 2] SmartConnect service IP
	[Enter] Keep the current SmartConnect settings:
	SmartConnect zone name: (not set)
	 SmartConnect service IP: (not set)
Configure SmartConnect settings >>>
```

Type in `1`, and press `enter` to continue.

```sh
Enter SmartConnect zone name
SmartConnect zone name >>>
```

Type in appropriate SmartConnect zone name, (note: in this example runbook we are using `black-canary.onefs`), and press `enter` to continue.

```sh
Configure SmartConnect settings
	[ 1] SmartConnect zone name
	[ 2] SmartConnect service IP
	[Enter] Keep the current SmartConnect settings:
	SmartConnect zone name: black-canary.onefs
	 SmartConnect service IP: (not set)
Configure SmartConnect settings >>>
```
Type in `2`, and press `enter` to continue.

```sh
Enter SmartConnect service IP
SmartConnect service IP >>>
```

Type in appropriate service IP, (note, in this example runbook we are using `10.3.96.3` as service IP), and press `enter` to continue.

```sh
Configure SmartConnect settings
	[ 1] SmartConnect zone name
	[ 2] SmartConnect service IP
	[Enter] Keep the current SmartConnect settings:
	SmartConnect zone name: black-canary.onefs
	 SmartConnect service IP: 10.3.96.3
Configure SmartConnect settings >>>
```

Press `enter` to continue.

```sh
Configure DNS settings
	[ 1] DNS servers
	[ 2] Search domains
	[Enter] Keep current DNS settings:
	     DNS servers: (not set)
	  Search domains: (not set)
Configure DNS settings >>>
```

Press `enter` to continue.

```sh
Configure external subnet
	[ 1] ext-1 - External interface
	[ 2] Use internal interface for external subnet
	[Enter] Exit configuring external network.
Configure external subnet >>>
```

Press `enter` to continue.

```sh
Configure cluster date and time
	[ 1] Configure time zone
	[ 2] Configure day and time
	[Enter] Keep the current date and time: 2023/03/15 10:04:32 GMT.
Configure date >>> 
```

Press `enter` to continue.

```sh
Configure cluster join mode
	[ 1] Manual
	[ 2] Secure
	[Enter] Keep the current join mode: Manual
Configure join mode >>>
```

Type in `1`, and press `enter` to continue.

```sh
Join mode set to Manual.
You have made the following configuration changes:

Cluster name           : (not set) -> vonefs-black-canary
Encoding               : (not set) -> utf-8
int-a netmask          : (not set) -> 255.255.248.0
int-a IP ranges        : (not set) -> { 10.3.104.2-10.3.104.2 }
ext-1 netmask          : (not set) -> 255.255.248.0
ext-1 IP range         : (not set) -> { 10.3.96.2-10.3.96.2 }
ext-1 gateway          : (not set) -> 10.3.96.1
SmartConnect zone name : (not set) -> black-canary.onefs
SmartConnect service IP: (not set) -> 10.3.96.3

Do you wish to commit these changes? [yes]
Commit changes? >>>
```

Type in `yes`, and press `enter` to finish the initial setup wizard.
