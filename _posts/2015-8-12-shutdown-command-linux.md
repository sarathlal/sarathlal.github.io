---
title:  The shutdown command in Linux
layout: post
tags:
  - Linux
  - Linux Commands
  - Ubuntu
---

In Linux OS, we have simple graphical user interface to shutdown the systems. But the flexibility of shutdown command is more awesome and it is too useful in many situations.

The shutdown command brings the system down in a secure way. All logged-in users are notified that the system is going down, and login operations are blocked. Also all the running processes are notified that the system is going to down by the signal SIGTERM. This will help to save the files and stop the running processes.

The main attarction of the shut down command was it is possible to shut the system down immediately, or after a specified delay.

When we enter shutdown command, it will signalling the `init` process to change the current runlevel. The runlevel 0 means halt the system, runlevel 6 means reboot the system, and runlevel 1 make the system into a state where administrative tasks can be performed. Runlevel 1 is the default, unless the `-h` or `-r` options are specified.

	shutdown [-akrhPHfFnc] [-t sec] time [message]

### Options

* `-a` -	Control access to the shutdown command using the control access file /etc/shutdown.allow.
* `-k` -	Do not shut down, but send the warning messages as if the shutdown were real.
* `-r` -	Reboot after shutdown.
* `-h` -	Instructs the system to shut down and then halt.
* `-P` -	Instructs the system to shut down and then power down.
* `-H` -	If `-h` is also specified, this option instructs the system to drop into boot monitor on systems that support it.
* `-f` -	Skip `fsck` after reboot. ( The `fsck` is a program run on Linux, Unix, and their variants that checks the file system for any errors )
* `-F` -	Force `fsck` after reboot.
* `-n` -	Don't call `init` to do the shutdown of processes; instruct shutdown to do that itself. ( The use of this option is discouraged, and its results are not always predictable.)
* `-c` -	Cancel a pending shutdown. With this option, it is not possible to give the time argument, but you can still specify an explanatory message that will be sent to all users.
* `-t sec` -	Tell `init` to wait sec seconds between sending processes the warning and the kill signal, before changing to another runlevel.
* `time` -	The time argument specifies when to perform the shutdown operation.

	The time can be formatted in different ways:

	1. It can be an absolute time in the format hh:mm. The `hh` is the hour (1 or 2 digits, from 0 to 23) and `mm` is the minute of the hour (in two digits).
	2. It can be in the format +m, in which m is the number of minutes to wait.
	3. The word `now` is the same as specifying +0; it shuts the system down immediately.

* message	- A message to be sent to all users, along with the standard shutdown notification.

### Halting vs. Powering Off

The `halt` instructs the hardware to stop all CPU functions. That means, it stops the machine, leaving it in a powered-on state (which usually implies that someone has to reboot or shut it down manually afterwards)

But the `poweroff` sends an `ACPI` signal which instructs the system to power down. That means it first stop all CPU functions and then give signal to power down.

### Examples

	shutdown 8:00
	
Schedule the system to shut down at 8 A.M.

	shutdown -P 8:00

Schedule the system to shut down & power off at 8 A.M.

	shutdown 20:00

Schedule the system to shut down at 8 P.M.

	shutdown -P 20:00

Schedule the system to shut down & power off at 8 P.M.

	shutdown +15 "Upgrading hardware, downtime should be minimal"

Schedule the system to shut down in fifteen minutes. Along with the normal message alerting users that the system is shutting down, they will be given the descriptive message about a hardware upgrade.

	shutdown now

Bring down the system immediately.

	shutdown -r now

Bring down the system immediately, and automatically reboot it.

	shutdown -P now

Bring down the system immediately, and automatically power off the system.
