## ID: 800001

## INV

## Source: IPS

## Category: Suspect Event

## Description:
Suspected SQL Injection detected

## Objective Statement
Characters commonly used in SQL Injection have been detected as entered by a user where this is not considered normal activity.

These characters may have been enthered through a user-input form or used as parameters in a URL.


SQL Injection allows attackers to obtain information from a database. This data can include anything stored in a database such as  user credentials like usernames and passwords. SQL Injection can also be used to bypass authentication.  Given the right conditions SQL Injection can allow an attacker to execute system commands, and alter the database by inserting or deleting content.


## Result Analysis

To investigate whether SQL injection has occured review web server logs and database query logs.  Database query logs would have malformed queries where the original intended query was modified and likely comment end parts of the query.
In Web server logs look for POST request data submitted to the web server that contains the suspect characters, also look for GET requests that have parameters containing suspected characters.

Examples of suspcious characters include:

```bash
'
"
`
;
=
-- 
#
/
*


%27
%22
%60
%3B
%3D
%23
%2F
%00
%16
```

*References for Futher Learning*

- https://www.owasp.org/index.php/SQL_Injection
- http://php.net/manual/en/security.database.sql-injection.php


## Mitigation

- Filter and sanitize user input 
- Use a Web Application Firewall to detect and stop attack attempts
- Use a block feature of an IDS/IPS for suspected SQLi attack traffic
- Use parametered queries in SQL
- Create another SQL account that has limited permissions on the specific table or database so another databases and tables cannot be attacked
- https://www.owasp.org/index.php/SQL_Injection_Prevention_Cheat_Sheet

## Data Query Code
- SQL injection
- SQLi
- database
- MySQL PHP




