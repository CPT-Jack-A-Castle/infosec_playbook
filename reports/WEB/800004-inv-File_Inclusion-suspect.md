## ID: 800004

## INV

## Source: IDS 

## Category: Suspect Event

## Description: A file not intended to be displayed has been included and potentially displayed on a webpage.

## Objective Statement:
File inclusion can be achieved through a few different ways such as PHP Inclusion and Directory Traversal. An attacker can use file inclusion methods to gather information from the system and exfiltrate data.  Any file that the web daemon (web service) has read permissions can be accessed if the web site is vulnerable to this type of attack.
If the attacker can access web configuration files the attacker may be able to gather database credentials, and find settings that may expose other security weaknesses.


## Result Analysis:

**1. PHP Inclusion**
A common way for PHP to display a page called index.php would be like so:
```
www.dpi911.com/?page=index.php
```
Similarly a login page would look like:
```
www.dpi911.com/?page=login.php
```

An attacker can change this in the URL to include files not intended to be displayed.

```
www.dpi911.com/?page=/etc/passwd
```

**2. Directory Traversal**

Websites commonly use the following way to display index.html.
```
www.dpi911.com/index.html
```

An attacker can change the URL to include other files.

```
www.dpi911.com/../../../../etc/passwd
```

*References for Futher Learning*
- https://www.owasp.org/index.php/Testing_for_Local_File_Inclusion
- https://www.offensive-security.com/metasploit-unleashed/file-inclusion-vulnerabilities/
- http://hakipedia.com/index.php/Local_File_Inclusion
- https://www.owasp.org/index.php/Path_Traversal
- https://www.owasp.org/index.php/Testing_Directory_traversal/file_include_(OTG-AUTHZ-001)


## Mitigation
- Restrict permissions the web server daemon has so it cannot access important files
- Proper input sanitizing
- Avoid PHP File inclusion techniques
- Use Web Application Firewall to detect and block
- https://www.incapsula.com/web-application-security/rfi-remote-file-inclusion.html

## Data Query Code
- Local File Inclusion
- PHP File inclusion
- file bypass
- data exfiltration