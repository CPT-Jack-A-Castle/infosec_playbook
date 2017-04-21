## ID: 600001

## INV

## Source: IDS

## Category: Suspect

## Description: Attack may have escape the restrict Python shell and gained linux shell

## Objective Statement:
The VOIP server was running a python shell which would allow administrators to issue commands remotely and users to connect to run python scripts and commands. This alert was triggered because commands that can be used to obtain root shell access were detected.
With a root shell the attacker can execute anything they want, as they have full privileges as the root user. Python allows the "os" library to execute linux and windows commands depending on the operating system running underneath. Commands will be execute with whatever privilege the python shell is running with.

## Result Analysis:
This alert was triggered because commands to create shell access were executed.  This play requires an investigation to see if the suspected attacker connected to a root shell. Investigate the systems authorization log, /var/log/auth.log.
There are primarily 2 ways the attacker can gain shell access. The first is to add their own SSH key to the authorized_keys file of root user, or any other user. The second is to run system command to create a netcat socket to connect to an attacker, or listen for an attacker to connect.

Checking IDS for SSH login alerts, and checking /var/log/messages and ssh logs will help determine if an attacker connected.  
Check the /home/<user>/ and /root/   .ssh/authorized_keys will reveal when it was last edited, and any unwanted keys.  
If the attack is suspected to still be running check all ports for traffic.  


Sample netcat listener
```bash
import os
print(os.system("bash -c 'ncat -l -p 10023 -e /bin/bash &'" ))
```

Sample of attacker adding SSH key
```
import os
print(os.system("bash -c 'echo \"ssh-rsa <redcated SSH KEY > root@kali\" >> /root/.ssh/authorized_keys'" ))
print(os.system("bash -c 'service sshd restart'" ))
```


*References for Futher Learning*
- http://www.pythonforbeginners.com/os/subprocess-for-system-administrators
- https://docs.python.org/2/library/commands.html
- https://unix.stackexchange.com/questions/238180/execute-shell-commands-in-python

## Mitigation
- Do not run the python shell as root
- Require authentication to use the shell
- Turn off the python shell, create accounts for users to ssh with, and then use python.
- Get users to install python on their own machines
- Prevent the running of system commands by python.

## Data Query Code
- escape python shell
- ssh public key
- netcat listener
