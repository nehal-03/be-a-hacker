# Downloading Files:

## Using `wget` :
`wget https://assets.tryhackme.com/additional/linux-fundamentals/part3/myfile.txt` 

`scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt`
- SCP: Secure copy
- IP address of the remote system: 192.168.1.30
- User on the remote system:	ubuntu
- Name of the file on the remote system:	documents.txt
- Name that we wish to store the file as on our system:	notes.txt

## Using **_Python3 web server_** :
Ubuntu machines come pre-packaged with python3. Python helpfully provides a lightweight and easy-to-use module called "HTTPServer". This module turns your computer into a quick and easy web server that you can use to serve your own files, where they can then be downloaded by another computing using commands such as `curl` and `wget`. 

Python3's "HTTPServer" will serve the files in the directory that you run the command, but this can be changed by providing options that can be found in the manual pages. Simply, all we need to start the module is 
`run python3 -m  http.server` 

 [Watch Dog](https://github.com/sc0tfree/updog) : A more advanced yet lightweight webserver. 

# Processes in Linux:
### Processes have ids known as PID.

## Viewing Processes

We can use the friendly `ps` command to provide a list of the running processes as our user's session and some additional information such as 
  - its status code, 
  - the session that is running it, 
  - how much usage time of the CPU it is using, 
  - and the name of the actual program or command that is being executed.

To view system process use `ps aux`.

[Top command](https://linuxhint.com/top_-command-_linux/) : Gives you real-time statistics about the processes running on your system instead of a one-time view.

## Managing Processes
To kill a command, we can use the appropriately named `kill` command and the associated PID that we wish to kill. i.e., to kill PID 1337, we'd use _kill 1337_.

Below are some of the signals that we can send to a process when it is killed:
  - SIGTERM - Kill the process, but allow it to do some cleanup tasks beforehand
  - SIGKILL - Kill the process - doesn't do any cleanup after the fact
  - SIGSTOP - Stop/suspend a process

The process with an ID of 0 is a process that is started when the system boots. 
This process is the system's `init` on Ubuntu, such as systemd, which is used to provide a way of managing a user's processes and sits in between the operating system and the user. 

For example, once a system boots and it initialises, **_systemd_** is one of the first processes that are started. Any program or piece of software that we want to start will start as what's known as a child process of systemd. 

This means that it is controlled by systemd, but will run as its own process (although sharing the resources from systemd) to make it easier for us to identify and the likes.

## Getting Processes/Services to Start on Boot

Some applications can be started on the boot of the system that we own. For example, web servers, database servers or file transfer servers. This software is often critical and is often told to start during the boot-up of the system by administrators.

In this example, we're going to be telling the apache web server to be starting apache manually and then telling the system to launch apache2 on boot.

Enters the use of `systemctl` -- this command allows us to interact with the systemd process/daemon. Continuing on with our example, systemctl is an easy to use command that takes the following formatting: `systemctl [option] [service]`

For example, to tell apache to start up, we'll use systemctl start apache2. Seems simple enough, right? Same with if we wanted to stop apache, we'd just replace the [option] with stop (instead of start like we provided)

We can do four options with systemctl:
 - Start
 - Stop
 - Enable
 - Disable

# Backgrounding and Foregrounding in Linux:
 `echo` is the only command provided that hasn't been told to run in the background.
 > Using & after the echo command will retun ID of the echo process rather than the actual output as it is running in the background.
 > This is great for commands such as copying files because it means that we can run the command in the background and continue on with whatever further commands we wish to execute.

Rather than relying on the `&` operator, we can use `Ctrl + Z` on our keyboard to background a process. It is also an effective way of "pausing" the execution of a script or command.

With our process backgrounded using either `Ctrl + Z` or the `&` operator, we can use fg to bring this back to focus like below, where we can see the `fg` command is being used to bring the background process back into use on the terminal, where the output of the script is now returned to us.

# Maintaining Your System: Automation

We're going to be talking about the cron process, but more specifically, how we can interact with it via the use of crontabs . Crontab is one of the processes that is started during boot, which is responsible for facilitating and managing cron jobs.

A crontab is simply a special file with formatting that is recognised by the cron process to execute each line step-by-step. Crontabs require 6 specific values:

Value	Description:
```
MIN	What minute to execute at
HOUR	What hour to execute at
DOM	What day of the month to execute at
MON	What month of the year to execute at
DOW	What day of the week to execute at
CMD	The actual command that will be executed.

0 *12 * * * cp -R /home/cmnatic/Documents /var/backups/
```
If we do not wish to provide a value for that specific field, i.e. we don't care what month, day, or year it is executed -- only that it is executed every 12 hours, we simply just place an asterisk `*`.

Crontabs can be edited by using `crontab -e`, where you can select an editor (such as Nano) to edit your crontab.

TryHackMe rooms that are dedicated to Linux tools or utilities:

The find command - https://tryhackme.com/room/thefindcommand
Bash Scripting - https://tryhackme.com/room/bashscripting
Regular Expressions - https://tryhackme.com/room/catregex





