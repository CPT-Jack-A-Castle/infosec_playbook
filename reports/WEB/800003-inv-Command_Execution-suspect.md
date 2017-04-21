## ID: 800003

## INV

## Source: IDS

## Category: Suspect Event

## Description: A suspect attacker may have been able to execute system commands.

## Objective Statement:
This alert will be generated is special characters that are used to inject commands are detected. If an attacker is able to execute system commands they effectively have shell access to execute commands with the same permissions as the web daemon (web service).
The attacker can use this to gain information about the system, exfiltrate sensitive data and even get a live shell or escalate privileges.

## Result Analysis:

Characters such as `;` and `&&` have been detected in user-input when they were not expected.  These characters can be used to alert functionality and pass commands to the system for execution.  This can also be in a URL paramter.

Sample Command Execution:

 A form asks users to input a website to ping to check if it is online. Malicious user input could look like:
```bash
dpi911.com ; uname -a

google.com ; ls -al

facebook.com ; cat /etc/passwd
```

URL parameters can look like 

```bash
https://www.dpi911.com/dvwa/commandinject.php?id=1; ls -al 
```

*References for Futher Learning*
- https://www.owasp.org/index.php/Top_10_2013-A1-Injection
- https://www.owasp.org/index.php/Injection_Flaws

## Mitigation
- Filter and sanitize user input
- Avoid sending sensitive data by URL parameters
- Use Web Application Firewall to detect and block
- https://www.owasp.org/index.php/Injection_Prevention_Cheat_Sheet

## Data Query Code
- Remote code / command execution
- command injection
- code injection