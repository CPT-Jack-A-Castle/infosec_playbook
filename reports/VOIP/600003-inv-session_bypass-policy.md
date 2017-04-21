## ID: 600003

## INV

## Source: IDS

## Category: Policy

## Description: PHP session bypass

## Objective Statement:
In this attack a user was able to escalate privileges of their session on the web portal for the VOIP software by issuing a simple command.

## Result Analysis:
By using the python shell, or the netcat shell from previous plays simply entering in a command with the session ID upgrades the session from a regular user to a administrator account. From there the attack has fully compromised the VOIP software. They can intercept calls by disabling encryption, add and remove users, change other account privileges, change passwords, and alert many other settings.
The VOIP service should be considered fully compromised and needs to be reinstalled from scratch.  Check apache logs to see what the attacker did on the website, check authorization logs to see how the attacker issued the commands, such as through ssh, or the netcat shell.


Noticed attempts to login to this service found below:
```
192.168.1.250 - - 10/Apr/2017:10:37:38 -0400? "GET /admin/assets/less/cache/lessphp_bb505981b0e6e7b6f787d3f3575a6b06c43faa24.css 
HTTP/1.1" 200 143547 "http://192.168.1.61/admin/config.php?display=cli" 
"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit?/537.36 (KHTML, like Gecko) Chrome/55.0.2883.87 Safari/537.36"
```

## Mitigation
- Do not allow for command line access without authentication 
- Upgrade the online portal if it is not the latest version
- If possible switch portals, or disable the portal all together as it is riddled with many security flaws
- Time more time to configure the web portal if there is no other options and it is required

## Data Query Code
- PHP sessions bypass
- privilege escalation
- open backdoors
