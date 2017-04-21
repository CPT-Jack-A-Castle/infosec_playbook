## ID: 500002

## HF

## Source: IDS

## Category: suspect

## Description:  SSH Brute Force

## Objective Statement:
This play is for the event an attack gains remote SSH access.  SSH can be brute forced by simply throwing thousands of user credentials at it until gains access.  Weak passwords and poor configuration are a threat to security. If an attack gets SSH access they have the full privileges of the account they gained access to. They can potentially get root access and do anything they want on the server.  This alert was triggered becuase many failed login attempts were detected.

## Result Analysis:
The SSH service has a poor configuration, it allows unlimited login attempts for any user. Access logs in /var/log/auth.log should be analyzed to determine if the attacker gained access. The SSH configuration files should be changed to allow a small number of maximum attempts before blocking login.  Password authentication can also be turned off so that the administrator of the DNS server can only authorize SSH keys. This would require the administrator manually adding the keys for approved access.
If a login attempt was successful the system is compromised, ideally it should be rebuild, wiping the operating system and starting from scratch.  To see what the attacker did the auth.log file will contain any commands execute as root, the user the attacker logged in has a bash history, which can be checked, as long as it was not cleared or deleted. 

*References for Futher Learning*
- http://www.cisco.com/c/en/us/support/docs/security-vpn/secure-shell-ssh/4145-ssh.html
- https://linux.die.net/man/5/ssh_config
- https://www.digitalocean.com/community/tutorials/how-to-configure-custom-connection-options-for-your-ssh-client


## Mitigation
- See the suggestions in the Result Analysis
- Implement maximum log in attempts
- Disable root login if it is enabled for SSH
- Require certain password strenght 
- Implement password policy
- Do not use same passwords across multiple machines

## Data Query Code
- ssh brute force
- multiple failed logins
